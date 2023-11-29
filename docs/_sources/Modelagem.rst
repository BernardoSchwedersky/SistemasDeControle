==============================
Respostas de Sistemas Lineares
==============================

Os sistemas dinâmicos lineares invariantes no tempo (LTI) desempenham um papel fundamental na compreensão e no controle de uma ampla gama de fenômenos dinâmicos. A capacidade de descrever o comportamento de sistemas complexos por meio de modelos matemáticos lineares tem implicações significativas na análise e no projeto de sistemas de controle. 

A resposta de um sistema LTI para uma entrada qualquer pode ser obtida utilizando a função de transferência que rege o comportamento do processo. Assumindo que a função de transferência seja conhecida e representada por:

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
	
	y(t)=k(1-e^{-\frac{1}{\tau}t})

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
	G(s)=\frac{k\omega_n^2}{s^2+\xi \omega_n s+\omega_n^2}.

De forma semelhante ao caso de primeira ordem, essa função de transferência é estruturada de forma que o parâmetro $k$ represente o ganho estático do sistema, o que pode ser verificado ao aplicarmos o teorema do valor final. O parâmetro $\xi$ é denominado fator de amortecimento e o parâmetro $\omega_n$ é denomindado como frequência natural. O impacto desses parâmetros na resposta, e a intuição por trás dos mesmos, será discutido a seguir.

A principal característica de um sistema de segunda ordem consiste na existência de 2 polos. A posição dos polos pode ser determinada facilmente, sendo

.. math::
	p_1=\xi\omega_n + \omega_n \sqrt{\xi^2-1},
	
	p_2=\xi\omega_n - \omega_n \sqrt{\xi^2-1}.

Fica evidente que a natureza da posição dos polos depende do argumento dentro da raiz quadrada, $\xi^2-1$. Esse argumento é positivo quando $\xi>1$, o que faz com que os polos sejam reais e distintos. Caso o argumento seja igual a 0 (\xi=1), os polos serão reais e iguais. Por fim, se o argumento for negativo ($\xi<1$), os polos terão uma parte imaginária, sendo então um par complexo conjugado. Para cada um desses 3 casos, a resposta ao degrau assumirá uma forma diferente. Iremos então, analisar cada um desses casos individualmente.

Caso Superamortecido ($\xi>1$) e Criticamente Amortecido ($\xi=1$)
------------------------------------------------------------------

Quando temos $\xi>1$, a resposta do sistema é superamortecida. O termo superamortecido vêm do fato de que a resposta ao degrau para esse sistema não apresenta componentes oscilatórias. De fato, a resposta ao degrau é representada, no domínio do tempo, pela expressão

.. math::
	y(t)=c_1+c_2e^{-p_1 t}+c_3e^{-p_2 t}.

Devido à resposta ser formada pela soma de duas componentes exponenciais, o formato geral da resposta é semelhante ao verificado para sistemas de primeira ordem. 

Para o caso especial em que $\xi=1$, o comportamento do sistema é denominado criticamente amortecido. Neste caso, ambos os polos estarão na mesma posição ($	p=\xi\omega_n$). Dessa forma, a resposta do sistema não apresentará componentes oscilatórias, sendo que a resposta ao degrau será representada por

.. math::
	y(t)=c_1+(c_2+c_3 t)e^{-p t}.

O comportamento geral dos sistemas superamortecidos e criticamente amortecidos, considerando $k=1$ e $\omega_n=1$, é apresentada na figura a seguir.

.. figure:: /figures/modelagem/Figxi1.png
	:figwidth: 70%
	:align: center	 

Caso Subamortecido ($\xi<1$)
----------------------------

O terceiro tipo de resposta possível é denominada resposta subamortecida, a qual acontece quando $\xi<1$. Neste caso, o argumento $\xi^2-1$ é negativo, fazendo com que a posição dos polos seja uma grandeza complexa, com parte imaginária não nula, sendo representada por $p=\sigma\pm j\omega=\xi\omega_n \pm j\omega_n\sqrt{1-\xi^2}$. Devido à isso, o formato da resposta ao degrau, no domínio do tempo, apresenta uma componente oscilatória ($cos(\cdot)$) multiplicando a compontente exponencial, na forma

.. math::
	y(t)=c_1+c_2e^{-\xi\omega_n t}cos(\omega_n\sqrt{1-\xi^2} t)

Devido à existência do $cos(\cdot)$, a resposta apresentará um comportamento oscilatório, sendo acentuado à medida que o valor de $\xi$ é reduzido. Um exemplo do comportamento geral deste caso, para $k=1$ e $\omega_n=1$, é apresentado na figura a seguir. 

.. figure:: /figures/modelagem/Figxi2.png
	:figwidth: 70%
	:align: center

Repare que quanto menor o valor de $\xi$, mais significativa é a contribuição do termo oscilatório, fazendo com que o sistema demore mais para atingir o regime permanente, e apresente uma ultrapassagem (ou sobresinal) maior.

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

A medida que o valor de $\omega_n$ aumenta, a velocidade da resposta aumenta. Porém, a ultrapassagem (sobresinal) se mantém sempre a mesma, já que o valor de $\xi$ foi mantido constante. O efeito da variação de $\omega_n$ pode ser verificada, iterativamente, no diagrama a seguir.

.. admonition:: Efeito do $\omega_n$ na resposta ao degrau

	.. raw:: html
	   :file: charts/sis2ordemwn.html

Sistemas de Alta Ordem
======================

.. raw:: html
   :file: charts/sisaltaordem.html
   
Sistemas de Fase Não Mínima
===========================

.. raw:: html
   :file: charts/sisfasenminima.html
   
   
   
Referências
===========

LATHI, B. P. Sinais e Sistemas Lineares. Porto Alegre: Bookman, 2006. 2 ed.  ISBN: 978-8560031139

NISE, Norman S. Engenharia de sistemas de controle. 7. ed. Rio de Janeiro: LTC, 2017. 772 p. ISBN 978-8521634355