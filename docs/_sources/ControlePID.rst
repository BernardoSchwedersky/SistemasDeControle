============
Controle PID
============	

O controlador PID (Proporcional-Integral-Derivativo) é o algoritmo de controle mais utilizado na indústria, devido à vários aspectos. O principal motivo de sua ampla utilização é sua simplicidade, a qual faz com que seja mais fácil a compreensão do funcionamento do controlador e o seu ajuste. Ele combina três ações de controle distintas: a ação proporcional, a ação integral e a ação derivativa, cada uma com um papel específico no comportamento da resposta em malha fechada do sistema.

Neste capítulo serão apresentadas as principais características do controlador PID, bem como, alguns métodos para sintonia de seus parâmetros. Na seção a seguir será apresentada a formulação convencional do controlador PID, considerando a configuração paralela, e também as configurações alternativas. Em seguinda, serão abordados aspectos da implementação prática do PID, como os problemas que afetam a ação derivativa e o windup do integrador. Por fim, serão apresentados alguns métodos para sintonia do controlador PID.

Ações do Controlador PID
========================

O controlador PID é uma arquitetura de controlador geral e modular, caracterizada pela presença de três parcelas distintas, as quais podem ser ajustadas individualmente. O impacto de cada parcela do controlador PID no comportamento do sistema de controle pode ser interpretado individualmente, o que facilita a compreensão do funcionamento do PID e facilita o ajuste do mesmo.

Em um controlador PID, o sinal de controle é obtido pela soma do efeito de três parcelas -- proporcional, integral e derivativa. À cada uma dessas parcelas é associado um parâmetro de ajuste, com o qual, é possível sintonizar a importância de cada parcela no comportamento geral do controlador. Um diagrama de blocos ilustrando a estrutura geral do controlador PID é apresentado a seguir. 

.. figure:: /figures/ControlePID/blocosEstrutura.png
	:figwidth: 50%
	:align: center	
	
Ação Proporcional
-----------------

A ação proporcional gera um sinal de controle proporcional à magnitude do erro. Quanto maior o erro, maior a ação corretiva aplicada. Essa ação pode ser representada pela equação

.. math::
	u_P(t) = K_p e(t),

onde :math:`K_p` é o ganho proporcional.

Ao aumentarmos a ação integral, o controlador apresenta uma resposta mais agressiva. Quando aplicado à um sistema não integrador (Tipo 0), o aumento da ação integral resultará em uma redução do erro em regime permanente (apesar de ser incapaz de eliminá-lo), e sintonias muito agressivas resultarão em oscilações. 

Ação Integral
-------------

A ação integral soma os erros passados e ajusta o controle para garantir que o erro médio seja zero.  

.. math::
	u_I(t) = K_i \int e(t) dt


ou, no domínio de Laplace:

.. math::
	U_I(s) = \frac{K_i}{s} E(s)

onde :math:`K_i` é o ganho integral.


Ação Derivativa
---------------

A ação derivativa reage à taxa de variação do erro, ajudando a reduzir oscilações e melhorar a estabilidade.  

.. math::
	u_D(t) = K_d \frac{d e(t)}{dt}

ou, no domínio da Transformada de Laplace:

.. math::
	U_D(s) = K_d s E(s)

onde :math:`K_d` é o ganho do derivativo.


Formulação do PID
=================

Cada ação do controlador utiliza como sinal de entrada o erro entre o valor de referência e a saída do processo, :math:`e(t)=r(t)-y(t)`, retornando em sua saída uma parcela do sinal de controle. Ao somarmos as parcelas do sinal de controle produzidas por cada parcelas do PID, teremos o sinal de controle a ser aplicado no processo. É importante notar que, por serem parcelas individuais, podemos definir versões simplificadas do PID, nas quais uma ou mais parcelas não estão presentes. Por exemplo, se não utilizarmos a parcela derivativa, nós obteremos o controlador PI (Proporcional-Integral).

O controlador PID (Proporcional, Integral e Derivativo) pode ser formulado de diferentes maneiras dependendo da aplicação e da forma matemática utilizada. As três formulações principais são: **paralelo, ideal e série**.  

PID Paralelo (Padrão ou Clássico)
---------------------------------

A formulação paralela expressa o PID como a soma das três ações de controle separadas:

.. math::
	u(t) = K_p e(t) + K_i \int e(t) dt + K_d \frac{d e(t)}{dt}

Se obtermos a Transformada de Laplace, podemos representar o PID paralelo pela equação

.. math::
	U(s) = K_p E(s) + K_i \frac{E(s)}{s} + K_d s E(s) \\
	C(s) = \frac{U(s)}{E(s)} = K_p + \frac{K_i}{s} + K_d s

Essa formulação permite ajustes independentes dos ganhos proporcional :math:`K_p`, integral :math:`K_i` e derivativo :math:`K_d`, sendo a mais comum para implementação digital.

PID Ideal
---------

A formulação ideal é uma variação da paralela, onde as três ações do PID são multiplicados por :math:`K_p`. Dessa forma, o parâmetro :math:`K_p` não altera apenas a parcela proporcional, e sim as três parcelas. A formulação do PID ideal é

.. math::
	u(t) = K_p \left( e(t) + \frac{1}{T_i} \int e(t) dt + T_d \frac{d e(t)}{dt} \right)


Ao obtermos a Transformada de Laplace, podemos representar o PID ideal como

.. math::
	C(s) = K_p \left( 1 + \frac{1}{T_i s} + T_d s \right)

Nesta formulação temos os parâmetros tempos de integração e derivação, :math:`T_i` e :math:`T_d`, ao invés dos ganhos, fazendo com que a intepretação do efeito de tal ajuste seja diferente do PID paralelo. Por exemplo, o PID ideal

---

PID Série (ou Interativo)
-------------------------

Na formulação em série, o controlador PID é visto como o produto de três termos individuais, refletindo um efeito encadeado das ações:

.. math::
	C(s) = K_p \left( 1 + \frac{1}{T_i s} \right) \left( 1 + T_d s \right)

Aplicando a Transformada de Laplace, podemos representar o controlador PID série pela equação

.. math::
	C(s) = K_p \left( 1 + \frac{1}{T_i s} + T_d s + \frac{T_d}{T_i} \right)

Apesar de ter uma interpretação mais complicada, devido ao acoplamento entre o efeito das três ações, essa formulação é bastante usada em controladores comerciais.


Aspectos da Implementação Prática
=================================

(Em breve)

Problemas no Derivativo
-----------------------

(Em breve)

Problemas no Integrador
-----------------------

(Em breve)

Métodos de Sintonia
===================

Sintonia Analítica
------------------

A sintonia analítica de controladores pode ser realizada de diferentes formas. Dois métodos clássicos são o método baseado no Lugar das Raízes e o método baseado no Diagrama de Bode, os quais serão abordados em capítulos a seguir. Nesta seção nos concentraremos em formas simples de sintonia de controladores, com as quais o controlador resultante podem ser implementádo com a estrutura do PID. 

Partindo de uma malha de controle realimentado convencional, como a apresentada a seguir, podemos definir a função de transferência do sistema em malha fechada como

.. math::
	G_{mf}=\frac{C(s)G(s)}{1+C(s)G(s)}.

Se efeturmos uma manipulação algébrica, de forma a isolar :math:`C(s)`, podemos obter o que segue

.. math::
	[1+C(s)G(s)]G_{mf}=C(s)G(s) \\
	G_{mf}=C(s)[G(s)-G(s)G_{mf}] \\
	C(s)=\frac{1}{G(s)}\frac{G_{mf}(s)}{1-G{mf}(s)}.
	
Dessa forma, podemos determinar a função de transferência do controlador em função do processo, :math:`G(s)`, e da função de transferência em malha fechada do sistema, :math:`G_{mf}(s)`. Se escolhermos uma função de transferência desejada para o sistema de controle em malha fechada, :math:`G_d(s)`, podemos facilmente sintonizar um controlador ao assumirmos que :math:`G_{mf}=G_d`.

Note que o que está sendo feito nessa sintonia é o **cancelamento** da dinâmica do processo, já que o controlador contém, explícitamente, o inverso da função de transferência do processo. Apesar de parecer cômodo e fácil, o projeto de controladores considerando cancelamento (de polos, zeros, ou da dinâmica completa do processo) **não é recomendado**. A seguir são apresentados dois exemplos, um deles apresentando um caso em que a sintonia atinge o comportamento desejado, e um caso em que a o cancelamento resulta em uma malha de controle problemática.

	**Exemplo 1:** Projeto de PI considerando cancelamento de planta.
	
	Considere um processo de aquecimento de um tanque utilizando uma resistência elétrica. A dinâmica desse sistema pode ser representada, de forma simplificada, por um sistema de 1ª ordem na forma :math:`G(s)=\frac{2}{50s+1}`. Faremos o projeto de um controlador PI no qual a função de transferência desejada, em malha fechada, é :math:`G_d(s)=\frac{1}{75s+1}`.

	Projeto: para obter um controlador por cancelamento, basta substituirmos :math:`G_{mf}=G_d` em
	
	.. math::
		C(s)=\frac{1}{G(s)}\frac{G_{mf}(s)}{1-G{mf}(s)},
		
	o que resulta, para o problema em questão, na função de transferência
	
	.. math::
		C(s)=\frac{(50s+1)}{2}\frac{\frac{1}{(75s+1)}}{1-\frac{1}{75s+1}}=\frac{(50s+1)}{150s}.
		
	O controlador resultante apresenta um polo na origem e um zero em :math:`1/50`. Essa é a mesma estrutura de um controlador PI, o qual pode ser representado, na forma ideal, como
	
	.. math::
		C_{PI}=K_p\frac{(T_i s+1)}{T_i s}=\frac{50s+1}{150s}.
		
	Dessa forma, temos a sintonia :math:`T_i=50` e :math:`K_p=1/3`.

	**Exemplo 2:** Projeto de PI considerando cancelamento de planta instável. (**Note que esse é um exemplo dos problemas do cancelamento**)
	

	
	
	**Exemplo 3:** Projeto de PI analítico sem cancelamento.

	Considerando um sistema definido por :math:`G(s)=\frac{3}{s+10}`, iremos obter um controlador PI, na forma ideal, de forma a posicionar todos polos em malha fechada do sistema em :math:`(s+7)`.
	
	Solução: o processo, por ser um sistema de primeira ordem, apresenta apenas 1 polo, e o controlador PI, representado por :math:`C_{PI}=K_p\frac{(T_i s+1)}{T_i s}`, apresenta um polo na origem e um zero. Se obtivermos a função de transferência em malha fechada desse sistema de controle, teremos

	.. math::
		G_{mf}(s)=\frac{\frac{3K_p}{T_i}(T_i s+1)}{(s^2+(10+3K_p)s+\frac{3K_p}{T_i})}.
		
	Dessa forma, vemos que o sistema, em malha fechada, apresenta dois polos. A especificação é posicionarmos os polos em :math:`(s+7)`, então, a função de transferência desejada para o sistema deverá ter o seguinte formato
	
	.. math::
		G_d(s)=\frac{\dots}{(s+7)(s+7)}.

	Para sintonizarmos o PI, basta igualarmos os denominadores, obtendo
	
	.. math::
		(s^2+(10+3K_p)s+\frac{3K_p}{T_i})=(s^2+14s+49),

	o que resulta em :math:`K_p=4/3` e :math:`T_i=4/49`.

Sintonia Tabeladas
------------------

Exercícios Sugeridos
====================

-----------
Exercício 1
-----------

Se um sistema de controle PID for projetado utilizando a configuração paralela, e a implementação prática dele for realizada utilizando um controlador comercial, o qual implementa um controlador PID na configuração ideal, obtenha as equações que convertem os parâmetros :math:`K_p`, :math:`K_i` e :math:`K_d`, obtidos para um PID paralelo, nos parâmetros do PID ideal.  

Solução:
--------


	
	
-----------
Exercício 2
-----------

Projete um controlador PI utilizando o método do ganho limite de Ziegler-Nichols para o sistema :math:`G(s)=\frac{1}{s^3+7s^2+10s}`. Para o controlador projetado, obtenha a função de transferência :math:`C(s)` e desenhe o diagrama de blocos do sistema de controle.

Solução:
--------

.. container:: toggle, toggle-hidden

    :math:`K_{cr}=70`, :math:`\omega=\sqrt{10}` e :math:`C(s)=\frac{31,5s(s+0,32)}{s}`.
    

-----------
Exercício 3
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
Exercício 4
-----------

Projete um sistema de controle PID para o processo apresentado na figura a seguir, por meio do método da curva de reação de Ziegler-Nichols.

.. figure:: /figures/Lista1/exercicio.png
	:figwidth: 80%
	:align: center 


Solução:
--------

.. container:: toggle, toggle-hidden

	:math:`K=1`, :math:`L\approx 0,2` e :math:`T \approx 2,1`. Com isso, obtemos um PID na forma ideal com :math:`K_p-12,6`, :math:`T_i=0,4` e :math:`T_d=0,1` pela inspeção da tabela.
	
	
-----------
Exercício 5
-----------

Imagine que você deseja empreender na área da piscicultura, criando peixes ornamentais. Apesar de alguns peixes serem capazes de se adaptar à mudanças na temperatura do ambiente, muitos são sensíveis à temperaturas muito altas ou baixas. Para isso, você relembrou da disciplina de Sistemas de Controle e resolveu criar um sistema de controle da temperatura da água dos tanques onde são criados os peixes. Após adicionar um sistema de aquecimento por resistências elétricas e conectá-lo à um controlador PID industrial, você realizou um ensaio para estimar a função de transfêrencia do sistema e obteve o seguinte diagrama de blocos para o sistema de controle realimentado.

.. figure:: /figures/ControlePID/ExercicioPID.png
	:figwidth: 70%
	:align: center 

Para facilitar o processo, você perguntou à uma ferramenta de IA generativa (LLM) qual a forma mais fácil de projetar esse controlador PID, sendo que o objetivo é acelerar a resposta do processo. A ferramenta de IA generativa refletiu "profundamente" e sugeriu projetar o controlador realizando o cancelamento da função de transferência do processo e escolher como função de transferência em malha fechada desejada, uma função de transferência rápica, como por exemplo :math:`G_d(s)=\frac{1}{s+1}`. Levando em conta a sugestão da IA, obtenha:

a) A função de transferência do controlador, :math:`C(s)`, que faz :math:`G_{mf}=G_d`;

b) Os parâmetros de ajuste a serem inseridos no controlador PID industrial, caso ele esteja na configuração **Paralela**.

c) Obtenha as funções de transferência em malha fechada entre a referência e a saída, :math:`\frac{Y(s)}{R(s)}`, e entre a saída e a pertubação, :math:`\frac{Y(s)}{P(s)}`. Explique porquê a velocidade de resposta para uma pertubação é mais lenta que a resposta à um degrau de referência.

d) Discuta se o método sujerido pela IA é adequado e quais os possíveis problemas que podem ser encontrados sintonizando um processo dessa maneira;

-----------
Exercício 6
-----------

Você percebeu que a sugestão de método de sintonia fornecida pela IA generativa pode ser problemática em alguns casos, então resolveu refazer o projeto. Para isso, você estabeleceu como objetivo projetar um controlador PI definido pela função de transferência :math:`C(s)=\frac{K_p(T_i s+1)}{T_i s}`. Neste projeto, você estabeleceu que é desejado obter um sistema sem sobressinal, no qual, a resposta é definida por um par de polos em :math:`(s+0,005)`. Realize  projeto, obtendo o controlador que alcança tal especificação e mostre que o sistema em malha fechada apresenta o comportamento desejado.
