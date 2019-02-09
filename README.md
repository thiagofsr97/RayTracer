# RayTracer
Fernando Máximo Alves - 11500204

Thiago Filipe Soares da Rocha -  11502567

# Imagem

A imagem gerada com o render é de um gato feito de triângulos e que possui exatamente 9 triângulos, com as cores variando de acordo com a coordenada z de cada vértice.
# Implementação

A técnica utilizada no render foi o rayTracer que dispara "raios" de um posição de origem seguindo uma direção d nos objetos que se encontram na cena, para saber se um raio atingiu um objeto uma rotina de intersecção é executada. Nesse presente trabalho as rotinas de intersecção implementadas foram para testar a intersecção entre raio e triângulo.

Foram implementadas duas rotinas de intersecção raio triângulo, a primeira que se encontra no livro de Peter Shirley e a segunda de Moller e Trumbore que apresenta maior velocidade e menor custo de memória.

Para demonstrar a diferença entre os dois métodos, foi utilizado um for para criar 1000 imagens do gato totalizando um número de 9000 triângulos e o tempo de execução foi calculado para cada uma das rotinas utilizando o a biblioteca time.h .

Utilizando a rotina encontrada no livro de Peter Shirley o render levou um tempo de 22.82 segundos para renderizar a cena. Na rotina do artigo de Moller o render levou um tempo menor, que foi um total de 18.9 segundos para renderizar a cena.
