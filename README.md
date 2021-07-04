# Passo a passo do metodo bolha:

1. carrega o valor de neg = -32768 
    lw 6,0,neg     	

2. carrega o valor de n= 5 
    lw 7,0,n	

3. faz o nand do registrador 6 com o 7 para gerar o -1
4. será usado para fazer comparações futuras
    nand 5,6,7	
		
5. adiciona 1 ao reg7 e armazena no reg6, servirá para o print do array
    addi 6,7,1	

6. carrega o i= 0
    lw 1,0,i		