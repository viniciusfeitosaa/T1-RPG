O problema Horror List consiste em determinar qual filme possui o maior Índice de Horror (Horror Index) dentro de um catálogo interconectado de filmes.

Entrada
Uma linha com três inteiros: 
N (filmes)
H (filmes de horror)
L (similaridades/arestas)

Uma linha com $H$ inteiros separados por espaço: 

IDs dos filmes da Horror List.
  
L linhas subsequentes, cada uma com um par de inteiros a e b (a / b), indicando similaridade entre os filmes a e b.

Saída
Um único inteiro representando o ID do filme com o maior Índice de Horror (com desempate pelo menor ID).


Restrições
1 < N < 1000

1 < H < N

0 < L < 10000

0 < a, b < N

Input
6 3 5
0 5 2
0 1
1 2
4 5
3 5
0 2

Output
1
