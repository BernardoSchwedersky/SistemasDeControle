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

		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
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

		G = control.tf([1,1],[1,5,10])
		plt.clf()
		control.root_locus(G, plot=True, xlim=[-5,5], ylim=[-5,5], plotstr='k')

		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
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

		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
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

		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
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

.. math:
	A(s)+KB(s)=0,

e usando a equação

.. math:
	\frac{dK}{ds}=-\frac{B(s)'A(s)-A(s)'B(s)}{A(s)^2}=0

obtemos

.. math:	
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

		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
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

	Se desenharmos o lugar das raízes para o sistema $G(s)$, observamos que :math:`s=-5` faz parte do lugar das raízes de $G(s)$. Dessa forma, podemos aplicar diretamente a condição de módulo, para encontrar o valor de :math:`C(s)=K` que faz com que um dos polos em malha fechada seja :math:`s=-5`.

	A condição de módulo é :math:`|C(s)G(s)|=1`. Para encontrarmos o valor de K, devemos substituir :math:`s=-5` em :math:`|C(s)G(s)|=1`, e resolver a equação para K.

	.. math:
		|C(s)G(s)|=|k\frac{(s+4)}{(s+1)(s+3)}|=1
		|k\frac{(-5+4)}{(-5+1)(-5+3)}|=1
		|k\frac{-1}{(-4)(-2)}|=1
		|k\frac{-1}{8}|=1
		k=8

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,4],[1,4,3])
		plt.clf()
		roots,gains=control.root_locus(G, plot=False, xlim=[-15,5], ylim=[-5,5], plotstr='k')

		plt.plot(gains,roots)
		plt.ylabel(r'Imaginário - $\sigma$')
		plt.xlabel(r'Real - j$\omega$')
		plt.title('Lugar das Raízes')
		plt.show()
		plt.savefig('source/figures/rl3.png')
		
	.. figure:: /figures/rl3.png
		:figwidth: 80%
		:align: center









