# Introdução à Regressão Ridge

## Regressão Linear Simples
Na regressão linear simples, buscamos encontrar uma linha que melhor se ajuste aos dados. O modelo é representado pela equação:

\[ y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_p x_p \]

Onde:
- \( y \) é a variável dependente.
- \( x_1, x_2, \ldots, x_p \) são as variáveis independentes.
- \( \beta_0, \beta_1, \ldots, \beta_p \) são os coeficientes do modelo.

## Problemas da Regressão Linear
1. **Multicolinearidade**: Quando duas ou mais variáveis independentes estão altamente correlacionadas, pode ser difícil estimar os coeficientes de forma precisa.
2. **Overfitting**: Em modelos com muitas variáveis, o modelo pode se ajustar demais aos dados de treinamento, capturando o ruído em vez do sinal.

## Regularização
Para mitigar esses problemas, usamos técnicas de regularização, que adicionam uma penalidade aos coeficientes do modelo. A Regressão Ridge é uma forma de regularização que utiliza a penalidade L2.

## Regressão Ridge
A Regressão Ridge adiciona um termo de penalização ao erro residual da regressão linear. A função de custo a ser minimizada na Regressão Ridge é:

\[ J(\beta) = \sum_{i=1}^{n} \left( y_i - \hat{y}_i \right)^2 + \lambda \sum_{j=1}^{p} \beta_j^2 \]

Onde:
- \(\sum_{i=1}^{n} \left( y_i - \hat{y}_i \right)^2\) é a soma dos erros quadrados (termo de erro).
- \(\lambda \sum_{j=1}^{p} \beta_j^2\) é o termo de penalização L2, onde \(\lambda\) é um parâmetro de regularização.

## Vantagens da Regressão Ridge
1. **Redução do Overfitting**: O termo de penalização ajuda a evitar que o modelo se ajuste demais aos dados de treinamento.
2. **Trata Multicolinearidade**: Ao penalizar os coeficientes, a Regressão Ridge pode lidar melhor com variáveis altamente correlacionadas.

## Desvantagens
1. **Não Zera Coeficientes**: Ao contrário da Regressão Lasso (outra técnica de regularização), a Regressão Ridge não zera coeficientes, o que pode ser uma desvantagem se você quiser um modelo mais interpretável com algumas variáveis eliminadas.

## Implementação
A Regressão Ridge pode ser implementada em várias bibliotecas de machine learning, como o scikit-learn em Python. Aqui está um exemplo básico:

```python
from sklearn.linear_model import Ridge
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_boston
from sklearn.metrics import mean_squared_error

# Carregar um conjunto de dados de exemplo
data = load_boston()
X = data.data
y = data.target

# Dividir os dados em conjunto de treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Criar e ajustar o modelo de Regressão Ridge
ridge_reg = Ridge(alpha=1.0)  # alpha é o parâmetro de regularização
ridge_reg.fit(X_train, y_train)

# Fazer previsões e avaliar o modelo
y_pred = ridge_reg.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f'Mean Squared Error: {mse}')
