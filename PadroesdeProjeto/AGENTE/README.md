
# GitHub Onboarding Agent

Um agente de IA que acompanha um desenvolvedor aprendendo Git e GitHub. Ele **ensina os
conceitos, monta um plano, executa operações Git de verdade, observa o resultado e decide o
próximo passo**. Quando não tem certeza do que fazer, para e pergunta ao usuário em vez de
chutar.

Projeto acadêmico da disciplina de **Padrões de Projeto** da FATEC. O foco é a arquitetura:
cinco padrões GoF trabalhando juntos **no mesmo fluxo de execução**.

---

## O que o agente faz

O usuário escreve um objetivo em linguagem natural, por exemplo:

> "Quero criar uma branch feature/login"
> "Quero enviar minha alteração para revisão"

O agente então:

1. **Planeja** os passos com um LLM local (ex.: `gitStatus` → `gitBranch` → `gitCheckout`).
2. **Executa** cada passo no repositório Git de trabalho.
3. **Observa** o resultado e decide: continuar, replanejar, pedir ajuda ao humano ou falhar.
4. **Ensina** pelo caminho, consultando uma base de conhecimento sobre Git/GitHub.
5. **Pede aprovação** antes de qualquer ação sensível, como abrir um pull request.

Se o pedido for vago ("Arruma aí o meu repositório"), se o plano vier com baixa confiança
ou se os comandos falharem repetidamente, o agente **troca de estratégia em tempo de
execução** e passa a conduzir a conversa com o usuário (Human-in-the-Loop).

---

## Arquitetura: os cinco padrões

> Strategy planeja · State avança · Command executa · Observer testemunha · Composite mostra

| Padrão | Papel no projeto | Classes principais |
|---|---|---|
| **Strategy** | Escolhe e troca o planejador em runtime | `ReActStrategy`, `PlanThenExecuteStrategy`, `HumanInTheLoopStrategy`, `StrategySelector` |
| **State** | Controla as fases da tarefa | `InitState`, `PlanningState`, `ExecutingState`, `ObservingState`, `WaitingApprovalState`, `ErrorState`, `CompletedState`, `AgentStateMachine` |
| **Command** | Encapsula cada ferramenta que o agente pode usar | `GitStatus`, `GitBranch`, `GitCheckout`, `GitAdd`, `GitCommit`, `GitPush`, `CreatePullRequest`, `KnowledgeSearch` + `CommandInvoker` |
| **Observer** | Registra a trilha de raciocínio, erros e progresso | `AgentEventPublisher` (implementado à mão), `TraceObserver`, `ErrorObserver`, `ProgressObserver`, `GuiObserver` |
| **Composite** | Monta a interface gráfica como uma árvore de painéis | `UIComponent`, `UIComposite`, `GoalPanel`, `PlanPanel`, `StatePanel`, `TraceLogPanel`, `ProgressPanel`, `ApprovalPanel` |

Fluxo de estados:

```
INIT → PLANNING → EXECUTING → OBSERVING ─┬─ CONTINUE → EXECUTING
                                          ├─ REPLAN   → PLANNING
                                          ├─ ESCALATE → WAITING_APPROVAL → PLANNING
                                          └─ FAIL     → ERROR
                                                     └→ COMPLETED
```

Os diagramas UML (classes, sequência e estados) estão em `docs/`.

---

## Ferramentas e tecnologias

| Categoria | Ferramenta | Uso no projeto |
|---|---|---|
| Linguagem | **Java 21** | records, sealed interfaces, pattern matching |
| Framework | **Spring Boot 3.4.5** | injeção de dependência e configuração |
| IA | **Spring AI 1.0.0** | `ChatClient` para o LLM e `SimpleVectorStore` para o RAG |
| LLM local | **llama.cpp** + **Gemma 2 (2B)** | modelo aberto rodando na máquina, via API compatível com OpenAI |
| Git | **JGit 6.10** | executa as operações Git direto do Java |
| GitHub | **API REST do GitHub** (`RestClient`) | abre pull requests |
| Interface | **Swing** | janela gráfica (também existe modo console) |
| Build | **Maven** | build, dependências e testes |
| Testes | **JUnit 5** + **AssertJ** | 86 testes que rodam sem o LLM |
| Documentação | **PlantUML** | diagramas de classes, sequência e estados |

Nenhum serviço pago é necessário: o modelo roda localmente, e o GitHub só é usado para
abrir pull requests.

---

## Como rodar

```bash
# 1. Suba o modelo local
llama-server -m gemma-2-2b-it-Q4_K_M.gguf --port 8080 -c 4096

# 2. Crie um repositório de teste para o agente operar
mkdir -p ~/agent-workspace && cd ~/agent-workspace && git init
echo "# teste" > README.md && git add . && git commit -m "commit inicial"

# 3. Rode o agente
mvn spring-boot:run                                               # modo console
mvn spring-boot:run -Dspring-boot.run.arguments=--agent.ui=swing  # janela Swing

# Testes
mvn test
```

As configurações ficam em `src/main/resources/application.yml` (workspace, limites de
tentativas, limiar de confiança e dados do GitHub).

---

## Minha contribuição: escolha e integração do modelo de IA
 
Fiquei responsável por **escolher o modelo de linguagem** que o agente usa e por
**integrá-lo ao projeto**. Isso inclui o caminho inteiro entre o código Java e o LLM.
 
**A escolha do modelo:**
 
- **Requisitos:** o modelo tinha que ser **aberto** e **rodar localmente na máquina da
  FATEC**, sem serviço pago nem chave de API. A regra que adotei foi usar o menor modelo
  que desse conta da tarefa.
- **Candidatos avaliados:** Gemma 2 (2B e 4B) e Qwen 3. Escolhi o **Gemma 2 2B Instruct**
  quantizado em `Q4_K_M`. Ele roda numa máquina modesta e é suficiente para montar planos
  curtos de operações Git.
- **Runtime:** escolhi o **llama.cpp** (`llama-server`) em vez do Ollama, que estava
  instável na época. O `llama-server` expõe uma API compatível com a da OpenAI, então o
  projeto se conecta a ele com o starter oficial do Spring AI
  (`spring-ai-starter-model-openai`), sem nenhuma biblioteca de IA extra.
**A integração:**
 
- **`application.yml`**: aponta o Spring AI para o servidor local (`base-url`
  `http://localhost:8080`, modelo `gemma-2-2b-it`, `api-key` fictícia) e usa
  `temperature: 0.2` para respostas mais previsíveis. O Tomcat foi movido para a porta
  8081 para não colidir com o `llama-server`.
- **`LlmConfig`**: monta o `ChatClient` com um system prompt curto de propósito, já que
  modelos pequenos se perdem em prompts longos.
- **`LlmGateway`**: a **única porta de saída** para o LLM. Nenhuma estratégia, estado ou
  comando conhece o Spring AI. Por isso o resto do projeto é testável sem o modelo
  carregado, e trocar de LLM exige mudar um único ponto.
- **Saída em JSON forçada**: o gateway pede `response_format: json_object`. Com isso o
  llama.cpp restringe a geração a JSON válido usando uma gramática interna. O Gemma 2B
  errava o formato do plano com frequência quando o pedido vinha só no texto do prompt, e
  essa opção corta o problema na origem.
- **`PromptTemplates`**: o contrato de planejamento. Monta o prompt com o catálogo de
  ferramentas, o histórico da sessão e o pedido do usuário, e lê a resposta. A leitura é
  tolerante com os erros típicos de modelos pequenos (bloco ```` ```json ````, frase antes
  do objeto, `confidence` como texto). O que não der para ler com segurança vira
  escalonamento para o humano, nunca um chute.
- **`LlmGatewayManualTest`**: o teste de aceite da integração. O contexto Spring sobe
  sempre, e a chamada real ao modelo só roda com `-Dllm.local=true`, para que a suíte de
  testes não dependa do servidor estar no ar.
**Por que essa parte importa:** o modelo é o que transforma o pedido em linguagem natural
num plano executável. Com um modelo aberto e local, o projeto roda sem custo e sem
internet. Com o gateway isolado e a saída em JSON forçada, um modelo pequeno se torna
confiável o bastante para o agente funcionar.
