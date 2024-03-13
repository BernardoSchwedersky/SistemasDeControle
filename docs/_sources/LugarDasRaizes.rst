===========================
Lugar Geométrico das Raízes
===========================

Conceito
========

Em um sistema de controle realimentado, as raízes do polinômio característico do sistema em malha fechada são os polos do sistema, os quais determinam a sua resposta dinâmica. O polinômio característico é obtido a partir da equação característica do sistema em malha fechada, que é a equação obtida ao igualar à zero o denominador da função de transferência do sistema.

Considerando um sistema de controle realimentado em que o controlador é :math:`C(s)=K`, conforme apresentado no diagrama de blocos a seguir:


os polos do sistema em malha fechada podem ser obtidos ao encontrar as raízes de :math:`1+KG(s)=0`. Como o ganho :math:`K` é uma variável, os polos assumirão valores distintos para cada valor de :math:`K`.



	**Exemplo 1:** Considerando um processo integrador, descrito pela função de transferência :math:`G(s)=\frac{1}{s(s+10)}`, controlado por um controlador proporcional, :math:`C(s)=K`, podemos obter a função de transferência do sistema em malha fechada conforme:

	.. math::
		G_{mf}=\frac{C(s)G(s)}{1+C(s)G(s)}=\frac{K\frac{1}{s(s+10)}}{1+K\frac{1}{s(s+10)}}=\frac{K}{s^2+10s+K}.

	A posição dos polos do sistema em malha fechada é obtida encontrando as raízes de :math:`s^2+10s+K=0`, existindo polos distintos para cada valor de :math:`K`. Se substituirmos :math:`K` por diversos valores, podemos encontrar a posição dos polos para cada configuração, conforme apresentado na tabela a seguir:
		
	+-------+-----------+-----------+
	| K     | Polo 1    | Polo 2    |
	+=======+===========+===========+
	| 0     | -10       | 0         |
	+-------+-----------+-----------+
	| 5     | -9,47     | -0,53     |
	+-------+-----------+-----------+
	| 10    | -8,87     | -1,13     |
	+-------+-----------+-----------+
	| 15    | -8,16     | -1,84     |
	+-------+-----------+-----------+
	| 20    | -7,24     | -2,78     |
	+-------+-----------+-----------+
	| 25    | -5        | -5        |
	+-------+-----------+-----------+
	| 30    | -5+j2,34  | -5-j2,34  |
	+-------+-----------+-----------+
	| 35    | -5+j3,16  | -5-j3,16  |
	+-------+-----------+-----------+
	| 40    | -5+j3,87  | -5-j3,87  |
	+-------+-----------+-----------+

	Podemos notar que, quando :math:`K=0`, a posição dos polos do sistema em malha fechada é igual à dos polos do sistema em malha aberta. A medida que que o ganho é incrementado, a posição dos polos em malha fechada se aproxima, até que, para :math:`K=25`, temos um par de polos em :math:`-5`. Ao incrementarmos ainda mais o ganho, é verificado que os polos deixam de ser puramente reais, tornando-se complexos conjugados. 
		
	Podemos apresentar graficamente a variação da posição dos polos do sistema em malha fechada no plano complexo. Para o sistema do exemplo, a variação da posição dos polos é apresentada no diagrama a seguir.
		
	.. raw:: html
		:file: charts/ExemploRaizes.html

O lugar das raízes (*root locus*) é uma representação gráfica das posições dos polos do sistema em relação à variação de um parâmetro 
(geralmente o ganho do controlador). O eixo x do gráfico representa a parte real das raízes (polos e zeros), enquanto o eixo y representa a 
parte imaginária. À medida que o parâmetro varia, o lugar das raízes mostra como as posições dos polos em malha fechada mudam.

A análise do lugar das raízes é útil para entender o comportamento dinâmico do sistema e fazer ajustes no sistema de controle, de forma à atender aos requisitos de desempenho desejados. As aplicações práticas do diagrama do lugar das raízes incluem:

- Projeto de Controladores - Ao analisar o lugar das raízes, é possível projetar controladores de forma a garantir a estabilidade e alcançar o desempenho desejado para o sistema. A inspeção do diagrama permite identificar como o ganho do sistema afeta a estabilidade e permite o ajuste para que sejam atendendidos requisitos específicos, como tempo de resposta, coeficiênte de amortecimento e máxima ultrapassagem percentual (sobressinal).

- Análise de Sistemas de Controle - Além de auxiliar no projeto, a inspeção do diagrama permite analisar o comportamento do sistema de controle. O lugar das raízes ajuda a visualizar como a estabilidade é afetada por mudanças nos parâmetros do sistema de controle (ganho).


Vetores de Números Complexos
============================

As funções de transferência são funções da variável complexa :math:`s=\sigma + j\omega`. Essa variável complexa pode ser representada tanto na forma cartesiana (:math:`s=\sigma + j\omega`), como na forma polar (:math:`s=M\angle \theta`). A representação polar apresenta como parâmetros o módulo e o ângulo, obtidos ao representarmos a grandeza complexa :math:`s` como um vetor iniciando na origem e terminando em :math:`s`. A relação entre essas duas representações é apresentada a seguir.

.. figure:: /figures/LugarDasRaizes/NImag1.png
	:figwidth: 30%
	:align: center	
	
Quando definimos uma função dessa variável complexa, como por exemplo :math:`F(s)=s+a`, obtemos outra grandeza complexa, equivalente à grandeza original deslocada por :math:`a`, na forma :math:`F(s)=(\sigma +a) + j\omega`. De forma similar, podemos representar graficamente essa nova grandeza conforme a figura a seguir.
	
.. figure:: /figures/LugarDasRaizes/NImag2.png
	:figwidth: 30%
	:align: center

A função :math:`F(s)=(\sigma +a) + j\omega` representa uma função de transferência com um zero e nenhum polo. Dessa forma, :math:`F(s)` pode ser representado por um vetor partindo de :math:`-a` e terminando em :math:`s`. Se escolhermos qualquer ponto de teste no plano complexo, por exemplo :math:`s_p=\sigma_p-j\omega_p`, podemos encontrar qual o módulo e ângulo desse ponto em relação à função complexa :math:`F(s)`.

	**Exemplo 2:** Encontrar o módulo e o ângulo do ponto de teste :math:`s_1=2-j1` em relação à função complexa :math:`F(s)=s+1`;
	
	Para encontrar os valores de módulo e ângulo de um ponto em relação à uma função complexa, devemos substituir a variável :math:`s` da função complexa pelo ponto de teste :math:`p`.

	.. math::
		F(s_1)=(2-j1)+1=3-j1

	Após a substituição, podemos converter a grandeza complexa que estava na forma cartesiana para a forma polar, onde o módulo é :math:`M=\sqrt{\sigma^2+\omega^2}` e o ângulo é :math:`\theta=tan^{-1}(\frac{\omega}{\sigma})`.
	
	.. math::
		M=\sqrt{3^2+1^2}=\sqrt{10}
		
		\theta=tan^{-1}{\frac{-1}{3}}=-18,4^o
		
		F(s_1)=\sqrt{10} \angle -18,4^o
		
Para uma função de transferência genérica, na qual existem :math:`m` zeros e :math:`n` polos, a qual pode ser representada de forma genérica como

.. math:
	F(s)=\frac{\prod_{i=1}^{m} (s+z_i)}{\prod_{i=1}^{n} (s+p_i)},
	
podemos representar o módulo de qualquer ponto de teste usando

.. math::
	M=\frac{\prod_{i=1}^{m} \mid(s+z_i)\mid}{\prod_{i=1}^{n} \mid(s+p_i)\mid},
	
nas quais o módulo é formado pela multiplicação dos módulos dos vetores iniciados em cada zero, dividido pela multiplicação dos módulos dos vetores iniciados em cada polo.

Já o ângulo pode ser obtido por

.. math::
	\theta=\sum_{i=1}^{m} \angle(s+z_i)-\sum_{i=1}^{n} \angle(s+p_i),
	
sendo formado pela subtração entre a soma dos ângulos dos vetores associados à cada zero e a soma dos ângulos dos vetores associdos aos polos.

	**Exemplo 3:** obtenção do valor de :math:`F(s)` testados no ponto :math:`s_1=-3+j4`;
	
	Solução: podemos desenhar os vetores iniciando em cada zero e polo e terminando no ponto de teste :math:`s_1`, como apresentado na figura a seguir:
	
	.. figure:: /figures/LugarDasRaizes/ExemploF.png
		:figwidth: 30%
		:align: center	

	Se calcularmos o módulo e o ângulo de cada um dos três vetores iremos obter os valores a seguir
	
	.. list-table:: 
		:widths: 5 10 10 
		:header-rows: 1
		:stub-columns: 0

		* - 
		  - Vetor - Forma Cartesiana
		  - Vetor - Forma Polar
		* - :math:`(s+1)`
		  - :math:`-2+j4`
		  - :math:`\sqrt{20}\angle 116,6^o`
		* - :math:`s`
		  - :math:`-3+j4`
		  - :math:`5\angle126,0^o`
		* - :math:`(s+2)`
		  - :math:`-1+j4`
		  - :math:`\sqrt{20}\angle 104,0^o`

	Dessa forma, para obtermos o valor de :math:`F(s_1)` devemos encontrar o módulo e o ângulo. O módulo é obtido pela multiplicação dos zeros, dividido pela multiplicação dos polos, na forma :math:`M=\frac{\sqrt{20}}{5\sqrt{17}}`. O ângulo é obtido pela subtração entre a soma dos ângulos dos zeros com a soma dos ângulos dos polos, na forma :math:`\theta=116,6^o-126,9^o-104,0^o=114,3^o`. Com isso, 
	
	.. math::
		F(s_1)=0,217\angle 114,3^o.

Condições para Pertencimento ao Lugar das Raízes
================================================

Na seção anterior foi apresentado como podemos calcular o módulo e o ângulo de um ponto qualquer no plano complexo, em relação à uma função complexa, por exemplo, uma função de transferência. Utilizando essa informação do módulo e ângulo, podemos determinar se um ponto qualquer faz parte do lugar das raízes do sistema de controle, ou seja, se esse ponto é uma dos possíveis polos em malha fechada do sistema, alcançável ao ajustarmos o ganho do controlador.

Considerando que o comportamento em malha fechada é determinado pela função de transferência 

.. math::
	G_{mf}=\frac{C(s)G(s)}{1+C(s)G(s)}
	
onde o controlador é composto por um ganho variável e um conjunto de polos e zeros, na forma :math:`C(s)=K\frac{N(s)}{D(s)}=KC_{gu}(s)`, onde :math:`C_{gu}(s)` representa o conjunto de polos e zeros do controlador, considerando ganho unitário. Por simplicidade, iremos representar o controlador como tendo ganho unitário, e sendo multiplicado externamento pelo ganhho variável, na forma :math:`KC(s)`, onde :math:`C(s)=\frac{N(s)}{D(s)}`. Dessa forma, o sistema em malha fechada é representado como

.. math::
	G_{mf}=\frac{KC_{gu}(s)G(s)}{1+KC_{gu}(s)G(s)}.
	
A equação característica do sistema é dada por

.. math::
	1+KC_{gu}(s)G(s)=0
	
.. math::
	KC_{gu}(s)G(s)=-1

Como :math:`KC_{gu}(s)G(s)` é uma grandeza complexa, podemos representar a equação característica como duas equações reais, uma representando o módulo e outra o ângulo da equação característica. As duas equações são a condição de módulo

.. math::
	|KC_{gu}(s)G(s)|=1
	
e a condição de ângulo (fase)

.. math::	
	\angle KC_{gu}(s)G(s)=180^o (2k+1) \hspace{1cm} k=0,1,2,\dots

Ou seja, para um ponto qualquer do plano complexo ser uma das raízes em malha fechada do sistema, ele deverá deverá ser uma solução da equação característica, devendo então verificar as duas condições (módulo e ângulo). 

Como o diagrama do lugar das raízes considera todas os possíveis polos em malha fechada, decorrentes do ajuste do ganho :math:`K`, podemos garantir que qualquer ponto que satisfazer a condição de módulo fará parte do lugar das raízes do sistema, já que poderemos escolher um valor de :math:`K` que fará com que a condição de módulo seja satisfeita.


Para um ponto do plano complexo fazer parte do lugar das raízes, ele deve satisfazer a condição de ângulo, :math:`\angle KC_{gu}(s)G(s)=180^o (2k+1) \hspace{1cm} k=0,1,2,\dots`.
	
Para determinarmos qual o valor do ganho :math:`K` faz com que um polo em malha fechada esteja sobre o ponto testado, devemos usar a condição de módulo, :math:`|KC_{gu}(s)G(s)|=1`.
	

	**Exemplo 4:** Considerando o sistema apresentado no Exemplo 1, vamos determinar se os pontos :math:`s_1=-3` e :math:`s_2=-4+j1` fazem parte do lugar das raízes do sistema de controle:
	
	Solução: Para um ponto do plano complexo fazer parte do lugar das raízes é necessário que a condição de ângulo seja satisfeita. Dessa forma, devemos verificar se :math:`\angle KC_{gu}(s)G(s)=180^o (2k+1) \hspace{1cm} k=0,1,2,\dots`. Como o controlador é apenas :math:`C(s)=K`, temos

	.. math::
		KG(s)=\frac{s}{s(s+10)},
	
	.. math::	
		\angle KG(s)=\angle(k)-\angle(s)-\angle(s+10),
		
	.. math::	
		\angle KG(s)=-\angle(s)-\angle(s+10).
	
	Substituindo o ponto de teste :math:`s_1=-3` obtemos:
	
	.. math::
		\angle KG(s_1)=-\angle(-3)-\angle(+7),
	
	.. math::	
		\angle KG(s_1)=-180^o - 0^o=-180^o.
		
	Como a fase se repete a cada :math:`360^o`, o ângulo :math:`-180^o` é equivalente à :math:`180^o`, fazendo com que a condição de ângulo seja verificada para o ponto de teste :math:`s_1`. Dessa forma, :math:`s_1` faz parte do lugar das raízes do sistema. 

	Podemos testar :math:`s_2` da mesma forma, como segue:
	
	.. math::
		\angle KG(s_2)=-\angle(-4+j1)-\angle(+6+j1),
	
	.. math::	
		\angle KG(s_2)=-atan(\frac{1}{-4})-atan(\frac{1}{6}),
		
	.. math::
		\angle KG(s_2)=-165,96^o-9,46^o=-175,42^o.
	
	Dessa forma, como :math:`\angle KG(s_2)` não é :math:`180^o` nem um dos múltiplos ímpares de :math:`180^o`, conforme :math:`180^o (2k+1)`, o ponto de teste :math:`s_2` não faz parte do lugar das raízes do sistema de controle.

Esboço do Diagrama
==================

Para um ponto de teste fazer parte do lugar das raízes é verificarmos a condição de ângulo. Testarmos todos os pontos do plano complexo é inviável, porém, o traçado do diagrama pode ser realizado seguindo um conjunto de regras empíricas, que tornam possível o esboço do lugar das raízes.

Para os esboço do lugar das raízes iremos utilizar 7 regras. Com essas regras simples é possível gerar um esboço muito próximo ao traçado real do lugar das raízes.

.. admonition:: Regra 1: Número de ramos

	O número de ramos do lugar das raízes é igual ao número de polos em malha fechada do sistema de controle. Um ramo é definido como a trajetória que um polo realiza a medida que o ganho do sistema de controle é incrementado.
	
		**Exemplo 5**: o lugar das raízes de um sistema de controle onde :math:`C(s)=K` e :math:`G(s)=\frac{1}{s(s+1)(s+3)}` terá um número de ramos equivalente ao número de polos em malha fechada. Como a equação característica é :math:`s^3+4s^2+3s+K`, vemos que o sistema terá 3 ramos. O lugar das raízes para esse sistema é apresentado na figura a seguir (**selecione na legenda cada um dos ramos**).
	
		.. raw:: html
			:file: charts/ExemploLRRamos.html
			
.. admonition:: Regra 2: Simetria

	O lugar das raízes é simétrico em relação ao eixo real. Isso acontece pois, quando o sistema apresenta polos complexos, eles sempre ocorrerão em pares complexos conjugados. Dessa forma, sempre que houver um ramo com parte complexa, existirá um segundo ramo com parte complexa conjugada.
	
		**Exemplo 6**: considerando o mesmo sistema do exemplo 5, podemos observar a simetria do lugar das raízes. No diagrama que foi apresentado, podemos observar que os ramos 2 e 3 são simétricos, o que é esperado, já que, a medida que as raízes se desprendem do eixo real, ela passam a existir sempre em pares complexos conjugados.
	
.. admonition:: Regra 3: Segmentos sobre o eixo real

	O lugar das raízes existe à esquerda de um número ímpar de polos e zeros em malha aberta. Dessa forma, podemos determinar toda a porção do eixo real que faz parte do lugar das raízes ao inserir todos polos e zeros do processo e do controlador, e desenharmos a porção em que exista um número ímpar de polos e zeros à direita da porção.
	
		**Exemplo 7**: considerando um sistema de controle onde o controlador é :math:`C(s)=K\frac{s+1}{s}` e o processo é definido por :math`G(s)=\frac{s-1}{s+3}`, podemos esboçar a porção do lugar das raízes sobre o eixo real. Para tal, devemos posicionar todos os polos e zeros de :math:`C(s)G(s)` no plano complexo, e definir a porção que faz parte do lugar percorrendo o eixo real da direta para a esquerda. Toda a porção que tiver um número ímpar de polos e zeros à sua direita fará parte do lugar. Podemos verificar isso na figura a seguir. Podemos ver que existem 2 ramos, já que temos duas raízes em malha fechada, e esses ramos formam as duas porções do eixo real pertencentes ao lugar. Para este exemplo, o lugar das raízes está todo contido sobre o eixo real, o que pode ser visto na figura a seguir.

		.. raw:: html
			:file: charts/ExemploLREixoReal.html
			
.. admonition:: Regra 4: Pontos de início e fim
	
	O lugar das raízes se inicia na posição dos polos em malha aberta e termina na posição dos zeros em malha aberta. Caso existam mais polos do que zeros, os polos excedentes terminarão em zeros virtuais, localizados em posições tendendo ao infinito.
	
		**Exemplo 8**: se levarmos em conta o sistema do exemplo 7, podemos observar os pontos de início e fim do lugar das raízes. Quando o ganho :math:`K=0`, os polos em malha fechada se encontram sobre a posição dos polos em malha aberta. À medida que aumentarmos o ganho, os polos se moverão na trajetória determinada pelos ramos, tendendo à posição dos zeros em malha aberta, quando :math:`K\rightarrow \infty`. **Mova o seletor de ganho na figura do exemplo 7 para observar o polo em malha fechada se movendo.**
	
.. admonition:: Regra 5: Assíntotas

	Quando existirem mais polos do que zeros, a diferença entre o número de polos e zeros é equivalente ao número de assíntotas, na forma :math:`\# a = \# polos - \# zeros`. Cada assíntota representa uma direção na qual os polos que não terminarem na posição dos zeros em malha aberta se moverão.
	Podemos determinar qual o ponto de ínico das assíntotas, bem como o ângulo das mesmas. Considerando o ponto de partida das assíntotas definido como :math:`\sigma_a`, podemos obtê-lo utilizando a equação a seguir:
	
	.. math::
		\sigma_a=\frac{\sum polos - \sum zeros}{\# polos - \# zeros}.
		
	Ou seja, o ponto de partida das assíntotas é obtido pela subtração entre a soma das posições dos polos e a soma das posições dos zeros, dividido pela diferença entre o número de polos e zeros (número de assíntotas).
	Por sua vez, o ângulo das assíntotas, definido como :math:`\theta_a`, pode ser obtido na forma:
	
	.. math:: 
		\theta_a=\frac{(2k+1)\pi}{\# polos - \# zeros}, \hspace{1cm} k=0,1,2,\dots
		
	Como o número de assintotas é definido por :math:`\# a = \# polos - \# zeros`, devemos obter um ângulo para cada assíntota. Dessa forma, devemos substituir :math:`k` ao menos :math:`a` vezes, obtendo os :math:`a` ângulos paras as respectivas :math:`a` assíntotas.

		**Exemplo 8:** considerando o sistema de controle apresentado na figura a seguir, determine o número de assíntotas e o ângulo das mesmas.
		
		.. figure:: /figures/LugarDasRaizes/DiagramaExemplo7.png
			:figwidth: 60%
			:align: center	
		
		Solução:
		
		O sistema já se encontra no formato desejado para a determinação do lugar das raízes, já que temos um processo definido por :math:`G(s)=\frac{s+3}{s(s+1)(s+2)(s+4)}` e um controlador com ganho variável. O sistema em malha aberta possuí um zero e quatro polos. Dessa forma, o número de assíntotas é:
		
		.. math::
			a=\# polos - \# zeros = 4-1=3.
			
		Para encontrarmos a posição de início das assíntotas devemos usar a equação:
		
		.. math::
			\sigma_a=\frac{\sum polos - \sum zeros}{\# polos - \# zeros},
		
		.. math::
			\sigma_a=\frac{(0-1-2-4) - (-3)}{4 - 1}=\frac{-4}{3}.
		
		Por sua vez, podemos determinar o ângulo das assíntotas conforme a equação:
		
		.. math:: 
			\theta_a=\frac{(2k+1)\pi}{\# polos - \# zeros}, \hspace{1cm} k=0,1,2,\dots
			
		.. math:: 
			\theta_a=\frac{(2k+1)\pi}{4-1}, \hspace{1cm} k=0,1,2,\dots
			
		.. math:: 
			\theta_a=\frac{(2k+1)\pi}{3}, \hspace{1cm} k=0,1,2,\dots
			
		Devido à existirem três assíntotas, devemos substituir :math:`k` por 0, 1 e 2. Dessa forma obtemos:
		
		.. math:: 
			\theta_1=\frac{(0+1)\pi}{3}=\frac{\pi}{3},
			
		.. math:: 
			\theta_2=\frac{(2+1)\pi}{3}=\pi,
			
		.. math:: 
			\theta_2=\frac{(4+1)\pi}{3}=\frac{5\pi}{3}.
			
		Ou seja, o lugar das raízes do sistema apresenta três assíntotas iniciando em :math:`\sigma_a=\frac{-4}{3}`, e com ângulos :math:`\theta_1=\frac{\pi}{3}`, :math:`\theta_1=\pi` e :math:`\theta_1=\frac{5\pi}{3}`. Se desenharmos o lugar das raízes para o sistema em questão, incluíndo no esboço as assíntotas, podemos observar o comportamento das raízes à medida que o ganho aumenta. Um dos polos tende à assíntota com ângulo :math:`\pi`, enquanto um par de polos se encontra sobre o eixo real, se desprendendo do mesmo para seguir em direção às assíntotas com àngulo :math:`\theta_1=\frac{\pi}{3}` e :math:`\theta_1=\frac{5\pi}{3}`. Esse diagrama é apresentado a seguir (**clique na legenda para vizualizar as assíntotas e ramos do lugar**).
		
		.. raw:: html
			:file: charts/ExemploLR7a.html
			
.. admonition:: Regra 6: Pontos de saída e chegada no o eixo real

	Um par de ramos deixa o eixo real, ou retorna ao eixo real quando um par de polos apresenta parte real igual, e parte complexa igual à zero. Dessa forma, o par de polos está sobre a mesma posição, prestes a se tornar um par complexo conjugado. Se, ao aumentarmos o ganho, o par de polos se encontra e torna-se complexo conjugado, teremos um ponto de saída do eixo real. Por sua vez, se o par de polos é complexo conjugado, e ao aumentarmos o ganho eles se encontrarm, tornando-se puramente real, temos um ponto de chegada no eixo real. 
	Para encontrarmos qual são os pontos de chegada e saída podemos utilizar o método de tranição. Partindo da equação
	
	.. math::
		KC_{gu}(s)G(s)=-1,
	
	podemos definir 
	
	.. math::
		T(s)=C_{gu}(s)G(s),
	
	a qual é uma função de transferência contendo todos polos e zeros do processo e do controlador. Se definirmos que :math:`T(s)` apresenta m zeros e n polos, a condição para encontrarmos os pontos de chegada e saída é a relação
	
	.. math::
		\sum_{i=1}^{m}\frac{1}{\sigma-z_i}=\sum_{j=1}^{n}\frac{1}{\sigma-p_j},
		
	na qual :math:`z_i` representa a posição do i-ésimo zero e :math:`p_j` representa o j-ésimo polo, ambos para :math:`T(s)`. Se resolvermos a equação para :math:`\sigma`, iremos obter as posições de entrada e saída do eixo real. 
	
		**Exemplo 9**: considerando um sistema de controle representado pelo diagrama de blocos a seguir:
		
		.. figure:: /figures/LugarDasRaizes/Exemplo9.png
			:figwidth: 60%
			:align: center	
		
		Já foi determinada a porção do eixo real que faz parte do lugar das raízes, e já foi determinado que não existem assíntotas. Por isso, sabemos que o par de polos irá se encontrar em algum ponto, se desprenderá do eixo real fazendo uma trajetória elíptica, e retornará ao eixo real para que os polos se dirijam na direção do par de zeros. Devemos então determinar quais os pontos de saída e chegada no eixo real.
		
		Solução:
		Utilizando a condição do método de transição, iremos obter os pontos de saída e entrada usando a equação
		
		.. math::
			\sum_{i=1}^{m}\frac{1}{\sigma-z_i}=\sum_{j=1}^{n}\frac{1}{\sigma-p_j}.
		
		Para o sistema em questão, temos apenas 2 ramos, então, teremos apenas 1 ponto de saída e 1 ponto de entrada. Partindo de :math:`T(s)=\frac{(s+1)(s+2)}{(s-1)(s-2)}`, vemos que existem 2 zeros em (-1,-2) e 2 polos localizados em (1,2). Substituindo na condição, obtemos
		
		.. math::
			\frac{1}{\sigma+1}+\frac{1}{\sigma+2}=\frac{1}{\sigma-1}+\frac{1}{\sigma-2}.
		
		Resolvendo a equação podemos encontrar os valores de :math:`\sigma`, conforme
		
		.. math::
			\frac{(2\sigma+3)}{(\sigma+1)(\sigma+2)}=\frac{(2\sigma-2)}{(\sigma-1)(\sigma-2)}
			
		.. math::
			(2\sigma+3)(\sigma^2-3\sigma+2)=(2\sigma-3)(\sigma^2+3\sigma+2)
		
		.. math:::
			2\sigma^3-6\sigma^2+4\sigma+3\sigma^2-9\sigma+6=2\sigma^3+6\sigma^2+4\sigma-3\sigma^2-9\sigma-6
			
		.. math::
			-6\sigma^2=-12
			
		.. math::
			\sigma=\pm \sqrt{2}\approx\pm 1,41.
		
		Para o sistema em análise, obtivemos um par de valores que indicam os pontos de saída e chegada. Os valores são :math:`\sigma=\pm \sqrt{2}`, sendo que não sabemos, a priori, qual é o ponto de saída e qual é o de chegada. Saberemos ao inspecionarmos o diagrama. Como o ponto :math:`\sigma=+\sqrt{2}` está entre o par de polos, ele será o ponto de saída, e o ponto :math:`\sigma=-\sqrt{2}` será o ponto de chegada, já que se encontra entre o par de zeros. O diagrama é apresentado na figura a seguir (**vizualize os ramos do diagrama clicando na legenda**).
		
		.. raw:: html
			:file: charts/ExemploLRSaidaEixo.html		
	
	
.. admonition:: Regra 7: Ponto de cruzamento com o eixo imaginário
	
	O lugar das raízes pode cruzar com o eixo imaginário em diversas situações. Sabemos que, no momento em que o lugar cruza com o eixo imaginário, os polos em malha fechada apresentam parte real nula, sendo o sistema marginalmente estável, ou instável. Para encontrarmos os pontos de cruzamento com o eixo real podemos utilizar a tabela de Routh-Hurwitz, encontrando qual o valor de :math:`K` faz com que tenhamos ao menos um termo igual a 0 na primeira coluna, o que significa que o sistema é marginalmente estável, ou instável. Utilizando o valor de :math:`K` obtido, podemos resolver a equação característica :math:`1+KC_{gu}(s)G(s)=0`, com :math:`s=\pm j\omega` para encontrarmos a posição, :math:`\pm jw`, dos polos no instante em que o lugar cruza com o eixo imaginário.

		**Exemplo 10**:
		Considerando o lugar das raízes do sistema apresentado no exemplo 9, iremos determinar o ponto exato em que o lugar cruza com o eixo imaginário. 
		
		Solução: Para determinar esse ponto, podemos utilizar a tabela de Routh-Hurwitz. Para construir a tabela, é necessário utilizar a equação característica do sistema em malha fechada.
		
		.. math::
			1+\frac{K(s+1)(s+2)}{(s-1)(s-2)}=0
			
		.. math::
			(s-1)(s-2)+K(s+1)(s+2)=0
			
		.. math::
			s^2-3s+2+Ks^2+3Ks+2K=0
			
		.. math::
			(1+K)s^2+(3K-3)s+(2+2K)=0
			
		A tabela de Routh-Hurwitz pode ser construída conforme
		
			+-------------+-----------+-----------+
			|             | Coluna 1  | Coluna 2  |
			+=============+===========+===========+
			| :math:`s^2` |    1+K    |   2+2K    |
			+-------------+-----------+-----------+
			| :math:`s^1` |    3K-3   |     0     |
			+-------------+-----------+-----------+
			| :math:`s^0` |    2+2K   |     0     |
			+-------------+-----------+-----------+
			
		A condição para que o sistema seja marginalmente estável, ou seja, existam polos sobre o eixo imaginário, é termos algum termo igual à 0 na primeira coluna da tabela. Por isso, iremos igualar todos os termos da primeira coluna à 0, de forma a encontrar quais valores de :math:`K` fazem com que o sistema seja marginalmente estável.

		.. math::
			1+K=0,
			
			K=-1.
		
		.. math:
			3K-3=0,
			
			K=1.
		
		.. math::
			2+2K=0,
			
			K=-1.
		
		O diagrama do lugar das raízes que estamos criando considera as posições das raízes entre :math:`0\ge K \le \infty`. Dessa forma, a solução que procuramos é :math:`K=1`, ja que a outra solução retorna um ganho fora da região que estamos considerando.
		Após obtermos o ganho que faz com que tenhamos raízes sobre o eixo imaginário, devemos substituir esse ganho na equação característica e obtermos o valor de :math:`\omega`, para raízes :math:`s=\pm j\omega`.
		
		.. math::
			(1+K)s^2+(3K-3)s+(2+2K)=0
			
		.. math::
			2s^2+4=0
			
		.. math::
			s^2=-2
		
		.. math::
			(j\omega)^2=-2
			
		.. math::
			j^2\omega^2=-2
			
		.. math::
			\sqrt{-1}^2\omega^2=-2
			
		.. math::
			\omega^2=2
			
		.. math::
			\omega=\pm\sqrt{2}

		Ou seja, ao substituirmos :math:`s=j\omega`, obtivemos :math:`\omega=\pm\sqrt{2}` sendo os pontos de cruzamento com o eixo imaginário. Podemos verificar que esse é o ponto de cruzamento no diagrama apresentado no exemplo 9.
		
		
Essas são as principais regras que, se aplicadas corretamente, permitem a realização de um esboço do lugar das raízes sem a necessidade de um computador. A seguir são apresentados dois exercícios que demonstram como podemos desenhar o lugar e analisar o mesmo, extraindo informações do sistema de controle.

	**Exercício 11**: Esboço completo do lugar das raízes:
	
	(em breve)
	
	