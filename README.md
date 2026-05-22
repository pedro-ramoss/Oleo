📈 Previsão do Preço do Petróleo com Machine Learning (Versão 2)
📖 Sobre o Projeto

Este projeto representa a segunda versão do meu estudo de previsão de preços do petróleo utilizando Ciência de Dados e Machine Learning.

A primeira versão foi desenvolvida durante os meus primeiros contatos com análise de dados em Python. O foco era entender conceitos fundamentais como manipulação de datasets, visualização de informações e construção de modelos preditivos básicos.

Após aprofundar meus conhecimentos em Python, análise exploratória de dados e algoritmos de Machine Learning, decidi reconstruir o projeto aplicando técnicas mais avançadas e uma estrutura mais organizada. O resultado foi uma solução mais robusta, capaz de realizar previsões futuras com melhor desempenho e maior confiabilidade.

🎯 Objetivo

Construir um modelo de Machine Learning capaz de prever o preço de fechamento do petróleo para os próximos 7 dias com base no comportamento histórico do mercado.

Além da previsão, o projeto busca demonstrar todo o fluxo de trabalho de um cientista de dados:

Importação dos dados
Limpeza e tratamento
Análise exploratória
Engenharia de atributos
Treinamento do modelo
Avaliação de desempenho
Geração de previsões futuras
📊 Base de Dados

A base utilizada contém informações históricas do mercado de petróleo entre agosto de 2000 e abril de 2026, incluindo:

Data
Preço de abertura
Máxima do dia
Mínima do dia
Fechamento
Variação percentual diária

Total de registros analisados: 6.435 observações.

🔍 Análise Exploratória

Durante a etapa exploratória foram realizadas:

Evolução histórica do preço

Visualização da série temporal para identificação de tendências e ciclos de mercado.

Distribuição das variações diárias

Análise da volatilidade dos preços através de histogramas.

Correlação entre variáveis

Construção de uma matriz de correlação para compreender a relação entre os indicadores do mercado.

⚙️ Engenharia de Atributos

Para melhorar a capacidade preditiva do modelo foram criadas novas variáveis temporais:

Dia
Mês
Ano

Também foi criada a variável alvo:

Fechamento_futuro_7d

Representando o preço de fechamento esperado sete dias após cada observação.

🤖 Modelo Utilizado

Foi utilizado o algoritmo:

Random Forest Regressor

Configuração:

RandomForestRegressor(
    n_estimators=200,
    max_depth=10,
    random_state=42
)

A divisão dos dados foi realizada respeitando a ordem temporal:

80% para treinamento
20% para teste

Sem embaralhamento dos registros (shuffle=False), preservando a natureza temporal da série.

📈 Resultados

Métricas obtidas no conjunto de teste:

Métrica	Resultado
R²	0.8263
MAE	3.8519
RMSE	5.3696
Interpretação
O modelo consegue explicar aproximadamente 82,6% da variação dos preços futuros.
O erro médio absoluto ficou próximo de US$ 3,85 por barril.
Os resultados indicam boa capacidade de captura dos padrões históricos do mercado.
🔮 Exemplo de Previsão

Último preço registrado:

US$ 96.57

Preço previsto para 7 dias à frente:

US$ 97.57

Variação prevista:

+1.00 US$/barril
🚀 Evolução em Relação à Versão 1
Versão 1	Versão 2
Análise básica dos dados	Análise exploratória completa
Poucas visualizações	Diversos gráficos analíticos
Estrutura simples	Pipeline organizado
Foco em aprendizado inicial	Aplicação de boas práticas
Sem previsão futura estruturada	Previsão para 7 dias à frente
Avaliação limitada	Métricas R², MAE e RMSE
Menor compreensão do problema	Engenharia de atributos e modelagem mais robusta

Esta evolução demonstra meu desenvolvimento em áreas como análise exploratória, preparação de dados, modelagem preditiva e avaliação de algoritmos de Machine Learning.

🛠️ Tecnologias Utilizadas
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-Learn
Random Forest Regressor
📚 Aprendizados

Ao longo do desenvolvimento deste projeto aprofundei conhecimentos em:

Manipulação de dados com Pandas
Estatística aplicada
Visualização de dados
Feature Engineering
Machine Learning supervisionado
Avaliação de modelos de regressão
Organização de projetos de Ciência de Dados
Boas práticas de programação em Python
