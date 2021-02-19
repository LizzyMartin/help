---
title: Página de correção
parent: Cub3d
has_children: false
nav_order: 5
---

# Página de correção

 - [ ] **Nome do executável**
 O projeto deve compilar (sem re-link) quando é digitado o comando **make** e o nome do executável deve ser cub3D.
 
 - [ ] **Arquivo de configuração**
Checar se você pode configurar TODOS os seguintes elementos no arquivo de configuração. A formatação deve ser igual a descrita no subject.

	- resolução da imagem / tamanho da janela - R
	- caminho para a textura do norte - NO
	- caminho para a textura do leste - EA
	- caminho para a textura do sul - SO
	- caminho para a textura do oeste - WE
	- caminho para a textura do sprite - S
	- cor do chão - F
	- cor do teto - C
	- o mapa

	Também checar se o programa retorna um erro e encerra de forma apropriada quando o arquivo de configuração é mal configurado (por exemplo: uma chave desconhecida, chaves duplicadas, caminho inválido, etc.) ou se o nome do arquivo não termina com a extensão **.cub**.

 - [ ] **Exibição de elementos técnicos**
O programa deverá passar nesses 5 testes:

	- Um janela deve abrir na inicialização do programa se o argumento "--save" não for passado. A janela deve continuar aberta durante toda execução e deve ter a resolução definida no arquivo de configuração.
	- Uma imagem representando o interior de um labirinto deve ser exibida dentro da janela.
	- Quando o argumento "---save" é passado, o programa não deverá abrir uma janela, mas deverá gerar um arquivo no formato bmp com a resolução definida no arquivo de configuração (chave R).
	- Esconda toda ou parte da janela (usando as bordas ou outra janela por exemplo), minimize e maximize a janela, o conteúdo da janela deverá se manter consistente em todos os casos.
	- Defina uma resolução (chave R) maior que o display no arquivo de configuração. O programa deverá ajustar o tamanho da janela para caber na tela.

 - [ ] **Eventos básicos do usuário**
in progress
