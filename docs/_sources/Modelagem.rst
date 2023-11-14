==============================
Respostas de Sistemas Lineares
==============================

Os sistemas dinâmicos lineares invariantes no tempo (LTI) desempenham um papel fundamental na compreensão e no controle de uma ampla gama de fenômenos dinâmicos. A capacidade de descrever o comportamento de sistemas complexos por meio de modelos matemáticos lineares tem implicações significativas na análise e no projeto de sistemas de controle. 

A resposta de um sistema LTI para uma entrada qualquer pode ser obtida utilizando a função de transferência que rege o comportamento do processo. Assumindo que a função de transferência seja conhecida e representada por:

.. math::
	G(s)=\frac{Y(s)}{X(s)},
	
a resposta para uma entrada qualquer, :math:`x(t)`, pode ser obtida usando

.. math::
	Y(s)=G(s)X(s),
	
na qual :math:`X(s)` representa a transformada de Laplace da entrada. 

Para obtermos a resposta no domínio do tempo, :math:`y(t)`, podemos subdividir :math:`G(s)X(s)` em frações parciais e obter a transformada inversa da equação. Os modelos de entrada que são tipicamente usados consistem no impulso unitário, degrau unitário, e na rampa unitária. Essas entradas, bem como as suas transformadas, são apresentadas a seguir.

.. admonition:: Modelagem de entradas

	+---------+----------+---------------+
	|         | $x(t)$   | $X(s)$        |
	+=========+==========+===============+
	| Impulso | $\delta$ | 1             |
	+---------+----------+---------------+
	| Degrau  | $u(t)$   |$\frac{1}{s}$  |
	+---------+----------+---------------+
	| Rampa   | $tu(t)$  |$\frac{1}{s^2}$|
	+---------+----------+---------------+


Detalhes sobre como obter essas respostas podem ser encontradas na seção 2.4 do livro de Lathi, B. P. (2006). 

Para sistemas LTIs, existem poucas combinações de possíveis respostas, fazendo com que seja possível analisar o comportamento dinâmico para os casos típicos. Analisaremos, a seguir, os comportamentos gerais dos sistemas de primeira e segunda ordem, sistemas de ordem elevada e sistemas de fase não-mínima, quando sujeitos à entradas do tipo degrau. 


Sistemas de Primeira Ordem
==========================

Considerando um sistema dinâmico regido pela equação diferencial

.. math::
	\tau \frac{dy}{dt}+y(t)=kx(t),
	
se aplicarmos a transformada de Laplace e reorganizarmos no formato de uma função de transferência, obteremos a forma geral de uma função de transferência de primeira ordem

.. admonition:: Função de transferência de primeira ordem

	.. math::
		G(s)=\frac{k}{\tau s+1}=\frac{k/\tau}{s+1/\tau}.
	
O parâmetro $k$ é quivalente ao ganho estático do processo, pois, se aplicarmos um degrau unitário como entrada, e usarmos o teorema do valor final, veremos que o valor da saída quando o tempo tende à infinito será $k$.

Por sua vez, o parâmetro $\tau$ representa a constante de tempo do sistema. Esse parâmetro está diretamente ligado ao tempo no qual o sistema demora para atingir o valor final, com valores maiores de $\tau$ representando sistemas com dinâmicas mais lentas.

A resposta ao degrau unitário no domínio do tempo é obtida usando a equação a seguir:

.. math::
	y(t)=k(1-e^{-\frac{1}{\tau}t})

Nos diagramas a seguir são apresentados, interativamente, o efeito da mudança de $k$ e $\tau$.

.. admonition:: Efeito da mudança no parâmetro $\tau$

	.. raw:: html
		:file: charts/sis1ordemtau.html


.. admonition:: Efeito da mudança no parâmetro $k$

	.. raw:: html
		:file: charts/sis1ordemk.html
   
   
Sistemas de Segunda Ordem
=========================

Variando a Constante de Amortecimento
-------------------------------------

.. raw:: html
   :file: charts/sis2ordemcsi.html

Variando a Frequência Natural
-----------------------------

.. raw:: html
   :file: charts/sis2ordemwn.html

Sistemas de Alta Ordem
======================

.. raw:: html
   :file: charts/sisaltaordem.html
   
Sistemas de Fase Não Mínima
===========================

.. raw:: html
   :file: charts/sisfasenminima.html
   
   
   
Referências
===========

LATHI, B. P. Sinais e Sistemas Lineares. Porto Alegre: Bookman, 2006. 2 ed.  ISBN: 978-8560031139

NISE, Norman S. Engenharia de sistemas de controle. 7. ed. Rio de Janeiro: LTC, 2017. 772 p. ISBN 978-8521634355