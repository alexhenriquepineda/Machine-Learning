# Algoritmo Support Vector Machine (SVM)

## Princípios Básicos

### Hiperplano de Separação
Em um problema de classificação binária, o objetivo do SVM é encontrar um hiperplano que melhor separe as duas classes de dados. Este hiperplano é definido como uma linha (em 2D) ou um plano (em 3D) que divide o espaço de características.

### Margem Máxima
A margem é a distância entre o hiperplano de separação e os pontos de dados mais próximos de cada classe, conhecidos como vetores de suporte. O SVM busca maximizar esta margem para aumentar a separação entre as classes, o que geralmente melhora a capacidade de generalização do modelo.

### Vetores de Suporte
Os vetores de suporte são os pontos de dados que estão mais próximos do hiperplano de separação. Eles são críticos para definir a posição e a orientação do hiperplano. O nome "Support Vector Machine" deriva do fato de que apenas esses pontos de suporte influenciam a posição do hiperplano, enquanto os outros pontos de dados não têm impacto direto.

## Funcionamento do SVM

1. **Construção do Hiperplano**
   - O SVM inicialmente tenta encontrar um hiperplano linear que separe os dados de duas classes. Este hiperplano é definido pela equação: 


$$w \cdot x + b = 0$$


Onde:
     - $\(w \)$ é o vetor de pesos.
     - $\( x \)$ é o vetor de características.
     - $\( b \)$ é o termo de bias.

2. **Maximização da Margem**
   - O objetivo é encontrar os valores de \( w \) e \( b \) que maximizem a margem. A margem é maximizada resolvendo o problema de otimização:

     
     $$\min \frac{1}{2} \|w\|^2$$
     

     Sujeito às restrições:

     
   $$y_i (w \cdot x_i + b) \geq 1$$
   

     Onde $\( y_i \)$ é a classe dos pontos de dados $\( x_i \)$.

3. **Função de Custo e Lagrangeanos**
   - A otimização do SVM é realizada usando multiplicadores de Lagrange, que transformam o problema de otimização em um problema de minimização. A função Lagrangiana é dada por:

     
     $$L(w, b, \alpha) = \frac{1}{2} \|w\|^2 - \sum_{i=1}^{n} \alpha_i [y_i (w \cdot x_i + b) - 1]$$
     

     Onde $\( \alpha_i \)$ são os multiplicadores de Lagrange.

4. **Função Kernel**
   - Para casos onde os dados não são linearmente separáveis, o SVM utiliza funções kernel para mapear os dados para um espaço de alta dimensão onde um hiperplano linear pode ser usado para separação. Funções kernel comuns incluem:
     - **Kernel Linear**: $\( K(x_i, x_j) = x_i \cdot x_j \)$
     - **Kernel Polinomial**: $\( K(x_i, x_j) = (x_i \cdot x_j + c)^d \)$
     - **Radial Basis Function (RBF)**: $\( K(x_i, x_j) = \exp(-\gamma \|x_i - x_j\|^2) \)$
     - **Kernel Sigmoide**: $\( K(x_i, x_j) = \tanh(\alpha x_i \cdot x_j + c) \)$

5. **Classificação Multiclasse**
   - Embora o SVM seja originalmente um classificador binário, ele pode ser adaptado para problemas multiclasse usando estratégias como "um contra todos" (one-vs-all) ou "um contra um" (one-vs-one). Na estratégia "one-vs-all", um classificador SVM é treinado para cada classe, diferenciando-a de todas as outras classes. Na estratégia "one-vs-one", um classificador SVM é treinado para cada par de classes.

## Vantagens e Desvantagens

### Vantagens
- **Alta Eficácia em Espaços de Alta Dimensão**: O SVM é eficiente em espaços de alta dimensão, onde o número de dimensões é maior que o número de amostras.
- **Eficiência em Memória**: Utiliza um subconjunto de pontos de treinamento (vetores de suporte) no processo de decisão.
- **Flexibilidade**: O uso de funções kernel permite que o SVM se adapte a dados não linearmente separáveis.

### Desvantagens
- **Ineficiente para Grandes Conjuntos de Dados**: O SVM pode ser computacionalmente intensivo para grandes conjuntos de dados.
- **Escolha do Kernel**: O desempenho do SVM depende da escolha apropriada do kernel e dos parâmetros do kernel.
- **Sobreposição das Classes**: Pode ser menos eficaz quando as classes são bastante sobrepostas.

Em resumo, o SVM é uma ferramenta poderosa no arsenal de algoritmos de aprendizado de máquina, oferecendo um bom equilíbrio entre complexidade e capacidade de generalização, especialmente em problemas de classificação complexos.

```python
# Importar bibliotecas necessárias
import numpy as np
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score

# Carregar conjunto de dados Iris
iris = datasets.load_iris()
X = iris.data
y = iris.target

# Dividir o conjunto de dados em treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Criar o classificador SVM
svm_model = SVC(kernel='linear')

# Treinar o modelo
svm_model.fit(X_train, y_train)

# Fazer previsões no conjunto de teste
y_pred = svm_model.predict(X_test)

# Avaliar a precisão do modelo
accuracy = accuracy_score(y_test, y_pred)
print(f'Acurácia: {accuracy * 100:.2f}%')
```
