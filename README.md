Em classificação binária, essas métricas são diretas. Por exemplo, a Sensibilidade (Recall) é a taxa de verdadeiros positivos, e a Especificidade é a taxa de verdadeiros negativos.

No entanto, em um cenário multiclasse, temos mais de duas classes (neste caso, diferentes níveis de obesidade).

Para avaliar o desempenho do modelo em todas as classes, as métricas são frequentemente calculadas para cada classe individualmente e depois combinadas usando diferentes métodos de média.

No código trabalhado, usei a média weighted (ponderada) para Precisão, Sensibilidade (Recall) e F1-score.

Cálculo das métricas por classe: 

Para cada classe (por exemplo, 'Normal_Weight', 'Obesity_Type_III'), a métrica é calculada como se fosse um problema de classificação binária, onde essa classe é a classe "positiva" e todas as outras classes são a classe "negativa".

Média Ponderada: 

A média weighted calcula a métrica para cada classe e depois tira a média, ponderada pelo número de instâncias de cada classe nos rótulos verdadeiros (y_test). 
Isso é útil quando você tem um conjunto de dados desbalanceado (algumas classes têm significativamente mais amostras do que outras), pois dá mais importância ao desempenho nas classes mais frequentes.
Vamos analisar cada métrica no contexto da média ponderada para multiclasse:

Acurácia: 

Esta é a mais simples e é calculada da mesma forma em binária e multiclasse: a proporção de instâncias corretamente classificadas em relação ao número total de instâncias.

Precisão (ponderada): 

Para cada classe, é a razão entre as instâncias dessa classe corretamente previstas e o número total de instâncias previstas como essa classe. 
A média ponderada é a média dessas pontuações de precisão por classe, ponderada pelo número de instâncias verdadeiras para cada classe. 
Ela indica quantas das instâncias previstas como uma determinada classe realmente pertencem a essa classe, em média, considerando o desbalanceamento de classes.

Sensibilidade (Recall) (ponderada): 

Para cada classe, é a razão entre as instâncias dessa classe corretamente previstas e o número total de instâncias reais dessa classe. 
A média ponderada é a média dessas pontuações de recall por classe, ponderada pelo número de instâncias verdadeiras para cada classe. 
Ela indica quantas das instâncias reais de uma determinada classe foram corretamente identificadas pelo modelo, em média, considerando o desbalanceamento de classes.

Especificidade (ponderada): 

Como mostrei no código, calcular a especificidade em multiclasse é um pouco mais complexo. 
Para cada classe, é a razão entre os verdadeiros negativos (instâncias corretamente identificadas como não pertencentes a essa classe) e o número total de negativos reais (instâncias que não pertencem a essa classe). 
A média ponderada combina essas pontuações de especificidade por classe, ponderada pelo número de instâncias verdadeiras para cada classe. 
Ela indica quão bem o modelo evita classificar incorretamente instâncias como uma determinada classe, em média, considerando o desbalanceamento de classes.

F1-score (ponderado): 

Esta é a média harmônica da precisão e do recall para cada classe. A média ponderada é a média dessas pontuações de F1 por classe, ponderada pelo número de instâncias verdadeiras para cada classe. 
Ela fornece uma única pontuação que equilibra precisão e recall, dando uma melhor visão geral do desempenho do modelo, especialmente na presença de desbalanceamento de classes.
