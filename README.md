# Acidentes nas rodovias federais de Pernambuco (PRF, 2025)

Projeto final do curso de **Analista de Dados da EBAC**: seleção, análise exploratória, tratamento e visualização de dados públicos de acidentes de trânsito.

**Dashboard interativo (Looker Studio):** [abrir o dashboard](https://datastudio.google.com/u/0/reporting/811ceb1a-4f5c-42e8-a8f1-2d85e763b02f/page/p_f5c0dxo08d)
**Relatório de insights:** [04_relatorio/Relatorio_Insights_PRF_PE_2025.pdf](04_relatorio/Relatorio_Insights_PRF_PE_2025.pdf)

## Problema

Onde, quando e por que acontecem os acidentes mais graves nas rodovias federais de Pernambuco, e quem são as vítimas?

## Principais resultados

Em 2025 a PRF registrou **3.013 acidentes** em PE, com **336 mortos** e **3.348 feridos**. 10,0% dos acidentes tiveram pelo menos uma morte.

- **BR-101 e BR-232** concentram 65% dos acidentes.
- **Madrugada (0h–5h):** 20,4% dos acidentes têm morte, contra 5,7% de manhã.
- **Pista simples:** 17,8% dos acidentes têm morte, contra 6,0% em pista dupla.
- **Colisão frontal** é o tipo mais letal (36,7 mortos a cada 100 acidentes).
- **Motos** respondem por 49% dos mortos; 27% dos pedestres envolvidos morreram.
- As causas mais frequentes são **falhas do condutor** (ausência de reação, reação tardia, acessar a via sem observar).

## Dados

| Tabela | Fonte | Linhas (PE) | Colunas |
| --- | --- | --- | --- |
| Ocorrências (1 linha por acidente) | [PRF – Dados abertos](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf) | 3.013 | 30 |
| Pessoas (1 linha por envolvido) | [PRF – Dados abertos](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf) | 7.646 | 35 |
| População por município | [IBGE – Estimativas 2025](https://www.ibge.gov.br/estatisticas/sociais/populacao/9103-estimativas-de-populacao.html) | 185 | 4 |

Relacionamentos: `ocorrencias.id = pessoas.id` e `ocorrencias.municipio = populacao.municipio` (código IBGE após o tratamento).

## Etapas

| Notebook | O que faz |
| --- | --- |
| [Etapa1_Selecao_Dados_PRF_PE.ipynb](Etapa1_Selecao_Dados_PRF_PE.ipynb) | Lê os arquivos da PRF e do IBGE, filtra PE, confere os requisitos mínimos e testa os cruzamentos |
| [Etapa2_Analise_Exploratoria_PRF_PE.ipynb](Etapa2_Analise_Exploratoria_PRF_PE.ipynb) | 9 análises: qualidade, tendência temporal, distribuição, outliers, correlação, causas e letalidade, mapa, perfil das vítimas, trechos críticos |
| [Etapa3_Tratamento_Dados_PRF_PE.ipynb](Etapa3_Tratamento_Dados_PRF_PE.ipynb) | Remove duplicatas, trata ausentes e valores impossíveis, padroniza formatos, cria 25 colunas derivadas e valida as tabelas finais |

## Estrutura do repositório

```
├── Etapa1_Selecao_Dados_PRF_PE.ipynb
├── Etapa2_Analise_Exploratoria_PRF_PE.ipynb
├── Etapa3_Tratamento_Dados_PRF_PE.ipynb
├── 01_dados_brutos/     arquivos originais da PRF e do IBGE
├── 02_dados_pe/         tabelas filtradas para Pernambuco (saída da Etapa 1)
├── 03_dados_finais/     tabelas tratadas usadas no dashboard (saída da Etapa 3)
└── 04_relatorio/        relatório de insights em PDF
```

## Como reproduzir

1. Abra os notebooks no [Google Colab](https://colab.research.google.com/).
2. Etapa 1: envie os arquivos de `01_dados_brutos/`.
3. Etapas 2 e 3: envie os arquivos de `02_dados_pe/`.

Ferramentas: Python (pandas, matplotlib), Google Colab e Looker Studio.
