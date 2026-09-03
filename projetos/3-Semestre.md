<h1 align="center">🚀 API 3º Semestre - Banco de Dados</h1>

<p align="center">
  🎓 <strong>Parceiro Acadêmico:</strong><br>
  FATEC São José dos Campos - Prof. Jessen Vidal
</p>

<p align="center"><img src="https://github.com/user-attachments/assets/26f47534-4a27-4e2e-82f5-2dbc83337876" alt="Capa" style="width:700px;height:400px;"></p>

---

## 📌 Resumo do Projeto

> Desenvolvimento de uma ferramenta web para captura e armazenamento de notícias estratégicas e dados relevantes associados, com web scraping automatizado de portais de notícias e APIs públicas, categorização por tags e sinônimos, e consultas filtradas por data, tag e conteúdo.

---

## ⚠️ Problema

> Dificuldade em acompanhar, de forma organizada e automatizada, notícias estratégicas de múltiplos portais e APIs públicas, sem uma ferramenta que centralizasse, categorizasse e permitisse consultar esses dados de forma eficiente.

---

## 💡 Solução

> Construção de uma aplicação web em Java com Spring Boot, capaz de cadastrar portais e APIs, executar rotinas periódicas de web scraping, associar notícias a tags (com suporte a sinônimos e regionalismos) e disponibilizar telas de consulta com filtros por data, tag e conteúdo.

---

## 🛠 Tecnologias Adotadas

- **Java 22 / Spring Boot**: Spring Data JPA, Spring Web e Spring Thymeleaf para a lógica de negócio, persistência e camada web da aplicação.
- **MySQL**: banco de dados relacional utilizado para armazenar portais, APIs, notícias, tags e jornalistas.
- **Jsoup**: biblioteca utilizada para o web scraping das notícias.
- **Jackson**: manipulação de dados JSON e XML retornados pelas APIs cadastradas.
- **Lombok**: redução da verbosidade do código Java.
- **Git/GitHub**: controle de versão, pull requests e revisão de código do time.
- **Jira**: gestão do backlog e das sprints do projeto.

---

## 🔷 Requisitos Funcionais

- Cadastro de portais de notícias, APIs, tags e jornalistas.
- Processo de web scraping para captura e armazenamento de notícias e dados de APIs.
- Indicação de tags relacionadas por sinônimo/regionalismo.
- Tela de consulta de notícias e de APIs, com filtros de pesquisa por data, tag e conteúdo.

---

## 👨‍💻 Contribuições Individuais

Atuei como **Developer** no time, focado principalmente na camada de backend em Java/Spring: filtros e consultas de notícias, categorização por tags e sinônimos, e correções na rotina de web scraping.

<details>
  <summary>🔍 Filtros e Busca de Notícias por Tag e Data</summary>
    <blockquote>
        Implementei e otimizei os filtros de consulta de notícias por tag e por data, unificando métodos de busca no service e repository para permitir o uso combinado dos filtros mantendo a funcionalidade individual de cada um.
    </blockquote>
</details>

<details>
  <summary>🏷️ Vínculo de Notícias e APIs com Tags e Sinônimos</summary>
    <blockquote>
        Desenvolvi a lógica de verificação de regionalismo e sinônimos das tags, garantindo que notícias sem nenhuma tag correspondente fossem descartadas do banco e que o vínculo entre tag e conteúdo funcionasse de forma consistente no cadastro e nas buscas.
    </blockquote>
</details>

<details>
  <summary>🐛 Correções na Rotina de Web Scraping</summary>
    <blockquote>
        Corrigi problemas no scrapper relacionados a duplicidade de registros, ajustando o service, repository e model para uso de hash na identificação de notícias já capturadas, evitando salvamentos duplicados.
    </blockquote>
</details>

<details>
  <summary>📄 Paginação e Mensagens de Estado Vazio</summary>
    <blockquote>
        Implementei o tratamento de páginas sem resultados, criando mensagens padronizadas para quando nenhuma notícia ou API é encontrada, além de ajustes na paginação das telas de consulta.
    </blockquote>
</details>

<details>
  <summary>⚙️ Otimização de Filtros e Ordenação da API</summary>
    <blockquote>
        Otimizei os filtros de consulta de APIs cadastradas, incluindo a implementação de ordenação decrescente dos resultados e simplificação das queries no repository.
    </blockquote>
</details>


---

## 📚 Aprendizados Efetivos

Este projeto aprofundou minha experiência como desenvolvedor backend, com um domínio de negócio mais complexo (captura, categorização e consulta de notícias) e uma stack mais robusta que a dos semestres anteriores.

### Spring Boot e Persistência de Dados

Ganhei mais autonomia trabalhando com Spring Data JPA, estruturando controllers, services e repositories de forma organizada, e lidando com relacionamentos mais complexos entre notícias, tags e portais no MySQL.

### Web Scraping e Tratamento de Duplicidade

Aprendi a lidar com os desafios práticos de rotinas automatizadas de captura de dados, como evitar duplicidade de registros e garantir a integridade das informações mesmo com execuções recorrentes do scraping.

### Otimização de Consultas

Desenvolvi mais sensibilidade para otimizar queries e combinar múltiplos filtros de busca sem duplicar lógica, unificando métodos que antes tratavam os filtros de forma separada.

### Colaboração via Pull Requests

Trabalhar em um repositório com fluxo de pull requests mais maduro (revisões, merges, commits assinados) me aproximou de práticas de times de desenvolvimento profissionais.

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
    <td>Spring Boot (JPA/Web)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>MySQL</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Jsoup (Web Scraping)</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
  <tr>
    <td>Git/GitHub (PRs)</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>Jira</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
</table>

### 🤝 Soft Skills

<table align="center">
  <tr>
    <th width="270px">Habilidade</th>
    <th width="280px">Casos de uso</th>
  </tr>
  <tr>
    <td>Resolução de Problemas</td>
    <td>Investiguei e corrigi problemas de duplicidade na rotina de scraping, propondo uma solução baseada em hash.</td>
  </tr>
  <tr>
    <td>Atenção a Detalhes</td>
    <td>Ajustei mensagens de erro e estados vazios para garantir uma experiência consistente nas telas de consulta.</td>
  </tr>
  <tr>
    <td>Colaboração Técnica</td>
    <td>Abri e revisei pull requests com o time, integrando código de diferentes branches de funcionalidades.</td>
  </tr>
  <tr>
    <td>Pensamento Analítico</td>
    <td>Unifiquei filtros de busca combinando lógica de tags, datas e conteúdo sem perder a funcionalidade individual de cada filtro.</td>
  </tr>
</table>

---

## 🔧 Como Contribuí em Cada Sprint
 
**Sprint 1**: Contribuição inicial na estrutura de captura de notícias e organização dos dados por portal.
 
**Sprint 2**: Desenvolvimento dos filtros de busca de notícias por tag e por data, e otimização das queries de consulta.
 
**Sprint 3**: Implementação da verificação de regionalismo/sinônimos das tags e do vínculo entre tags e notícias pelo conteúdo.
 
**Sprint 4**: Correções no scrapper (duplicidade via hash), tratamento de paginação e mensagens de estado vazio, e otimização dos filtros e ordenação da consulta de APIs.

---
</p>