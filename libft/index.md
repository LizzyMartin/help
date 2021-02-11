---
title: Libft
has_children: true
nav_order: 1
---

# Libft

Libft é o primeiro projeto a ser entregue no 42-cursus. É composto por uma parte obrigatória (Mandatory part) e uma parte bônus.

[Download do subject](en.subject.pdf){: .btn .btn-green }

Em resumo, conforme o subject:

```
Nome do programa: libft.a

Arquivos para serem entregues: *.c, libft.h, Makefile 

Descrição: Escreva sua própria biblioteca, contendo um resumo das funções importantes para seu curso.
```

A parte obrigatória é subdividida em duas partes.

## Parte 1 – Funções Libc
Libc é a biblioteca padrão de C, dessa forma, todas as funções aqui devem ser feitas consultando o manual e ter o prefixo “ft_”. São elas:
- memset
- bzero
- memcpy
- memccpy
- memmove
- memchr
- memcmp
- strlen
- strlcpy
- strlcat
- strchr
- strrchr
- strnstr
- strncmp
- atoi
- isalpha
- isdigit
- isalnum
- isascii
- isprint
- toupper
- tolower
- calloc (usar a função malloc)
- strdup (usar a função malloc)

## Parte 2 – Funções Adicionais
Nessa parte são listadas funções que não estão incluídas na libc ou que estão incluídas de uma forma diferente. Algumas delas podem ser úteis para a realização das funções da parte 1. São elas:

- ft_substr
- ft_strjoin
- ft_strtrim
- ft_split
- ft_itoa
- ft_strmapi
- ft_putchar_fd
- ft_putstr_fd
- ft_putendl_fd
- ft_putnbr_fd