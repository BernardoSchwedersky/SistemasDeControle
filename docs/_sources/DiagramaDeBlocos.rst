==================
Diagrama de Blocos
==================	

Quando trabalhamos com sistemas dinâmicos representados por funções de transferência, podemos aproveitar algumas propriedades da Transformada de Laplace, de forma a facilitar a manipulação e análise desses sistemas. Uma propriedade que apresenta especial utilidade é a propriedade da convolução no tempo, a qual define que, a convolução de dois sinais no tempo é equivalente à multiplicação no domínio da Transformada de Laplace.

.. admonition:: Propriedade da Convolução no Tempo 
	
	.. math::
		x(t)\ast y(t) \Leftrightarrow X(s)Y(s)
	
A propriedade da convolução no tempo é interessante no escopo do estudo do comportamento de sistemas dinâmicos LIT pois, a resposta de um sistema dinâmico LIT para uma entrada qualquer, :math:`x(t)`, é dada pela convolução entre a entrada e a resposta ao impulso, :math:`h(t)`, do sistema. Utilizando a propriedade, podemos obter a resposta de um sistema pela simples multiplicação das transformadas da resposta ao impulso e entrada, sendo que a Transformada de Laplace da resposta ao impulso é a função de transferência do sistema.

.. admonition:: Resposta de um sistema LIT para uma entrada
	
	.. math::
		y(t)=h(t)\ast x(t) \\
		Y(s)=H(s)X(s)
		
Dessa forma, podemos representar a resposta do sistema utilizando uma representação denominada Diagrama de Blocos. De forma geral, o Diagrama de Blocos é representado por três elementos básicos: blocos, setas e somadores. Blocos representam subsistemas, sendo tipicamente modelados e escritos como funções de transferência. Sinais são as entradas e saídas dos blocos, nos quais a direção do fluxo é indicada pela seta, podenso ser tensões, velocidades, forças, etc. Somatórios são os pontos nos quais sinais são somados ou subtraídos, com a subtração sendo indicada por um sinal negativo próximo ao sinal. 

Nesse diagrama, o sistema dinâmico é representado pelo bloco, cujo valor é sua função de transferência. Os sinais de entrada e saída são representados por setas direcionadas, cujo valor é equivalente à Transformada de Laplace dos sinais. O valor do sinal de saída do bloco é dado pela simples multiplicação entre o conteúdo do bloco e o sinal de entrada.

.. figure:: /figures/Blocos/Bloco.png
	:figwidth: 30%
	:align: center

Pela saída de um bloco ser obtida pela multiplicação entre o bloco e sua entrada, podemos realizar manipulações no diagrama, o que é comumente denominado como álgebra de blocos. Existem três operações básicas na álgebra de blocos, a composição em cascata, a composição em paralelo e a composição em realimentação. A seguir, será apresentada cada uma dessas composições.

Composição em cascata
=====================

Quando temos dois sistemas agrupados em série, com a saída de um dos sistemas sendo a entrada do outro, podemos realizar a composição em cascata. Um exemplo dessa estrutura é apresentado a seguir.

.. figure:: /figures/Blocos/BlocoCascata.png
	:figwidth: 60%
	:align: center

Podemos escrever a equação que descreve cada bloco como segue.
	
.. math::
	Y(s)=G(s)P(s) \\
	P(s)=H(s)X(s).

Ao reorganizarmos essa expressão, podemos subsitituir a segunda equação na primeira, eliminando :math:`P(s)`. Dessa forma, temos
	
.. math::
		Y(s)=G(s)H(s)X(s).
		
Fica evidente que, ao conectar dois blocos em cascata, o diagrama pode ser simplificado multiplicando as funções de transferência dos dois blocos, resultado no diagrama a seguir.
	
.. figure:: /figures/Blocos/BlocoCascata2.png
	:figwidth: 30%
	:align: center	
		
Composição em paralelo 
======================

O segundo tipo de composição é em paralelo. Quando conectamos dois sistemas com seus sinais de entrada e saída sendo os mesmos, temos uma conexão em paralelo, conforme apresentado a seguir.

.. figure:: /figures/Blocos/BlocoParalelo.png
	:figwidth: 60%
	:align: center	

Podemos escrever a equação que define esse diagrama como segue.
	
.. math::
	Y(s)=G(s)X(s)+H(s)X(s).
	
Podemos reorganizar essa equação, resultando na versão simplificada da composição em paralelo, conforme apresentado a seguir. 
	
.. math::
	Y(s)=[G(s)+H(s)]X(s).	
		
.. figure:: /figures/Blocos/BlocoParalelo2.png
	:figwidth: 30%
	:align: center	

Composição em realimentação
===========================

A composição de blocos em realimentação é caracterizada pela conexão de um sinal de saída como uma das entradas do bloco, fazendo com que o sinal seja realimentado no próprio sistema. Essa estrutura é apresentada a seguir.

.. figure:: /figures/Blocos/BlocoReal.png
	:figwidth: 50%
	:align: center	
		
Ao escrevermos a equação que representa o sistema, temos a seguinte equação.
	
.. math::
	Y(s)=G(s)[X(s)-Y(s)].
		
Ao reorganizarmos a equação, podemos obter a seguinte versão simplificada.
	
.. math::
	Y(s)+G(s)Y(s)=G(s)X(s) \\	
	[1+G(s)]Y(s)=G(s)X(s) \\
	Y(s)Y(s)=\frac{G(s)}{1+G(s)}X(s).

Repare que o sinal realimentado apresenta sinal negativo, ou seja, temos uma realimentação negativa. O sistema resultante apresenta um denominador :math:`1+G(s)`. Caso a realimentação fosse positiva, o sinal no denominador seria oposto. Dessa forma, um diagrama com realimentação pode ser simplificado conforme o diagrama a seguir.
		
.. figure:: /figures/Blocos/BlocoReal2.png
	:figwidth: 30%
	:align: center	

.. admonition::
	**Exemplo 1 - Simplificação de um sistema com álgebra de blocos**

	Para o sistema apresentado no diagrama a seguir, iremos obter a função de transferência equivalente por meio da álgebra de blocos.
	
	.. figure:: /figures/Blocos/BlocoEx1.png
		:figwidth: 60%
		:align: center		

	O primeiro passo consiste em simplificar os termos que se encontram em uma das configurações convencionais. Temos um par de termos em paralelo que pode ser simplificado, e em seguida, dois termos em cascata, simplificados como segue.

	.. figure:: /figures/Blocos/BlocoEx2.png
		:figwidth: 60%
		:align: center	
		
	.. figure:: /figures/Blocos/BlocoEx3.png
		:figwidth: 70%
		:align: center	

	.. figure:: /figures/Blocos/BlocoEx4.png
		:figwidth: 70%
		:align: center	
	
	Por fim, podemos simplificar o diagrama que apresenta uma realimentação negativa, resultado no diagrama a seguir.

	.. figure:: /figures/Blocos/BlocoEx5.png
		:figwidth: 30%
		:align: center
	
Exercícios Sugeridos
====================

-----------	
Exercício 1
-----------

Represente as seguintes expressões por meio de um diagrama de blocos:

a) :math:`Y(s)=G(s)[X(s)+P(s)D(s)]`.

b) :math:`Y(s)=P(s)D(s)+G(s)[R(s)-D(s)-Y(s)]`.

-----------	
Exercício 2
-----------

Encontre a função de transferência em malha fechada para os seguintes sistemas:

a) 

.. figure:: /figures/Lista1/exMF1.png
	:figwidth: 60%
	:align: center

b) 

.. figure:: /figures/Lista1/exMF2.png
	:figwidth: 60%
	:align: center
	
Solução:
--------

.. container:: toggle, toggle-hidden
	
	a) :math:`G(s)=\frac{C(s)G(s)}{1+C(s)G(s)D(s)}`

	b) :math:`G(s)=\frac{F(s)C(s)G(s)}{1+C(s)G(s)}`
    
-----------
Exercício 3
-----------

Simplifique os diagramas de blocos a seguir:

a) 

.. figure:: /figures/Lista1/exDB1.png
	:figwidth: 60%
	:align: center
    
b)

.. figure:: /figures/Lista1/exDB2.png
	:figwidth: 60%
	:align: center
	
Solução:
--------

.. container:: toggle, toggle-hidden
	
	a) :math:`G(s)=\frac{C(s)G(s)+B(s)+\frac{1}{1+D(s)}}{1+C(s)G(s)+B(s)+\frac{1}{1+D(s)}}`
	