==============================
Respostas de Sistemas Lineares
==============================

Os sistemas dinâmicos lineares invariantes no tempo (LTI) desempenham um papel fundamental na compreensão e no controle de uma ampla gama de fenômenos físicos. A capacidade de descrever o comportamento de sistemas complexos por meio de modelos matemáticos lineares tem implicações significativas na análise e no projeto de sistemas de controle, permitindo a compreensão do funcionamento de determinado sistema e o projeto de malhas de controle capazes de atingir certos  requisitos de desempenho. 

A resposta de um sistema LTI, para uma entrada qualquer, pode ser obtida utilizando a função de transferência que rege o comportamento do processo. Assumindo que a função de transferência seja conhecida e representada por:

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
	
O parâmetro $k$ pode ser entendido como o ganho estático do processo, pois, se aplicarmos um degrau unitário como entrada, e usarmos o teorema do valor final, veremos que o valor da saída quando o tempo tende à infinito será $k$.

Por sua vez, o parâmetro $\tau$ representa a constante de tempo do sistema. Esse parâmetro está diretamente ligado ao tempo no qual o sistema demora para atingir o valor final, com valores maiores de $\tau$ representando sistemas com dinâmicas mais lentas.

A resposta ao degrau unitário no domínio do tempo é obtida usando a equação a seguir:

.. math::
	:name: eq:1
	
	y(t)=k(1-e^{-\frac{1}{\tau}t})u(t)

Nos diagramas a seguir são apresentados de forma interativa o formato geral da resposta de sistemas de primeira ordem, e o efeito da mudança de $k$ e $\tau$ na mesma (Arraste a barra para selecionar o valor de $k$ e $\tau$).

.. admonition:: Efeito da mudança no parâmetro $\tau$

	.. raw:: html
		:file: charts/sis1ordemtau.html


.. admonition:: Efeito da mudança no parâmetro $k$

	.. raw:: html
		:file: charts/sis1ordemk.html
		
   
O parâmetro $\tau$ apresenta uma relação direta com o tempo em que o sistema demora para atingir o valor final (em regime permanente). Analisando a equação que define a resposta ao degrau no domínio do tempo, vemos que o sistema demora $\tau$ segundos para atingir $63,21 \%$ do valor final de sua resposta. Essa relação entre $\tau$ e instantes de tempo da resposta de sistemas de primeira ordem é destacada na tabela a seguir. 

.. admonition:: Relação entre $\tau$ e instantes de tempo da resposta de sistemas de primeira ordem

	+----------+------------+
	| Tempo    | $y(t)/k$   |
	+==========+============+
	| $\tau$   | 0,6321     |
	+----------+------------+
	| $2\tau$  | 0,8647     |
	+----------+------------+
	| $3\tau$  | 0,9502     |
	+----------+------------+
	| $4\tau$  | 0,9817     |
	+----------+------------+
	| $5\tau$  | 0,9933     |
	+----------+------------+
   
Sistemas de Segunda Ordem
=========================

Sistemas de segunda ordem são caracterizados pela equação diferencial genérica 

.. math::
	\frac{d^2 y}{dt^2}+2\xi \omega_n \frac{dy}{dt} + \omega_n^2 y(t)=kx(t).

Se aplicarmos a transformada de Laplace e reorganizarmos no formato de uma função de transferência, obteremos a função de transferência de segunda ordem genérica, definida como

.. math::
	G(s)=\frac{k\omega_n^2}{s^2+\xi \omega_n s+\omega_n^2}=\frac{k\omega_n^2}{(s-p_1)(s-p_2)}.

De forma semelhante ao caso de primeira ordem, essa função de transferência é estruturada de forma que o parâmetro $k$ represente o ganho estático do sistema, o que pode ser verificado ao aplicarmos o teorema do valor final. O parâmetro $\xi$ é denominado fator de amortecimento e o parâmetro $\omega_n$ é denomindado como frequência natural. O impacto desses parâmetros na resposta, e a intuição por trás dos mesmos, será discutido a seguir.

A principal característica de um sistema de segunda ordem consiste na existência de 2 polos. A posição dos polos pode ser determinada facilmente, sendo

.. math::
	p_1=-\xi\omega_n + j\omega_n \sqrt{\xi^2-1},
	
	p_2=-\xi\omega_n - j\omega_n \sqrt{\xi^2-1}.

Fica evidente que a natureza da posição dos polos depende do argumento dentro da raiz quadrada, $\xi^2-1$. Esse argumento é positivo quando $\xi>1$, o que faz com que os polos sejam reais e distintos. Caso o argumento seja igual a 0 (\xi=1), os polos serão reais e iguais. Por fim, se o argumento for negativo ($\xi<1$), os polos terão uma parte imaginária, sendo então um par complexo conjugado. Para cada um desses 3 casos, a resposta ao degrau assumirá uma forma diferente. Iremos então, analisar cada um desses casos individualmente.

Caso Superamortecido ($\xi>1$) e Criticamente Amortecido ($\xi=1$)
------------------------------------------------------------------

Quando temos $\xi>1$, a resposta do sistema é superamortecida. O termo superamortecido vêm do fato de que a resposta ao degrau para esse sistema não apresenta componentes oscilatórias. De fato, a resposta ao degrau é representada, no domínio do tempo, pela expressão

.. math::
	y(t)=k[c_1+c_2e^{p_1 t}+c_3e^{p_2 t}]u(t).

Devido à resposta ser formada pela soma de duas componentes exponenciais, o formato geral da resposta é semelhante ao verificado para sistemas de primeira ordem. 

Para o caso especial em que $\xi=1$, o comportamento do sistema é denominado criticamente amortecido. Neste caso, ambos os polos estarão na mesma posição ($p=\xi\omega_n$). Dessa forma, a resposta do sistema não apresentará componentes oscilatórias, sendo que a resposta ao degrau será representada por

.. math::
	y(t)=k[c_1+(c_2+c_3 t)e^{p t}]u(t).

O comportamento geral dos sistemas superamortecidos e criticamente amortecidos, considerando $k=1$ e $\omega_n=1$, é apresentada na figura a seguir.

.. figure:: /figures/modelagem/Figxi1.png
	:figwidth: 70%
	:align: center	 

Caso Subamortecido ($\xi<1$)
----------------------------

O terceiro tipo de resposta possível é denominada resposta subamortecida, a qual acontece quando $\xi<1$. Neste caso, o argumento $\xi^2-1$ é negativo, fazendo com que a posição dos polos seja uma grandeza complexa, com parte imaginária não nula, sendo representada por $p=\sigma\pm j\omega=\xi\omega_n \pm j\omega_n\sqrt{1-\xi^2}$. Devido à isso, o formato da resposta ao degrau, no domínio do tempo, apresenta uma componente oscilatória ($cos(\cdot)$) multiplicando a compontente exponencial, na forma

.. math::
	y(t)=k[c_1+c_2e^{-\xi\omega_n t}cos(\omega_n\sqrt{1-\xi^2} t)]u(t) \\
	y(t)=k[c_1+c_2e^{-\sigma t}cos(\omega t)]u(t)

Devido à existência do $cos(\cdot)$, a resposta apresentará um comportamento oscilatório, sendo acentuado à medida que o valor de $\xi$ é reduzido. Um exemplo do comportamento geral deste caso, para $k=1$ e $\omega_n=1$, é apresentado na figura a seguir. 

.. figure:: /figures/modelagem/Figxi2.png
	:figwidth: 70%
	:align: center

Repare que quanto menor o valor de $\xi$, mais significativa é a contribuição do termo oscilatório, fazendo com que o sistema demore mais para atingir o regime permanente, e apresente uma ultrapassagem percentual (ou sobresinal) maior.

No diagrama a seguir, é possível avaliar o efeito da mudança no valor do $\xi$ na resposta ao degrau de um sistema com $k=1$ e $\omega_n=1$ (Arraste a barra para selecionar o valor de $\xi$).

.. admonition:: Efeito do $\xi$ na resposta ao degrau

	.. raw:: html
	   :file: charts/sis2ordemcsi.html

Frequência Natural - $\omega_n$
-------------------------------

Enquanto o coeficiente de amortecimento $\xi$ influencia diretamente no tipo de resposta que o sistema de segunda ordem irá apresentar, o parâmetro $\omega_n$ afeta apenas a velocidade da resposta. Se analisarmos a expressão, no domínio do tempo, para os três tipos de respostas de um sistema de segunda ordem, vemos que $\omega_n$ está associado ao expoente do termo exponencial, e à frequência instantânea do termo oscilatóro. No fim das contas, se mantermos $\xi$ constante, a variação de $\omega_n$ resultará na mudança da velocidade da resposta do sistema, porém, sem mudanças no tipo da resposta, e nem no tamanho da ultrapassagem (sobresinal). O comportamento de um sistema, considerando $\xi=0,5$ e $k=1$ é apresentado na figura a seguir. 

.. figure:: /figures/modelagem/Figwn.png
	:figwidth: 70%
	:align: center

A medida que o valor de $\omega_n$ aumenta, a velocidade da resposta aumenta. Porém, a ultrapassagem (sobresinal) se mantém sempre a mesma, já que o valor de $\xi$ foi mantido constante. O efeito da variação de $\omega_n$ pode ser verificada, interativamente, no diagrama a seguir.

.. admonition:: Efeito do $\omega_n$ na resposta ao degrau

	.. raw:: html
	   :file: charts/sis2ordemwn.html

Aproximações Analíticas
-----------------------

Como apresentado nas seções prévias, o comportamento dinâmico geral de um sistema de segunda ordem depende de :math:`\xi` e :math:`\omega_n`, já que a posição dos polos desse tipo de sistema são

.. math::
	p_1=-\sigma \pm j\omega=-\xi\omega_n \pm \omega_n \sqrt{\xi^2-1}=-\xi\omega_n \pm j\omega_n \sqrt{1-\xi^2}, 
	
com a parte real do polo sendo :math:`\sigma=\xi\omega_n` e a parte imaginária sendo :math:`\omega=\omega_n \sqrt{1-\xi^2}`.

As duas principais características da resposta dinâmica de um sistema de segunda ordem subamortecido são o tempo de acomodação (:math:`T_s`) e a ultrapassagem percentual (:math:`M_p`). O tempo de acomodação é definido como o tempo necessário para a resposta do sistema atingir um valor :math:`2\%` próximo do valor em regime permanente. Note que alguns livros definem valores percentuais diferentes, como por exemplo, :math:`1\%` ou :math:`5\%`. Por sua vez, a ultrapassagem percentual é definida como a diferença percentual entre o valor absoluto do maior pico da resposta, em relação ao valor atingido em regime permanente.

Como mostrado previamente, o parâmetro :math:`\xi` está diretamente ligado à ultrapassagem percentual, sendo a relação inversamente proporcional, já que quanto menor for :math:`\xi`, maior será a ultrapassagem. Note que :math:`\xi` deve ser positivo, e para o sistema ser subamortecido, :math:`\xi<1`. Uma aproximação para a ultrapassagem percentual é 

.. math::
	\ln(M_p) \approx \frac{\sigma \pi}{\omega}.
	
Se substituirmos :math:`\sigma` e :math:`\omega`, podemos obter uma expressão que relaciona :math:`\xi` e :math:`M_p`, definida como

.. math::
	\xi^2 \approx \frac{\ln(M_p)^2}{\pi^2+\ln(M_p)^2}.

O tempo de acomodação (:math:`T_s`) também pode ser obtido a partir de aproximações analíticas. Uma aproximação bastante útil, especialmente válida quando :math:`\xi<0,8` é

.. math::
	T_s\approx -\frac{\ln(2\%)}{\sigma}.
	
Ou seja, se soubermos o tempo de acomodação do sistema de segunda ordem subamortecido, podemos estimar o valor da parte real dos polos como

.. math::
	\sigma \approx -\frac{\ln(2\%)}{T_s}.

	**Exemplo 1: Obtenção da função de transferência de um sistema a partir do gráfico da resposta no tempo.**
	
	Considerando um sistema dinâmico, cuja resposta ao degrau é apresentada a seguir, vamos obter uma função de transferência que represente de forma adequada esse sistema.
	
	.. raw:: html
	   :file: charts/RespostaDeSistemas/ExemploResposta2Ordem.html

	A resposta do sistema, no domínio do tempo, apresenta um comportamento típico de sistemas de segunda ordem subamortecidos, já que temos um sobressinal. A inspeção do gráfico indica que o máximo sobressinal é :math:`M_p=5\%`, já que o sistema apresenta um valor de pico de :math:`2,1`, o qual é :math:`5\%` maior que o valor que a resposta do sistema atinge em regime permanente, que é :math:`2`. Podemos utilizar o valor da ultrapassagem percentual para obter o coeficiente de amortecimento :math:`\xi`. Podemos encontrar o valor aproximado como
	
	.. math::
		\xi \approx \sqrt{\frac{\ln(0,05)^2}{\pi^2+\ln(0,05)^2}}=0,69.

	Outra informação que pode ser extraída da resposta temporal do sistema é o tempo de acomodação. Pela inspeção do gráfico, é possível estimar o tempo de acomodação verificando o instante em que a resposta está contida em uma vizinhança :math:`2\%` próxima do valor em regime permanente da resposta. O instante de tempo :math:`T_s=10,5` é o instante em que o sistema atingiu um valor :math:`2\%` próximo do valor final, sendo então o tempo de acomodação do sistema. A partir de :math:`T_s`, podemos encontrar o valor da parte real dos polos, que é
	
	.. math::
		\sigma \approx -\frac{\ln(2\%)}{T_s} \approx \frac{3,91}{10,5} \approx 0,95.
	
	A partir de :math:`\sigma` e :math:`\xi`, podemos encontrar :math:`\omega_n` e :math:`\omega`. Partindo de :math:`\sigma=\xi\omega_n`, obtemos
	
	.. math::
		\omega_n=\frac{\sigma}{\xi}=1,38.
		
	Usando a equação :math:`\omega=\omega_n \sqrt{\xi^2-1}` podemos obter
	
	.. math::
		\omega=1,38 \sqrt{0.69^2-1}=
	
Sistemas de Alta Ordem
======================

Sistemas que apresentam mais de um par de polos podem ser caracterizados como sistemas de alta ordem. Esses sistemas dinâmico são descritos por uma equação diferencial de ordem elevada, fazendo com que a função de transferência possua um polinômio no denominador com grau maior que dois, resultando em mais de dois polos. De forma geral, o comportamento deste tipo de sistema, não pode ser analisado de forma simples como sistemas de primeira e segunda ordem. Porém, muitos sistemas de alta ordem apresentam polos cuja parte real varia significativamente, fazendo com que nem todos os polos contribuem igualmente para o comportamento do sistema. Algumas partes da dinâmica dinâmica (modos característicos) podem ser ignoradas, especialmente as associadas à polos com parte real com módulo elevado (ou seja, muito rápidos), fazendo com que o comportamento de tais sistemas possa ser aproximado como um sistema de primeira ou segunda ordem, a depender de quais são os polos dominantes. 

Um sistema de alta ordem poderá ser aproximado por um sistema de primeira ou segunda ordem se houver um polo, ou um par de polos, cuja constante de tempo é muito maior -- parte real muito menor -- do que todos os demais. Quanto maior for a diferença entre a posição do/dos polos dominantes em relação aos demais, melhor será a aproximação. A aproximação é satisfatória para diferenças a partir de 5 vezes. 

	**Exemplo 2: Aproximação de um sistema de ordem elevada utilizando polos dominantes**
	
	Para um sistema representado pela função de transferência 
	
	.. math:::
		G(s)=\frac{250(s+3)(s+10)}{(s+1)(s+5)(s+15)(s+100)}

	temos 4 polos, definidos como :math:`s_1=-1`, :math:`s_2=-5`, :math:`s_3=-15` e :math:`s_4=-100`. A resposta do sistema é definida pel combinação linear dos modos característicos desse sistema, provenientes de cada um dos polos. A resposta ao impulso desse sistema é definida como :math:`h(t)=c_1 e^{s_1 t}+c_2 e^{s_2 t}+c_3 e^{s_3 t}+c_4 e^{s_4 t}=h(t)=c_1 e^{-1 t}+c_2 e^{-5 t}+c_3 e^{-15 t}+c_4 e^{-100 t}`, onde as constantes :math:`c_1`, :math:`c_2`, :math:`c_3` e :math:`c_4` definem a importância de cada modo na resposta do sistema. Quanto maior for o módulo do termos no expoente do modo característico, mais rápido será o exponencial. Dessa forma, fica evidente que o termo :math:`c_1 e^{-1 t}` será o polo dominante, ja que os demais termos irão convergir para :math:`0` rapidamente. Dessa forma, podemos aproximar :math:`G(s)` utilizando um sistema de primeira ordem, com polo :math:`s=-1`, e o mesmo ganho estático da função de transferência original. Para obtermos o ganho estático da função de transferência, basta definirmos :math:`s=0`, resultando em :math:`k=1`. Dessa forma, podemos representar a função de transferência de alta ordem pela função aproximada :math:`G(s)\approx \frac{1}{(s+1)}`. No diagrama a seguir é apresentada a resposta de ambos os sistemas, para uma entrada do tipo degrau. Note que, quando selecionamos o polo dominante sendo próximo de :math:`s=-1`, temos uma resposta ao degrau semelhante.

	.. raw:: html
	   :file: charts/sisaltaordem.html
   
Efeito dos Zeros e Sistemas de Fase Não Mínima
==============================================

Até o momento, a existência de zeros e seu efeito na resposta dinâmica do sistema foram ignorados. De forma geral, a presença de zeros pode alterar o comportamento do sistema, porém, seu efeito só é considerável quando a posição do zero é próxima da posição dos polos mais lentos do sistema. Se o zero estiver uma distância muito maior, em relação ao eixo imaginário, que algum polo do sistema, seu efeito será negligenciável. Por sua vez, zeros cuja posição é próxima do polo mais lento (polo cuja posição é a mais próxima ao eixo imaginário), ou mais próximo ao eixo imaginário, afetarão a resposta dinâmica, aumentando o sobressinal (ultrapassagem percentual).

Um caso de interesse é a existência de zeros no semi-plano direito, os quais introduzem um comportamento denominado fase não mínima. Um sistema com fase não mínima apresenta um comportamento peculiar, com resposta no sentido inverso ao esperado, durante os instantes iniciais da excitação do sistema. Quanto mais próximo for a posição do zero, em relação ao eixo imaginário, mais proeminente será o comportamento de fase não mínima. Um exemplo do comportamento de um sistema com zero é apresentado na Figura a seguir. Repare que, a medida que aproximamos o zero do eixo imaginário, observamos um sobressinal maior (quando o zero está no semi-plano esquerdo) ou um comportamento de fase não mínima mais acentuado (quando o zero está no semi-plano direito).

.. raw:: html
   :file: charts/sisfasenminima.html
   
Exercícios Sugeridos
====================

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
	
   
Referências
===========

LATHI, B. P. Sinais e Sistemas Lineares. Porto Alegre: Bookman, 2006. 2 ed.  ISBN: 978-8560031139

NISE, Norman S. Engenharia de sistemas de controle. 7. ed. Rio de Janeiro: LTC, 2017. 772 p. ISBN 978-8521634355