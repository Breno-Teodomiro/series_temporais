# Capítulo 2 - Análise e Previsão de Séries Temporais

---

Projeto prático do **Capítulo 2** do curso da Data Science Academy, focado em **previsão de demanda de produtos ao longo do tempo** para apoiar decisões de logística e planejamento.

## Objetivo do Projeto

Construir e comparar modelos de séries temporais para prever `itens_vendidos` por data, loja e produto, usando três abordagens:

- `SARIMAX` (estatístico clássico)
- `Prophet` (modelo aditivo com sazonalidade)
- `XGBoost` (machine learning com engenharia de atributos temporais)

## Problema de Negócio que Este Projeto Resolve

Este projeto ajuda empresas de varejo e distribuição a responder perguntas como:

- **Quanto devo comprar/repor de cada produto nos próximos dias/semanas?**
- **Como evitar ruptura (falta) e excesso de estoque ao mesmo tempo?**
- **Como antecipar picos de demanda por sazonalidade, calendário e tendência?**
- **Como melhorar o planejamento operacional de compras, armazenagem e transporte?**

### Visão de impacto no negócio

Com previsões mais confiáveis, a empresa pode:

- Reduzir custo de estoque parado
- Diminuir perda de vendas por indisponibilidade de produto
- Planejar promoções e reposição com antecedência
- Melhorar nível de serviço (SLA) e experiência do cliente
- Apoiar decisões de compras com base em dados

## Dataset

Arquivo: `dados/dataset.csv`

- Período: **2013-01-01 a 2017-12-31**
- Registros: **913.000**
- Lojas: **10**
- Produtos: **50**
- Variável alvo: `itens_vendidos`

Colunas:

- `data`
- `loja`
- `produto`
- `itens_vendidos`

## Estrutura do Projeto

```text
cap02/
├── dados/
│   └── dataset.csv
├── imagens/
│   └── EC1.png
├── notebooks/
│   ├── EstudoCaso1-Parte1.ipynb   # SARIMAX
│   ├── EstudoCaso1-Parte2.ipynb   # Prophet
│   └── EstudoCaso1-Parte3.ipynb   # XGBoost
├── main.py
├── pyproject.toml
└── uv.lock
```

## Modelagem Aplicada

### 1) SARIMAX (`notebooks/EstudoCaso1-Parte1.ipynb`)

Fluxo principal:

- Análise exploratória da série
- Decomposição (tendência/sazonalidade/resíduo)
- Teste de estacionaridade (Dickey-Fuller)
- Diferenciação
- Ajuste e avaliação do modelo SARIMAX

Métricas registradas no notebook:

- `MAE`: **5.2111**
- `MSE`: **42.1234**

### 2) Prophet (`notebooks/EstudoCaso1-Parte2.ipynb`)

Fluxo principal:

- Preparação da série para o formato do Prophet
- Treinamento com componentes de tendência/sazonalidade
- Geração e avaliação de previsões

Métricas registradas no notebook:

- `MAE`: **5.1434**
- `MSE`: **41.5138**

### 3) XGBoost (`notebooks/EstudoCaso1-Parte3.ipynb`)

Fluxo principal:

- Engenharia de atributos de data/hora
- Criação de lags (`shift`)
- Rolling window features
- Exponentially Weighted Mean (EWM)
- Treino com validação e early stopping

Observação:

- O notebook contém o pipeline completo e treino, mas as células finais de `MAE/MSE` não estão salvas com saída no arquivo atual.

## Tecnologias

- Python 3.9.13
- NumPy, Pandas, Matplotlib
- Statsmodels
- Scikit-learn
- Prophet
- XGBoost
- JupyterLab
- Gerenciamento de ambiente: `uv`

## Como Executar

### 1) Pré-requisitos

- `uv` instalado
- Python `3.9.13`

### 2) Instalar dependências

```bash
uv sync
```

### 3) Rodar notebooks

```bash
uv run jupyter lab
```

Abra os notebooks na pasta `notebooks/` e execute as células em ordem.

## Próximos Passos Recomendados (Negócio + Técnico)

- Salvar e comparar formalmente as métricas dos 3 modelos no mesmo recorte temporal
- Definir baseline operacional (ex.: média móvel) para provar ganho real
- Incluir métricas de negócio (custo de ruptura, custo de estoque, fill rate)
- Avaliar performance por loja e por produto (segmentação)
- Criar rotina de re-treino periódico para uso em produção

## Autor

Projeto de estudos referente ao Capítulo 2 do curso **Análise e Previsão de Séries Temporais com Inteligência Artificial** (Data Science Academy).
