=============================
Projeto pelo Lugar das Raízes
=============================

O diagrama do lugar das raízes é uma ferramenta útil, não só para analisar a estabilidade e o desempenho de um sistema de controle, mas também para auxiliar no projeto do controlador. O diagrama apresenta, graficamente, todas as possíveis posições dos polos em malha fechada, alcançáveis ao ajustarmos um parâmetro do sistema de controle, o qual é, geralmente, o ganho do controlador. Utilizando o conhecimento acerca da estrutura do diagrama, e como ele é modificado ao adicionarmos polos e zeros na estrutura do controlador, podemos projetar o sistema de controle de forma a garantir que o desempenho do sistema em malha fechada seja próximo do desempenho desejado.

Neste capítulo, iremos explorar a interrelação entre algumas estruturas de controladores e o impacto de sua utilização na estrutura do diagrama do lugar das raízes. Se baseando no conhecimento da influência de cada estrutura, iremos aprender como projetar um sistema de controle capaz de atender alguns requisitos de desempenho em malha fechada.

Especificação em Malha Fechada
==============================

Para compreendermos melhor como as características de desempenho de um sistema de controle se relacionam com o diagrama do lugar das raízes, primeiramente, iremos analisar a influência dessas especificações na posição das raízes no diagrama. As principais especificações são relacionadas à existência de erro nulo em regime permanente, ao tempo de acomodação do sistema, e ao tamanho da ultrapassagem percentual (sobressinal).

Erro em Regime Permanente
-------------------------

Talvez a principal especificação em um sistema de controle é a necessidade de erro nulo em regime permanente para algum tipo de sinal de referência. O sinal de referência mais típico é o degrau unitário, já que uma parcela significativa dos sistema de controle são regulatórios, com o valor de referência sendo constante, o que pode ser modelado por um degrau unitário. Outro tipo comum de referência é a rampa unitária, a qual pode ser utilizada para modelar transições suaves entre valores distintos de referência.

As condições para existência de erro nulo foram apresentadas anteriormente, sendo que, para referências do tipo degrau, a condição é a existência de um integrador no processo ou no controlador. Como um integrador é equivalente à um polo na origem (:math:`(s)`), para termos erro nulo para referências do tipo degrau, é necessário termos um polo na origem do diagrama do lugar das raízes. Caso não exista um polo na origem e é desejado a garantia de erro nulo em regime permanente, devemos inserir o polo na origem. Para referência do tipo rampa é nécessário um integrador duplo, ou seja, dois polos na origem. Caso o sistema não apresente um integrador duplo, será necessário introduzir no controlador a quantidade de zeros na origem necessária para que o lugar das raízes tenha um par de polos na origem. 

Tempo de Acomodação
-------------------

O tempo de acomodação é diretamente relacionado à parte real dos polos dominantes do sistema. 



Ultrapassagem Percentual
------------------------

Controlador Proporcional
========================


Controlador Proporcional Integral (PI)
======================================


Controlador Avanço (Lead)
=========================



Controlador Proporcional Derivativo (PD)
========================================



Controlador Atraso (Lag)
========================

	
