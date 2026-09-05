<h1 align="center">🚀 API 4º Semestre - Banco de Dados</h1>

<p align="center">
  🎓 <strong>Parceiro Acadêmico:</strong><br>
  Empresa Visiona
</p>

<p align="center"><img src="https://github.com/user-attachments/assets/8960e749-d776-4c0b-b62f-91915e6cf180" alt="Capa" style="width:700px;height:400px;"></p>

---

## 📌 Resumo do Projeto

> Desenvolvimento de uma aplicação para manipulação de dados agrícolas armazenados em banco relacional, com visualização em tela e acesso por API, voltada à gestão de áreas agrícolas: cadastro de talhões, classificação automática por IA de ervas daninhas, aprovação por safra e dashboards de produtividade.

---

## ⚠️ Problema

> A empresa parceira precisava de uma ferramenta que centralizasse o cadastro de áreas agrícolas e permitisse aos analistas revisar e aprovar mapas de classificação automática (marcação de ervas daninhas por IA), além de acompanhar o progresso das análises por meio de dashboards.

---

## 💡 Solução

> Construção de uma aplicação full stack, com backend em Java/Spring Boot expondo uma API RESTful e frontend em Vue, permitindo cadastro de usuários com diferentes permissões, cadastro de áreas via upload de arquivos .geojson, edição e aprovação de mapas por safra, e dashboards com métricas de produtividade em tempo real.

---

## 🛠 Tecnologias Adotadas

<p>
  <img src="https://img.shields.io/badge/Java%2022-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white">
  <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white">
  <img src="https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white">
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">
</p>

- **Java 22 / Spring Boot 3.3.3**: Spring Data JPA, Spring Web, Spring Security e Spring DevTools para a API RESTful.
- **Vue**: componentização, gerenciamento de estado e visualização de dados em tempo real no frontend.
- **MySQL**: banco de dados relacional para armazenar usuários, áreas, safras e relatórios.
- **Docker**: containerização do ambiente de desenvolvimento.
- **Git/GitHub**: controle de versão, branches por sprint e pull requests entre repositórios de client e server.
- **Figma**: wireframes das telas de cada sprint.

---

## 🔷 Requisitos Funcionais

- Três tipos de usuários: administrador, analista e consultor, cada um com permissões específicas.
- Cadastro de áreas agrícolas via upload de arquivo `.geojson`, com nome da fazenda, cultura, produtividade, área, tipo de solo, cidade e estado.
- Visualização e edição dos mapas de classificação automática (IA) por talhão e por safra.
- Aprovação dos mapas de classificação pelo analista, com controle de tempo de aprovação.
- Dashboards com métricas de progresso de análise e produtividade das safras.

---

## 👨‍💻 Contribuições Individuais

Atuei como **Developer** no time, majoritariamente na camada de backend (Java/Spring), com foco na funcionalidade de **safra**: entidade, endpoints de atribuição e aprovação, relatórios e listagem por safra.

<details>
  <summary>🌾 Modelagem e Evolução da Entidade Safra</summary>
    <blockquote>
        Implementei a entidade Safra e evoluí sua estrutura ao longo da sprint, adicionando colunas necessárias para vincular corretamente os talhões e as análises a cada ciclo de safra.
    </blockquote>
</details>

<details>
  <summary>🔗 Endpoints de Atribuição e Aprovação</summary>
    <blockquote>
        Desenvolvi os endpoints de atribuição de safra ao analista e de aprovação de talhão, viabilizando o fluxo em que o analista recebe os talhões para análise e os aprova após a revisão do mapa de classificação.
    </blockquote>
</details>

<details>
  <summary>📊 Relatórios por Safra</summary>
    <blockquote>
        Criei o RelatorioSafra, o RelatorioDTO e o RelatorioController, além de atualizar o SafraService, estruturando a camada de relatórios que alimenta os dashboards de produtividade e progresso de análise.
    </blockquote>
</details>

<details>
  <summary>📋 Listagem Baseada em Safra</summary>
    <blockquote>
        Refatorei a listagem de talhões para que passasse a ser organizada por safra em vez de talhão individual, tornando a consulta mais alinhada ao fluxo de trabalho do consultor e do analista.
    </blockquote>
</details>

---

## 📚 Aprendizados Efetivos

Este projeto elevou a complexidade em relação aos semestres anteriores, unindo backend robusto, frontend reativo e um domínio de negócio (classificação agrícola por IA) que exigiu atenção redobrada às regras específicas do fluxo de aprovação.

### Modelagem de Entidades com Regras de Negócio Complexas

Trabalhar na entidade Safra, que conecta talhões, análises e aprovações, aprofundou minha capacidade de modelar relacionamentos que refletem um fluxo de trabalho real, com estados (pendente, em análise, aprovado) e responsabilidades por perfil de usuário.

### Construção de Relatórios e Camada de Dashboard

Desenvolver o RelatorioSafra e o RelatorioController me ensinou a estruturar a camada de dados que alimenta visualizações em tempo real, pensando desde já no formato de saída (DTOs) que o frontend consumiria.

### Evolução Incremental de Funcionalidades

Refatorar a listagem de talhões para ser baseada em safra, já com a funcionalidade em produção, reforçou a importância de código desacoplado e testável para permitir mudanças de escopo sem grandes retrabalhos.

### Colaboração em Repositórios Separados (Client/Server)

Atuar em um projeto dividido entre repositórios de frontend e backend, integrados via submódulos, me aproximou de práticas comuns em times maiores, exigindo mais atenção à comunicação entre APIs e contratos de dados.

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
    <td>Java</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Spring Boot (JPA/Web/Security)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Vue.js</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
  <tr>
    <td>MySQL</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Docker</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Git/GitHub (submódulos e PRs)</td>
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
    <td>Pensamento Analítico</td>
    <td>Modelei o fluxo de atribuição e aprovação por safra considerando as regras específicas de cada perfil de usuário.</td>
  </tr>
  <tr>
    <td>Adaptabilidade</td>
    <td>Refatorei a listagem de talhões para safra em meio à sprint, ajustando-me a uma mudança de escopo sem comprometer o prazo.</td>
  </tr>
  <tr>
    <td>Colaboração Técnica</td>
    <td>Integrei código entre os repositórios de server e client, alinhando contratos de API com o restante do time.</td>
  </tr>
  <tr>
    <td>Atenção a Detalhes</td>
    <td>Estruturei DTOs e controllers de relatório com cuidado para garantir consistência dos dados exibidos nos dashboards.</td>
  </tr>
</table>

---

## 🔧 Como Contribuí em Cada Sprint

**Sprint 1**: Apoio na estruturação inicial do backend e no cadastro de usuários e áreas agrícolas.

**Sprint 2**: Início do desenvolvimento das funcionalidades relacionadas à safra, base para a atribuição de talhões aos analistas.

**Sprint 3**: Modelagem e evolução da entidade Safra, implementação dos endpoints de atribuição e aprovação, criação do RelatorioSafra, RelatorioDTO e RelatorioController, e refatoração da listagem de talhões para ser baseada em safra.

---

</p>