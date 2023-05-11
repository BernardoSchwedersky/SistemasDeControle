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