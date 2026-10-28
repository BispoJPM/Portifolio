<h1 align="center">🚀 API 6º Semestre - Banco de Dados</h1>

<table width="100%">
  <tr>
    <td width="33%" align="left"><a href="5-Semestre.md">← Projeto anterior: 5º Semestre</a></td>
    <td width="34%" align="center"><a href="../README.md">Todos os projetos</a></td>
    <td width="33%" align="right"></td>
  </tr>
</table>

<p align="center">
  🎓 <strong>Empresa Parceira:</strong><br>
  Akaer
</p>

---

## 📌 Resumo do Projeto

> Desenvolvimento da plataforma **Índice** para a Akaer. A solução tem como objetivo otimizar a busca e o acesso a documentos e normas técnicas da empresa, que atualmente se encontram dispersos em um sistema onde os usuários consomem muito tempo até encontrar o documento que realmente atende sua demanda — muitas vezes sendo necessário ler páginas de diversos arquivos antes de identificar o correto. Por meio do uso de Inteligência Artificial e Machine Learning, o Índice estabelece correlações entre a pesquisa do usuário e os documentos que possam corresponder ao desejado, agilizando e tornando mais precisa a localização da informação. A plataforma conta com tela de pesquisa (campo textual e filtros pré-determinados), fluxo de upload de documentos em três etapas, listagens de documentos do usuário e do sistema, visualização de detalhes com controle de permissão de acesso, fluxo de nova revisão de documentos e telas administrativas para controle de permissões e de usuários. Dessa forma, além de acelerar a consulta, o Índice garante segurança e autorização no acesso aos documentos, permitindo que perfis autorizados decidam quem pode visualizar cada documento e estabeleçam a relação entre as áreas da empresa, apoiando a gestão documental e a tomada de decisão.

---

## ⚠️ Problema

> A Akaer possui um sistema com diversos documentos e normas que seus usuários podem acessar. O problema atual está no tempo que os clientes demoram realizando buscas até chegar aos documentos que realmente precisam — muitas vezes é necessário ler páginas de diversos documentos até descobrir se aquele é o documento que vai atender sua demanda. Além disso, hoje os documentos não possuem segurança e autorização para serem visualizados, o que pode acarretar em problemas de segurança.

---

## 💡 Solução

> Utilizando IA e machine learning, o sistema **Índice** monta correlações entre a pesquisa do usuário e os documentos que possam corresponder ao desejado. A plataforma dispõe de:
>
> - Uma **tela de pesquisa** com campo de pesquisa textual e filtros pré-determinados;
> - Um **fluxo de upload de documentos**;
> - **Login com diferentes perfis de usuário**, de forma que alguns perfis possam controlar os demais e decidir níveis de autorização (quem pode ver qual documento) e a relação entre as áreas da empresa.

---

## 🛠 Tecnologias Adotadas

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white">
  <img src="https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white">
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white">
  <img src="https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
</p>

- **Python e Django**: desenvolvimento dos serviços backend e da API consumida pela aplicação.
- **PostgreSQL**: armazenamento relacional de informações estruturadas, como projetos, disciplinas e metadados.
- **MongoDB**: armazenamento de dados documentais e informações flexíveis relacionadas aos arquivos.
- **Vue.js, TypeScript e Vite**: construção da interface web e integração com a API.
- **Docker Compose**: execução integrada da API e dos bancos de dados em um ambiente padronizado.
- **Git e GitHub**: versionamento e colaboração em repositórios separados para backend, frontend e documentação do projeto.

---

## 🔷 Requisitos Funcionais

- Envio, validação, organização e visualização de documentos técnicos.
- Extração e padronização de metadados para facilitar a identificação dos arquivos.
- Pesquisa por atributos e pelo conteúdo dos documentos, com filtros e sugestões de materiais relacionados.
- Classificação assistida por IA, agrupamento temático e geração de resumos a partir dos documentos encontrados.
- Consulta ao histórico e envio de revisões de documentos.
- Controle de permissões e solicitações de acesso para documentos restritos.
- Registro e acompanhamento das operações relacionadas à ingestão e ao acesso aos arquivos.

---

## 👨‍💻 Contribuições Individuais

Atuei como **Developer full stack**, contribuindo no backend e no frontend em diferentes frentes do Índice: ingestão e validação de documentos, revisões, pesquisa com resumos por IA, tratamento de duplicidades e rastreabilidade de ações.

<details>
  <summary>📤 API de upload e validação de arquivos</summary>
  <blockquote>
    No backend, implementei o endpoint de upload e organizei a lógica em componentes de view, serviço, serializer e modelo de domínio. O fluxo valida tamanho e tipo do arquivo, incluindo a verificação de assinatura binária (magic bytes), antes de armazená-lo temporariamente. Também configurei parâmetros do armazenamento temporário, documentei as configurações de upload e contribuí para o reconhecimento de arquivos DOCX.
  </blockquote>
</details>

<details>
  <summary>📚 Envio de múltiplos arquivos e revisões</summary>
  <blockquote>
    Trabalhei no suporte a vários arquivos associados a um documento e no envio seletivo de arquivos de revisão. No frontend, implementei a seleção e o envio de pacotes de revisão e ajustei a ação de revisão no histórico, além de atualizar a fila de upload, o formulário, as stores de documento e autenticação, o composable de envio e a comunicação com a API.
  </blockquote>
</details>

<details>
  <summary>🧾 Integração entre upload, interface e documentos duplicados</summary>
  <blockquote>
    Ajustei o contrato e a rota usados pelo frontend para submeter documentos, incluindo o tratamento da resposta HTTP 409 como uma resposta de conflito esperada no fluxo. Implementei o aviso de duplicidade com o código e o título do documento já existente e o envio dessas informações ao diálogo. Também alinhei a validação de extensões e ícones para arquivos DOCX e atualizei testes do formulário, da confirmação e do envio.
  </blockquote>
</details>

<details>
  <summary>🔁 Identificação de duplicidades e integridade dos envios</summary>
  <blockquote>
    No backend, implementei o cálculo de hash SHA-256 antes da persistência e o tratamento de arquivos cujo hash já existe. Refinei a regra para bloquear duplicidades no contexto correto sem impedir que o mesmo arquivo seja utilizado em projetos diferentes. No frontend, tratei a resposta da API e apresentei o aviso com informações do documento encontrado. Também acrescentei testes para tentativas de envio duplicado e corrigi a integração do fluxo com os registros de auditoria.
  </blockquote>
</details>

<details>
  <summary>🕘 Histórico, detalhes e contexto do usuário</summary>
  <blockquote>
    Ajustei a exibição do histórico do arquivo selecionado e o envio do usuário atual para a tela de detalhes do documento, preservando o contexto necessário durante a consulta. Também reposicionei a ação de revisão junto ao histórico para aproximá-la do fluxo de uso.
  </blockquote>
</details>

<details>
  <summary>🤖 Resumos de pesquisa com Ollama</summary>
  <blockquote>
    Integrei o Ollama à geração de resumos a partir dos resultados de pesquisa, ajustei o tempo limite padrão da operação e documentei as configurações necessárias no README e no modelo de variáveis de ambiente do backend.
  </blockquote>
</details>

<details>
  <summary>🔐 Auditoria e rastreabilidade de ações</summary>
  <blockquote>
    Implementei registros de auditoria para ações sensíveis de usuários e operações relacionadas a documentos, incluindo tipos de ação, índices e eventos de upload. Também registrei solicitações de acesso a documentos. Criei e ajustei testes para os eventos, serviços e solicitações de acesso, corrigi falhas encontradas na integração da trilha de auditoria e alinhei os dados de demonstração aos novos campos exigidos.
  </blockquote>
</details>

---

## 📚 Aprendizados Efetivos

### Desenvolvimento Full Stack com Repositórios Integrados

Contribuir em repositórios separados para frontend e backend reforçou a importância de manter contratos claros entre a interface e a API, especialmente em fluxos que envolvem envio de arquivos, usuários e histórico.

### Versionamento e Ciclo de Vida de Documentos

Trabalhar com revisões e histórico ampliou minha compreensão sobre como preservar a rastreabilidade de documentos e apresentar ao usuário o contexto correto de cada versão.

### Regras de Negócio e Testes

O tratamento de duplicidades mostrou que comparar arquivos exige considerar o contexto do negócio: um documento repetido pode ser inválido dentro de um mesmo fluxo e, ainda assim, ser legítimo em outro projeto. Testes automatizados ajudam a proteger esse comportamento.

### Gestão de Documentação Técnica

O projeto aproximou conceitos de banco de dados, busca e inteligência artificial de um problema real de engenharia, no qual encontrar a informação certa com segurança e rapidez é essencial.

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
    <td>Python / Django</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Vue.js / TypeScript</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>PostgreSQL / MongoDB</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Testes Automatizados</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Docker / Docker Compose</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
</table>

### 🤝 Soft Skills



---

<table width="100%">
  <tr>
    <td width="33%" align="left"><a href="5-Semestre.md">← Projeto anterior: 5º Semestre</a></td>
    <td width="34%" align="center"><a href="../README.md">Todos os projetos</a></td>
    <td width="33%" align="right"></td>
  </tr>
</table>
