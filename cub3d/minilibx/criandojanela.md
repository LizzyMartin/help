---
title: Criando uma janela simples
parent: Minilibx
grand_parent: Cub3d
has_children: false
nav_order: 3
---

# Criando uma janela/window simples

Conforme o manual (man3) antes de tudo devemos iniciliazar a conexão entre o _software_ e o _display_. Uma vez que a conexão é estabelecida, somos capazes de usar outras funções do MiniLibX para enviar e receber mensagens do display como "Eu quero desenhar um pixel azul na janela" ou "O usuário apertou uma tecla?". Tá, mas como criamos essa conexão? Com o **mlx_init()**! Essa função é somente encarregada de criar a conexão. Nenhum parâmetro é nexessário e ela irá retornar um **void \*** (usado para chamadas de rotina da biblioteca).

Beleza, já sei como criar uma conexão, mas como fazer para criar uma janela? Para isso há a função **mlx_new_window**. Vamos dar uma olhada nela:
```c
void *mlx_new_window (void *mlx_ptr, int size_x, int size_y, char *title);
```
Ela espera receber 4 parâmetros:
- **void \*mlx_ptr**: a nossa conexão que foi cirar com o mlx_init()
- **int size_x**: a largura de nossa janela
- **int size_y**: a altura de nossa janela
- **char \*title**: o título que aparecerá no frame da janela
- É retornado um **void \*** para conseguir usarmos a janela em outras chamadas :grin:

**OBS:** se por algum motivo aconteça uma falha ao criar uma nova janela, a função irá retornar NULL, caso contrário o um ponteiro não nulo é retornado como um identificador da janela.

Porém, ainda falta uma coisa. Precisamos dizer para nosso programa continuar rodando até que um evento ou qualquer outra coisa fale o contrário. Para isso temos a função **mlx_loop**. Sua definição é dada por:
```c
int mlx_loop ( void *mlx_ptr );
```
A função nunca retorna, ela é um **loop** infinito que espera até que um evento ocorra. Somente um parâmetro é necessário (a conexão criada com o mlx_init()). Pronto, já sabemos criar nossa primeira janela usando o MiniLibX. O código final pode ser visto logo abaixo.

```c
int		main(void)
{
	void	*mlx;
	void	*window;

	mlx = mlx_init();
	window = mlx_new_window(mlx, 900, 300, "my first window");
	mlx_loop(mlx);
}
```