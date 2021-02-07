---
title: Cub3d
has_children: true
nav_order: 2
---

# Cub3d

![wolf3d](/images/wolfen.gif)

Esse projeto é inspirado no famoso jogo dos anos 90 Wolfenstein 3D. Ele permite explorar o _ray-casting_ e seu objetivo é fazer uma visualização dinâmica dentro de uma labirinto.

> [Wolf3d online](http://users.atw.hu/wolf3d/)

> [Download do subject em inglês](cub3d.pdf)

## Metas

Algumas das metas com esse projeto são: rigor, uso de C, uso de algoritmos básicos, procura de informações etc. Uma vez que é um projeto de design gráfico, ele irá permitir uma melhora nas habilidades das seguintes áreas: janelas, cores, eventos, preencher figuras, etc.

## Instruções em comum

- O projeto deverá passar pela Norminette;
- As funções não devem apresentar comportamentos não definidos como segmentation fault, bus error, double free, etc);
- Toda memória heap alocada deve ser liberada quando necessário. **Leaks não são permitidos**;
- O Makefile deverá compilar os arquivos fontes com as flags **-Wall -Wextra -Werror**;
- O Makefile deverá conter as regras: **$(NAME), all, clean, fclean e re**;
- Para incluir bônus no projeto, deverá criar a regra **bonus** no Makefile. Os arquivos do bônus deverão ser terminados em **_bonus.{c/h}**. A parte obrigatória e o bônus são avaliadas separadamente;


## Parte obrigatória

| Nome do programa | cub3D |
|-|-|
| **Arquivos para serem entregues** | Todos seus arquivos |
| **Makefile** | all, clean, fclean, re, bonus |
| **Argumentos** | um mapa no formato *.cub |
| **Funções externas** | - open, close, read, write, printf, malloc, free, perror, strerror, exit - todas as funções da biblioteca math (-lm man man 3 math) - todas as funções do MinilibX |
| **Libft autorizado?** | Sim |
| **Descrição** | Você deve criar uma representação gráfica 3D "realista" de um labirinto na perspectiva de primeira pessoa. Você deve criar essa representação usando os princípios do _raycasting_ |

Considerações:
- Você deve usar o minilibX;
- O gerenciamento de sua janela deverá permanecer suave: trocar para outra janela, minimizar, etc;
- Exiba diferentes texturas para as paredes que irá variar dependendo de qual direção a parede está (norte, sul, lest, oeste);
- Seu programa deverá ser capaz de exibir um item (sprite) ao invés de uma parede;
- Seu programa deverá ser capaz de definir as cores do chão e do teto;
- Seu programa deverá salvar a primeira imagem renderizada no formato **bmp** quando o segundo argumento for **--save**;
- Se nenhum segundo argumento for passado, o programa exibirá a imagem numa janela com as respectivas seguintes regras:
    - As setas esquerda (<) e direita (>) do teclado deverá permitir que você olhe para esquerda e direita no labirinto;
    - As teclas W, A, S e D deverão permitir que você se mova;
    - Ao pressionar ESC a janela deverá ser fechada e o programa deverá ser finalizado de forma limpa;
    - Ao clicar na cruz vermelha no frame da janela, a janela deverá ser fechada e o programa severá ser finalizado de forma limpa;
    - Se o tamanho declarado da tela for maior que a resolução do display, o tamanho da janela deverá ser definido dependendo da atual resolução do display;
    - O uso de imagens do minilibX é extremamente recomendado.
- Seu programa deverá ter como primeiro argumento o arquivo da descrição da cena (extensão .cub)
    - O mapa deve ser composto de apenas 4 possíveis caracteres: 0 para um espaço vazio, 1 para uma parede, 2 para um item e N, S, E ou W para a posição de inicio do jogador e sua orientação. Esse é um mapa simples válido: </br></br>
        ```shell
        111111
        100101
        102001
        1100N1
        111111
        ``` 
    - O mapa deve ser fechado por paredes, caso contrário o programa deverá retornar um erro;
    - Com exceção do conteúdo do mapa, cada tipo de elemnto pode ser separado por um ou mais linhas vazias;
    - Com exceção do conteúdo do mapa que sempre deverá ser o último, cada tipo de elemento pode ser definido em qualquer ordem no arquivo;
    - Exceto pelo mapa, cada tipo de informação do elemnto pode ser separado por um ou mais espaços;
    - O mapa deve ser parseado como ele é no arquivo. Espaços são partes válidas no mapa e você deve suporta-los. Você deve ser capaz de parsear qualquer tipo de mapa, desde que respeite as regras;
    - Cada elemento (exceto o mapa)...