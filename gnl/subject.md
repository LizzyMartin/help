---
title: Interpretando o subject
parent: Get Next Line
has_children: false
nav_order: 1
---

# Informações obtidas do subject

| Nome da função             | get_next_line                                                                            |
|----------------------------|------------------------------------------------------------------------------------------|
| Protótipo                  | int get_next_line(int fd, char **line);                                                  |
| Arquivos a serem entregues | get_next_line.c, get_next_line_utils.c, get_next_line.h                                  |
| Parâmetros                 | #1. *File Descriptor* para leitura <br> #2. O valor do que foi lido                           |
| Retorno                    | 1 : A linha foi lida <br>0 : Chegou no fim do arquivo (EOF)<br> -1 : Um erro aconteceu           |
| Funções externas           | read, malloc, free                                                                       |
| Descrição                  | Escreva uma função que retorna uma linha lida de um  *file descriptor*, sem a nova linha |

- Chamando sua função ```get_next_line``` em loop permitirá que você leia uma linha por vez do texto disponível no *file descriptor* até atingir o EOF.
- Tenha certeza que sua função comporte bem quando ler de um arquivo e quando ler da entrada padrão (standard input).
- ```libft``` não é permitido para este projeto. Você deve adicionar o arquivo **get_next_line_utils.c** que contém as funções necessárias para o get_next_line funcionar.
- Seu programa deve compilar com a flag **-D BUFFER_SIZE=xx** que será usada como o tamanho do buffer para as chamadas de leitura no ser ```get_next_line```. Este valor será modificado pelos avaliadores e pela Moulinette.
- A compilação será feita da seguinte forma: gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line.c  get_next_line_utils.c
- Seu **read** deve usar o BUFFER_SIZE definido durante a compilação para ler de um arquivo ou do stdin.
- No arquivo header ```get_next_line.h``` você deve ter pelo menos o protótipo da função get_next_line.

**Dicas**
- Sua função continua funcionando se o valor do BUFFER_SIZE for 9999? E se o BUFFER_SIZE for 1? e 10000000? Você sabe o por quê?
- Você deveria tentar ler o mínimo possível sempre que get_next_line for chamado. Se você encontrar uma nova linha, precisará retornar a linha atual. Não leia o arquivo inteiro e processe cada linha.
- Não envie seu projeto sem testar. Existem muitos testes para rodar. Tente ler de um arquivo, de um *redirecting input*, do stdin. Como seu programa se comporta quando você encia uma nova linha para a saída padrão (standard output)? E CTRL-D?

- Nós consideramos que get_next_line tem um comportamento indefinido se, entre duas chamadas, o mesmo *file descriptor* alternar para um arquivo diferente antes que o EOF seja atingido no primeiro fd.
- lseek não é permitido. A leitura do arquivo deve ser feito apenas uma vez.
- Por fim, nós consideramos que get_next_line tem um comportamento indfinido quando lê um arquivo binário. Porém, se você desejar, você pode tornar esse comportamento coerente.
- Variáveis globais são proibidas.

**Parte bônus**
- Utilizar apenas uma variável estática.
- Gerenciar vários *file descriptor*.

**Visualizar subject**
<iframe src="en.subject.pdf" width="600" height="700" style="border: none;"></iframe>

# O que podemos tirar do subject?
```get_next_line``` é uma função que permite ler o conteúdo de um fd linha por linha. Em loop ele lê o arquivo até atingir o EOF. Os pontos principais para a realização do projeto são:

- Funções open, read, close e gerenciamento do tamanho do buff.
- Utilização de variáveis temporárias.
- Variáveis estáticas.
- Alocação adequada e destruição da memória heap.
- Gerenciar múltiplos fd.

A execução é feita da seguinte forma:

- ./gnl -> Leitura pelo stdin
- ./gnl "arquivo" -> Leitura de um único arquivo
- ./gnl "arquivo1" "arquivo2" "arquivo3" -> Leitura de multiplos arquivos
- ./gnl "arquivo1" "arquivo2" "arquivo3" mix n -> Leitura de **n** linhas de multíplos arquivos

E o retorno será:
- 1 se a linha for lida.
- 0 senão ler, fim do arquivo.
- -1 se der erro.