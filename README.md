# IA-Trabalho-2-Raposa-e-os-Gansos


Implementar um programa em C que jogue o jogo "A raposa e os gansos".


Especificação:
==============

O jogo "A raposa e os gansos" é um jogo de tabuleiro onde dois
jogadores se enfrentam, um deles com 13 gansos e outro com uma raposa.

O seu programa deve conseguir jogar tanto com os gansos quanto com a
raposa.

O objetivo dos gansos é imobilizar a raposa e o objetivo da raposa é
eliminar os gansos do tabuleiro.

Tanto a raposa quanto os gansos se movimentam na vertical ou na
horizontal, uma posição de cada vez, desde que a posição de destino
esteja desocupada.

Para eliminar um ganso do tabuleiro a raposa pode saltar sobre ele. Os
saltos podem ser tanto na vertical quanto na horizontal. Para saltar
sobre um ganso, a raposa deve estar na posição vizinha a do ganso e a
posição de destino do salto deve estar vazia e ser vizinha à posição
do ganso. Em uma mesma jogada a raposa pode fazer uma sequência de
saltos, eliminando assim mais de um ganso.

O jogo termina, quando não for possível mover a raposa ou quando o
número de gansos for menor que 4.

O tabuleiro inicial é dado por:

     1234567
    #########
   1#  ggg  #
   2#  ggg  #
   3#ggggggg#
   4#-------#
   5#---r---#
   6#  ---  #
   7#  ---  #
    #########

onde 'g' representa um ganso, 'r' representa a raposa, '-' representa
uma posição livre do tabuleiro.

As jogadas são descritas por sequências de caracteres e podem ser de
dois tipos: as de movimento (m) e as de saltos (s).

As jogadas de movimento podem ser feitas tanto pela raposa quanto
pelos gansos. São dadas pelo formato:

   <jogador> m <l_ini> <c_ini> <l_fin> <c_fin>

onde, jogador indica quem está jogando, l_ini e c_ini indicam a linha
e a coluna da posição inicial do movimento e l_fin e c_fin a posição
final do movimento. O movimento deve ser na vertical ou na horizontal
e a distância entre a posição inicial e final do movimento deve ser no 
máximo 1.

Por exemplo, a jogada que move um ganso da posição (linha 3, coluna 4)
para a posição (linha 4, coluna 4) do tabuleiro é dada por:

   g m 3 4 4 4

As jogadas de salto só podem ser feitas pela raposa e são dadas pelo
formato:

   r s <num_tuplas> <l_ini> <c_ini> <l_salto_1> <c_salto_1> ...

onde, num_tuplas indica o número de pares de números que compõem o
restante da sequência de caracteres que representa a jogada, l_ini e
c_ini indicam a posição inicial e, l_salto_i e c_salto_i indicam a
posição destino do salto i. Note que o número de saltos é igual a
num_tuplas - 1, pois a primeira tupla indica a posição inicial.

Por exemplo, a jogada:

   r s 5 3 1 3 3 3 5 5 5 5 7

salta a raposa 4 vezes, partindo da posição (3,1), assumindo que as
posições (3,3), (3,5), (5,5) e (5,7) estão vazias e, elimina 4 gansos
que estão nas posições (3,2), (3,4), (4,5) e (5,6).

Considere a seguinte sequência de jogadas, partindo do tabuleiro
inicial e com o jogador dos gansos fazendo o primeiro movimento:

1) Um movimento possível para o lado dos gansos é mover o ganso da 
   posição (linha 3, coluna 3) para a posição (4,3). Esta jogada é
   representada por:

   g m 3 3 4 3

   Após esta jogada o novo tabuleiro é:

     1234567
    #########
   1#  ggg  #
   2#  ggg  #
   3#gg-gggg#
   4#--g----#
   5#---r---#
   6#  ---  #
   7#  ---  #
    #########

2) Na vez da raposa o outro jogador decide movê-la da posição (5,4)
   para a posição (5,3). Esta jogada é representada por:

   r m 5 4 5 3

   O novo tabuleiro resultante é:

     1234567
    #########
   1#  ggg  #
   2#  ggg  #
   3#gg-gggg#
   4#--g----#
   5#--r----#
   6#  ---  #
   7#  ---  #
    #########

3) O jogador dos gansos agora move o ganso da posição (3,5) para a
   posição (4,5):

   g m 3 5 4 5

     1234567
    #########
   1#  ggg  #
   2#  ggg  #
   3#gg-g-gg#
   4#--g-g--#
   5#--r----#
   6#  ---  #
   7#  ---  #
    #########

4) Neste ponto da partida o jogador da raposa pode escolher entre os
   seguintes movimentos possíveis:
   
      a) r m 5 3 5 2
      b) r m 5 3 6 3
      c) r m 5 3 5 4
      d) r s 2 5 3 3 3
      e) r s 3 5 3 3 3 3 5
      f) r s 4 5 3 3 3 3 5 5 5
      
   Assumindo que a jogada escolhida foi a (e), o tabuleiro resultante é:

     1234567
    #########
   1#  ggg  #
   2#  ggg  #
   3#gg--rgg#
   4#----g--#
   5#-------#
   6#  ---  #
   7#  ---  #
    #########

   Note que a jogada escolhida pela raposa eliminou 2 gansos do
   tabuleiro. Se a jogada (f) fosse escolhida, 3 gansos seriam
   eliminados.
