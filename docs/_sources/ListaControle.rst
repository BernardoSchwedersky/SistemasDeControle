===================
Lista de Exercícios
===================		


Lugar Geométrico das Raízes
===========================

-----------
Exercício 1
-----------

Desenhe o diagrama do lugar das raízes, considerando um sistema de controle realimentado com controlador :math:`C(s)=k`, para os seguintes processos:
    
- **a)** :math:`G(s)=\frac{1}{s(s+1)}`

Solução:
--------

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1],[1,1,0])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-5,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - j$\omega$')
		plt.xlabel(r'Real - $\sigma$')
		plt.title('Lugar das Raízes')

		plt.savefig('source/figures/rlA.png')

	.. figure:: /figures/rlA.png
		:figwidth: 80%
		:align: center


- **b)** :math:`G(s)=\frac{(s+1)}{(s+2)(s+5)}`

Solução:
--------

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,1],[1,7,10])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-5,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - j$\omega$')
		plt.xlabel(r'Real - $\sigma$')
		plt.title('Lugar das Raízes')

		plt.savefig('source/figures/rlB.png')

	.. figure:: /figures/rlB.png
		:figwidth: 80%
		:align: center
		
- **c)** :math:`G(s)=\frac{1}{s(s+2)(s+5)}`

Solução:
--------

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1],[1,7,10,0])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-5,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - j$\omega$')
		plt.xlabel(r'Real - $\sigma$')
		plt.title('Lugar das Raízes')

		plt.savefig('source/figures/rlC.png')

	.. figure:: /figures/rlC.png
		:figwidth: 80%
		:align: center

- **d)** :math:`G(s)=\frac{(s+1)(s+5)}{s(s+2)(s+3)}`

Solução:
--------
		
.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,6,5],[1,5,6,0])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-15,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - j$\omega$')
		plt.xlabel(r'Real - $\sigma$')
		plt.title('Lugar das Raízes')

		plt.savefig('source/figures/rlD.png')

	.. figure:: /figures/rlD.png
		:figwidth: 80%
		:align: center		

-----------
Exercício 2
-----------
	
Encontre o ponto de partida e chegada no eixo real para o diagrama do lugar das raízes do processo :math:`G(s)=\frac{(s+4)}{s(s+1)}`.

Solução:
--------

Podemos obter analiticamente os pontos de partida e chegada do eixo real considerando

.. math::
	A(s)+KB(s)=0,

e usando a equação

.. math::
	\frac{dK}{ds}=-\frac{B(s)'A(s)-A(s)'B(s)}{A(s)^2}=0

obtemos

.. math::	
	s^2+2s-(s+4)(2s+1)=0
	-s^2-7s-4=0

resultando em :math:`s=-0,62` e :math:`s=-6,37`. Graficamente podemos verificar esse resultado, por meio do diagrama a seguir.

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,4],[1,1,0])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-15,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - j$\omega$')
		plt.xlabel(r'Real - $\sigma$')
		plt.title('Lugar das Raízes')

		plt.savefig('source/figures/rl2.png')

	.. figure:: /figures/rl2.png
		:figwidth: 80%
		:align: center
		
-----------
Exercício 3
-----------
	
Usando a condição de módulo, encontre o valor de K que faz com que o polo :math:`s=-5` seja um dos polos em malha fechada de um sistema de controle realimentado, considerando :math:`C(s)=K` e :math:`G(s)=\frac{(s+4)}{(s+1)(s+3)}`.

Solução:
--------

.. container:: toggle, toggle-hidden

	Se desenharmos o lugar das raízes para o sistema :math:`G(s)`, observamos que :math:`s=-5` faz parte do lugar das raízes de :math:`G(s)`. Dessa forma, podemos aplicar diretamente a condição de módulo, para encontrar o valor de :math:`C(s)=K` que faz com que um dos polos em malha fechada seja :math:`s=-5`.

	A condição de módulo é :math:`|C(s)G(s)|=1`. Para encontrarmos o valor de K, devemos substituir :math:`s=-5` em :math:`|C(s)G(s)|=1`, e resolver a equação para K.

	.. math::
		|C(s)G(s)|=|k\frac{(s+4)}{(s+1)(s+3)}|=1
		|k\frac{(-5+4)}{(-5+1)(-5+3)}|=1
		|k\frac{-1}{(-4)(-2)}|=1
		|k\frac{-1}{8}|=1
		k=8

-----------
Exercício 4
-----------

Projete um controlador PI para o processo :math:`G(s)=\frac{3}{(s+3)}`, de forma a garantir erro nulo em regime permanente.
    
Solução:
--------	


.. container:: toggle, toggle-hidden

	O projeto de um controlador que garanta regime permanente é simples. A condição para o sistema apresentar erro nulo em regime permanente para uma referência do tipo degrau é o processo ser do tipo-1, ou seja, possuir um integrador em sua função de transferência, ou o controlador possuir um integrador. Como o sistema é uma função de transferência de 1ª ordem, sem integrador, é necessário projetar um controlador cuja estrutura contenha um integrador. O diagrama do lugar das raízes para o processo, considerando :math:`C(s)=K` é:
		
	.. container:: toggle, toggle-hidden

		.. exec_code:: realCTsignals signalplots
			:linenos:
			:hide_output:

			import numpy as np
			import matplotlib.pyplot as plt
			import control

			G = control.tf([3],[1,3])
			plt.clf()
			control.root_locus(G, plot=True, xlim=[-15,5], ylim=[-5,5], plotstr='k')

			plt.ylabel(r'Imaginário - j$\omega$')
			plt.xlabel(r'Real - $\sigma$')
			plt.title('Lugar das Raízes')

			plt.savefig('source/figures/rl4a.png')

		.. figure:: /figures/rl4a.png
			:figwidth: 80%
			:align: center	


	A escolha ideal é o controlador PI, o qual é definido como

	.. math::
		C_{PI}=\frac{K(s+z)}{s}
		
	no qual :math:`K` representa o ganho do controlador, :math:`\frac{1}{s}` representa o integrador e :math:`(s+z)` é o zero do controlador. Para ser um PI, a posição do zero deve ser à esquerda do integrador, ou seja, :math:`z<0`, resultando em um atraso de fase. Uma sintonia simples consiste em escolher a posição do zero como o valor intermediário entre o integrador e o polo do processo, fazendo :math:`z=-1,5`. O diagrama do Lugar das Raizes com o controlador é: 

	 
	.. container:: toggle, toggle-hidden

		.. exec_code:: realCTsignals signalplots
			:linenos:
			:hide_output:

			import numpy as np
			import matplotlib.pyplot as plt
			import control

			G = control.tf([3,4.5],[1,3,0])
			plt.clf()
			control.root_locus(G, plot=True, xlim=[-15,5], ylim=[-5,5], plotstr='k')

			plt.ylabel(r'Imaginário - j$\omega$')
			plt.xlabel(r'Real - $\sigma$')
			plt.title('Lugar das Raízes')

			plt.savefig('source/figures/rl4b.png')

		.. figure:: /figures/rl4b.png
			:figwidth: 80%
			:align: center	

	A escolha de K é livre para esse caso. Podemos escolher um valor elevado de K, para fazer os polos em malha fechada serem mais distantes do eixo imaginário, acelerando a resposta em malha fechada. Porém, como a única especificação era garantir erro nulo em regime permanente, qualquer valor de K não nulo é suficiente.
	
-----------
Exercício 5
-----------

Projete um controlador para o processo :math:`G(s)=\frac{1}{s(s+2)}`, fazendo com que exista erro nulo para referências do tipo degrau, sobressinal máximo de 10%, e o tempo de acomodação (2\% próximo do valor final) seja 1,3 segundos. Desenhe o diagrama de blocos do sistema de controle resultante, e verifique se o sistema projetado tem seus polos em malha fechada próximo dos polos desejados.

Solução:
--------


.. container:: toggle, toggle-hidden


	Lugar das raízes para o sistema em malha aberta
	
	.. container:: toggle, toggle-hidden

		.. exec_code:: realCTsignals signalplots
			:linenos:
			:hide_output:

			import numpy as np
			import matplotlib.pyplot as plt
			import control

			G = control.tf([1],[1,2,0])
			plt.clf()
			control.root_locus(G, plot=True, xlim=[-15,5], ylim=[-5,5], plotstr='k')

			plt.ylabel(r'Imaginário - j$\omega$')
			plt.xlabel(r'Real - $\sigma$')
			plt.title('Lugar das Raízes')

			plt.savefig('source/figures/rl5a.png')

		.. figure:: /figures/rl5a.png
			:figwidth: 80%
			:align: center	
	

	Lugar das raízes para o sistema com o controlador :math:`C(s)=\frac{s+3,05}{s+20}`	
	
	.. container:: toggle, toggle-hidden

		.. exec_code:: realCTsignals signalplots
			:linenos:
			:hide_output:

			import numpy as np
			import matplotlib.pyplot as plt
			import control

			G = control.tf([1,3.05],[1,22,40,0])
			plt.clf()
			control.root_locus(G, plot=True, xlim=[-25,5], ylim=[-5,5], plotstr='k')

			plt.ylabel(r'Imaginário - j$\omega$')
			plt.xlabel(r'Real - $\sigma$')
			plt.title('Lugar das Raízes')

			plt.savefig('source/figures/rl5b.png')

		.. figure:: /figures/rl5b.png
			:figwidth: 80%
			:align: center	
			
			

Diagrama de Bode
================

-----------
Exercício 1
-----------

Esboce o diagrama de Bode para os sistemas representados pelas seguintes funções de transferência:

.. math::
	G_1=\frac{5}{s+5}

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:
		
		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([5],[1,5])
		plt.clf()
		ag,phase,omega = control.bode_plot(G,Hz=True,dB=True,color='k')
		plt.ylabel("Fase (graus)")
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exBode1a.png')

	.. figure:: /figures/exBode1a.png
		:figwidth: 80%
		:align: center	

		
.. math::
	G_2=\frac{10(s+0,1)}{s(s+2)}	

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:
		
		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([10,1],[1,2,0])
		plt.clf()
		ag,phase,omega = control.bode_plot(G,Hz=True,dB=True,color='k')
		plt.ylabel("Fase (graus)")
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exBode1b.png')

	.. figure:: /figures/exBode1b.png
		:figwidth: 80%
		:align: center	

.. math::
	G_3=\frac{(s+0,5)}{(s+0,25)}

.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:
		
		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,0.5],[1,0.25])
		plt.clf()
		ag,phase,omega = control.bode_plot(G,Hz=True,dB=True,color='k',omega_limits=[0.001,100]) 
		plt.ylabel("Fase (graus)")
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exBode1c.png')

	.. figure:: /figures/exBode1c.png
		:figwidth: 80%
		:align: center	
	
-----------
Exercício 2
-----------

A estabilidade de um sistema de controle em malha fechada pode ser analisada a partir do diagrama de Bode do sistema em malha aberta. Para um sistema representado pela função de transferência :math:`G(s)=\frac{1}{s(s+0,1)(s+5)}`, que pode ser representado pelo diagrama de Bode 

.. exec_code:: realCTsignals signalplots
	:linenos:
	:hide_output:
	
	import numpy as np
	import matplotlib.pyplot as plt
	import control

	G = control.zpk([],[-0,-0.1,-5],gain=1)
	plt.clf()
	ag,phase,omega = control.bode_plot(G,Hz=True,dB=True,color='k',omega_limits=[0.001,100]) 
	plt.ylabel("Fase (graus)")
	plt.xlabel("Frequência (rad/s)")
	plt.savefig('source/figures/exBode2.png')

.. figure:: /figures/exBode2.png
	:figwidth: 80%
	:align: center	

determine as margens de ganho e fase, bem como as frequências associadas à essas métricas.


Diagrama de Nyquist
===================

-----------
Exercício 1
-----------

O diagrama de Nyquist é uma ferramenta usada para avaliar a estabilidade de sistemas em malha fechada a partir das funções de transferência em malha aberta do controlador e processo. Considerando um sistema cuja função de transferência é :math:`G(s)=\frac{1}{s(s+2)(s+5)}` e o controlador é representado por :math:`C(s)=\frac{K}{(s+0,1)(s+10)}`. Para esse sistema, o diagrama do lugar das raízes indica que existe uma faixa de valores do ganho K que faz com que o sistema de controle seja instável. Avalie, por meio do diagrama de Nyquist quais das opções de valores de K retorna um sistema de controle estável.

.. exec_code:: realCTsignals signalplots
	:linenos:
	:hide_output:
	
	import numpy as np
	import matplotlib.pyplot as plt
	import control

	G = control.zpk([],[-0,-2,-5],gain=1)
	C = control.zpk([],[-0.1,-10],gain=1)
	K = 1
	plt.clf()
	control.nyquist_plot(K*C*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist1a.png')

	K = 10
	plt.clf()
	control.nyquist_plot(K*C*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist1b.png')

	K = 50
	plt.clf()
	control.nyquist_plot(K*C*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist1c.png')


Ganho K=1
---------

.. figure:: /figures/exNyquist1a.png
	:figwidth: 80%
	:align: center	

Ganho K=10
----------

.. figure:: /figures/exNyquist1b.png
	:figwidth: 80%
	:align: center	
	
Ganho K=50
----------

.. figure:: /figures/exNyquist1c.png
	:figwidth: 80%
	:align: center	
	
	
-----------
Exercício 2
-----------

Uma das virtudes do diagrama de Nyquist é permitir a análise da estabilidade em malha fechada de sistemas instáveis em malha aberta. Por exemplo, para o sistema representado por :math:`G(s)=\frac{(s+1)}{(s-2)(s+5)}`, discuta sobre a estabilidade de um sistema de controle em malha fechada para as seguintes opções de ganho:

.. exec_code:: realCTsignals signalplots
	:linenos:
	:hide_output:
	
	import numpy as np
	import matplotlib.pyplot as plt
	import control

	G = control.zpk([-1],[2,-5],gain=1)
	K = 1
	plt.clf()
	control.nyquist_plot(K*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist2a.png')

	K = 10
	plt.clf()
	control.nyquist_plot(K*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist2b.png')

	K = 20
	plt.clf()
	control.nyquist_plot(K*G)
	plt.ylabel("Eixo imaginário")
	plt.xlabel("Eixo real")
	plt.savefig('source/figures/exNyquist2c.png')

Controlador 1
-------------

.. math::
	C_1=1

.. figure:: /figures/exNyquist2a.png
	:figwidth: 80%
	:align: center	

Controlador 2
-------------

.. math::
	C_2=10
	
.. figure:: /figures/exNyquist2b.png
	:figwidth: 80%
	:align: center	
	
Controlador 3
-------------

.. math::
	C_3=20

.. figure:: /figures/exNyquist2c.png
	:figwidth: 80%
	:align: center	
	

Projeto na Frequência
=====================

-----------
Exercício 1
-----------

Para um sistema definido pela função de transferência :math:`G(s)=\frac{10}{(s+10)}`, projete um controlador que faça com que exista erro nulo para referências do tipo degrau sem que o desempenho do sistema seja afetado.


-----------
Exercício 2
-----------

Usando as técnicas de projeto no domínio da frequência, projete um controlador para o processo :math:`G(s)=\frac{1}{s(s+2)}`, fazendo com que exista erro nulo para referências do tipo degrau, sobressinal máximo de 10%, e o tempo de acomodação (2\% próximo do valor final) seja 1,3 segundos. 

	
Exercícios do Livro
===================

Lista de exercícios selecionados do livro "Nise, N. S., Engenharia de Sistemas de Controle - 7ª Edição".

Capítulo 8

8.1

8.2

8.4

8.6

8.12

8.19

Capítulo 9 

9.1

9.8

9.13

Capítulo 10

10.4

10.6

Capítulo 11

11.1 a)

11.3 a)

11.9
