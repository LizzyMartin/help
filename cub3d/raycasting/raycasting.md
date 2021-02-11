---
title: Raycasting
parent: Cub3d
has_children: true
nav_order: 2
---

# Raycasting

O fenômeno do _ray-casting_ começou com o lançamento do jogo Wolfenstein 3D em 1992. Nesse jogo, o jogador é alocado em um labirinto 3D como ambiente e ele/ela deve encontrar uma saída enquanto batalha com múltiplos oponentes. Wolfenstein 3D se tornou um clássico devido sua rapidez e suavidade na animação. O que possibilitou esse tipo de animação foi uma abordagem inovadora da renderização 3D conhecida como **ray-casting**.

## O que é ray-casting?

Ray-casting é uma técnica que transforma uma forma limitada de dado (como um mapa bem simples ou uma planta) em uma projeção 3D ao traçar os raios a partir de um ponto de vista. Por exemplo, o ray-casting tansforma a figura A na figura B conforme mostrado abaixo.

![Introdução ao raycasting](images/ray1.gif){:style="display: block; margin: 0 auto;"}

**OBS**: Essa não é a única aplicação do raycasting, ele também pode ser usado para renderizar terrenos (ver figura abaixo). O importante é somente lembrar que o "ray-casting" traça raios a partir do visualizador até os objetos.

![Introdução ao raycasting](images/ray2.jpg){:style="display: block; margin: 0 auto;"}

## Ray-casting vs Ray-tracing

Assim como o ray-casting, o ray-tracing determina a visibilidade de superfícies traçando raios de luz imaginários a partir de um ponto de vista até o objeto em uma cena.

Olhando assim parece que ray-casting e ray-tracing são a mesma coisa. Na perspectiva de programadores, ray-casting é uma implementação especial (subclasse) do ray-tracing.

Essa distinção acontece porque de forma geral o ray-casting é mais rápido que o ray-tracing. Isso é possível porque o ray-casting usa algumas limitações geométricas para acelerar o processo de renderização. Por exemplo: as paredes **são sempre perpendiculares** com o chão. 

