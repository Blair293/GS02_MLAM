# Global Solution MLAM — Mobilidade urbana e bicicletas compartilhadas

## Integrantes
- Victor Hugo Lavaqui — RM: 573838

## Problema e objetivo
Investigar como condições climáticas e horários se relacionam com a demanda por bicicletas compartilhadas, aplicando probabilidade, testes de hipóteses, análise bivariada, regressão linear múltipla e regressão logística.

## Base de dados e fonte
**Bike Sharing Dataset — UCI Machine Learning Repository**
- Fonte oficial: https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset
- `dataset/hour.csv`: base principal, 17.379 registros horários.
- `dataset/day.csv`: base complementar, 731 registros diários.
- Dados de Washington, D.C., referentes a 2011–2012.

A variável resposta principal é `cnt` (total de aluguéis). `casual` e `registered` não são usadas como preditoras porque sua soma corresponde a `cnt`, evitando vazamento de informação.

## Estrutura
```text
Global-Solution-MLAM/
├── dataset/
│   ├── hour.csv
│   └── day.csv
├── notebooks/
│   └── analise_estatistica.ipynb
├── relatorio/
│   └── relatorio_estatistico.pdf
├── graficos/
│   ├── dispersao_temperatura_demanda.png
│   └── matriz_correlacao.png
├── requirements.txt
└── README.md
```

## Análises
1. Distribuição Normal: P(X < média) e P(X > mediana) para `cnt`, sob a premissa didática de Normalidade.
2. Testes Z unilaterais para média: n=20, α=6%, H1: μ<μ0; e n=25, α=9%, H1: μ>μ0.
3. Análise bivariada: `temp` × `cnt`, com dispersão, covariância, Pearson, regressão simples, R², teste F e previsão.
4. Regressão linear múltipla: `cnt` em função de `temp`, `hum`, `windspeed` e `hr`, com matrizes, R², teste F e previsão.
5. Regressão logística: classificação de demanda alta/baixa a partir de `temp`, `hum`, `windspeed` e `hr`, com equação, matriz de confusão e acurácia.

## Como executar
Requisitos: Python 3.10 ou superior.

Na raiz do repositório:
```bash
pip install -r requirements.txt
jupyter notebook
```
Abra `notebooks/analise_estatistica.ipynb` e execute as células em ordem. Os caminhos relativos do notebook contemplam a execução pela raiz do repositório ou pela pasta `notebooks`.

## Resultados e interpretação
O relatório PDF apresenta uma síntese dos resultados calculados na base. O notebook contém os códigos, tabelas, testes, equações, gráficos e previsões, permitindo reproduzir a análise.

## Limitações
- A Normalidade é uma hipótese solicitada no exercício; a distribuição empírica pode não ser Normal.
- Dados históricos de uma cidade específica (Washington, D.C., 2011–2012); não representam necessariamente a realidade atual ou de outras localidades.
- Correlação e regressão não demonstram causalidade.
- A classe alta/baixa depende do corte pela mediana da própria base.
- Recomenda-se validação temporal e atualização dos dados antes de uso operacional.
- `casual` e `registered` não entram como preditoras de `cnt` para evitar vazamento.

## Reprodutibilidade
Os testes de hipótese e a divisão treino/teste usam semente 42.
