# Regressao Linear

## Tipos de Relacionamento
### Determinístico:
Quando falamos de um fenômeno determinístico, estamos descrevendo algo que pode ser completamente previsto, com certeza absoluta, dadas as condições iniciais e as leis que regem esse fenômeno. Aqui estão algumas características importantes do pensamento determinístico:

1. Equação que descreve exatamente a relação entre duas variáveis:

- No contexto de modelagem matemática, uma relação determinística implica que existe uma equação ou função matemática que descreve exatamente como uma variável dependente é influenciada por uma variável independente. Por exemplo, se estamos estudando o movimento de um objeto em queda livre, podemos usar a equação da queda livre para prever exatamente a posição do objeto em qualquer momento no futuro, desde que conheçamos a posição inicial, a velocidade inicial e a aceleração devido à gravidade.

2. Certeza absoluta:

- Em um sistema determinístico, não há incerteza. Uma vez que todas as variáveis relevantes são conhecidas com precisão e as leis que governam o sistema são claras, podemos prever com certeza absoluta o resultado futuro.
  
3. Previsibilidade:

- Como não há incerteza, os eventos futuros em um sistema determinístico podem ser previstos com precisão, desde que possamos medir e entender completamente todas as variáveis envolvidas e as relações entre elas.

  
No entanto, na prática, muitos sistemas do mundo real não são completamente determinísticos devido a fatores como ruído, aleatoriedade ou falta de conhecimento completo sobre todas as variáveis e suas interações. Isso nos leva ao conceito de estocasticidade.

### Estocástico:

Ao contrário de um sistema determinístico, um sistema estocástico é caracterizado pela aleatoriedade e incerteza. Aqui estão algumas características importantes:

1. A relação entre duas variáveis não é perfeita:

- Em um contexto estatístico, uma relação entre duas variáveis não é perfeita, o que significa que não podemos prever com certeza absoluta o valor de uma variável dada o valor de outra. Em vez disso, lidamos com probabilidades e distribuições.
  
2. Incerteza:

- Em sistemas estocásticos, há uma certa quantidade de incerteza associada aos resultados futuros. Isso pode ser devido à natureza aleatória de certos eventos ou à nossa falta de conhecimento completo sobre todas as variáveis envolvidas e suas interações.
  
3. Aleatoriedade:

- A aleatoriedade desempenha um papel fundamental em sistemas estocásticos. Os resultados podem variar de uma realização para outra, mesmo quando as condições iniciais são as mesmas. Isso ocorre porque os eventos são influenciados por fatores aleatórios ou imprevisíveis.


Quando falamos sobre modelos de Machine Learning de regressão linear, estamos tratando de um tipo de relacionamento que se aproxima mais do determinístico do que do estocástico. Vou explicar por quê:

Determinístico:

Os modelos de regressão linear buscam estabelecer uma relação linear entre variáveis independentes e dependentes. Isso implica que, idealmente, há uma equação precisa que descreve a relação entre as variáveis, ou seja, um modelo determinístico. No entanto, na prática, os dados geralmente contêm algum nível de ruído ou variabilidade, o que significa que a relação encontrada pelo modelo pode não ser perfeitamente precisa. Portanto, embora o modelo busque capturar um relacionamento determinístico, ele pode não capturar todas as nuances da relação verdadeira.

Estocástico:

Embora os modelos de regressão linear sejam mais associados a relacionamentos determinísticos, eles ainda podem ser afetados por elementos estocásticos, especialmente devido ao ruído nos dados ou à presença de variabilidade não explicada. Isso significa que, embora o modelo procure estabelecer uma relação precisa entre as variáveis, há uma certa quantidade de incerteza associada às previsões do modelo. Essa incerteza pode ser quantificada por meio de técnicas estatísticas, como intervalos de confiança ou avaliação da significância dos coeficientes.
Em suma, os modelos de regressão linear são principalmente usados para capturar relacionamentos que se aproximam do determinístico, buscando estabelecer uma relação precisa entre as variáveis. No entanto, eles também reconhecem a presença de elementos estocásticos nos dados, o que pode resultar em alguma incerteza nas previsões do modelo.



## Equação da reta

A equação da reta de regressão linear é uma representação matemática da relação entre uma variável independente (x) e uma variável dependente (y). Ela é representada pela forma geral:

![linear-regression](https://media.geeksforgeeks.org/wp-content/uploads/20231129130431/11111111.png)

#### y = a + b.x

- y: É a variável dependente, ou seja, aquela que queremos prever ou explicar.
- x: É a variável independente, ou seja, aquela que usamos para prever ou explicar y.
- a: É o intercepto, também conhecido como coeficiente linear. Este termo representa o valor de y quando x é igual a zero. Ele determina onde a linha de regressão corta o eixo y. (Aumento ou diminuição da distância em relação ao eixo X.)
- b: É a inclinação, também conhecida como coeficiente angular. Este termo representa a mudança na variável dependente (y) para uma mudança unitária na variável independente (x). Em outras palavras, indica o quanto y muda quando x aumenta em uma unidade. (Altera o ângulo da reta em relação ao eixo X.)

### Premissas da Regressão Linear
1. A relação entre as características e a variável resposta é linear;
   - Esta premissa implica que a relação entre a variável independente (características) e a variável dependente (variável resposta) pode ser descrita por uma linha reta. Em outras palavras, a mudança na variável independente resulta em uma mudança proporcional na variável dependente. Se essa relação não for linear, a regressão linear pode não ser a técnica apropriada para modelar os dados.
2. Os erros são independentes;
   - Esta premissa afirma que os erros de previsão (diferença entre os valores observados e os valores previstos) não estão relacionados entre si. Em outras palavras, o erro em uma observação não influencia o erro em outra observação. Se os erros não forem independentes, isso pode levar a estimativas imprecisas dos parâmetros da regressão e a conclusões errôneas sobre a significância dos coeficientes.
3. Os erros são normalmente distribuídos;
   - Esta premissa assume que os erros de previsão seguem uma distribuição normal, ou seja, a distribuição dos erros é simétrica em torno de zero. Isso implica que a maioria dos erros está próxima de zero, com valores cada vez menores à medida que se afastam de zero. A normalidade dos erros é importante para fazer inferências estatísticas, como intervalos de confiança e testes de hipóteses, e para garantir que as previsões sejam precisas.
4. Os erros para cada valor previsto tem variâncias iguais;
   - Esta premissa, conhecida como homocedasticidade, significa que a dispersão dos erros em torno da linha de regressão é constante para todos os níveis da variável independente. Em outras palavras, a variabilidade dos erros é a mesma em toda a faixa de valores da variável independente. Se os erros tiverem variâncias desiguais, isso pode levar a estimativas enviesadas dos parâmetros e à imprecisão das previsões.




  
