=====================
Lista de Exercícios 1
=====================	

Modelagem de Sistemas e Função de Transferência
===============================================

-----------
Exercício 1
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
	
-----------
Exercício 2
-----------

Para o circuito apresentado na figura a seguir, encontre a função de transferência considerando como entrada a tensão na fonte (:math:`V_f(t)`) e como saída:

a) :math:`V_c`

b) :math:`i_r`

.. figure:: /figures/Lista1/exCir.png
	:figwidth: 40%
	:align: center

Sistemas de 1ª e 2ª Ordem
=========================

-----------
Exercício 1
-----------

Esboce a resposta ao degrau para os seguintes sistemas:

a) :math:`G(s)=\frac{4}{s+4}`.
    
b) :math:`G(s)=\frac{11}{s^2+11s+10}`.
   
c) :math:`G(s)=\frac{1}{s^2+2s}`.

Solução:
--------

.. container:: toggle, toggle-hidden

	a) :math:`y(t)=(1-e^{-4t})u(t)`.

	b) :math:`y(t)=(1,1-1,22e^{-t}+0,12e^{-10t})u(t)`.
	
-----------	
Exercício 2
-----------

Para os seguinte gráficos, estime a função de transferência:

a)

.. figure:: /figures/Lista1/exRe.png
	:figwidth: 80%
	:align: center

b) 

.. figure:: /figures/Lista1/exRe2.png
	:figwidth: 80%
	:align: center
	
Solução:
--------

.. container:: toggle, toggle-hidden
	
	a) :math:`G(s)=\frac{1}{0,95s+1}`.
    
	b) :math:`G(s)=\frac{2}{0,25s+1}`.

-----------	
Exercício 3
-----------

Suponha que você esteja cansado da engenharia e deseje trabalhar com algo artesanal. Após ver alguns vídeos na internet, você se interessa pela produção de produtos com vidro soprado e inicia essa jornada. Você adquire um forno com ajuste manual para a produção do vidro e se adapta bem ao seu funcionamento. Porém, para acelerar sua produção, você se recorda da disciplina de Sistemas de Controle, e decide usar seus conhecimentos para desenvolver um controle automático para o forno de produção de vidro. A primeira etapa que você realiza é um ensaio com o forno em funcionamento, para estimar um modelo dinâmico para o mesmo. Nesse ensaio, você aguarda a temperatura estabilizar em um valor próximo ao que você sempre utiliza o forno, e após isso, você aumenta em 5\% a potência do forno. Após o aumento, você anota os valores de temperatura em intervalos constantes de tempo. A partir dos valores obtidos nesse ensaio, apresentados na tabela a seguir, determine qual é o modelo que representa o comportamento dinâmico do forno.

.. admonition:: Tabela: Valores de temperatura coletados em cada instante de tempo.

	+-----------+-----------------+
	| Tempo (s) | Temperatura (C) |
	+===========+=================+
	| 0         | 1420            |
	+-----------+-----------------+
	| 15        | 1434            |
	+-----------+-----------------+
	| 30        | 1445            |
	+-----------+-----------------+
	| 45        | 1451            |
	+-----------+-----------------+
	| 60        | 1450            |
	+-----------+-----------------+
	| 75        | 1456            |
	+-----------+-----------------+
	| 90        | 1458            |
	+-----------+-----------------+
	| 105       | 1458            |
	+-----------+-----------------+
	| 120       | 1459            |
	+-----------+-----------------+
	| 135       | 1459            |
	+-----------+-----------------+
	| 150       | 1460            |
	+-----------+-----------------+

Solução:
--------

.. container:: toggle, toggle-hidden

	:math:`G(s)=\frac{800}{30s+1}+1420`

-----------	
Exercício 4
-----------

Considerando o modelo obtido para o forno de produção de vidro, obtido no exercício da seção sobre sistemas de 1ª e 2ª ordem, obtenha a função de transferência em malha fechada que aceleraria o processo em 5\% e garantiria um sobressinal máximo de 3\%.

-----------	
Exercício 5
-----------

Você foi contratado por uma empresa de produção de aves e recebeu a tarefa de desenvolver o sistema para chocar ovos automaticamente. O processo para chocar um ovo requer o controle preciso da temperatura do ovo em um valor de :math:`37,7\text{ }^oC`. Para desenvolver o controle de temperatura dessa chocadeira, seu líder técnico lhe especifica que o equipamento deve alcançar a temperatura de operação em menos de 1 minuto e não deve passar de :math:`38,0\text{ }^oC`, para evitar que o ovo atinja uma temperatura que represente um risco e resulte na perda do ovo. Com base nessa especificação, qual será a função de transferência de segunda ordem desejada para o sistema em malha fechada?


-----------	
Exercício 6
-----------

Sistemas de alta ordem podem ser, em muitos casos, aproximados por sistemas de ordem inferior. Baseado nisso, esboce a resposta ao degrau para o sistema cuja função de transferência é representada por:

.. math::
	G(s)=\frac{1800}{(s+3)(s+20)(s+30)(s+35)}

Solução:
--------

.. container:: toggle, toggle-hidden

	Polos em :math:`s=0,06+j0,041` e :math:`s=0,06-j0,041`. :math:`G(s)=\frac{0,073^2}{s^2+2*0,82*0,073+0,073^2}`.
    

	

Realimentação e Diagrama de Blocos
==================================

Encontre a função de transferência em malha fechada para os seguintes sistemas:

-----------	
Exercício 1
-----------

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
Exercício 2
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
	
	
	
Estabilidade em Malha Aberta e em Malha Fechada
===============================================

-----------
Exercício 1
-----------

Avalie a estabilidade em malha aberta para os sistemas dinâmicos a seguir e esboce a posição dos polos do sistema no plano complexo.

a) :math:`G(s)=\frac{s-1}{(s^2+12s+36)}`
    
b) :math:`G(s)=\frac{7}{(s^2+9)}`

c) :math:`G(s)=\frac{s^2+4}{(s^2+4s-12)}`

d) :math:`G(s)=\frac{1}{(s^3+8s^2+12s)}`

Solução:
--------

.. container:: toggle, toggle-hidden

	a) Polos em -6 e -6. Estável.

	b) Polos em :math:`+j3` e :math:`-j3`. Marginalmente estável.

	c) Polos em -6 e 2. Instável.
		
	d) Polos em 0 e -2 e -6. Marginalmente estável.

-----------
Exercício 2
-----------
    
Para o sistema de controle realimentado a seguir, determine se o processo é estável em malha aberta e se é garantida estabilidade em malha fechada considerando:
    
.. figure:: /figures/Lista1/exES.png
	:figwidth: 60%
	:align: center

a) :math:`C=10`

b) :math:`C=\frac{5}{(s+5)}`

c) :math:`C=\frac{2(s+2)}{(s+3)}`

Solução:
--------

.. container:: toggle, toggle-hidden

	Sistema é instável em malha aberta.

	a) Polo em -9. Estável.
    
    b) Polos em 0 e -4. Marginalmente estável.

    c) Polos em :math:`-2+\sqrt{2}/2$ e $-2-\sqrt{2}/2`. Estável.


-----------
Exercício 3
-----------

Utilizando o critério de Routh-Hurwitz, avalie para quais valores de :math:`k` o sistema a seguir é estável.

.. figure:: /figures/Lista1/exRH.png
	:figwidth: 60%
	:align: center   
	
Solução:
--------

.. container:: toggle, toggle-hidden

	O sistema é estável para :math:`k<13`.


Erro Nulo em Regime Permanente
==============================

-----------
Exercício 1
-----------

Verifique se os sistemas de controle apresentado a seguir apresentam erro nulo em regime permanente para uma referência do tipo degrau. Caso não apresentem erro nulo, encontre o valor do erro para um degrau :math:`u(t)=2`.

a) 

.. figure:: /figures/Lista1/exErro0.png
	:figwidth: 60%
	:align: center 
	
b) 

.. figure:: /figures/Lista1/exErro3.png
	:figwidth: 60%
	:align: center 
    
c) 

.. figure:: /figures/Lista1/exErro2.png
	:figwidth: 60%
	:align: center 
	
d) 
  
.. figure:: /figures/Lista1/exErro1.png
	:figwidth: 60%
	:align: center   

Solução:
--------

.. container:: toggle, toggle-hidden

	a) Erro em regime permanente é :math:`\frac{1}{3}`.
	
	b) Erro em regime permanente é 0.
	
	c) Erro em regime permanente tende ao infinito.
	
	d) Erro em regime permanente é 0.
 
-----------
Exercício 2
-----------

Repita a questão anterior, porém considerando que a referência aplicada é uma rampa unitária, :math:`r(t)=tu(t)`, a qual é representada no domínio da transformada de Laplace por :math:`R(s)=\frac{1}{s^2}`.

Solução:
--------

.. container:: toggle, toggle-hidden
   
    a) Erro em regime permanente tende ao infinito.

    b) Erro em regime permanente igual a :math:`\frac{2}{15}`.

    c) Erro em regime permanente tende ao infinito.

    d) Erro em regime permanente igual a :math:`\frac{6}{5}`.
	
	
Controle PID
============

-----------
Exercício 1
-----------

Projete um controlador PI utilizando o método do ganho limite de Ziegler-Nichols para o sistema :math:`G(s)=\frac{1}{s^3+7s^2+10s}`. Para o controlador projetado, obtenha a função de transferência :math:`C(s)` e desenhe o diagrama de blocos do sistema de controle.

Solução:
--------

.. container:: toggle, toggle-hidden

    :math:`K_{cr}=70`, :math:`\omega=\sqrt{10}` e :math:`C(s)=\frac{31,5s(s+0,32)}{s}`.
    

-----------
Exercício 2
-----------

Ao iniciar o trabalho em uma indústria, você recebe como tarefa a melhoria do funcionamento de um sistema de controle definido pela função de transferência :math:`G(s)=\frac{1}{s^2+8s}`. Avaliando o funcionamento atual do sistema, você identifica que está sendo usando um controlador do tipo PI, implementado na forma paralela, com :math:`K_c=5` e :math:`K_1=1`. Para avaliar o funcionamento desse sistema de controle:

a) Discuta se a escolha de um controlador PI foi correta, para o tipo de sistema;

b) Obtenha a função de transferência :math:`C(s)` do controlador;

c) Desenhe o diagrama de blocos do sistema de controle;
    
d) Obtenha a faixa de valores de :math:`K_p` que garantem que o sistema é estável.
       
    
Solução:
--------

.. container:: toggle, toggle-hidden

	a) Não é a escolha correta. O sistema apresenta um integrador, sendo então do tipo 1. Dessa forma, não é necessário utilizar a parcela integradora, pois o sistema já é integrador e naturalmente apresentará erro nulo em regime permanente para entradas do tipo degrau. O uso da parcela integradora apenas tornará a resposta do sistema mais lenta.

    b) :math:`C(s)=\frac{5s+1}{s}`
    
    d) O sistema é estável para qualquer valor de :math:`K_p>\frac{1}{8}`.
    
-----------
Exercício 3
-----------

Projete um sistema de controle PID para o processo apresentado na figura a seguir, por meio do método da curva de reação de Ziegler-Nichols.

.. figure:: /figures/Lista1/exercicio.png
	:figwidth: 80%
	:align: center 


Solução:
--------

.. container:: toggle, toggle-hidden

	:math:`K=1`, :math:`L\approx 0,2` e :math:`T \approx 2,1`. Com isso, obtemos um PID na forma ideal com :math:`K_p-12,6`, :math:`T_i=0,4` e :math:`T_d=0,1` pela inspeção da tabela.

Discretização de Controladores
==============================

-----------
Exercício 1
-----------

Obtenha a função de transferência em tempo discreto e a equação diferenças para o controlador projetado no Exercício 1 da seção Controle PID. Escolha um período de amostragem adequado e utilize o método explícito de Euler e o método Trapezoidal.
	
Exercícios do Livro
===================

Lista de exercícios selecionados (Seção de Problemas) do livro "NISE, Norman S. Engenharia de sistemas de controle. 7. ed. Rio de Janeiro: LTC, 2017. 772 p. ISBN 978-8521634355".

1.1.

1.2.

1.4.

2.8.

2.12.

2.55.

2.66.

4.2

4.15.

4.20.

4.29.

4.31.

4.32.

4.69.

5.2. 

5.11.

5.14.

6.1.

6.3.

6.9.

6.12.

6.43.

7.1.

7.10.

7.20.

