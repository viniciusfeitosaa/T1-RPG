Marco 1 — Modelagem

•	filmes → vértices;
•	similaridade entre filmes → arestas;
•	Horror List → vértices especiais/iniciais;
•	Horror Index → distância até a Horror List;
•	resposta → vértice com maior distância, usando menor ID em caso de empate.


2. Enunciado
filmes que consideram ruins. Esses filmes formam a Horror List.

filme pertencente à Horror List → HI = 0;
filmes semelhantes aos anteriores recebem índices progressivamente maiores;
filmes sem qualquer caminho até um filme da Horror List → HI = ∞.

O programa deve encontrar o filme com maior Horror Index. Se vários filmes tiverem o mesmo maior índice, devemos retornar o filme de menor ID.


3. Entrada
A primeira linha contém três números:
N H L

Eles significam:
Símbolo	Significado
N	Número total de filmes
H	Número de filmes na Horror List
L	Número de relações de similaridade


A segunda linha contém os H IDs dos filmes pertencentes à Horror List.
Depois aparecem L linhas, cada uma contendo:

Exemplo oficial
6 3 5
0 5 2
0 1
1 2
4 5
3 5
0 2
Interpretando:
N = 6
H = 3
L = 5


Portanto temos os filmes:
V={0,1,2,3,4,5}

A Horror List é:
Horror = {0,5,2} 

E as similaridades são:
E = {(0,1), (1,2), (4,5), (3,5), (0,2)}

4. Saída
A saída é extremamente simples: apenas um número inteiro.
Esse número representa o ID do filme com o maior Horror Index.
Se houver empate:
escolhemos o filme com o menor ID.
No primeiro exemplo oficial:
1


5. Restrições
1 <=  H < N <= 1000

e
0 <= L <= 10000

Além disso:
0 <= x_i < N 

para os filmes da Horror List, e as relações de similaridade satisfazem:
0 <= a_i < b_i < N

Isso já começa a nos dar uma pista importante para o Marco 2.
Podemos ter:
•	até 1.000 vértices;
•	até 10.000 arestas.


Tipo do grafo
Nosso grafo é:
Não direcionado
Porque: A similaridade é bidirecional.
A é similar a B

E

B é similar a A


Não existe:
B não é similar a A

Não ponderado
Não existe um valor associado à similaridade.

Pode ser desconexo
O problema não garante que todos os filmes estejam conectados aos filmes da Horror List.
Podemos ter:
0 -- 1 -- 2

3 -- 4

Se:
Horror = {0}

o componente:
3 -- 4

não possui caminho até 0.
Então:
HI(3)=HI(4) são infinitamente distantes


Instância pequena
7 2 6
0 5
0 1
1 2
2 3
3 4
4 5
3 6

Temos:
N=7

filmes:
V={0,1,2,3,4,5,6\}

Horror List:
H={0,5}

E:
E={(0,1), (1,2), (2,3), (3,4), (4,5), (3,6)}

Visualmente:
H                   		H
0 --- 1 --- 2 --- 3 --- 4 --- 5
                  |
                  |
                  6

Calculando o resultado
Filme	Horror Index
0	0
1	1
2	2
3	2
4	1
5	0
6	3

Logo:
{6}

é nossa saída esperada.

Hipótese inicial de solução
Como nosso grafo é não ponderado, usaremos BFS porque explora o grafo por níveis.
Mas ela conterá mais de 1 origem, então será uma BFS de múltiplas fontes.

