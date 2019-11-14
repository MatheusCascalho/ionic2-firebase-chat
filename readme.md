# RELATÓRIO TÉCNICO
## LABORATÓRIO DE SISTEMAS DIGITAIS
## IGOR DE OLIVEIRA PENIDO - MATHEUS CASCALHO DOS SANTOS - RAFAEL COSTA BENEVIDES 
### Projeto - 02
#### Introdução 
Diante das instruções apresentadas, o grupo montou uma ALU ou ULA (Unidade Lógica Aritmética) relacional de 8 bits. 
Uma Unidade Lógica Aritmética é um circuito digital que realiza operações de adição e booleana AND, funcionando como uma grande calculadora eletrônica. Entretanto no projeto foi modificada para realizar apenas operações relacionais.

ALU.vhd
O grupo então definiu na entidade as entradas e a saída:
```(
X, Y : in    unsigned(7 downto 0);-- Duas entradas de 8 bits.
Q     : out   unsigned(1 downto 0)-- Uma saída de 2 bits.
);
```

E no process as operações relacionais:
```
process (X, Y)-----------------------------Lista de sensibilidade com as entradas.
	begin
		if((X) < (Y)) then ----Caso o segundo valor seja maior que o primeiro, 
			Q <= "01";---retorna na saída ‘01’.
		elsif((X) > (Y)) then--Caso o primeiro valor seja maior que o primeiro,
			Q <= "10";---retorna na saída ‘10’.
		else
			Q <= "11";---Caso sejam iguais, retorna ‘11’.
		end if;
	end process;
```

Montando assim, o seguinte circuito lógico:
   		
(Figura 01-Circuito lógico do ALU relacional.)

Resultados
Após a criação do circuito, o grupo criou um testbench para avaliar os resultados e conferi-los.
(Figura 02 - Simulação no Model-Sim.)

A partir da Figura 02 podemos ver, por exemplo, onde a linha amarela está que ‘a’ ,que é o sinal para ‘x’ na simulação (10010110 ou 150), é menor que ‘b’, que é o sinal de ‘y’ na simulação (11111010 ou 250), aparecendo então na ‘saida’ ‘01’, o que corresponde ao sinal de Q.
Implementação na placa FPGA.
O dispositivo utilizado é Cyclone II existente no kit DE2 da altera.
	(Figura 03-Pinos utilizados para entrada e saída.)

Foram utilizados dezesseis toggle switch para os dezesseis bits de entrada e dois LED green para os dois bits de saída.
Conclusão
A implementação do código VHDL da  interface ALU para operadores relacionais foi relativamente simples, já que tomamos como base o código do projeto anterior. Porém, simplificamos um pouco mais na questão de fazer operações aritméticas com o “unsigned” e adaptamos as operações para fazer comparações entre números. O código compilou e a simulação funcionou como o esperado. A implementação na placa FPGA também foi simples: colocamos os bits das estradas nos “switches” e os da saída em dois leds. O aprendizado e o conhecimento obtido com o Projeto 01 foram essenciais para a construção desse.
 
