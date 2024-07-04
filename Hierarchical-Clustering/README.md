# Motivação

Imagine que você é um Cientista de Dados trabalhando para uma empresa de varejo. Seu chefe solicita que você segmente os clientes nos seguintes grupos: clientes de baixo, médio, médio ou platinum com base no comportamento de gastos para fins de marketing direcionado e recomendações de produtos.

Sabendo que não há rótulo histórico associado a esses clientes, como é possível categorizá-los?

É aqui que o clustering pode ajudar. É uma técnica de aprendizado de máquina não supervisionado usada para agrupar dados não rotulados em categorias semelhantes.

Este tutorial irá focar mais na abordagem de clustering hierárquico, uma das muitas técnicas em aprendizado de máquina não supervisionado. Ele começará fornecendo uma visão geral do que é o clustering hierárquico, antes de compará-lo a algumas técnicas existentes.

Depois, ele guiará você por uma implementação passo a passo em Python usando a popular biblioteca Scipy.

## Definição de Clustering Hierárquico

A abordagem de clustering hierárquico é baseada na determinação de clusters sucessivos com base em clusters previamente definidos. É uma técnica voltada para agrupar dados em uma árvore de clusters chamada dendrograma, que representa graficamente a relação hierárquica entre os clusters subjacentes.

# Comparação do Clustering Hierárquico com Outras Técnicas de Clustering

O clustering hierárquico é um algoritmo poderoso, mas não é o único disponível, e cada tipo de clustering possui suas vantagens e desvantagens.

Vamos entender como ele se compara a outros tipos de clustering, como K-means e clustering baseado em modelos. Existem muitas técnicas adicionais, mas essas duas, junto com o clustering hierárquico, são amplamente utilizadas e fornecem um framework para ajudar a entender melhor as outras.

Você pode aprender mais sobre clustering em aprendizado de máquina em nosso artigo separado, que cobre cinco algoritmos essenciais de clustering.

# Hierarchical clustering vs K Means clustering

Ao contrário do clustering hierárquico, o clustering K-means procura particionar os pontos de dados originais em "K" grupos ou clusters, onde o usuário especifica "K" antecipadamente.

A ideia geral é procurar clusters que minimizem a distância euclidiana quadrada de todos os pontos em relação aos centros em todos os atributos (variáveis ou características) e mesclar esses indivíduos de maneira iterativa.


## Benefícios
- É computacionalmente eficiente em comparação com o clustering hierárquico e pode ser usado para analisar grandes conjuntos de dados.
- O K-means é mais fácil de entender e implementar.

## Desvantagens
- É menos flexível do que o clustering hierárquico porque obriga o usuário a especificar o número de clusters antecipadamente, o que pode não ser óbvio em algumas situações.
- O resultado não é estável e muda de uma iteração para outra para o mesmo conjunto de dados.
- É mais sensível a outliers devido ao impacto dos outliers na média do cluster.
- Tanto o K-means quanto o clustering hierárquico são incapazes de lidar diretamente com dados categóricos e podem não funcionar bem com dados que não são contínuos ou têm variância muito grande.

Apesar de suas limitações, o clustering K-means ainda é um método popular devido à sua facilidade de uso e eficiência computacional. É frequentemente usado como ponto de referência para comparar o desempenho de outras técnicas de clustering.

# Model-based clustering

Tanto o clustering K-means quanto o clustering hierárquico utilizam uma matriz de distâncias para representar as distâncias entre todos os pontos no conjunto de dados. O clustering baseado em modelos, por outro lado, aplica técnicas estatísticas para identificar clusters nos dados. Abaixo está o processo geral:

1. Decidir o modelo estatístico a ser utilizado e escolher o número de clusters.
2. Ajustar o modelo aos dados.
3. Identificar os clusters com base nos parâmetros do modelo.

## Benefícios
- O clustering baseado em modelos é mais flexível do que o clustering hierárquico porque permite o uso de diferentes modelos para identificar diferentes tipos de clusters.
- Funciona melhor em dados com formas ou estruturas complexas.

## Desvantagens
- É computacionalmente mais caro do que o clustering hierárquico, especialmente para grandes conjuntos de dados.
- Requer um melhor entendimento das técnicas de modelagem estatística, pois a escolha do modelo pode afetar o resultado final.
- Assim como o clustering K-means, requer a especificação antecipada do número de clusters.

# Aplicações do Clustering Hierárquico

O clustering hierárquico tem uma variedade de aplicações em nossa vida cotidiana, incluindo (mas não se limitando a) biologia, processamento de imagens, marketing, economia e análise de redes sociais.

## Biologia
A clusterização de sequências de DNA é um dos maiores desafios na bioinformática. 

Os biólogos podem aproveitar o clustering hierárquico para estudar relações genéticas entre organismos e classificar esses organismos em grupos taxonômicos. Isso é benéfico para análise rápida e visualização das relações subjacentes.

## Processamento de Imagens
O clustering hierárquico pode ser utilizado no processamento de imagens para agrupar regiões ou pixels semelhantes de uma imagem em termos de cor, intensidade ou outras características. Isso pode ser útil para tarefas adicionais como segmentação de imagens, classificação de imagens e reconhecimento de objetos.

## Marketing
Especialistas em marketing podem usar o clustering hierárquico para estabelecer uma hierarquia entre diferentes tipos de clientes com base em seus hábitos de compra para melhores estratégias de marketing e recomendações de produtos. Por exemplo, diferentes produtos em varejo podem ser recomendados aos clientes sejam eles de baixo, médio ou alto gasto.

## Análise de Redes Sociais
Redes sociais são uma grande fonte de informações valiosas quando exploradas eficientemente. O clustering hierárquico pode ser usado para identificar grupos ou comunidades e entender suas relações entre si e a estrutura da rede como um todo.

# O Algoritmo de Clustering Hierárquico

Nesta seção, vamos abordar três conceitos principais: os passos do algoritmo hierárquico, um destaque sobre os dois tipos de clustering hierárquico (aglomerativo e divisivo) e, finalmente, algumas técnicas para escolher a medida de distância correta.

## Passos envolvidos no algoritmo de clustering hierárquico

O algoritmo de clustering hierárquico utiliza medidas de distância para gerar clusters. Esse processo de geração envolve os seguintes passos principais:

1. **Preprocessamento dos dados**: Pré-processar os dados removendo dados ausentes e aplicando quaisquer tarefas adicionais para tornar os dados o mais limpos possível. Este passo é mais geral para a maioria das tarefas de aprendizado de máquina.

2. **Calcular a matriz de distância**: Calcular a matriz de distância que contém a distância entre cada par de pontos de dados usando uma métrica de distância específica, como distância Euclidiana, distância Manhattan ou similaridade de cosseno. A métrica de distância padrão é a Euclidiana.

3. **Mesclar os clusters mais próximos**: Mesclar os dois clusters que estão mais próximos em termos de distância.

5. **Atualizar a matriz de distância**: Atualizar a matriz de distância com relação aos novos clusters formados.

6. **Repetir os passos 2, 3 e 4**: Repetir os passos de cálculo de distância, mesclagem de clusters e atualização da matriz de distância até que todos os clusters sejam mesclados para formar um único cluster.


# Exemplos de Clustering Hierárquico

Podemos considerar o clustering aglomerativo e divisivo como espelhos um do outro. Vamos dar uma olhada mais detalhada em como cada um opera, juntamente com um exemplo de clustering hierárquico e visualização gráfica.

## Clustering Hierárquico Aglomerativo

Este primeiro cenário corresponde à abordagem explicada anteriormente. Ele começa considerando cada observação como um cluster singleton (um cluster com apenas um ponto de dados). Em seguida, mescla iterativamente clusters até que apenas um cluster seja obtido. Esse processo também é conhecido como abordagem de baixo para cima.

Como mostrado na ilustração abaixo:

- Começamos considerando cada animal como seu próprio cluster único.
- Em seguida, geramos três clusters diferentes a partir desses animais únicos com base em suas similaridades:
  - Aves: Águia e Pavão
  - Mamíferos: Leão e Urso
  - Animais com mais de três pernas: Aranha e Escorpião
- Repetimos o processo de mesclagem para criar o cluster de vertebrados combinando os dois clusters mais similares: Aves e Mamíferos.
- Após este passo, os dois clusters restantes, Vertebrados e Animais com mais de três pernas, são mesclados para criar um único cluster de Animais.


# Clustering Divisivo

Por outro lado, o clustering divisivo é top-down porque começa considerando todos os pontos de dados como um único cluster. Em seguida, ele os separa até que todos os pontos de dados sejam únicos.

A partir deste gráfico de abordagem divisiva:

- Observamos que todo o conjunto de dados de animais é considerado como um único bloco.
- Em seguida, dividimos esse bloco em dois clusters: Vertebrados e Animais com mais de 3 pernas.
- O processo de divisão é aplicado iterativamente aos clusters criados anteriormente até obtermos animais únicos.


