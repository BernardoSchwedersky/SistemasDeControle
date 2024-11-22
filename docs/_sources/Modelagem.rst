===============================
Modelagem de Sistemas Dinâmicos
===============================

Diversos fenômenos da natureza (sejam eles físicos, químicos, elétricos, ...) podem ser modelados utilizando informações das grandezas associadas ao fenômeno e suas derivadas. Quando determinamos um modelo de um fenômeno por meio de uma equação que relaciona o valor de uma variável e de suas derivadas, temos uma equação diferencial. Esse tipo de representação é útil pois permite a análise do comportamento do fenômeno e é útil para o controle de processos pois servirá de base para a obtenção de modelos que representem o comportamento geral do sistema, permitindo simular o fenômeno e também desenvolver estratégias de controle computacionalmente.

A obtenção de um modelo que represente o processo se baseia na utilização das leis que regem os fenômenos que estão sendo modelados, e nas leis que regem a interconexão dos elementos do sistema. Existem metodologias consolidadas para sistemas de diversas naturezas, sendo que, ao final do processo de modelagem é obtida uma equação diferencial relacionando as grandezas de interesse do processo. A seguir é apresentado um exemplo do processo de modelagem de um sistema elétrico com componentes passivos.

	**Exemplo 1: Modelagem de um sistema elétrico com componentes passivos**

	Neste exemplo será apresentado o processo para obtenção de uma equação diferencial que represente o comportamento dinâmico de um sistema elétrico composto apenas por componentes passivos - resistores, indutores e capacitores. O sistema que será modelado é apresentado na figura a seguir.
	
	.. figure:: /figures/Modelagem/CircuitoRLC.png
		:figwidth: 60%
		:align: center	
	
	Para este sistema, consideraremos que o tensão na fonte de alimentação é a variável de entrada do sistema e iremos determinar qual a variável de saída desejada. Qualquer grandeza pode ser escolhida como variável de saída, sendo possível obter equações diferenciais que relacionam a entrada com qualquer um dos sinais de saída. A variável que foi escolhida neste exemplo, para ser a saída, é a tensão sobre o capacitor, :math:`v_c(t)`. Por convenção, iremos adotar :math:`x(t)` para representar a entrada do sistema, e :math:`y(t)` para representar a saída.
	
	Para obtermos a equação que relaciona a saída :math:`y(t)=v_c(t)` com a entrada :math:`x(t)` utilizaremos a lei das malhas de Kirchoff, que define a soma das quedas de tensão em um circuito fechado sendo :math:`0`. Dessa forma, podemos escrever a equação
	
	.. math::
		x(t)-v_i(t)-v_r(t)-v_c(t)=0,
		
	na qual :math:`v_i(t)` representa a queda de tensão no indutor e :math:`v_r(t)` a queda de tensão no resistor. Cada elemento pode ser modelado individualmente, resultando em uma equação que relaciona a tensão e a corrente aplicadas à cada elemento individual. Por exemplo, para o resistor, temos a relação :math:`v_r(t)=Ri(i)` e para o indutor temos :math:`v_i(t)=L\frac{di(t)}{dt}`. Ao substituirmos as expressões individuais, e identificarmos a saída como :math:`y(t)=v_c(t)`, obtemos a expressão
	
	.. math::
		x(t)-L\frac{di(t)}{dt}-Ri(t)-y(t)=0.
		
	Repare que a equação obtida já contém os sinais de entrada e saída, porém também o sinal :math:`i(t)`. Devemos representar esse sinal em função dos sinais de entrada e saída, o que pode ser alcançado utilizando a equação que relaciona a tensão e a corrente sobre o capacitor, :math:`i(t)=C\frac{dv_c(t)}{dt}`. Ao substituirmos :math:`i(t)`, obtemos a equação diferencial 

	.. math::
		x(t)-LC\frac{d^2 v_c(t)}{dt^2}-RC\frac{dv_c(t)}{dt}-y(t)=0.	
	
	Essa equação resultante é uma equação diferencial ordinária de um sistema linear invariante no tempo. Observe que a equação é formada apenas por constantes (R, L e C) e pelos sinais de entrada e saída, em conjunto com suas derivadas. Sabemos que o sistema é invariante no tempo pois nenhum dos parâmetros (valores que multiplicam a entrada, a saída, e as respectivas derivadas) é função do tempo, ou seja, todos os parâmetros são constantes.
	
Para fins de controle, a equação diferencial obtida no exemplo apresentado é o tipo mais comum e desejado, pois permite que se use a teoria dos sistema lineares invariantes no tempo (LIT), em conjunto com a Transformada de Laplace, para análise e projeto de controladores. Caso o sistema apresente parâmetros variantes no tempo, ou não seja linear, não teriamos um sistema LIT, o que faria com que fosse necessário o uso de técnicas mais avançadas para a análise e projeto de controladores, conceitos que não serão abordados neste curso.

Transformada de Laplace
=======================

A transformada de Laplace é uma ferramenta matemática útil para a obtenção da resposta de sistemas dinâmicos LITs, permitindo que a equação diferencial que representa o sistema seja transformada para o domínio da variável complexa :math:`s`, no qual é possível obter a solução do comportamento futuro do sistema de forma simplificada. A grande vantagem da utilização dessa transformada é ela transformar uma equação diferencial em uma equação algébrica, a qual pode ser facilmente manipulada, o que facilita a análise e o projeto de sistemas de controle.

A transformada direta de Laplace (unilateral) é definida pela equação

.. math::
	X(s)=\mathcal{L}[x(t)] \\
	X(s)=\int_0^\infty x(t)e^{-st}dt,

transformando um sinal no domínio do tempo, :math:`x(t)`, em um sinal no domínio da váriavel complexa :math:`s=\sigma +j\omega`. No contexto da análise e projeto de sistemas de controle, podemos utilizar a versão unilateral da transformada, pois os fenômenos que estamos modelando são, geralmente, causais.

Um exemplo da obtenção da transformação direta, para o um sinal exponencial, é apresentado a seguir.

	**Exemplo 2: Transformada direta de Laplace para um sinal exponencial**

	Considerando o sinal :math:`x(t)=e^{at}`, podemos obter a sua transformada de Laplace resolvendo a integral que define a transformação direta.
	
	.. math::
		X(s)=\mathcal{L}[x(t)=e^{at}]=\int_0^\infty e^{at}e^{-st}dt \\
		X(s)=\int_0^\infty e^{(a-s)t}dt \\
		X(s)=\frac{1}{a-s}\begin{bmatrix} e^{a-s}\end{bmatrix}_0^\infty \\
		X(s)=\frac{1}{a-s}\begin{bmatrix} 0-1\end{bmatrix}=\frac{1}{s-a}

	Note que a integral converge apenas para :math:`s>a`.

Podemos obter a transformada de Laplace para uma série de sinais típicos, os quais são úteis para a análise de sistemas de controle. Uma tabela de transformadas é apresentada a seguir.

.. admonition:: Tabela de Transformadas Unilaterais de Laplace 

	+---------------+-------------------+
	| $x(t)$        | $X(s)$            |
	+===============+===================+
	| $\delta$      | 1                 |
	+---------------+-------------------+
	| $u(t)$        |$\frac{1}{s}$      |
	+---------------+-------------------+
	| $tu(t)$       |$\frac{1}{s^2}$    |
	+---------------+-------------------+
	| $e^{at}u(t)$  |$\frac{1}{s-a}$    |
	+---------------+-------------------+
	| $cos(bt)u(t)$ |$\frac{s}{s^2-b^2}$|
	+---------------+-------------------+

Resposta de Sistemas Dinâmicos pela Transformada de Laplace
===========================================================

Podemos utilizar a Transformada de Laplace para obter a resposta de um sistema dinâmico LIT por meio da aplicação da transformação direta, seguida de manipulações algébricas e aplicação da transformação inversa. Esse processo de resolução se baseia na utilização de uma propriedade da Transformada de Laplace, a qual define a Transformada da derivada de um sinal. A propriedade é definida como:

.. admonition:: Propriedade da Transformada de Laplace: Diferenciação no Tempo 

	Para um sinal no domínio do tempo, :math:`x(t)`, o qual apresenta a transformada, :math:`\mathcal{L}[x(t)]=X(s)`, podemos obter a transformada da derivada de :math:`x(t)` utilizando a expressão
	
	.. math::
		\mathcal{L}\begin{bmatrix} \frac{dx(t)}{dt}\end{bmatrix}=sX(s)-x(0^{-}),

	onde o termo :math:`x(0^{-})` representa a condição inicial do sinal, para o instante de tempo :math:`t=0^{-}`.
	
	Essa propriedade pode ser aplicada recursivamente, sendo obtidas as expressões para derivadas de mais alta ordem, conforme apresentado a seguir:

	.. math::
		\mathcal{L}\begin{bmatrix} \frac{d^2 x(t)}{d^2 t}\end{bmatrix}=s^2X(s)-sx(0^{-})-\frac{dx(0^{-})}{dt}.	

	Se considerarmos as condições iniciais como nulas (o que é geralmente feito na análise de sistemas de controle), podemos escrever a expressão genérica para a propriedade da diferenciação no tempo na seguinte forma:
	
	.. math:: 
		\mathcal{L}\begin{bmatrix} \frac{d^n x(t)}{d^n t}\end{bmatrix}=s^n X(s).
		
Essa propriedade é interessante pois permite a obtenção da transformada de uma equação diferencial, a qual, no domínio da variável complexa :math:`s`, se torna uma equação algébrica. Com essa equação algébrica, podemos realizar várias manipulações e obter a solução da equação diferencial, por meio da transformação inversa. Esse processo é demonstrado no exemplo a seguir.

	**Exemplo 3: Obtenção da resposta de um sistema dinâmico pela Transformada de Laplace**
	
 	Vamos considerar o problema modelado pela Lei de Resfriamento de Newton. Essa lei modela o equilíbrio térmico entre um corpo e o ambiente, sendo proporcional à diferença entre a temperatura e o ambiente. Uma versão simplificada da lei pode ser descrita pela equação diferencial
		
	.. math::
		\frac{dT(t)}{dt}=-k\big(T(t)-T_a\big),
			
	onde :math:`T(t)` representa a temperatura do objeto, :math:`T_a` representa temperatura do ambiente e :math:`k` é uma constante positiva que representa a taxa de resfriamento ou aquecimento do sistema, associada à àrea da superfície do objeto.
		
	Se desejarmos obter a função que modela a evolução da temperatura, :math:`T(t)`, em função da temperatura ambiente da constante :math:`k`, podemos utilizar a Transformada de Laplace para encontrar a função que soluciona essa equação diferencial. Aplicando a transformação obtemos:
		
	.. math::
		sT(s)-T(0^{-})=-k\big(T(s)-\frac{T_a}{s}\big) \\
		(s+k)T(s)=T(0^{-})+\frac{kT_a}{s} \\
		T(s)=\frac{T(0^{-})}{s+k}+\frac{kT_a}{s(s+k)} \\
		T(s)=\frac{T(0^{-})}{s+k}+\frac{T_a}{s}+\frac{-T_a}{(s+k)}
		
	Aplicando a transformação inversa, obtemos a equação que modela a evolução da temperatura, no domínio do tempo, como segue:

	.. math::
		T(t)=T_a u(t)+(T(0^{-})-T_a)e^{-kt}u(t).

Função de Transferência
=======================

Como foi apresentado na seção anterior, a transformada de Laplace pode ser usada para obtenção da resposta de um sistema dinâmico LIT para uma determinada entrada e condições iniciais. De forma geral, durante a análise e projeto de sistemas de controle, iremos desconsiderar as condições iniciais, fazendo com que um sistema dinâmico LIT possa ser representado pela divisão de dois polinômios no domínio da variável complexa :math:`s`. Essa representação é denominada Função de Transferência, sendo definida como a razão entre a transformada de Laplace da saída do sistema, :math:`\mathcal{L}[y(t)]`, pela transformada de Laplace da entrada do sistema, :math:`\mathcal{L}[x(t)]`. A obtenção da função de transferência, a partir da equação diferencial, envolve a aplicação da transformada e a manipulação da equação resultante, de forma a obter a razão :math:`\frac{\mathcal{L}[y(t)]}{\mathcal{L}[x(t)]}=\frac{Y(s)}{X(s)}=H(s)`. Um exemplo da obtenção da Função de Transferência é apresentado a seguir.

	**Exemplo 4: Obtenção da Função de Transferência de um sistema elétrico com componentes passivos**

	Considerando o sistema dinâmico apresentado no Exemplo 1, podemos obter a função de transferência do sistema, partindo da equação diferencial que foi obtida a partir da modelagem, como segue:
	
	.. math::
		x(t)-LC\frac{d^2 v_c(t)}{dt^2}-RC\frac{dv_c(t)}{dt}-y(t)=0 \\
		LC\frac{d^2 v_c(t)}{dt^2}+RC\frac{dv_c(t)}{dt}+y(t)=x(t) \\
		LC\frac{d^2 v_c(t)}{dt^2}+RC\frac{dv_c(t)}{dt}+y(t)=x(t)
		
	Como a saída do sistema é :math:`y(t)=v_c(t)`, podemos aplicar a transformada, obtendo
	
	.. math::
		LCs^2 Y(s)+RCsY(s)+Y(s)=X(s),

	o que resulta, após a reorganização, na função de transferência
	
	.. math::
		\frac{Y(s)}{X(s)}=\frac{1}{LCs^2+RCs+1}.
		

Exercícios Sugeridos
====================

-----------
Exercício 1
-----------

Para o circuito apresentado na figura a seguir, encontre a função de transferência considerando como entrada a tensão na fonte (:math:`x(t)`) e como saída:

a) :math:`V_c`

b) :math:`i_r`

.. figure:: /figures/Lista1/exCir.png
	:figwidth: 40%
	:align: center
			
-----------
Exercício 2
-----------

Considerando os sistemas regidos por equações diferenciais a seguir, encontre a função de transferência que rege seu comportamento dinâmico, especifique a ordem do sistema, seus polos, seus zeros, e esboce a posição dos mesmo no plano complexo.

a) :math:`\frac{d^2}{dt}y(t)+7\frac{d}{dt}y(t)+10y(t)=x(t)`.

b) :math:`\frac{d}{dt}y(t)+10y(t)=\frac{d^2}{dt}x(t)+3x(t)`.

c) :math:`\frac{d^3}{dt}y(t) + 3\frac{d^2}{dt}y(t)+30\frac{d}{dt}y(t)+10y(t)=\frac{d^2}{dt}x(t)+10x(t)`.

Solução:
--------

.. container:: toggle, toggle-hidden

	a) :math:`G(s)=\frac{1}{s^2+7s+10}`, polos em :math:`s=-2` e :math:`s=-5` e nenhum zero.
	
	b) :math:`G(s)=\frac{s^2+3}{s+10}`, polos em :math:`s=-10` e zeros em :math:`s=\sqrt{3}s` e :math:`s=-\sqrt{3}s`.
	
	c) :math:`G(s)=\frac{s^2+10}{s^3+3s^2+30s+10}`, polos em :math:`s=-0,34`, :math:`s=-1,3+j5,2` e :math:`s=-1,3-j5,2`, e zero em :math:`s=-10`.	
	

Referências
===========

LATHI, B. P. Sinais e Sistemas Lineares. Porto Alegre: Bookman, 2006. 2 ed.  ISBN: 978-8560031139

NISE, Norman S. Engenharia de sistemas de controle. 7. ed. Rio de Janeiro: LTC, 2017. 772 p. ISBN 978-8521634355