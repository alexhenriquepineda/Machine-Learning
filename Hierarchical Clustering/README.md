# Motivação

Imagine que você é um Cientista de Dados trabalhando para uma empresa de varejo. Seu chefe solicita que você segmente os clientes nos seguintes grupos: clientes de baixo, médio, médio ou platinum com base no comportamento de gastos para fins de marketing direcionado e recomendações de produtos.

Sabendo que não há rótulo histórico associado a esses clientes, como é possível categorizá-los?

É aqui que o clustering pode ajudar. É uma técnica de aprendizado de máquina não supervisionado usada para agrupar dados não rotulados em categorias semelhantes.

Este tutorial irá focar mais na abordagem de clustering hierárquico, uma das muitas técnicas em aprendizado de máquina não supervisionado. Ele começará fornecendo uma visão geral do que é o clustering hierárquico, antes de compará-lo a algumas técnicas existentes.

Depois, ele guiará você por uma implementação passo a passo em Python usando a popular biblioteca Scipy.

## Definição de Clustering Hierárquico

A abordagem de clustering hierárquico é baseada na determinação de clusters sucessivos com base em clusters previamente definidos. É uma técnica voltada para agrupar dados em uma árvore de clusters chamada dendrograma, que representa graficamente a relação hierárquica entre os clusters subjacentes.
