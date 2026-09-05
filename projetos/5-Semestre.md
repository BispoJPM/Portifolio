<h1 align="center">🚀 API 5º Semestre - Banco de Dados</h1>

<p align="center"><img src="https://github.com/user-attachments/assets/9c2f315d-9621-4fed-be78-2aaac163f5b7" alt="Capa" style="width:700px;height:400px;"></p>



<p align="center">
  🎓 <strong>Empresa Parceira:</strong><br>
  SIATT - Sistemas Integrados de Alto Teor Tecnológico
</p>

---

## 📌 Resumo do Projeto

> Desenvolvimento do **Lunae**, uma ferramenta de extração, processamento e visualização analítica de dados, integrada às bases da SIATT, focada na criação de dashboards a partir das informações de projetos, programas, compras, materiais e horas trabalhadas da empresa.

---

## ⚠️ Problema

> A SIATT organiza seus projetos estratégicos em programas institucionais, mas as informações de compras, materiais, estoque e horas técnicas ficavam distribuídas em tabelas e sistemas diferentes, sem uma visão analítica consolidada. Isso dificultava responder perguntas como o custo real de um projeto ou o consumo de materiais e horas ao longo do tempo.

---

## 💡 Solução

> Construção de uma plataforma analítica que integra dados de tarefas, projetos, programas, compras e horas trabalhadas, a partir da importação de arquivos CSV fornecidos pela empresa. Os dados são tratados e armazenados em um banco estruturado em esquema estrela (star schema), alimentando dashboards interativos com gráficos de barra e linha para acompanhamento de consumo, custo e esforço técnico por projeto e programa.

---

## 🛠 Tecnologias Adotadas

<p>
  <img src="https://img.shields.io/badge/Vue.js%203-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white">
  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white">
  <img src="https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white">
  <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white">
  <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white">
</p>

- **Vue.js 3**: componentização, reatividade (Composition API) e visualização de dados em tempo real no frontend.
- **Django + DRF**: API RESTful, ORM e comandos de gerenciamento para o pipeline de ETL.
- **PostgreSQL**: banco relacional modelado em star schema (dimensões e fatos) para consultas analíticas.
- **Pandas**: tratamento e transformação dos arquivos CSV recebidos da SIATT antes da carga no banco.
- **Docker**: containerização do banco de dados para reprodutibilidade do ambiente.
- **Git/GitHub**: controle de versão, branches por feature e pull requests entre os repositórios de backend e frontend.
- **Slack**: comunicação com a empresa parceira para levantamento e refinamento de regras de negócio.

---

## 🔷 Requisitos Funcionais

- Importação e tratamento de arquivos CSV de projetos, tarefas, horas, materiais, compras e estoque.
- Armazenamento dos dados tratados em banco relacional modelado em star schema.
- API RESTful expondo endpoints analíticos por projeto, programa e material.
- Dashboards com gráficos de burnup de horas e custo por projeto e programa.
- Alertas e sugestões de próxima compra com base em lead time e nível de estoque.

---

## 👨‍💻 Contribuições Individuais

Atuei em duas frentes complementares neste projeto: como **Developer full stack** (Django + Vue.js), implementando funcionalidades analíticas de ponta a ponta, e como responsável pela frente de **Quality Assurance (QA)**, estruturando os processos, métricas e ferramentas de qualidade usados por todo o time.

### 💻 Como Developer

Minha atuação como desenvolvedor ficou concentrada em duas funcionalidades centrais do Lunae, ambas implementadas de ponta a ponta (backend → API → frontend), além de contribuições pontuais em outras áreas do sistema.

<details>
  <summary>📈 Gráfico de Burnup de Horas por Projeto</summary>
    <blockquote>
        Esta foi a funcionalidade mais extensa que desenvolvi, com mais de 20 commits ao longo de duas semanas de refinamento. A ideia era mostrar, para cada projeto ativo, a evolução acumulada de horas trabalhadas ao longo das semanas de sprint, permitindo comparar múltiplos projetos no mesmo gráfico.
        <br><br>
        <strong>No backend</strong>, criei o serviço de agregação que soma as horas por projeto e por período, calcula a semana de sprint correspondente a cada registro e acumula o total progressivamente. Também adicionei um filtro por programa e por status de projeto, para que o gráfico só mostre projetos relevantes no contexto analisado.
    </blockquote>

```python
# api/services/horas_svc.py
def get_burnup_horas_projetos(programa_id=None):
    filtros = {'projeto__status': 'Em andamento'}
    if programa_id:
        filtros['projeto__programa_id'] = programa_id

    registros = (
        FatoHoras.objects
        .filter(**filtros)
        .values('projeto__id', 'projeto__codigo_projeto', 'tempo__ano', 'tempo__mes')
        .annotate(total_horas=Sum('horas_trabalhadas'))
        .order_by('projeto__id', 'tempo__ano', 'tempo__mes')
    )

    projetos_map = defaultdict(list)
    for registro in registros:
        projeto_id = registro['projeto__id']
        projeto_nome = registro['projeto__codigo_projeto']
        mes_str = f"{registro['tempo__mes']:02d}/{registro['tempo__ano']}"
        projetos_map[(projeto_id, projeto_nome)].append({
            'mes': mes_str,
            'horas': float(registro['total_horas'] or 0),
        })

    resultado = []
    for (projeto_id, projeto_nome), serie in projetos_map.items():
        acumulado = 0
        serie_final = []
        for ponto in serie:
            acumulado += ponto['horas']
            serie_final.append({
                "mes": ponto['mes'],
                "horas": ponto['horas'],
                "horas_acumuladas": acumulado,
            })
        resultado.append({
            "projeto_id": projeto_id,
            "projeto": projeto_nome,
            "serie": serie_final,
        })
    return resultado
```

  <blockquote>
        <strong>No frontend</strong>, implementei o componente Vue que renderiza o gráfico com Chart.js, incluindo o cálculo dinâmico do eixo X (baseado nas semanas realmente registradas, não em um intervalo fixo), tooltip customizado mostrando as horas acumuladas por projeto, e paleta em tons de cinza para diferenciar as linhas sem depender de legendas coloridas chamativas.
    </blockquote>

```vue
<!-- src/components/BurnupHorasChart.vue -->
<script setup lang="ts">
  import { Chart } from 'chart.js'
  import { ref, shallowRef, watch } from 'vue'
  import { useProjetoStore } from '@/stores/projeto'

  const store = useProjetoStore()
  const canvasRef = ref<HTMLCanvasElement | null>(null)
  const chartInstance = shallowRef<null | Chart>(null)

  function buildChart () {
    if (!canvasRef.value || store.burnupHoras.length === 0) return
    if (chartInstance.value) {
      chartInstance.value.destroy()
      chartInstance.value = null
    }

    const labels = Array.from(
      new Set(store.burnupHoras.flatMap(p => p.serie.map(pt => pt.semana))),
    ).sort((a, b) => {
      const semanaA = Number(a.match(/\d+/)?.[0] || 0)
      const semanaB = Number(b.match(/\d+/)?.[0] || 0)
      return semanaA - semanaB
    })

    const projects: any = {}
    for (const projeto of store.burnupHoras) {
      projects[projeto.projeto] = {
        label: projeto.projeto,
        data: Array.from({ length: labels.length }).fill(null),
        spanGaps: true,
      }
      for (const ponto of projeto.serie) {
        const index = labels.indexOf(ponto.semana)
        if (index !== -1) projects[projeto.projeto].data[index] = Number(ponto.horas_acumuladas)
      }
    }

    chartInstance.value = new Chart(canvasRef.value, {
      type: 'line',
      data: { labels, datasets: Object.values(projects) },
      options: {
        responsive: true,
        interaction: { mode: 'index', intersect: false },
        plugins: {
          tooltip: {
            callbacks: {
              label: (ctx: any) => `${ctx.dataset.label}: ${Number(ctx.parsed.y).toLocaleString('pt-BR')}h acumuladas`,
            },
          },
        },
        scales: {
          x: { title: { display: true, text: 'Semana' } },
          y: { beginAtZero: true, title: { display: true, text: 'Horas investidas' } },
        },
      },
    })
  }

  watch(() => store.burnupHoras, () => buildChart(), { deep: true })
</script>
```

  <blockquote>
        O gráfico passou por vários ciclos de ajuste até o comportamento final: inicialmente eu agrupava por data exata, depois migrei para agrupamento por semana de sprint; tive que corrigir o "overflow" de semanas além da 4ª (projetos que ultrapassavam a duração planejada precisavam continuar aparecendo, agrupados em "semana 4+"), e ajustar para que a linha de cada projeto parasse no seu último ponto ativo em vez de se estender artificialmente até o fim do gráfico.
    </blockquote>
</details>

<details>
  <summary>🛒 Previsão e Alertas de Compra de Materiais</summary>
    <blockquote>
        Implementei o algoritmo que sugere quando e quais materiais precisam ser comprados novamente, com base no consumo médio diário, no estoque atual, nas compras já pendentes e no lead time histórico de cada fornecedor. A lógica calcula, para cada material, quantos dias de cobertura de estoque ainda restam e subtrai o lead time do fornecedor para descobrir a data-limite em que o pedido precisa ser feito.
    </blockquote>

```python
# api/services/alertas_svc.py
DIAS_COBERTURA_MAX = 60
STATUS_ENTREGUE = 'Entregue'

def get_sugestao_proxima_compra(data_referencia=None):
    data_referencia = data_referencia or date.today()

    tempo_range = FatoMateriais.objects.aggregate(
        data_min=Min('tempo__data'), data_max=Max('tempo__data'),
    )
    if not tempo_range['data_min']:
        return _empty_sugestao_proxima_compra()

    dias_periodo = max((tempo_range['data_max'] - tempo_range['data_min']).days + 1, 1)
    consumo_map = _get_consumo_map(dias_periodo)
    if not consumo_map:
        return _empty_sugestao_proxima_compra()

    estoque_map = _get_estoque_map()
    pendente_map = _get_pendente_map()
    lead_time_map = _build_lead_time_map(
        FatoCompras.objects
        .filter(lead_time__isnull=False, status__nome_status=STATUS_ENTREGUE)
        .values('material_id', 'fornecedor_id', 'fornecedor__razao_social')
        .annotate(lt_medio=Min('lead_time'))
    )

    materiais = []
    for mat_id, consumo_diario in consumo_map.items():
        if consumo_diario <= 0:
            continue
        estoque = estoque_map.get(mat_id, 0)
        pendente = pendente_map.get(mat_id, 0)
        dias_cobertura = (estoque + pendente) / consumo_diario
        if dias_cobertura >= DIAS_COBERTURA_MAX:
            continue

        lead_time, fornecedor = lead_time_map.get(mat_id, (30, 'Fornecedor não definido'))
        dias_para_pedir = dias_cobertura - lead_time
        data_limite_compra = data_referencia + timedelta(days=round(dias_para_pedir))

        materiais.append({
            'material_id': mat_id,
            'dias_cobertura': round(dias_cobertura),
            'lead_time': round(lead_time),
            'data_limite_compra': data_limite_compra.isoformat(),
            'comprar_imediatamente': data_limite_compra <= data_referencia,
        })

    if not materiais:
        return _empty_sugestao_proxima_compra()

    materiais.sort(key=lambda item: item['data_limite_compra'])
    return {
        'data_sugerida': materiais[0]['data_limite_compra'],
        'comprar_imediatamente': materiais[0]['comprar_imediatamente'],
        'materiais': materiais,
    }
```

  <blockquote>
        Também escrevi os testes unitários que validam os principais cenários de negócio da função — por exemplo, garantir que materiais com estoque confortável (cobertura acima de 60 dias) não gerem alerta, e que a compra seja sinalizada como imediata quando a data-limite já passou:
    </blockquote>

```python
# api/tests/test_alertas_unit.py
def test_retorna_compra_imediata_quando_data_limite_ja_passou(self):
    material = baker.make('api.DimMaterial', descricao='Sensor')
    ...
    resultado = get_sugestao_proxima_compra(data_referencia=date(2024, 4, 1))

    assert resultado['comprar_imediatamente'] is True
    assert resultado['materiais'][0]['fornecedor_sugerido'] == 'Fornecedor A'

def test_ignora_material_com_cobertura_maior_ou_igual_a_60(self):
    ...
    resultado = get_sugestao_proxima_compra(data_referencia=date(2024, 4, 1))
    assert resultado['materiais'] == []
    assert resultado['mensagem'] == 'Nenhum material precisa de compra no momento'
```

  <blockquote>
        No frontend, criei o card e o dropdown que exibem essa recomendação na tela de planejamento, com rolagem interna para o caso de múltiplos materiais precisarem de compra simultaneamente, e ajustei o layout depois de validar com o time que o card estava cortando sugestões quando a lista crescia.
    </blockquote>
</details>

### 🔬 Como QA

Esse foi meu primeiro contato tanto com DevOps quanto com QA dentro de um projeto real. Gostei bastante da experiência, principalmente por perceber o quanto o papel de QA se aproxima do papel de Scrum Master que já tinha exercido antes — ambos giram em torno de cuidar do processo, identificar riscos e ajudar o time a entregar com mais qualidade, só que com focos e ferramentas diferentes.

Além de desenvolver, fui responsável por estruturar toda a frente de qualidade do projeto — desde a definição de processos até a escolha e configuração das ferramentas usadas pelo time inteiro, tanto no backend quanto no frontend.

<details>
  <summary>🗓️ Facilitação de Qualidade nas Cerimônias Scrum</summary>
    <blockquote>
        Atuei como uma espécie de guardião da qualidade dentro das cerimônias ágeis do time:
        <br><br>
        • <strong>Sprint Planning</strong> — a partir da minha entrada no time na Sprint 2, apoiava a equipe a validar se as histórias atendiam ao DoR já estabelecido antes de entrarem na sprint.<br>
        • <strong>Daily Scrum</strong> — acompanhava impedimentos e riscos relacionados à qualidade que pudessem comprometer a entrega.<br>
        • <strong>Sprint Review</strong> — validava se os resultados apresentados de fato atendiam ao DoD antes de serem considerados concluídos.<br>
        • <strong>Sprint Retrospective</strong> — ajudava a identificar padrões recorrentes de problemas (ex: falhas de cobertura, retrabalho em code review) para propor melhorias no ciclo seguinte.
    </blockquote>
</details>

<details>
  <summary>📊 Métricas de Acompanhamento do Projeto</summary>
    <blockquote>
        Defini e consolidei as métricas usadas para acompanhar a saúde do projeto ao longo das sprints:
        <br><br>
        • <strong>Burndown</strong> — evolução do trabalho restante dentro da sprint.<br>
        • <strong>Burnup</strong> — relação entre escopo total e o que já foi entregue (interessante notar que a métrica de processo do QA e a funcionalidade de produto que desenvolvi como Developer compartilham o mesmo conceito, aplicado a contextos diferentes).<br>
        • <strong>Velocity</strong> — capacidade de entrega do time por sprint, usada para calibrar o planejamento das sprints seguintes.<br>
        • <strong>Throughput</strong> (geral e por integrante) — fluxo de entrega de tarefas ao longo do tempo, usado também para identificar equilíbrio na distribuição de trabalho entre os membros do time.<br>
        • <strong>Precisão de estimativas</strong> — comparação entre horas estimadas e realizadas, calculada como <code>Estimado ÷ Realizado × 100</code>, usada para melhorar a calibragem de estimativas futuras.
    </blockquote>
</details>

<details>
  <summary>✅ Ferramentas de Qualidade e Pipeline de CI</summary>
    <blockquote>
        Estruturei e documentei o conjunto de ferramentas de qualidade usado nos dois repositórios do projeto (backend e frontend), garantindo que nenhum código chegasse à branch principal sem passar por validação automática:
    </blockquote>

**Backend:**
```
isort api scripts   →   black api scripts   →   flake8 api scripts   →   pytest   →   pre-commit run --all-files
```

```ini
# .flake8
[flake8]
max-line-length = 88
extend-ignore =
    E203

per-file-ignores =
    api/models/__init__.py:F401
```

```toml
# pyproject.toml
[tool.black]
target-version = ["py312"]

[tool.isort]
profile = "black"
line_length = 88
skip = ["venv", "migrations"]
```

  <blockquote>
        Configurei também o limiar mínimo de <strong>80% de cobertura de testes</strong> no pytest (via <code>pytest.ini</code> e <code>coverage.xml</code>), abaixo do qual o pipeline do GitHub Actions falha automaticamente e bloqueia o merge do Pull Request.
    </blockquote>

**Frontend:**
```
npm run lint   →   npm run type-check   →   npm run test:coverage   →   npm run build
```

  <blockquote>
        No SonarCloud, configurei os dois projetos (<code>23deFevereiro_API_5_SEM_BACK</code> e <code>23deFevereiro_API_5_SEM_FRONT</code>) para monitorar cobertura, duplicação de código, code smells e vulnerabilidades, com exclusões específicas para migrations, testes e arquivos gerados automaticamente — e também documentei o passo a passo para o time conectar o SonarQube for IDE localmente no VS Code, permitindo identificar problemas antes mesmo de abrir um Pull Request.
    </blockquote>
</details>

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
    <td>Vue.js 3 (Composition API)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Django / Django REST Framework</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>PostgreSQL (Star Schema)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Testes Automatizados (pytest/Vitest)</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>SonarCloud</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>Flake8 / Black / isort / ESLint</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
  <tr>
    <td>CI/CD (GitHub Actions)</td>
    <td>★★★★☆</td>
    <td>Sei fazer com ajuda</td>
  </tr>
  <tr>
    <td>Docker</td>
    <td>★★★☆☆</td>
    <td>Entendi</td>
  </tr>
  <tr>
    <td>Git/GitHub (submódulos e PRs)</td>
    <td>★★★★★</td>
    <td>Sei fazer com autonomia</td>
  </tr>
</table>

### 🤝 Soft Skills

<table align="center">
  <tr>
    <th width="270px">Habilidade</th>
    <th width="280px">Casos de uso</th>
  </tr>
  <tr>
    <td>Visão Full Stack</td>
    <td>Desenvolvi a funcionalidade de burnup de ponta a ponta, do serviço no backend à visualização no frontend.</td>
  </tr>
  <tr>
    <td>Atenção a Detalhes</td>
    <td>Refinei diversas vezes a exibição do gráfico de burnup (eixo, hover, semanas) até alinhar com o comportamento esperado.</td>
  </tr>
  <tr>
    <td>Pensamento Analítico</td>
    <td>Modelei a lógica de sugestão de compra com base em lead time e histórico de consumo dos materiais.</td>
  </tr>
  <tr>
    <td>Cultura de Qualidade</td>
    <td>Apliquei e reforcei o DoR e o DoD já estabelecidos pelo time, disseminando boas práticas de qualidade como responsável pela frente de QA a partir da Sprint 2.</td>
  </tr>
  <tr>
    <td>Visão Analítica de Processo</td>
    <td>Consolidei métricas como burndown, burnup, velocity, throughput e precisão de estimativas para acompanhar a saúde do projeto.</td>
  </tr>
</table>

---

</p>