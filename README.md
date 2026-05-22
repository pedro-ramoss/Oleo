# 🎯 Objetivo

Prever o preço de fechamento do petróleo para os próximos 7 dias utilizando Machine Learning e dados históricos do mercado.


# 📦 Importação das Bibliotecas

```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score, mean_absolute_error, mean_squared_error
```

Nesta etapa foram importadas as bibliotecas responsáveis por:

Manipulação dos dados (Pandas)
Operações matemáticas (NumPy)
Visualização gráfica (Matplotlib e Seaborn)
Construção do modelo de Machine Learning (Scikit-Learn)
Avaliação do desempenho das previsões


# 📂 Carregamento dos Dados
```
df = pd.read_csv("Crude_Oil.csv", sep=",", parse_dates=["Date"])
df = df.sort_values("Date").reset_index(drop=True)
```

O dataset foi carregado e ordenado cronologicamente para preservar a sequência temporal dos preços do petróleo.

Isso é fundamental para evitar vazamento de informações futuras durante o treinamento.


# 🧹 Limpeza e Organização

```
df.drop(columns=["Volume", "Intraday_Volatility"], inplace=True)

df.columns = [
    "Data",
    "Abertura",
    "Alta",
    "Baixa",
    "Fechamento",
    "Variação"
]
```

Foram removidas colunas que não seriam utilizadas na modelagem.

Também foi realizada a padronização dos nomes das variáveis para facilitar a leitura e manutenção do código.


# 📊 Estatísticas Descritivas

```
df.describe()
```

Foram analisadas medidas estatísticas importantes:

Média
Mediana
Desvio padrão
Valores mínimos
Valores máximos

Essa etapa permitiu compreender a distribuição dos preços ao longo dos anos.


# 🔍 Verificação de Valores Nulos

```
df.isnull().sum()
```

Foi realizada uma validação da qualidade dos dados.

Nenhum valor ausente foi encontrado no conjunto de dados utilizado.


# 📈 Evolução Histórica dos Preços

```
plt.plot(df["Data"], df["Fechamento"])
```

O gráfico mostra a evolução do preço de fechamento do petróleo ao longo do tempo.

A visualização permite identificar:

Tendências de alta e baixa
Períodos de crise
Mudanças significativas no mercado


# 📉 Distribuição das Variações Diárias

```
sns.histplot(returns, bins=90, kde=True)
```

Foi construída uma distribuição das variações percentuais diárias.

O objetivo foi observar:

Frequência dos retornos
Concentração dos valores
Presença de movimentos extremos


# 🔗 Matriz de Correlação
```
corr = df.drop(columns=["Data"]).corr()
sns.heatmap(corr, annot=True)
```

A matriz de correlação permite identificar relações entre as variáveis do dataset.

Os preços de abertura, máxima, mínima e fechamento apresentaram forte correlação entre si, indicando comportamento semelhante.


# ⚙️ Engenharia de Atributos

```
df['Dia'] = df['Data'].dt.day
df['Mes'] = df['Data'].dt.month
df['Ano'] = df['Data'].dt.year
```
Foram criadas novas variáveis temporais a partir da data original.

Essas informações ajudam o modelo a identificar padrões sazonais ao longo do tempo.


# 🎯 Criação da Variável Alvo

```
df['Fechamento_futuro_7d'] = df["Fechamento"].shift(-7)
```

A variável alvo foi criada deslocando o preço de fechamento em 7 dias.

Dessa forma, o modelo aprende a prever o valor futuro utilizando apenas informações disponíveis no presente.


# 🏋️ Preparação para Treinamento

```
features = [
    'Abertura',
    'Alta',
    'Baixa',
    'Fechamento',
    'Variação',
    'Dia',
    'Mes',
    'Ano'
]
```

Foram selecionadas as variáveis que servirão como entrada para o modelo preditivo.

O objetivo é utilizar informações históricas e temporais para estimar o preço futuro.


# 🤖 Treinamento do Modelo

```
RandomForestRegressor(
    n_estimators=200,
    max_depth=10,
    random_state=42
)
```

Foi utilizado o algoritmo Random Forest Regressor.

Configurações utilizadas:

200 árvores de decisão
Profundidade máxima de 10 níveis
Semente fixa para reprodutibilidade

O Random Forest foi escolhido por sua capacidade de capturar relações não lineares nos dados.


# 📈 Comparação entre Valores Reais e Previstos

```
plt.plot(y_test)
plt.plot(y_pred)
```

Foi realizada uma comparação visual entre:

Valores reais
Valores previstos pelo modelo

A proximidade entre as curvas indica a capacidade do modelo em reproduzir os padrões históricos observados.


# 📏 Avaliação do Modelo

```
r2_score()
mean_absolute_error()
mean_squared_error()
```

Resultados    
Métrica	Valor    
R²	0.8263    
MAE	3.8519    
RMSE	5.3696    


O modelo explica aproximadamente 82,6% da variação dos preços.    
O erro médio absoluto foi de US$ 3,85 por barril.     
O RMSE indica boa precisão considerando a volatilidade natural do mercado de petróleo.    


# 🔮 Previsão Futura     

previsao[0]    
Resultado    
Indicador	Valor    
Preço Atual	US$ 96.57   
Preço Previsto (+7 dias)	US$ 97.57    
Análise    

O modelo estima uma leve valorização do petróleo para os próximos sete dias, demonstrando sua capacidade de gerar previsões futuras com base em padrões históricos.
