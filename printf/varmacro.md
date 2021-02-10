---
title: Variadic macro
parent: Printf
has_children: false
nav_order: 1
---

# Variadic macro (macro variável)

Para utilizar variadic functions nós precisamos entender as seguintes macros:

- va_list
- va_start
- va_arg
- va_end
- va_copy

Todas essas macros estão em stdarg.h que deve ser incluída em seu código como mostrado abaixo:
> #include <stdarg.h>

A palavra **variadic** nos diz que existe algum tipo de mudança ou variação envolvida aqui. A variação ou mudança aqui é que estamos lidando com um número desconhecido de argumentos para a função.

Uma função variável tem duas partes:

1. Argumentos obrigatório (mandatory arguments);
2. Argumentos opcionais (optional arguments).

Pelo menos um argumento obrigatório é exigido. A ordem é importante neste caso. Dessa forma, você terá argumentos obrigatórios primeiro e depois os argumentos opcionais.

Por exemplo no printf, a parte obrigatória seria a string “O número é %d” e a opcional o número. Se não tivesse um número seria apenas a parte obrigatória.

Uma prática comum é ter algum número que nos dirá quantos argumentos existem ou nós procuramos pelo sinal de parada na nossa lista opcional.

**va_list** é usado em situações que é necessário acessar parâmetros opcionais e é uma lista de parâmetros. Então, nossa lista terá algum dado que será acessado depois depois que nos declaramos nossa va_list e isso é feito assim:

> va_list someArgumentPointer;

Nessa situação nós precisamos mencionar que nossa lista terá dados apropriados.

**va_start** conectará nossa lista de argumento com someArgumentPointer e nós precisaremos dizer quantos elementos nossa função tem. Em ordem, devemos escrever assim:

> va_start( someArgumentPoiner, numberOfElements );

Isso significa que nós já declaramos nossa lista e passamos um números de elementos em nossa função.

**va_arg** é uma macro que obterá nossos dados que estão atualmente conectados à lista de argumentos e, para atingir essa tarefa, precisaríamos conhecer o tipo de dados. Então, escreveríamos assim:

> va_arg (someArgumentPointer, someType);

**va_end** é usado em situações em que gostaríamos de parar de usar someArgumentPointer. Outra situação em que usamos essa macro é quando precisamos redefinir nossa posição na lista. Ela é usada assim:

> va_end (someArgumentPointer);

**va_copy** é usado em situações nas quais precisamos salvar nossa localização atual, como um marcador de livro. Em outras palavras, se você estiver na situação em que está avançando na lista de argumentos, mas mais tarde precisará voltar em sua posição  atual para algum estado anterior. É feito assim:

> va_copy (va_list argumentDestination, va_list argumentSource);


## Exemplo em código

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdarg.h>

int 
addingNumbers( int nHowMany, ... )
{
  int              nSum =0;
  
  va_list       intArgumentPointer;
  va_start( intArgumentPointer, nHowMany );
  for( int i = 0; i < nHowMany; i++ )
    nSum += va_arg( intArgumentPointer, int );
  va_end( intArgumentPointer );
  
  return nSum;
} 

int
main( int         argc, 
      char**      argv)
{
 system( "clear" );
 printf( "\n\n Variadic functions: \n\n" );

 printf( "\n 10 + 20 = %d ",           addingNumbers( 2, 10, 20 )  );
 printf( "\n 10 + 20 + 30 = %d ",      addingNumbers( 3, 10, 20, 30 )  );
 printf( "\n 10 + 20 + 30 + 40 = %d ", addingNumbers( 4, 10, 20, 30, 40 )  );

 printf( "\n\n" );

 return EXIT_SUCCESS;
}
```

No código acima, para saber quantos números passaremos para a função variável, temos o primeiro número nHowMany e não se esqueça de adicionar três pontos. Esses três pontos dirão que você está interferindo na função variável. Isso poderá ser alcançado assim:

```c
int addingNumbers( int nHowMany, ... )
```

Então, temos a soma declarada e inicializadas como zero. Como já dito anteriormente, precisamos declarar nossa lista de argumentos com va_list e essa tarefa será realizada assim:

```c
va_list intArgumentPointer ;
```

Então precisamos conectar nossa lista de argumentos e dizer quantos elementos temos nela.

```c
va_start (intArgumentPointer, nHowMany) ;.
```

Agora, usamos o laço ‘for’ para avançar a lista de argumentos e adicionar elementos à soma anterior.

```c
va_arg (intArgumentPointer, int);
```

Então, como mencionado anteriormente, precisamos declarar que estamos fechando nosso intArgumentPointer.

Por fim, chame a função variável com vários argumentos:

```c
adicionandoNúmeros (2, 10, 20) 
adicionandoNúmeros (3, 10, 20, 30) 
adicionandoNúmeros (4, 10, 20, 30, 40)
```

## Referências
- [thegeekstuff](https://www.thegeekstuff.com/2017/05/c-variadic-functions/)
- [codeforwin](https://codeforwin.org/2017/09/variable-length-arguments-c.html#macros)