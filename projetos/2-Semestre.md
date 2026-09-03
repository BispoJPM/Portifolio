<h1 align="center">🚀 API 2º Semestre - Banco de Dados</h1>

<p align="center">
  🎓 <strong>Parceiro Acadêmico:</strong><br>
  FATEC São José dos Campos - Prof. Jessen Vidal
</p>

<p align="center"><img src="https://github.com/Porygonn/Porygon/assets/111442399/ad146d27-11e7-493d-bc00-03763d2e5f52" alt="Capa" style="width:700px;height:400px;"></p>

---

## 📌 Resumo do Projeto

> Desenvolvimento de uma ferramenta desktop (CRUD) para consolidação de dados climáticos de cidades do estado de São Paulo, permitindo o carregamento de arquivos CSV com variáveis climáticas, geração de relatórios (valor médio, boxplot e situacional) e o tratamento de registros suspeitos identificados durante a importação dos dados.

---

## ⚠️ Problema

> Pesquisadores precisavam de uma forma organizada de carregar, validar e analisar grandes volumes de dados climáticos vindos de diferentes estações, sem um sistema que identificasse automaticamente registros suspeitos ou gerasse relatórios consolidados por cidade e período.

---

## 💡 Solução

> Construção de uma aplicação Java Desktop com persistência em banco de dados relacional (MySQL via JDBC), capaz de importar arquivos CSV, separar os registros por variável climática, sinalizar valores fora do padrão para revisão e gerar relatórios de valor médio, boxplot e situação por cidade.

---

## 🎯 Objetivos

- Projetar um Banco de Dados relacional com múltiplas entidades e relacionamentos.
- Organizar a equipe por competências.
- Levantar e registrar Requisitos Funcionais e Não Funcionais usando técnicas de métodos ágeis e tradicionais.
- Projetar a arquitetura lógica do sistema.
- Implementar a aplicação, com persistência, usando Java Desktop.

---

## 🛠 Tecnologias Adotadas

- **Java Desktop**: linguagem utilizada para o desenvolvimento da aplicação, com conexão ao banco de dados via JDBC.
- **MySQL**: banco de dados relacional utilizado para armazenar estações, cidades, variáveis climáticas e registros importados.
- **Git/GitHub**: controle de versão e hospedagem do repositório do projeto.
- **Figma**: ferramenta utilizada para a criação do wireframe do produto.
- **Trello**: gestão ágil das sprints e do backlog do time.

---

## 🔷 Requisitos Funcionais

- Relatório de valor médio das variáveis climáticas por cidade, com escolha de período e periodicidade horária.
- Relatório com os elementos necessários para plotar um gráfico boxplot com base nos dados de uma estação em uma data específica.
- Relatório de situação, com os valores médios das últimas medidas de cada cidade.
- Gerenciamento de estações, cidades e unidades de medida, com visualização e alteração dos dados.
- Carregamento e validação de arquivos CSV contendo variáveis climáticas.
- Isolamento de registros suspeitos (ex: temperatura acima de 60°C ou abaixo de -20°C) para revisão, edição ou exclusão.
- Armazenamento separado de cada variável climática por registro, mesmo quando vindas do mesmo arquivo.

---

## 👨‍💻 Contribuições Individuais

Atuei como **Product Owner** do projeto, sendo responsável pela definição e priorização do backlog, pelo levantamento de requisitos junto aos professores orientadores e pelo alinhamento entre as necessidades do "pesquisador" (persona do projeto) e o time de desenvolvimento.

<details>
  <summary>📋 Levantamento e Priorização de Requisitos</summary>
    <blockquote>
        Conduzi o levantamento dos requisitos funcionais e não funcionais junto à tríade de professores da API, traduzindo as necessidades do domínio de dados climáticos em user stories claras e priorizáveis para o time.
    </blockquote>
</details>

<details>
  <summary>✅ Gestão do Backlog do Produto</summary>
  <blockquote>
  Organizei e mantive o backlog priorizado por criticidade e sprint, definindo a ordem de implementação das funcionalidades (carregamento de CSV, tratamento de registros suspeitos, relatórios de valor médio, situacional e boxplot, gerenciamento de estações e cidades).
  </blockquote>
</details>

<details>
  <summary>🗓️ Planejamento das Sprints</summary>
  <blockquote>
  Participei da definição do escopo de cada uma das quatro sprints do projeto, junto ao Scrum Master, garantindo que as entregas mais essenciais (carregamento e validação de dados) fossem priorizadas nas fases iniciais.
  </blockquote>
</details>

<details>
  <summary>🧩 Validação das Entregas</summary>
  <blockquote>
  Revisei as funcionalidades entregues a cada sprint, validando se atendiam aos critérios de aceite definidos e se estavam alinhadas com os requisitos levantados junto aos professores orientadores.
  </blockquote>
</details>

<details>
  <summary>🎨 Definição do Wireframe</summary>
  <blockquote>
  Apoiei a criação do wireframe do produto no Figma, ajudando a traduzir os requisitos funcionais em telas e fluxos de interação para o pesquisador usuário do sistema.
  </blockquote>
</details>

---

## 📚 Aprendizados Efetivos

Este projeto consolidou minha atuação como Product Owner em um contexto mais técnico e orientado a dados, exigindo maior aproximação com regras de negócio específicas de um domínio científico.

### Levantamento de Requisitos em Domínio Técnico

Aprendi a traduzir necessidades de um domínio específico (dados climáticos) em requisitos claros, lidando com regras de validação e tratamento de exceções (registros suspeitos) que exigiam entendimento técnico aprofundado.

### Priorização de Backlog Orientada a Valor

Desenvolvi mais autonomia na priorização de user stories, equilibrando complexidade técnica, dependências entre funcionalidades (como a necessidade de ter os dados carregados antes de gerar relatórios) e valor entregue ao usuário final.

### Alinhamento com Múltiplos Stakeholders

Atuar como ponte entre a tríade de professores orientadores e o time de desenvolvimento me ensinou a conciliar diferentes expectativas e traduzir feedbacks acadêmicos em ajustes práticos no backlog.

### Colaboração em Projetos com Persistência de Dados

Participar de um projeto com banco de dados relacional mais robusto me aproximou de discussões técnicas sobre modelagem de dados, o que enriqueceu minha visão como PO sobre viabilidade técnica das entregas.

---

## 🏆 Competências Desenvolvidas

### 🧠 Hard Skills

<table align="center">
  <tr>
    <th width="270px">Tecnologia/Metodologia</th>
    <th width="85px">Nota</th>
    <th width="200px">Classificação</th>
  </tr>
  <tr>
    <td>Gestão de Backlog / Priorização</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>Levantamento de Requisitos</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>Trello (Kanban)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Java</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
  <tr>
    <td>JDBC</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
  <tr>
    <td>MySQL</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Git/GitHub</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>

  <tr>
    <td>Figma</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
</table>

### 🤝 Soft Skills

<table align="center">
  <tr>
    <th width="270px">Habilidade</th>
    <th width="280px">Casos de uso</th>
  </tr>
  <tr>
    <td>Comunicação</td>
    <td>Alinhei as necessidades da tríade de professores com a capacidade técnica do time, traduzindo requisitos acadêmicos em user stories claras.</td>
  </tr>
  <tr>
    <td>Priorização</td>
    <td>Organizei o backlog por criticidade e dependência técnica, garantindo que o carregamento e a validação dos dados fossem entregues antes dos relatórios.</td>
  </tr>
  <tr>
    <td>Pensamento Analítico</td>
    <td>Compreendi as regras de negócio específicas do domínio climático para definir critérios de aceite coerentes com o uso real do sistema.</td>
  </tr>
  <tr>
    <td>Trabalho em Equipe</td>
    <td>Colaborei de perto com o Scrum Master e os desenvolvedores para viabilizar as entregas dentro do prazo de cada sprint.</td>
  </tr>
</table>

---

## 🔧 Como Contribuí em Cada Sprint

**Sprint 1**: Definição e priorização das user stories de carregamento de arquivos CSV, organização dos dados por estação e identificação de registros suspeitos.

**Sprint 2**: Priorização das funcionalidades de relatório de valor médio por cidade e relatório situacional, além do acompanhamento da modelagem do banco de dados MySQL.

**Sprint 3**: Validação das entregas do relatório boxplot e do CRUD de tratamento dos registros suspeitos, incluindo os alertas para o usuário.

**Sprint 4**: Priorização e validação da funcionalidade de edição de unidades de medida, estações e cidades, encerrando o backlog planejado para o semestre.

---

</p>