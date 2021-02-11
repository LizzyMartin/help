---
title: Get Next Line
has_children: true
nav_order: 2
---

# Get Next Line

O **get_next_line** é uma função que permite ler o conteúdo de um fd linha por linha. Em loop ele lê o arquivo até atingir o EOF. 

[Download do subject](en.subject.pdf){: .btn .btn-green }

Os pontos principais para a realização do projeto são:

- funções open, read, close e gerenciamento do tamanho do buff.
- variáveis estáticas.
- alocação adequada e destruição da memória heap.
- gerenciar múltiplos fd.

A execução é feita da seguinte forma:
- ./gnl -> Leitura pelo stdin
- ./gnl “arquivo” -> Leitura de um único arquivo
- ./gnl “arquivo1” “arquivo2” “arquivo3” -> Leitura de multiplos arquivos
- ./gnl “arquivo1” “arquivo2” “arquivo3” mix n -> Leitura de n linhas de multíplos arquivos

E o retorno será:
- **1** se a linha for lida.
- **0** senão ler, fim do arquivo.
- **-1** se der erro.