---
title: Instalando e compilando
parent: Minilibx
grand_parent: Cub3d
has_children: false
nav_order: 1
---

# Instalando e compilando um projeto com minbilibx

Podemos compilar usando:

```shell
gcc -g3 -fsanitize=address -o cub3d main.c minilibx/*.o minilibx/libmlx.a -I minilibx/mlx.h -lm -lXext -lX11 -lbsd
```

Entendendo os comandos:
- gcc:
- g3:
- fsanitize=address:
- o:
- I:
- lm:
- lXext:
- lX11:
- lbsd: