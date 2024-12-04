=============
Realimentação
=============	

Problemas de controle
=====================

O controle de sistema abrange diversos tipos de problemas, os quais apresentam características distintas. Dentre os principais tipos de problemas de controle controle, existem dois objetivos que são mais comuns: o **controle regulatório** e **controle servo**. A seguir, serão apresentadas as principais características desses dois tipos de objetivos de controle.

Controle Regulatório
--------------------
  
O controle regulatório consiste em **manter uma variável de processo em um valor constante, mesmo na presença de perturbações externas**. O objetivo do controlador neste cenário é manter a estabilidade do sistema e rejeitar as perturbações, sendo utilizado em sistemas onde o principal objetivo é manter a operação do mesmo em volta de condições fixas.

	**Exemplo 1: Controle regulatório de nível**
	
	
Controle Servo  
--------------

O controle servo, por sua vez, consiste em **seguir um valor de referência variável no tempo (trajetória ou referências dinâmicas)**. Este problema de controle é focado no rastreamento de referências, sendo o objetivo garantir que o sistema responda de maneira rápida às mudanças na referência e atinja os valores de referência sem erro em regime permanente.

	**Exemplo 2: Controle servo de um manipulador robótico**

Realimentação
=============

A realimentação (proveniente do termo em inglês "feedback") é um dos princípio fundamentais em sistemas de controle, sendo amplamente utilizado para alcançar os principais objetivos do sistema de controle, garantir que uma variável controlada atinja e mantenha um valor desejado (referência). Em sistemas de controle realimentado, onde desejamos controlar o sistema representado pela função de transferência :math:`G(s)`, a saída do sistema, :math:`Y(s)`, é medida e comparada com a referência, :math:`R(s)`, produzindo um sinal de erro, :math:`E(s)`. Esse sinal de erro é alimentado como entrada no controlador, representado por :math:`C(s)`, o qual será responsável por produzir o sinal de controle, :math:`U(s)`, capaz de corrigir desvios na saída medida, compensando perturbações, representadas por :math:`P(s)`.

Um sistema realimentado apresenta a estrutura básica apresentada no diagrma a seguir.

.. figure:: /figures/Realimentacao/Real.png
	:figwidth: 70%
	:align: center

Nesse sistema de controle :math:`C(s)` deve ser projetado, de forma garantir que o sistema de controle - como um todo - apresente o comportamento dinâmico desejado. De forma geral, o que é desejado é que o controlador apresente alguma/todas as seguintes características:

- Estabilidade;
- Erro nulo em regime permanente para determinada entrada;
- Comportamento dinâmico (tempo de acomodação, sobressinal, ...) conforme especificação.

Tanto a garantia da estabilidade, quanto do erro nulo em regime permanente, podem ser alcançadas verificando algumas condições básicas no sistema realimentado. Por sua vez, alcançar um comportamento dinâmico conforme determinada especificação requer um projeto cauteloso do controlador. Dessa forma, o caminho que é seguido, no projeto do controlador, consiste em compreender as condições para que tenhamos garantia de estabilidade e erro nulo em regime permanente para determinada entrada, conhecimento que é usado durante o projeto visando alcançar o comportamento dinâmico desejado. Dessa forma, a estabilidade e a garantia de erro nulo são "restrições" usada no projeto, o qual tem foco no comportamento dinâmico do controlador. A seguir, vamos analisar quais são as condições para que tenhamos uma malha de controle realimentado estável e que garanta erro nulo em regime permanente para diferentes entradas.


Estabilidade
============


Método de Routh-Hurwitz
-----------------------



Erro nulo em regime permanente
==============================

Nesta seção vamos analisar o problema da garantia de erro nulo em regime permanente para diferentes entradas. Para introduzir esse problema, iniciaremos com um exemplo.

	**Exemplo 1:** Para compreendermos o que é o erro em regime permanente, vamos analisar a resposta do sistema de controle apresentado a seguir. 

	.. figure:: /figures/Realimentacao/ErroNuloExemplo.png
		:figwidth: 70%
		:align: center
		
	Nesta malha de controle, podemos projetar o controlador :math:`C(s)` buscando atingir algum tipo de objetivo. Caso escolhamos o controlador :math:`C(s)=5`, teremos a função de transferência em malha fechada :math:`G_{mf}=\frac{10}{s^2+8s+12}`. Dessa forma, os polos do sistema em malha fechada são :math:`s=-2` e :math:`s=-6`, sendo a resposta do sistema, para um degrau unitário :math:`r(t)=u(t)`(o qual apresenta transformada :math:`r(s)=\frac{1}{s}'), definida como segue.

	.. math:: 
		G_{mf}=\frac{Y(s)}{R(s)}=\frac{10}{(s+2)(s+6)} \\
		Y(s)=\frac{10}{(s+2)(s+6)}R(s) \\
		Y(s)=\frac{10}{(s+2)(s+6)s} \\
		Y(s)=\frac{-5}{4}\frac{1}{(s+2)}+\frac{5}{12}\frac{1}{(s+6)}+\frac{5}{6}\frac{1}{s} \\
		y(t)=\frac{-5}{4}e^{-2t}u(t)+\frac{5}{12}e^{-6t}u(t)+\frac{5}{6}u(t)
		
	A resposta desse sistema de controle, para uma entrada do tipo degrau unitário, é a soma de duas exponenciais decrescentes e um degrau unitário. A medida que o tempo tende a infinito, os termos exponenciais se aproximam de :math:`0`, com o termo :math:`\frac{5}{6}u(t)` restando. Portanto, o sinal de referência é um degrau unitário, :math:`r(t)=u(t)`, porém, a resposta do sistema converge para :math:`y(t)=\frac{5}{6}u(t)` quanto o tempo tende a infinito. É evidente que, em regime permanente - quando o tempo converge para infinito - o sistema apresenta erro não nulo. Se definirmos o erro de seguimento de referência como :math:`e(t)=r(t)-y(t)`, vemos que, em regime permanente, o erro tende a :math:`e(t)=\frac{1}{6}u(t)`. Esse resultado é apresentado na figura a seguir.

	.. figure:: /figures/Realimentacao/ErroNuloExemplo2.png
		:figwidth: 70%
		:align: center
	
Como visto no exemplo, podemos verificar qual o erro em regime permanente ao analisarmos a resposta do sistema considerando o valor de referência desejado, e compararmos com com tal referência, o que resultado no sinal de erro. Ao verificarmos qual o valor desse erro a medida que o tempo tende ao infinito - que representa o regime permanente - temos uma estimativa do erro em regime peramenente. Realizar toda essa análise é trabalhosa e ela é apenas válida para a referência de entrada que foi testada. Por isso, será apresentada uma forma de análise sistemática do erro em regime permanente, a qual traz um resultado prático que subsidiará o projeto de controladores que garantam erro nulo para diferentes tipos de referências.

Análise do erro
---------------

Quando temos um sistema de controle realimentado típíco, como o apresentado na figura a seguir, podemos encontrar funções de transferência que relacionam diferentes sinais. A função de transferência que relaciona a saída em malha fechada é a mais típica, sendo representada por :math:`G_{mf}=\frac{Y(s)}{R(s)}=\frac{C(s)G(s)}{1+C(s)G(s)}`.

.. figure:: /figures/Realimentacao/Real.png
		:figwidth: 50%
		:align: center
		
Como desejamos analisar o erro em função do sinal de referência, podemos obter a função de transferência que relaciona tais sinais. Partindo do sinal de erro, podemos obter essa função de transferência como segue.

.. math::
	E(s)=R(s)-Y(s) \\
	Y(s)=G(s)C(s)E(s) \\
	E(s)=R(s)-G(s)C(s)E(s) \\
	[1+G(s)C(s)]E(s)=R(s) \\
	\frac{E(s)}{R(s)}=\frac{1}{[1+G(s)C(s)]}
	
A partir dessa função de transferência, podemos obter o valor do erro para qualquer entrada :math:`R(s)`, substituindo o sinal de referência na equação a seguir.

.. math::
	E(s)=\frac{1}{[1+G(s)C(s)]}R(s)
	
Para obtermos o valor em regime permanente de :math:`E(s)`, podemos expandir a equação usando frações parciais e obtermos a transformada inversa. Porém, existe uma forma mais fácil para obtermos o valor do erro em regime permanente, que é utilizando o teorema do valor final. 

.. admonition:: Teorema do valor final
	
	Para um sinal no domínio da transformada de Laplace, podemos obter qual será o valor dele, no domínio do tempo, para o tempo tendendo a infinito, com a seguinte equação.

	.. math::
		\lim_{t\to \infty}x(t)=\lim_{s\to 0}X(s)s
		
Se aplicarmos o teorema do valor final para o sinal de erro, podemos obter o valor do erro em regime permanente - equivalente ao :math:`\lim_{t\to \infty}e(t)`.

.. math::
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}E(s)s=\lim_{s\to 0}\frac{1}{1+G(s)C(s)}R(s)s \\

Essa é uma expressão genérica, que pode ser utilizada para obter o erro em regime permanente para qualquer sinal de referência.

	**Exemplo 2:** Retornamos para o problema analisado no **Exemplo 1**, no qual foi obtido o erro em regime permanente de uma malha de controle para uma referência do tipo degrau. A análise feita naquele exemplo será repetido, porém, utilizando a expressão do erro em regime permanente que foi derivada nesta seção.
	
	Para obtermos o erro em regime permanente, devemos substituir as funções de transferência que definem a malha de controle na equação a seguir.
	
	.. math::
		\lim_{t\to \infty}e(t)=\lim_{s\to 0}E(s)s=\lim_{s\to 0}\frac{1}{1+G(s)C(s)}R(s)s \\
		\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{1+\frac{10}{s^2+8s+2}}R(s)s \\
		\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{s^2+8s+2}{s^2+8s+12}R(s)s
		
	A equação obtida determina o erro para qualquer sinal de referência. Como queremos determinar o erro para referências do tipo degrau, devemos substituir :math:`R(s)=\frac{1}{s}`, obtendo a equação a seguir.
	
	.. math::
		\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{s^2+8s+2}{s^2+8s+12}\frac{1}{s}s \\
		\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{s^2+8s+2}{s^2+8s+12} \\
		\lim_{t\to \infty}e(t)=\frac{2}{12}=\frac{1}{6} \\
	
Condições para erro nulo
------------------------

Na seção anterior foi obtida a expressão matemática para o erro em regime permanente. Utilizando essa equação, podemos determinar condições para alcançarmos erro nulo em regime permanente para as referências típicas, que são o degrau unitário e a rampa unitária. Para o degrau unitário, temos :math:`G(s)=\frac{1}{s}`, fazendo com que a expressão do erro em regime permanente seja a seguinte.

.. math::
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}R(s)s \\
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}\frac{1}{s}s \\
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}
	
Para garantirmos erro nulo, é necessário termos :math:`\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}=0`. Se definirmos :math:`G(s)=\frac{\text{Num}(G)}{\text{Den(G)}}`, e :math:`C(s)=\frac{\text{Num}(C)}{\text{Den(C)}}`, podemos escrever a condição como :math:`\lim_{s\to 0}\frac{Den(G)Den(C)}{[Den(G)Den(C)+Num(G)Num(C)]}=0`. Tanto :math:`G(s)`, quanto :math:`C(s)` apresentam numerador e denominador formados por polinômios, cuja estrutura consiste na multiplicação de termos :math:`(s+a)`, onde :math:`a` representa uma grandeza complexa. 

A única configuração em que :math:`\lim_{s\to 0}\frac{Den(G)Den(C)}{[Den(G)Den(C)+Num(G)Num(C)]}=0` consiste em um sistema realimentado no qual :math:`Den(G)Den(C)` apresentam ao menos um termo :math:`s`. Isso é equivalente a termos um integrador no processo, :math:`G(s)`, ou no controlador, :math:`C(s)`, já que o integrador é definido como :math:`\frac{1}{s}`.

.. admonition:: Condição para erro nulo em regime permanente para referência do tipo degrau
	
	Para garantirmos erro nulo em regime permanente, para referência do tipo degrau, :math:`r(t)=u(t)`, é necessário existir um integrador, :math:`\frac{1}{s}`, ou no processo, :math:`G(s)`, ou no controlador, :math:`C(s)`. 

Caso desejamos que o sistema apresente erro nulo para uma referência do tipo rampa, definida como :math:`r(t)=tu(t)`, temos o sinal de referência :math:`R(s)=\frac{1}{s^2}`. Se substituirmos na equação que define o erro em regime permanente, temos a seguinte equação.

.. math::
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}\frac{1}{s^2}s \\
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{1}{[1+G(s)C(s)]}\frac{1}{s} \\
	\lim_{t\to \infty}e(t)=\lim_{s\to 0}\frac{Den(G)Den(C)}{[Den(G)Den(C)+Num(G)Num(C)]s}
	
Dessa forma, para termos erro nulo, é necessário :math:`\lim_{s\to 0}\frac{Den(G)Den(C)}{[Den(G)Den(C)+Num(G)Num(C)]s}=0`, o que só é alcançado se houver ao menos o termo :math:`\frac{1}{s^2}` em :math:`\frac{Den(G)Den(C)}`. Isso é equivalente a termos um duplo integrador, ou considerando o processo, :math:`G(s)`, e o controlador, :math:`C(s)`. Essa condição é alcançada, ou tendo um duplo integrador em uma das funções de transferência, ou havendo um integrador simples em ambas funções de transferência.

.. admonition:: Condição para erro nulo em regime permanente para referência do tipo rampa
	
	Para garantirmos erro nulo em regime permanente, para referência do tipo rampa, :math:`r(t)=tu(t)`, é necessário existir um duplo integrador, :math:`\frac{1}{s^2}`, considerando o processo, :math:`G(s)`, e o controlador, :math:`C(s)`. 
	
Note que, para uma referência do tipo degrau, é necessário que exista internamente, ao controlador ou processo, uma cópia do degrau. O mesmo ocorre para um sinal de referência do tipo rampa. Esse resultado é conhecido como **Princípio do Modelo Interno**, o qual define que, para que o erro do sistema de controle, :math:`E(s)`, decorrente da excitação de sinal de referência, :math:`R(s)`, possa ser eliminado, a função de transferência do sinal de referência, :math:`R(s)`, deve estar presente na função transferência em malha aberta :math:`G(s)C(s)`.