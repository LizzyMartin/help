---
title: Variadic function
parent: Printf
has_children: false
nav_order: 2
---

# Variadic function (função variável)

Na matemática e na programação, uma variadic function é uma função com um valor indefinido de argumentos, que aceita um número variável de argumentos. O suporte para funções variáveis varia entre as linguagens de programação.

Em C, a função variável contribui para a flexibilidade do programa que você está desenvolvendo. Para entender essa flexibilidade, vamos começar com um exemplo.

Se queremos somar dois números provavelmente escreveremos um programa assim:

```c
int 
addNumbers( int nNumberOne, int nNumberTwo )
{
  return nNumberOne + nNumberTwo;
}
```

Se nós queremos querermos adicionar três números, escreveremos um código assim:

```c
int addNumbers( int nNumberOne, int nNumberTwo, int nNumberThree )
{
  return nNumberOne + nNumberTwo + nNumberThree;
}
```

Conforme o número de dígitos que queremos somar aumenta, nós podemos continuar adicionando mais funções com um número apropriado de argumentos que representa o total de números que queremos somar.

Mas, isso provavelmente ficará um pouco pesado e difícil de fazer manutenção. Para solucionar isso usamos uma variadic function.

Nós tipicamente usamos uma função variável quando não sabemos o número total de argumentos que serão usados na função. Basicamente é uma única função que pode receber n argumentos.

O conceito de variadic function é usado em muitas funções do C, como o printf.

## Referências
- [thegeekstufft](https://www.thegeekstuff.com/2017/05/c-variadic-functions/)
- [wikipedia](https://en.wikipedia.org/wiki/Variadic_function)