# ENEM 2023 — Análise de Desempenho Educacional

> **"O que influencia o desempenho dos estudantes brasileiros?"**

---

## Contexto

O ENEM (Exame Nacional do Ensino Médio) é a maior avaliação educacional do Brasil, aplicada anualmente pelo INEP (Instituto Nacional de Estudos e Pesquisas Educacionais). Em 2023, quase 4 milhões de estudantes se inscreveram, tornando o exame uma das maiores fontes de dados educacionais do país.

Os microdados do ENEM são disponibilizados publicamente pelo INEP e permitem análises detalhadas sobre o desempenho dos estudantes, levando em consideração fatores como renda familiar, tipo de escola, raça/cor e localização geográfica.

---

## Objetivo

Este projeto tem como objetivo analisar os microdados do ENEM 2023 para responder à seguinte pergunta de negócio:

**O que influencia o desempenho dos estudantes brasileiros?**

Para isso, foram investigados os seguintes fatores:

- Desempenho por localização geográfica (estados e regiões)
- Impacto do tipo de escola (pública vs. privada)
- Influência da renda familiar no desempenho
- Diferenças por raça/cor e gênero
- Desempenho por disciplina

---

## Ferramentas utilizadas

| Ferramenta | Finalidade |
|------------|------------|
| **SQL (SQLite + DBeaver)** | Tratamento e análise dos dados |
| **Power BI** | Criação do dashboard executivo |

---

## ⚙️ Etapas do projeto

### 1. Coleta dos dados
Os microdados do ENEM 2023 foram obtidos diretamente no portal do INEP:
🔗 [gov.br/inep — Microdados ENEM](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/enem)

O arquivo contém **3.933.955 registros** com **76 colunas** cada.

### 2. Tratamento no SQL
O arquivo CSV foi importado diretamente no DBeaver (SQLite) e uma **view** foi criada para:

- Filtrar apenas participantes presentes nas 4 provas
- Traduzir os códigos do INEP para valores legíveis (ex: `TP_ESCOLA = 2` → `Pública`)
- Mapear as faixas de renda (Q006) conforme dicionário oficial do INEP
- Calcular a média geral de cada participante

### 3. Análise com SQL
Foram desenvolvidas **11 queries** cobrindo os principais aspectos do projeto, com uso de recursos avançados como:

- **Window Functions** (`RANK`, `LAG`)
- **CTEs** (Common Table Expressions)
- **CASE WHEN** para transformações
- **UNION ALL** para pivotamento de dados
- **GROUP BY** com múltiplas agregações

### 4. Dashboard no Power BI
O dashboard foi construído com **3 páginas temáticas**:

- **Visão Geral** — panorama nacional com KPIs, ranking dos estados e média por região
- **Fatores Socioeconômicos** — impacto da renda, tipo de escola e raça/cor
- **Desempenho Acadêmico** — análise por disciplina, gênero e perfil dos candidatos com nota 1000 na redação

---

## Principais insights

- **Alta abstenção**: 31,92% dos inscritos não compareceram — mais de 1,2 milhão de ausentes
- **MG lidera** o ranking nacional com média de **565 pts**; AM tem a menor média com **500 pts**
- **Desigualdade regional**: Sudeste (562 pts) supera o Norte (509 pts) em **53 pontos**
- **Gap escolar**: escola privada supera a pública em **105 pontos** de média geral
- **Renda é decisiva**: estudantes sem renda têm média de **480 pts**, enquanto a maior faixa alcança **658 pts** — diferença de **178 pontos**
- **Gênero e disciplina**: mulheres se destacam em redação (643 vs 599), homens em matemática (561 vs 517)
- **Raça/cor**: brancos têm a maior média (556 pts), indígenas a menor (490 pts) — gap de **66 pontos**
- **Nota 1000 na redação**: apenas 59 participantes atingiram a nota máxima — 77,97% do sexo feminino

---

## Dashboard

> O dashboard completo está disponível em [`dashboard/enem_2023.pdf`](dashboard/enem_2023.pdf)

**Página 1 — Visão Geral**
![Visão Geral](prints/pagina1.png)

**Página 2 — Fatores Socioeconômicos**
![Fatores Socioeconômicos](prints/pagina2.png)

**Página 3 — Desempenho Acadêmico**
![Desempenho Acadêmico](prints/pagina3.png)

---

## 🗃️ Fonte dos dados

- **INEP** — Microdados do ENEM 2023
- 🔗 [Download oficial](https://download.inep.gov.br/microdados/microdados_enem_2023.zip)
- **FGV Social** — Classificação de classes sociais por faixa de renda

---

## 👩‍💻 Autora

Desenvolvido como projeto de portfólio em **SQL e Power BI**.

---

*Projeto desenvolvido com dados públicos do INEP — Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira.*
