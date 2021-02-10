---
title: Desenhando um pixel na janela
parent: Minilibx
grand_parent: Cub3d
has_children: false
nav_order: 4
---

# Desenhando um pixel na janela

Já sabemos como criar uma janela (se ainda não souber acessar o tutorial pelo menu lateral)! Agora precisamos descobrir como interagir com ela, vamos começar inserindo um pixel. Para isso usaremos a função **mlx_pixel_put**.

## Sobre a mlx_pixel_put
```c
int mlx_pixel_put(void *mlx_ptr, void *win_ptr, int x, int y, int color);
```

A função mlx_pixel_put desenha um pixel definido na janela **win_ptr** usando as coordenadas x e y (x, y) e uma cor especificada.

A origem (0, 0) é canto superior esquerdo da janela e os eixos X e Y apontam respectivamente para direta e abaixo. Assim, lembre-se:
- x é direita
- y é abaixo

A conexão criada com o mlx_init (mlx_ptr) é necessária aqui também!

**OBS:** é impossível exibir qualquer coisa fora da janela ou exibir em outra janela na frente da selecionada. :shipit:

### Gerênciamento de cores
O parâmetro de cor é do tipo int. A cor exibida precisa ser encodada nesse inteiro seguindo um esquema definido.

Todas as cores exibidas podem ser divididas em 3 cores básicas: vermelho (**R**ed), verde (**G**reen) e azul (**B**lue), em um intervalo de 0 a 255 representando o quanto cada cor foi misturada para criar a cor original. Esses três valores devem ser definidos dentro do inteiro para exibir a cor desejada.

Os três últimos bytes do inteiro são preenchidos dessa forma:
```
| 0 | R | G | B | color integer
+---+---+---+---+
```

### Problemas com _endians_

"Endian" e "endianness" (ou "ordem-de-bytes") descrevem como os computadores organizam os bytes que compõem os números.

O mais comum na ordenação de múltiplos bytes em um único número é o **little-endian**, que é usado em todos os processadores Intel. Little-endian significa armazenar bytes na ordem do menor para o mais significativo (onde o byte menos significativo ocupa o primeiro, ou menor, endereço).

Já o **big-endian** é a ordem oposta, comparável a uma data ISO (2050-12-31). Big-endian é frequentemente chamada de "ordem de bytes de rede", por que os padrões da internet geralmente exigem que os dados sejam armazenados em big-endian, começando pelo nivel padrão do socket UNIX e indo a todas as estruturas padronizadas de dados binários da Web. Além disso, os computadores Mac mais antigos, que usam a série 68000 e microprocessadores PowerPC, usavam o big-endian. **[[fonte]](https://developer.mozilla.org/pt-BR/docs/Glossario/Endianness)**

E o que isso interfere no projeto? Devemos lembrar que o byte "blue" deve **sempre** ser o menos significativo.

O quarto valor mencionado no gerenciamento de cores é o valor alpha (transparência). Ele também fica no intervalo de 0 à 255, no qual 0 é totalmente opaco (visível) e 255 é totalmente transparente (invisível).

Tomando como exemplo o MacOSX que usa o padrão little-endian, as coisas escritas na memória byte a byte devem ser escritas nesse formato:
```
| B | G | R | A | Blue, Green, Red, Alpha
+---+---+---+---+
```

## Código final
Agora que entendemos a função por trás da "magia", o código fica bem simples de entender:
```c
#include "mlx.h"

int main()
{
    void *mlx = mlx_init();
    void *win = mlx_new_window(mlx, 600, 300, "Drawing a pixel :D");

    mlx_pixel_put(mlx, win, 600/2, 300/2, 0xFFFFFF);

    mlx_loop(mlx);
}
```
Repare que a nosso "x" vai de 0 à 600 e o nosso "y" de 0 à 300. Quando inserimos o 600/2 e 300/2 estamos dizendo que o pixel deve ficar centralizado na janela. A cor FFFFFF é o equivalente a cor branca.