---
title: Cub3d
has_children: true
nav_order: 4
---

# Cub3d

![wolf3d](/images/wolfen.gif){:style="float: right;margin-right: 7px;margin-top: 7px; width: 20%;"}

Esse projeto é inspirado no famoso jogo dos anos 90 Wolfenstein 3D. Ele permite explorar o _ray-casting_ e seu objetivo é fazer uma visualização dinâmica dentro de uma labirinto.

[Wolf3d online](http://users.atw.hu/wolf3d/)

[Download do subject em inglês](cub3d.pdf)

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
    - O mapa deve ser composto de apenas 4 possíveis caracteres: 0 para um espaço vazio, 1 para uma parede, 2 para um item e N, S, E ou W para a posição de inicio do jogador e sua orientação. Esse é um mapa simples válido:
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
    - A primeira informação de cada elemento (exceto o mapa) é do tipo identificador (composto por um ou dois caracteres), seguido por todas as informações específicas para cada objeto em uma ordem, como:
        - Resolução: <br/>
        ```R 1920 1080```<br/>
        identificador: **R**
        x: tamanho da renderização (1920)
        y: tamanho da renderização (1080)
        - Textura do norte:<br/>
        ```NO ./caminho_para_textura_norte```<br/>
        identificador: **NO**
        caminho para a textura norte
        - Textura do sul:<br/>
        ```SO ./caminho_para_textura_sul```<br/>
        identificador: **SO**
        caminho para a textura sul
        - Textura do oeste:<br/>
        ```WE ./caminho_para_textura_oeste```<br/>
        identificador: **WE**
        caminho para a textura oeste
        - Textura do leste:<br/>
        ```EA ./caminho_para_textura_leste```<br/>
        identificador: **EA**
        caminho para a textura leste
        - Textura do sprite:<br/>
        ```S ./caminho_para_textura_sprite```<br/>
        identificador: **S**
        caminho para a textura do sprite
        - Cor do chão:<br/>
        ```F 220,100,0```<br/>
        identificador: **F**
        cores R,G,B em um intervalo [0,255]: 0, 255, 255
        - Cor do teto:<br/>
        ```C 255,30,0```<br/>
        identificador: **C**
        cores R,G,B em um intervalo [0,255]: 0, 255, 255
    - Exemplo da parte obrigatória com uma cena **.cub** minimalista:
        ```shell
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
    - Se for encontrada alguma configuração errada de qualquer tipo no arquivo, o programa deve dar exit e retornar **"Error\n"** seguido por uma mensagem de erro explícita de sua escolha.

## Parte bônus

Lista de itens:
- Colisões com a parede;
- Skybox;
- Textura para o chão e/ou teto;
- Um HUD;
- Habilidade de olhar para cima e para baixo;
- Pular ou agachar;
- Um efeito de sombra relacionado à distância;
- Barra de vida;
- Mais itens no labirinto;
- Colisões com objetos;
- Sistema de pontos e/ou perca de vida ao pegar objetos/armadilhas;
- Portas que podem ser abertas e fechadas;
- Portas secretas;
- Animações de tiro ou sprites animados;
- Múltiplos níveis;
- Som e música;
- Rotacionar o ponto de visão com o mouse;
- Armas e inimigos para lutar!

```
Para o bônus ser válido, deverá ter pelos 14 dos itens acima feitos.
```

```
Outras funções são permitidas para a parte bônus desde que sejam justificadas.
```

## Exemplos

![01](/images/cub3d-1.png)
Jogo original Wolfenstein3D usando RayCasting. <br/><br/>

![02](/images/cub3d-2.png)
Exemplo de como o projeto poderá parecer.<br/><br/>

![03](/images/cub3d-3.png)
Exemplo da parte bônus com um minimapa, texturas para o chão e teto e um sprite animado.<br/><br/>

![04](/images/cub3d-4.png)
Outro exemplo da parte bônus com um HUD, barra de vida, efeitos sonoros e música, efeito de sombra e uma arma que pode atirar.<br/><br/>

![05](/images/cub3d-5.png)
Outro exemplo da parte bônus com outra escolha de arma e com o jogador olhando para o teto.<br/><br/>