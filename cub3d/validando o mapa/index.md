---
title: Validando o input
parent: Cub3d
has_children: true
nav_order: 3
---

# Validando o input

Work In Progress
{: .label .label-purple }

Segundo o subject, o input será um mapa .cub passado como argumento. O mapa seguirá esse padrão:

```
R 1920 1080
NO ./path_to_the_north_texture
SO ./path_to_the_south_texture
WE ./path_to_the_west_texture
EA ./path_to_the_east_texture
S ./path_to_the_sprite_texture
F 220,100,0
C 225,30,0
1111111111111111111111111
1000000000110000000000001
1011000001110000002000001
1001000000000000000000001
111111111011000001110000000000001
100000000011000001110111111111111
11110111111111011100000010001
11110111111111011101010010001
11000000110101011100000010001
10002000000000001100000010001
10000000000000001101010010001
11000001110101011111011110N0111
11110111 1110101 101111010001
11111111 1111111 111111111111
```

## 1 - Checando se a extensão do arquivo está correta

## 2 - Checando se cada identificador está presente e correto

## 3 - Checando se o mapa não tem nenhum caracter inválido

De acordo com o subject:

```
O mapa deve ser composto de apenas 4 possíveis caracteres: 0 para um espaço vazio, 1 para uma parede, 2 para um item e N, S, E ou W para a posição de inicio do jogador e sua orientação.
```

## 4 - Checando se o mapa é cercado de parede (1)

