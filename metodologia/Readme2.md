<div align="center">
  <img src="./assets/ImagemPerfil.jpeg" width="160" height="160" style="border-radius: 50%;" alt="Fagner Louis">

  <h1>Fagner Louis</h1>
  
  <h3 style="color: #666;">Administrador de Banco de Dados | Analista de Suporte N2</h3>
  
  <br>

  <p>
    <a href="https://www.linkedin.com/in/fagnerlouis/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
    <a href="https://github.com/fagnerlouis"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
  </p>
</div>

## Sobre Mim

Comecei minha trajetória na área de tecnologia atuando como suporte N2 e logo descobri meu grande interesse pela área de dados. Minha missão é consolidar minha carreira em banco de dados, atuando na administração, desenvolvimento e otimização de bases de dados.

- **Atuação:** Possuo experiência assumindo responsabilidades relacionadas à administração e manutenção de bases de dados corporativas, além de suporte N2 trabalhando com aplicações e resolução de problemas.
- **Formação:** Pós-graduado em **Administração de Banco de Dados**, cursando **Banco de Dados** na FATEC Prof. Jessen Vidal e formado em **Análise e Desenvolvimento de Sistemas** pela ETEP.
- **Objetivos:** Focado em consolidar minha carreira na área de banco de dados, unindo experiência profissional e acadêmica.
- **Background:** Iniciei com suporte técnico e consultas estruturadas em banco de dados, desenvolvendo forte conhecimento em bancos como PostgreSQL, SQL Server e SAP HANA, além de linguagens como Java e JavaScript.

<br><hr><br>

**Aplicações e dados**

<p>
<img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white"><img src="https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"><img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"><img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white"><img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white"><img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB"><img src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white"><img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white"><img src="https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white"><img src="https://img.shields.io/badge/SAP_HANA-0FAAFF?style=for-the-badge&logo=sap&logoColor=white">
</p>

<br>

## Meus Projetos

### Em 2026-1

### Empresa Parceira: [IPEM - Instituto de Pesos e Medidas](https://github.com/LizardsDBA/API-2026-3)

### Problema:
O desafio consiste no desenvolvimento de um sistema web para controle e análise dos abastecimentos das viaturas do IPEM – Regional de São José dos Campos, substituindo o atual processo manual realizado por meio de pranchetas físicas mantidas nos veículos. Atualmente, os técnicos registram informações como quilometragem, litros abastecidos, valor pago e número da nota fiscal de forma manual, o que dificulta a consolidação mensal dos dados, a análise comparativa entre viaturas e o acompanhamento do consumo médio de combustível. A proposta do projeto é digitalizar esses registros, garantindo maior organização, rastreabilidade e confiabilidade das informações, além de permitir a geração de indicadores gerenciais que apoiem a tomada de decisão e facilitem a consolidação dos dados para posterior inserção no SGI.


### Solução Entregue pela Equipe:
FlowTrack — Plataforma de Controle de Abastecimento e Utilização de Viaturas. O FlowTrack permitirá o registro digital da utilização de viaturas, substituindo o controle manual realizado em pranchetas. A solução possibilita registrar abastecimentos, início e término de uso dos veículos, mantendo histórico completo de quilometragem, consumo e despesas. Além disso, contará com gerenciamento de cadastros, avisos de manutenção preventiva baseados em quilometragem e visualização de indicadores e relatórios consolidados, facilitando o acompanhamento da frota e a organização das informações para posterior inserção no SGI.

[Repositório do Projeto](https://github.com/LizardsDBA/API-2026-3)

#### Tecnologias Utilizadas
> - **Java**: Utilizado no desenvolvimento do backend, proporcionando flexibilidade e facilidade de manutenção na lógica do sistema.
> - **JavaScript**: Ferramenta utilizada para o desenvolvimento da interface gráfica do usuário, permitindo uma criação rápida e simples da UI.
> - **HTML**: Utilizado para design e prototipagem da interface, ajudando no planejamento do layout da aplicação.
> - **Git e GitHub**: Essenciais para controle de versão e colaboração entre os membros da equipe, garantindo o gerenciamento eficiente do código.
> - **Jira**: Ferramenta usada para gerenciar as tarefas do projeto e organizar o fluxo de trabalho da equipe.

####  Contribuições Pessoais

<details>
  <summary><strong>Infraestrutura e Deploy</strong></summary>
  <br>

  - **Configuração de ambiente AWS**: configuração do `application.properties` para conexão com o banco de dados via AWS RDS.
  - **Containerização**: configuração de Docker e variáveis de ambiente para o deploy na AWS.
  - **Inicialização do banco**: configuração de criação automática do banco de dados (`create database if not exists`) para simplificar o setup em novos ambientes.
  - **Ajustes de setup inicial**: correções de configuração de senha, importação de seeds e ajustes de CSS realizados na primeira sprint do projeto.

  <br>

  **📎 Evidências da infraestrutura:**

  - 🗄️ Instância RDS
    <br>
    <img src="./assets/banco_rds.png" width="300">

  - 💻 Instância EC2
    <br>
    <img src="./assets/instancia_ec2.png" width="300">

</details>

<details>
  <summary><strong>Geolocalização e Integração com API de Endereços</strong></summary>
  <br>

  - **Migração da lógica para o backend**: centralização das chamadas à API de geolocalização, que antes eram feitas pelo frontend, passando a serem requisitadas pelo back-end. Eliminação do loop de geocodificação síncrona no carregamento da tela (que aplicava um delay de 1.1s por destino para respeitar o rate limit da API), passando a calcular a latitude/longitude uma única vez no momento do registro de saída da viatura — sem mais onerar o carregamento do dashboard.

    <br>
    <img src="./assets/remove_for.png" width="700">

  - **Fallback por texto**: implementação de busca de latitude/longitude por texto quando o CEP não é informado pelo usuário.

    <br>
    <img src="./assets/geolocalizacao_por_texto.png" width="500">

  - **Consulta de CEP**: integração com API de consulta de CEP para preenchimento automático de endereço, bairro, cidade e UF, com tratamento de erro caso o CEP não seja encontrado.

    <br>
    <img src="./assets/api_consulta.png" width="400">

  - **Otimização de performance**: cache de pontos já pesquisados, reduzindo chamadas repetidas à API e acelerando o carregamento do mapa.
  - **Refatoração da renderização**: separação da lógica de renderização do mapa da lógica de busca de dados.

    <br>
    <img src="./assets/mapa.png" width="600">

</details>

<details>
  <summary><strong>Modelagem do Banco de Dados</strong></summary>
  <br>

  - **Modelagem completa (MER)**: responsável pela modelagem de todo o banco de dados do projeto, definindo entidades, relacionamentos e regras de integridade. Diagrama construído em Mermaid e evoluído ao longo do projeto conforme o schema foi sendo ajustado às novas funcionalidades.

    <br>
    <img src="./assets/modelagem.png" width="700">

  - **Dicionário de Dados**: elaboração do dicionário de dados completo, documentando todas as tabelas, colunas, tipos e restrições do sistema.

  <br>

  **📎 Documento produzido:**

  - 📊 [Dicionário de Dados](https://github.com/LizardsDBA/API-2026-3/blob/main/docs/manuais/tecnico/Dicionario%20de%20dados.md)
    <br>
    <img src="./assets/dicionario_dados.png" width="200">

</details>

<details>
  <summary><strong>Product Owner</strong></summary>
  <br>

  - **Levantamento de requisitos**: comunicação constante com o cliente (IPEM) via Slack, tirando dúvidas sobre as funcionalidades e coletando as informações necessárias para a construção das User Stories.
  - **Validação de wireframes**: envio dos wireframes para aprovação do cliente, garantindo alinhamento entre o que estava sendo desenvolvido e a expectativa do usuário final.
  - **Construção das User Stories**: elaboração de todas as histórias de usuário do projeto, servindo de base para o planejamento das sprints.
  - **Priorização de entregas**: gerenciamento contínuo das prioridades do backlog ao longo do desenvolvimento.
  - **Documentação do projeto**: estruturação e escrita de toda a documentação (requisitos, escopo e entregas).

  <br>

  **📎 Documentos produzidos:**

  - 📘 [Manual Técnico](https://github.com/LizardsDBA/API-2026-3/blob/main/docs/manuais/tecnico/Manual%20Tecnico.md)
    <br>
    <img src="./assets/manual_tecnico.png" width="200">

  - 📗 [Manual do Usuário](https://github.com/LizardsDBA/API-2026-3/blob/main/docs/manuais/usuario/Manual%20Usuario.md)
    <br>
    <img src="./assets/manual_usuario.png" width="200">

</details>

#### Hard Skills

##### O que desenvolvi (Com autonomia)

- **SQL / MySQL**
  - Consultas utilizando `SELECT`;
  - Filtros com `WHERE`, `AND`, `OR` e `LIKE`;
  - Relacionamento de tabelas com `INNER JOIN`, `LEFT JOIN` e `RIGHT JOIN`;
  - Ordenação de resultados com `ORDER BY`;
  - Utilização de `DISTINCT`;
  - Funções de agregação como `COUNT`, `SUM`, `AVG`, `MIN` e `MAX`;
  - Investigação e validação de dados;
  - Análise de falhas em processos de integração e sincronização.

- **Git / GitHub**
  - `git clone`, `git add`, `git commit`, `git push` e `git pull`;
  - Criação e utilização de branches;
  - Merge entre branches;
  - Resolução de conflitos de merge;
  - Versionamento e desenvolvimento colaborativo;
  - Organização e manutenção de documentação no GitHub.

- **Linux**
  - Utilização do Linux como ambiente principal;
  - Navegação e manipulação de arquivos pelo terminal;
  - Instalação e atualização de pacotes;
  - Gerenciamento básico de processos e serviços;
  - Comandos como `ls`, `cd`, `cp`, `mv`, `rm`, `grep`, `find`, `chmod`, `ps` e `systemctl`;
  - Experiência com Kubuntu, Ubuntu, Linux Mint e openSUSE.

- **AWS**
  - Conceitos básicos de AWS;
  - Criação e configuração de instâncias EC2;
  - Armazenamento com S3;
  - Banco de dados com RDS;
  - Deploy básico de aplicações na AWS;
  - AWS CLI: `aws configure`, `aws s3 ls` e `aws s3 cp`.

- **Cloud Computing**
  - Máquinas virtuais e armazenamento em nuvem;
  - Banco de dados em Cloud;
  - Deploy de aplicações;
  - Conceitos básicos de escalabilidade e disponibilidade.


##### O que desenvolvi (Conhecimento intermediário)

- **Java / Spring Boot**
  - Programação Orientada a Objetos;
  - Criação e organização de projetos com Spring Boot;
  - Estruturação de aplicações em `Controller`, `Service` e `Repository`;
  - Integração de aplicações com banco de dados;
  - Desenvolvimento acadêmico de aplicações Backend.

- **APIs REST**
  - Métodos `GET`, `POST`, `PUT` e `DELETE`;
  - Criação e consumo de endpoints;
  - Utilização de parâmetros e corpo das requisições;
  - Desenvolvimento acadêmico de APIs REST com Spring Boot.

- **Docker**
  - Criação e execução de containers;
  - Utilização de imagens Docker;
  - Uso de Docker Compose;
  - Comandos como `docker ps`, `docker images`, `docker logs`, `docker exec` e `docker stop`;
  - Análise de logs e troubleshooting básico de containers.


##### O que gostaria de desenvolver e aprofundar

- **Spring Security**
  - Configuração básica do Spring Security;
  - Autenticação e autorização;
  - Controle de acesso por usuário e roles;
  - Proteção de endpoints;
  - Autenticação utilizando JWT.

- **Microservices**
  - Estrutura básica de microsserviços;
  - Criação de serviços independentes;
  - Comunicação entre APIs;
  - Requisições HTTP entre serviços;
  - Integração de microsserviços com banco de dados.

#### Soft Skills

##### O que desenvolvi

- **Organização**
  - Organização e acompanhamento das Sprints;
  - Gerenciamento das atividades através do Jira;
  - Organização da documentação no GitHub;
  - Preparação dos materiais para apresentações.

- **Comunicação**
  - Contato direto com clientes através do Slack e Microsoft Teams;
  - Participação em reuniões com a equipe;
  - Apresentação de entregas durante as Sprints;
  - Comunicação entre equipe, Product Owner e cliente.

- **Comunicação em Público**
  - Melhorar apresentações para clientes e equipes;
  - Desenvolver mais confiança ao apresentar projetos;
  - Aprimorar a comunicação técnica de forma simples e objetiva.

- **Trabalho em Equipe**
  - Desenvolvimento colaborativo em projetos acadêmicos;
  - Colaboração com Product Owner e desenvolvedores;
  - Participação nas decisões e melhorias do projeto;
  - Compartilhamento de ideias e soluções com a equipe.

- **Proatividade**
  - Proposição de novas funcionalidades e melhorias;
  - Participação além das responsabilidades de Scrum Master;
  - Contribuição técnica no desenvolvimento;
  - Busca por soluções durante problemas e dificuldades do projeto.

- **Resolução de Problemas**
  - Investigação de problemas técnicos;
  - Análise de dados e logs;
  - Identificação de falhas em integrações;
  - Busca pela causa do problema antes do direcionamento para outras equipes.

##### 🌱 O que gostaria de desenvolver

- **Liderança**
  - Desenvolver minha capacidade de liderar equipes;
  - Melhorar a distribuição e acompanhamento de atividades;
  - Aprender a apoiar a equipe na resolução de dificuldades.

- **Gestão de Projetos**
  - Aprofundar conhecimentos em metodologias ágeis;
  - Melhorar planejamento e acompanhamento de projetos;
  - Desenvolver conhecimentos em gestão de riscos e prioridades.

- **Inglês Profissional**
  - Aprimorar conversação;
  - Desenvolver vocabulário técnico de TI;
  - Melhorar a comunicação em reuniões e ambientes profissionais.

- **Tomada de Decisão**
  - Desenvolver análise de cenários;
  - Melhorar a definição de prioridades;
  - Tomar decisões com base em informações e dados.

- **Gestão de Equipes**
  - Desenvolver habilidades para coordenar pessoas;
  - Melhorar o acompanhamento das atividades da equipe;
  - Aprender técnicas de feedback e desenvolvimento de pessoas.

<br><hr><br>

## Experiência Profissional

**SPS Group | Junior SAP Business One Consultant** *(Dezembro/2025 – Atualmente)*
> Desenvolvimento e customização de ERP na plataforma Aster, integrado ao SAP Business One.
- Desenvolvimento de queries complexas em SQL Server (T-SQL) e SAP HANA, e uso de JavaScript em estruturas JSON para customizar interface e automatizar regras de negócio.
- Customização de telas: criação e modificação de campos, botões, validações e fluxos operacionais nas telas do SAP Business One via plataforma Aster.
- Desenvolvimento de relatórios personalizados, dashboards interativos e layouts de impressão com Crystal Reports (.RPT).
- Criação de UserPages para suportar processos de negócio específicos de clientes, estendendo as funcionalidades do sistema.
- Implementação de lógica de negócio via JavaScript event handlers e integrações através das APIs do SAP Service Layer.

**SPS Group | Trainee SAP Business One Consultant** *(Abril/2025 – Dezembro/2025)*
> Desenvolvimento e customização de ERP na plataforma Aster, integrado ao SAP Business One.
- Desenvolvimento de queries complexas em SQL Server (T-SQL) e SAP HANA, e uso de JavaScript em estruturas JSON para customizar interface e automatizar regras de negócio.
- Customização de telas: criação e modificação de campos, botões, validações e fluxos operacionais nas telas do SAP Business One via plataforma Aster.
- Desenvolvimento de relatórios personalizados, dashboards interativos e layouts de impressão com Crystal Reports (.RPT).
- Criação de UserPages para suportar processos de negócio específicos de clientes, estendendo as funcionalidades do sistema.
- Implementação de lógica de negócio via JavaScript event handlers e integrações através das APIs do SAP Service Layer.

**Log Smart Brasil | Senior Support Analyst (N3)** *(Março/2023 – Fevereiro/2025)*
> Suporte N3 em sistemas WMS e infraestrutura, atuando em chamados de média/alta complexidade.
- Testes de API utilizando Postman em ambientes locais e de produção.
- Desenvolvimento de queries avançadas em PostgreSQL, incluindo consultas customizadas para relatórios e análise de dados do sistema.
- Testes manuais de novas funcionalidades e correções de bugs para garantir estabilidade e precisão funcional do sistema.
- Manutenção e monitoramento de servidores, garantindo disponibilidade, performance e confiabilidade de aplicações em ambientes Linux.

**MB de Moura Baterias Epp | E-commerce Operations Analyst** *(Janeiro/2018 – Fevereiro/2023)*
> Atendimento ao cliente, gestão de e-commerce e suporte online, cobrindo atividades de pré-venda e pós-venda.
- Liderou a implementação da loja online da empresa no Mercado Livre, tornando-se um dos maiores vendedores de baterias de moto na plataforma.
- Otimizou processos logísticos e de envio, transformando a loja física em ponto de coleta do Mercado Livre, viabilizando operações de despacho internas.
- A iniciativa aumentou a receita mensal em mais de 40%, atraiu tráfego adicional para a loja física, reduziu a dependência de campanhas pagas no Google Ads e gerou receita adicional via operação de ponto de coleta.

<br><hr><br>

## Cursos e Formação

<details>
  <summary><b>Ver Histórico</b></summary>
  <br>
  <ul>
    <li><b>FATEC Prof. Jessen Vidal:</b> Superior em Banco de Dados (Cursando).</li>
    <li><b>Pós-Graduação:</b> Administração de Banco de Dados.</li>
    <li><b>ETEP São José dos Campos:</b> Análise e Desenvolvimento de Sistemas.</li>
  </ul>
</details>

<br>
<div align="center">
  <b>Obrigado por visitar meu portfólio! Sinta-se à vontade para conectar. 👨💻</b>
</div>
