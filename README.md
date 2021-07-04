
--------- inicio -------------------


#carrega o valor de neg = -32768 
lw 6,0,neg     	

#carrega o valor de n= 5 
lw 7,0,n	

#faz o nand do registrador 6 com o 7 para gerar o -1
#será usado para fazer comparações futuras
nand 5,6,7	
		
#adiciona 1 ao reg7 e armazena no reg6, servirá para o print do array
addi 6,7,1	

#carrega o i= 0
lw 1,0,i		


#adiciona 1 ao i para iniciar o loop do 1 ao 5
loop1: 	addi 1,1,1 	
	#carrega o j= i + 1
addi 2,1,1	
#verificar se chegou ao fim do loop para printar o array
       	 beq 2,6,print	
        


loop2:	lw 3,1,vetor	
#carrega o vetor[ i ]
	lw 4,2,vetor	
#carrega o vetor[ j ]
        	
nand 4,4,4	#faz o complemento do vetor[ j ]
        	addi 4,4,1	
        	
add 3,3,4	#subtração do vetor[ i ] - vetor[ j ]
        	lw 4,0,neg	
        	nand 4,4,3	
#verifica se o resultado da subtração foi negativo ou positivo
        

	 #se positivo então vetor[ i ] > vetor[ j ] -> trocar: | se não  -> checar:
         	beq 4,5,trocar	  
        	beq 0,0,checar           
        
trocar: lw 3,1,vetor	#carrega os valores
	lw 4,2,vetor	
        
        	sw 4,1,vetor	#armazena o vetor[ i ] no lugar do vetor[ j ] e virce versa
        	sw 3,2,vetor	
        
       	lw 3,1,vetor	#print dos dois vetores para verificar se ocorreu a troca corretamente
        	lw 4,2,vetor

        	beq 0,0,checar    #checar

checar: beq 2,7,loop1	   #se j = n volta para o loop1

	addi 2,2,1	#se não, adiciona 1 ao je retorna para o loop2
        	beq 0,0,loop2	

print:	lw 7,0,i	  	# percorre do 1 ao 5 do vetor 
	addi 7,7,1
	lw 1,7,vetor
        	addi 7,7,1
	lw 2,7,vetor
        	addi 7,7,1
       	lw 3,7,vetor
        	addi 7,7,1
       	lw 4,7,vetor
        	addi 7,7,1
       	lw 5,7,vetor
        	addi 7,7,1
  	lw 6,0,i			#zerar os reg para deixar somente os valores do vetor
       	lw 7,0,i			#deixar esteticamente bonito


halt #fim


--------------------  dados ------------------------
i: .fill 0
n: .fill 5
neg: .fill -32768

vetor: .fill 24
  .fill 4
  .fill 1
  .fill 8
  .fill 5
  .fill 3
