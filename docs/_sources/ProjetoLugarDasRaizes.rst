=============================
Projeto pelo Lugar das Raízes
=============================

O diagrama do lugar das raízes é uma ferramenta útil, seja para analisar a estabilidade e o desempenho de um sistema de controle, mas também para auxiliar no projeto do controlador. O diagrama apresenta, graficamente, todas as possíveis posições dos polos em malha fechada, alcançáveis ao ajustarmos um parâmetro do sistema de controle, o qual é, geralmente, o ganho do controlador. Utilizando o conhecimento acerca da estrutura do diagrama, e como ele é modificado ao adicionarmos polos e zeros na estrutura do controlador, podemos projetar o sistema de controle de forma a garantir que o desempenho do sistema em malha fechada seja próximo do desempenho desejado.

Neste capítulo, iremos explorar a interrelação entre algumas estruturas de controladores e o impacto de sua utilização na estrutura do diagrama do lugar das raízes. Inicialmente iremos explorar como podemos análisar o sistema de controle a partir do diagrama e como o diagrama se modifica ao alterarmos a estrutura do controlador. Se baseando no conhecimento da influência de cada estrutura, iremos explorar técnicas para projetar um sistema de controle capaz de atender alguns requisitos de desempenho em malha fechada.

Especificação em Malha Fechada
==============================

Para compreendermos melhor como as características de desempenho de um sistema de controle se relacionam com o diagrama do lugar das raízes, primeiramente, iremos analisar a influência dessas especificações na posição das raízes no diagrama. Como foi visto no capítulo sobre modelagem de sistemas, devido à estarmos lidando apenas com sistemas lineares e invariantes no tempo, é possível representar grande parte dos processos utilizando funções de transferência de primeira ou segunda ordem. Mesmo em casos em que o sistema é de ordem mais elevada, em muitos casos é possivel representar esse sistema por um sistema de primeira ou segunda ordem, devido à dominância de alguns dos polos do sistema. Como um sistema de controle terá, ao menos, a dinâmica do processo e a do controlador, se ambos forem de primeira ordem, o sistema de controle será de segunda ordem. Dessa forma, um sistema de controle poderá ser representado como um sistema de segunda ordem dominante, e o projeto e análise do mesmo será realizado de forma a resultar em um sistema de controle que se aproxime de um sistema de segunda ordem dominante.

Um sistema de segunda ordem genérico é representado pela equação

.. math::
	G(s)=\frac{k\omega_n^2}{s^2+\xi \omega_n s+\omega_n^2}.
	
Alterando os parâmetros :math:`\xi` e :math:`\omega_n` podemos alterar a resposta do dinâmica do sistema, com :math:`\xi` sendo relacionado à máxima ultrapassagem percentual (sobressinal), e :math:`\omega_n` relacionado ao tempo de acomodação da resposta. Esses parâmetros estão relacionados aos polos do sistema de segunda ordem, de acordo com as equações

.. math::
	p_{1,2}=\xi\omega_n \pm \omega_n \sqrt{\xi^2-1}.

Geralmente, o sistema será subamortecido, fazendo com que o termo dentro da raiz seja negativo, resultando polos complexos conjugados. Nesse caso, as raizes são

.. math:
	p_{1,2} = \sigma + j\omega,
	
onde :math:`\sigma=\xi\omega_n` e :math:`\omega=\omega_n \sqrt{\xi^2-1}`. Ou seja, a posição das raízes no plano complexo é definida pelos parâmetros :math:`\sigma` e :math:`\omega`, os quais são obtidos de :math:`\xi` e :math:`\omega_n`. Podemos analisar qual será a posição dos polos no lugar das raízes à medida que definirmos :math:`\xi` e :math:`\omega_n`, conforme apresentado nas figuras a seguir.

	.. raw:: html
		:file: charts/EspecificacaoCsi.html

Por sua vez, quando alteramos :math:`\omega_n`, podemos verificar que e

	.. raw:: html
		:file: charts/EspOmega.html
	
As principais especificações são relacionadas à existência de erro nulo em regime permanente, ao tempo de acomodação do sistema, e ao tamanho da ultrapassagem percentual (sobressinal).

-------------------------
Erro em Regime Permanente
-------------------------

Talvez a principal especificação em um sistema de controle é a necessidade de erro nulo em regime permanente para algum tipo de sinal de referência. O sinal de referência mais típico é o degrau unitário, já que uma parcela significativa dos sistema de controle são regulatórios, com o valor de referência sendo constante, o que pode ser modelado por um degrau unitário. Outro tipo comum de referência é a rampa unitária, a qual pode ser utilizada para modelar transições suaves entre valores distintos de referência.

As condições para existência de erro nulo foram apresentadas anteriormente, sendo que, para referências do tipo degrau, a condição é a existência de um integrador no processo ou no controlador. Como um integrador é equivalente à um polo na origem (:math:`(s)`), para termos erro nulo para referências do tipo degrau, é necessário termos um polo na origem do diagrama do lugar das raízes. Caso não exista um polo na origem e é desejado a garantia de erro nulo em regime permanente, devemos inserir o polo na origem. Para referência do tipo rampa é nécessário um integrador duplo, ou seja, dois polos na origem. Caso o sistema não apresente um integrador duplo, será necessário introduzir no controlador a quantidade de zeros na origem necessária para que o lugar das raízes tenha um par de polos na origem. 

-------------------
Tempo de Acomodação
-------------------

O tempo de acomodação é diretamente relacionado à parte real dos polos dominantes do sistema. Isso fica claro quando analisamos a aproximação analítica do tempo de acomodação em relação aos parâmetros do sistema de segunda ordem, dada por :math:`T_s=\frac{-\text{ln}(2\%)}{\sigma}`. Dessa forma, quanto mais negativo for :math:`\sigma`, menor será o tempo de acomodação do sistema. Ou seja, quanto mais à esquerda da parte negativa do plano complexo estiverem os polos desejados, mais rápido será o tempo de acomodação do sistema. Esse comportamento pode ser visto na figura a seguir.

.. raw:: html
	:file: charts/EspecificacaoSigma.html

Dessa forma, se a especificação for associada à um tempo máximo de acomodação, teremos duas regiões distintas: a região à esquerda do valor :math:`\sigma` desejado conterá todas as possíveis posições em que o tempo de acomodação é menor do que o especificado; por sua vez, a região à direita do valor de :math:`\sigma` desejado será composta pelas posições em que o sistema resultante terá tempo de acomodação maior que o especificado.

------------------------
Ultrapassagem Percentual
------------------------

A ultrapassagem percentual, ou máximo sobressinal, é representada por :math:`M_p`, sendo calculado como o valor percentual entre o ponto máximo da resposta do sistema e o valor final da mesma. Geralmente, a ultrapassagem está relacionada ao aparecimento de comportamentos oscilatórios na resposta, o que pode ser indesejado. Por isso, uma das especificações é o valor máximo de :math:`M_p`. A ultrapassagem está relacionada com o coeficiente de amortecimento, :math:`\xi`, do sistema, por meio da expressão:

.. math::
	\xi^2=\frac{\text{ln}(M_p)^2}{\pi^2+\text{ln}(M_p)^2}.

Quanto maior for a ultrapassagem percentual, menor será o valor de :math:`\xi`. Dessa forma, se especificarmos que o comportamento desejado do sistema tenha uma ultrapassagem máxima de :math:`5\%`, teremos um conjunto de possíveis posições dos polos em malha fechada que apresentam :math:`5\%` ultrapassagem, exatamente. Esse conjunto de raizes forma duas linhas no semiplano esquerdo, com o ângulo das mesmas sendo definido por :math:`\xi`. A àrea entre as duas linhas corresponde ao conjunto de posições em que o sistema apresentará comportamento melhor do que o especificado, ou seja, menor ultrapassagem. Por sua vez, a região externa às duas linhas representa a região cujo comportamento é pior que o especificado, ou seja, maior ultrapassagem. Esse comportamento pode ser visto na figura a seguir. 

.. raw:: html
	:file: charts/EspecificacaoMp.html

Análise pelo Lugar das Raízes
=============================

O lugar geométrico das raízes é uma ferramenta valiosa para a análise do comportamento de um sistema de controle. A simples inspeção do diagrama traz informações sobre os tipos de resposta que o sistema de controle pode apresentar, e também se o sistema pode apresentar instabilidade. No exemplo a seguir são apresentados alguns aspectos que podem ser avaliados com a inspeção do lugar das raízes.

	**Exemplo 1:** Considerando um processo definido pela função de transferência :math:`G(s)=\frac{6}{(s+1)(s+3)}`, controlado por um sistema realimentado no qual :math:`C(s)=\frac{K}{s}`, o qual representa um integrador com ganho variável. A análise do lugar das raízes traz informaçãoes sobre o impacto da adição do integrador e também como o ajuste do ganho afeta o comportamento do sistema.
	
	A adição do integrador é importante para garantirmos que exista erro nulo para referências do tipo degrau. Porém, ao realizarmos essa adição, o formato do lugar das raízes muda. Antes de adicionarmos o integrador, o lugar das raízes estava todo contido no semi-plano esquerdo, o que significar que, independente do ganho escolhido, o sistema nunca instabilizará. Porém, após adicionarmos o integrador, vemos que o lugar das raízes tem uma estrutura diferente, com ramos cruzando o eixo imaginário, o que indica que existe uma faixa de valores de ganho que faz com que o sistema seja instável. 
	
	.. raw:: html
		:file: charts/ExemploIntegrador.html
		
	O ajuste do ganho apresenta impacto no tipo de resposta que o sistema irá apresentar. Se analisarmos o caso em que o controlador é o integrador, e estamos ajustando o ganho, vemos que existem dois tipos de respostas possíveis. Para ganhos pequenos, o sistema apresenta todos polos em malha fechada sobre o eixo real, resultando em um comportamento típico de sistemas superamortecidos. A partir de um valor de ganho específico, um par de polos se desprende do eixo real, tornando-se complexo conjugado. Após isso, o sistema passa a apresentar um comportamento típico de sistema subamortecido, com sobresinal e resposta com componentes oscilatórias. Esse comportamento pode ser visto no diagrama apresentado a seguir. A medida que ajustamos o ganho do processo, vemos que a posição dos polos em malha fechada muda, fazendo com que a resposta do sistema à um degrau de referência mude. 
	
	.. raw:: html
		:file: charts/ExemploIntegradorComResposta.html
		
	Para o valor de :math:`K=0,21` temos os polos se desprendendo do eixo real, instante em que a resposta é criticamente amortecida. Valores maiores fazem a resposta ser subamortecida, enquanto valores menores fazem a resposta ser superamortecida. Valores de ganho acima de :math:`K=4` fazem a resposta do sistema instabilizar, já que os polos em malha fechada cruzam o eixo imaginário, adentrando o semi plano direito. 
	
Projeto pelo Lugar das Raízes
=============================

Sabendo como as especificações do sistema de controle se refletem no diagrama do lugar das raízes e como a posição dos polos em malha fechada se relaciona com a resposta dinâmica do sistema, podemos projetar o controlador de forma a atingir as especificações. O projeto acontecerá em várias etapas, podendo ser repetido caso o controlador projetado não alcance o desempenho desejado.

As etapas consistem em:

- Análise das especificações: Conversão das especificações na posição desejada dos polos em malha fechada;

- Esboço do lugar das raízes: Esboço considerando os elementos conhecidos do sistema de controle, como o processo :math:`G(s)` e polos conhecidos de :math:`C(s)`; 

- Projeto do compensador: O compensador consiste em um conjunto de polos e zeros que será adicionada no controlador de forma a fazer com que ramos do diagrama do lugar das raízes passem pela região desejada para os polos em malha fechada do sistema. Dessa forma, é possível ajustar o ganho do controlador de forma a fazer com que os polos do sistema de controle estejam sintonizados em uma posição cujo desempenho seja semelhante ao desejado.

- Ajuste do ganho: Se os ramos do lugar das raízes passar pela região em que o desempenho é o desejado, podemos escolher o valor do ganho que faça com que os polos em malha fechada estejam nesta posição desejada. 

- Verificação do projeto: Como o projeto considera que os polos em malha fechada serão um par complexo conjugado dominante e, geralmente, o projeto resulta em um sistema com mais de dois polos, devemos verificar se o sistema em malha fechada apresenta o par de polos projetado como os polos dominantes. Caso nao haja a dominância, o comportamento do sistema será pior que o especificado. 

----------------
Projeto do Ganho
----------------

O projeto de um sistema de controle utilizando o diagrama do lugar das raízes se baseia na análise do sistema de controle utilizando o diagrama e na escolha de compensadores e do ganho do controlador, para fazer com que os polos em malha fechada se encontrem na posição desejada - posição que faz com que o sistema alcance o desempenho especificado. O primeiro caso que será visto é o caso em que não é necessário utilizar um compensador, ou seja, basta ajustarmos o ganho para alcançarmos o desempenho desejado. O exemplo é apresentado a seguir.

	**Exemplo 2: Controle do ângulo de uma antena:**
	Antenas são utilizadas em diversas aplicações, devendo ser posicionadas em uma posição que facilite a recepção da mensagem transmitida. Para garantir que a antena esteja posicionada corretamente, podemos utilizar um sistema de controle realimentado. Na figura a seguir é apresentado um esboço de um sistema onde desejamos controlar o ângulo que define a altura do receptor e é apresentado o diagrama de blocos do sistema que será controlado.

	.. figure:: /figures/LugarDasRaizes/antena.png
		:figwidth: 80%
		:align: center	
		
	O objetivo do sistema de controle é garantir que a antena seja posicionada sem erro para referências estáticas e que a resposta do sistema de controle seja a mais rápida possível sem que exista sobressinal, de forma a evitar a oscilação da antena.
	
	**Solução:** a análise das especificações traz as informações acerca do que desejamos para o desempenho do sistema de controle. Como desejamos que o posicionamento tenha erro nulo para referências estáticas (referência do tipo degrau), é necessário termos ao menos um integrador na malha direta do sistema de controle (ou em :math:`G(s)`, ou em :math:`C(s)`). Isso já é alcançado, pois o processo apresenta um integrador na função de transferência que modela a dinâmica do motor e carga. Dessa forma, não é necessário adicionar nada ao controlador para atingir este requisito.

	Já o requisito acerca da velocidade do sistema, a qual deve ser a maior possível sem a existência de sobressinal, nos traz informação sobre a posição desejada das raízes em malha fechada. Para o sistema ser rápido, os polos devem estar o mais distante possível do eixo imaginário. Para não haver sobressinal, os polos não podem ter parte imaginária (:math:`\xi \ge 1`). Dessa forma, é desejado posicionarmos as raízes na posição mais à esquerda possível, contanto que as raízes sejam puramente reais. 

	Podemos utilizar o diagrama do lugar das raízes para investigarmos qual a posição das raízes garante as condições desejadas. Se esboçarmos o lugar, obteremos um diagrama semelhante ao apresentado a seguir.
	
	.. raw:: html
		:file: charts/ExemploProjetoAntena.html

	A análise gráfica do diagrama traz a informação que desejamos. Os polos do sistema se movimenta sobre o eixo real, até se encontrarem e se desprenderem do mesmo. Exatamente no ponto em que os polos deixam o eixo real, é o ponto em que temos os polos sendo reais e na posição mais distante do eixo imaginário. Dessa forma, devemos seleciona a posição em que os polos deixam o eixo real como a posição desejada para os polos em malha fechada.
	
	Para encontrarmos a posição em que os polos deixa o eixo imaginário, devemos usar a regra 6 do esboço do diagrama, que define os pontos de saída e chegada, :math:`\sigma`, no eixo real como
	
	.. math::
		\sum_{i=1}^{m}\frac{1}{\sigma-z_i}=\sum_{j=1}^{n}\frac{1}{\sigma-p_j}.

	Para o problema em questão, temos
	
	.. math::
		\frac{1}{(\sigma+0)}+\frac{1}{(\sigma+2)}+\frac{1}{(\sigma+10)}=0.
		
	Resolvendo para :math:`\sigma`, obtemos :math:`\sigma_1=-0,95` e :math:`\sigma_2=-7,05`. Inspecionando o diagrama, é evidente que o ponto :math:`\sigma_1=-0,95` representa o ponto em que os polos se desprendem do eixo real. Dessa forma, iremos definir a posição :math:`s=-0,95` como a posição desejada para os polos em malha fechada. 
	
	Após definirmos qual a posição desejada para os polos em malha fechada, e verificarmos que a posição desejada faz parte do lugar das raízes, podemos encontrar o valor do ganho :math:`K` que faz com que os polos em malha fechada estejam exatamente na posição desejada. Para isso, usaremos a condição de módulo, definida como

	.. math::
		|C(s)G(s)|=1.
		
	Para o problema em questão, teremos
	
	.. math::
		|\frac{3K}{s(s+2)(s+10)}|=1.
		
	Substituindo o valor da posição desejada, :math:`s=-0,95`, na condição de módulo, obtemos
	
	.. math::
		\frac{|3K|}{|0,95||-0,95+2||-0,95+10|}=1
	
	.. math::
		\frac{|3K|}{|0,95||1,05||9,05|}=1
		
	.. math::
		K=\frac{0,95\cdot 1,05 \cdot 9,05}{3}=3,01.
		
	Ou seja, se escolhermos o ganho como :math:`K=3,01`, iremos posicionar os polos em malha fechada em :math:`s=-0,95`, o que resultará no sistema com resposta mais rápida sem a presença de sobressinal. A resposta ao degrau do sistema é apresentada na figura a seguir. Repare que ganhos menores que o projetado fazem o sistema ser mais lento, e ganhos maiores introduzem sobressinal.
	
	.. raw:: html
		:file: charts/ExemploAntenaResposta.html	
		
-------------
Compensadores
-------------

Geralmente, o simples ajuste do ganho do controlador não é suficiente para atingirmos o desempenho desejado. Em muitos casos, não temos um integrador no processo, sendo necessária a adição do integrador no controlador, de forma a garantir erro nulo para referências do tipo degrau. Além disso, quando desejamos acelerar a resposta do sistema, geralmente teremos que adicionar algum comportamento dinâmico ao controlador. Em ambos os casos, podemos alcançar o objetivo adicionando um compensado ao controlador.

O compensador nada mais é do que um conjunto de polos e zeros que serão adicionados ao controlador. Na forma mais genérica, um controlador com compensador pode ser definido por

.. math:: C(s)=\frac{K(s+Z)}{(s+P)}.

O termo Z define a posição do zero do compensador, enquanto o termo P define a posição do polo do compensador. A adição do compensador influenciará a estrutura do lugar das raízes do sistema de controle, fazendo com que o lugar mude sua trajetória. Dessa forma, iremos analisar qual o impacto da posição do polo e do zero no desenho do lugar das raízes.

Como temos apenas um polo e um zero no compensador, existem duas configurações possíveis. Podemos ter o polo à direito da zero (:math:`-P>-Z`), configuração denominada compensador atraso (lag), ou temos o polo à esquerda do zero (:math:`-P<-Z`), configuração denominada compensador avanço (lead). O nome se dá pela contribuição de ângulo que cada um desses compensadores fornece. Quando calculamos o ângulo de um ponto de teste qualquer no plano complexo em relação à função de transferência do controlador, vemos que o zero fornece uma contribuição positiva de ângulo, enquanto o polo fornece uma contribuição negativa. Quando o polo está à direita do zero, o ângulo formado entre qualquer ponto de teste e o polo é maior que o ângulo formado por esse ponto e o zero, fazendo com que a contribuição resultante seja negativa. Por isso, dizemos que o compensador fornece um atraso de fase, já que ele adiciona uma fase negativa à todo lugar das raízes. A análise para o avanço é semelhante, devido ao zero estar à direito do polo, ele fornece uma contribuição de ângulo maior que o polo, fazendo com que a contribuição resultante seja positiva. Por isso esse compensador é denominado avanço, já que todo o lugar terá um aumento em sua fase. Essas duas configurações são apresentadas na figura a seguir.
  
.. raw:: html
	:file: charts/ExemploAvancoAtraso.html


Compensador Atraso de Fase (Lag)
--------------------------------

O compensador atraso de fase consiste na configuração em que o polo está à direita do zero. Isso faz com que a contribuição de fase seja negativa, sendo que, quanto mais distantes estiverem o polo e o zero, maior será a contribuição negativa de fase. Uma contribuição negativa de fase faz com que o lugar das raízes tenda a estar mais à direita em relação a posição inicial, o que faz com que o sistema tenda a ser mais lento, na média. Esse efeito pode ser visto na figura a seguir, na qual temos um compensador atraso no qual o polo é :math:`P=0` e o zero pode ser escolhido.

.. raw:: html
	:file: charts/ExemploAtraso.html
	
O compensador atraso de fase deteriora o desempenho transitório do sistema, fazendo com que os tempos de acomodação alcançáveis sejam menores. Porém, essa estrutura é fundamental para alcançarmos erro nulo em casos onde o sistema não é integrador. Nesse tipo de caso, é necessário adicionar o integrador na estrutura do controlador. Se adicionarmos apenas o integrador, teremos uma grande contribuição de fase negativa, o que tornará o sistema muito lento. Ao adicionarmos um zero à esquerda do polo, podemos amenizar o atraso adicionado pelo polo, sendo que, quanto mais próximo estiver o zero do polo, menor será o atraso adicionado pelo compensador. Porém, se adicionarmos o zero muito próximo do integrador, podemos confinar o integrador em uma posição em que existirá um polo em malha fechada muito lento, limitando a possibilidade de acelerar o processo aumentando o ganho do controlador.

	**Exemplo 3: Filtro passa-baixas ativo:** 
	
	Um filtro passa baixas passivo de segunda ordem pode ser definido pela função de transferência :math:`G(s)=\frac{1}{(R_1 C_1 s+1)(R_2 C_2 s+1)}`. Esse filtro é implementado pelo circuito apresentado a seguir.

	.. figure:: /figures/LugarDasRaizes/FiltroBiQuad.png
		:figwidth: 60%
		:align: center

	A escolha das resistências e capacitâncias determina a frequência de corte e o ganho do filtro. Idealmente, o ganho deve ser unitário, para que o sinal filtrado, :math:`v_o(t)`, seja uma versão sem ruído de :math:`v_i(t)`. Uma forma de aprimorar este filtro e garantir que o ganho do filtro seja unitário é contruir uma malha de controle, fazendo com que :math:`v_i(t)` seja o sinal de referência, e :math:`v_o(t)` a variável controlada. Se projetarmos este sistema de controle para alcançarmos erro nulo em regime permanente para referências do tipo degrau, o resultado será um filtro ativo. Realizaremos o projeto considerando :math:`R_1 C_1=0,2` e :math:`R_2 C_2=0,25`.
	
	**Projeto:**
	
	Para alcançarmos a especificação de erro nulo para referências do tipo degrau, devemos adicionar um integrador ao controlador, :math:`C(s)=\frac{K}{s}`. A adição do integrador modifica o lugar das raízes do sistema de controle, fazendo com que os ramos sejam atraidos para a direita, o que faz com que o sistema se torne mais lento. Independentemente da escolha do ganho, o sistema será mais lento em malha fechada do que em malha aberta. A diferença entre os lugares das raízes com e sem o integrador é apresentado a seguir.
	
	.. raw:: html
		:file: charts/ExemploFiltroAtivo.html

	Podemos amenizar o efeito do atraso de fase resultante da inserção do integrador ao utilizarmos um zero à esquerda do integrador, o que resultará na estrutura atraso de fase. Quanto mais próximo estiver o zero do integrador, menor será o atraso resultante. Quanto mais longe estiver o zero, menor será a sua influência, e maior será o atraso. Devido ao zero estar à esquerda do polos, essa configuração é o compensador atraso de fase.
	
	A escolha da posição do zero irá afetar a posição alcançável para as raízes em malha fechada. Se inserirmos o zero próximo ao integrador, o formato do lugar volta a ser similar ao caso em malha aberta, o que parece tentador. Porém, esta configuração faz com que o polo na origem fique preso ao zero, fazendo com que, independemente do ganho, o sistema fique lento. Uma segunda abordagem consiste em posicionar o zero próximo aos polos do sistema em malha aberta, o que faz com que o lugar seja atraído para a esquerda, porém, ainda esteja à direita do lugar para o sistema em malha aberta. Essas duas configurações são apresentadas na figura a seguir.

	.. raw:: html
		:file: charts/ExemploFiltroAtivo2.html
		
	A segunda alternativa é mais interessante, pois permitirá ajustar o ganho do controlador para que tenhamos um filtro ativo com frequência de corte similar ao do filtro	passivo. O ajuste de ganho pode ser feito para posicionarmos um dos polos em malha fechada em :math:`s=-2,5`. Podemos encontrar o valor do ganho :math:`k` para posicionar um dos polos em :math:`s=-2,5` utilizando a condição de ganho, fazendo :math:`|C(s)G(s)|=1`. Para tal, temos:
	
	.. math::
		|C(s)G(s)|=1
		
	.. math::
		|\frac{k(s+3,5)}{s}\frac{20}{(s+4)(s+5)}|=1
		
	substituindo :math:`s=-2,5` teremos:
	
	.. math::
		\frac{|k||(1)|}{|-2,5|}\frac{|20|}{(|1,5|)(|2,5|)}=1
		
	.. math::
		k=\frac{2,5 \cdot 1,5 \cdot 2,5}{1 \cdot 20}=	0,47

	Então, se sintonizarmos o ganho como :math:`k=0,47` faremos com que um dos polos em malha fechada esteja em :math:`s=-2,5`, com os outros dois polos sendo um par conjugado próximo do polo que foi escolhido. A posição dos polos em função do ganho escolhido, bem como a resposta do sistema em malha fechada para uma referência do tipo degrau unitário são apresentadas a seguir.
	
	.. raw:: html
		:file: charts/ExemploFiltroAtivo3.html
		
Como visto no exemplo, o controlador atraso é útil quando pretendemos melhorar o desempenho em regime permanente do sistema, ou seja, garantir erro nulo para algum tipo de referência, ou fazer com que o erro seja menor que certo valor. O controlador PI é um caso especial do controlador atraso, no qual a posição do polo é a origem, e a posição do zero é à esquerda do polo. O zero é usado para reduzir a perda de desempenho introduzida pelo polo lento que foi adicionado, porém, o sistema sempre apresentará desempenho inferior ao alcançável se não introduzissemos o polo lento.		

Compensador Avanço de Fase (Lead)
---------------------------------

Se desejarmos acelerar a resposta do sistema de controle, podemos adicionar um zero no semiplano esquerdo. O zero irá deslocar todo o lugar das raízes para a esquerda, fazendo com que o sistema de controle possa ser sintonizado de forma a apresentar tempos de acomodação menores que os alcançáveis sem o compensador. A função de transferência desse controlador é :math:`C(s)=ks`, a qual implementa um derivador puro, o que não é realizável. Devido à isso, a solução prática para acelerar o comportamento do sistema de controle consiste no uso da estrutura de compensador avanço, definica como :math:`C(s)=k\frac{(s+Z)}{s+P}`, na qual o polo está sempre à esquerda do zero. Se posicionarmos o polo bastante à esquerda dos demais elementos do lugar das raízes, o seu efeito influenciará pouco, restando o efeito do zero. A influência da estrutura avanço, com :math:`P=10`, no lugar de um sistema definido por :math:`G(s)=\frac{1}{(s+1)(s+2)}`, é apresentada na figura a seguir.

.. raw:: html
	:file: charts/ExemploAvanco.html

Quanto mais próximo está o zero da origem, mais à esquerda é deslocado o lugar. Quanto mais à esquerda está o lugar, mais rápidos poderão ser os polos em malha fechada. Dessa forma, podemos usar a estrutura avanço para deslocar o lugar para a esquerda, e fazer com que o sistema de controle alcance o desempenho especificado. O projeto de um compensador avanço é apresentado no exemplo a seguir.

	
	**Exemplo 4: Controle da posição angular de um motor DC:**

	Neste exemplo iremos controlar a posição angular, :math:`\theta(t)`, de um motor DC. Neste tipo de motor, podemos manipular a velocidade angular, :math:`\omega(t)`,  por meio da mudança da sua tensão de alimentação, :math:`v(t)`. Já a posição angular pode ser obtida pela integral da velocidade angular. Um diagrama de blocos deste processo é apresentado a seguir.

	.. figure:: /figures/LugarDasRaizes/MotorDC.png
		:figwidth: 60%
		:align: center	
	
	Considerando um motor parametrizado pela função de transferência :math:`G(s)=\frac{4}{s^2+6s+8}`, iremos projetar um controlador que seja capaz de apresentar erro nulo para referências do tipo degrau, máxima ultrapassagem percentual de :math:`5\%` e tempo de acomodação menor do que :math:`3` segundos.
	
	**Solução:**
	
	O projeto do controlador se inicia pela análise do sistema em malha aberta e das especificações. A análise do sistema em malha aberta revela que o sistema é composto por uma função de transferência de segunda ordem associada à um integrador. Já a análise das especificações nos revela que:
	
	- A especificação de erro nulo para referências do tipo degrau implica na necessidade de termos um integrador na malha direta do sistema de controle. Como o sistema já é integrador, essa especificação é naturalmente atendida.
	
	- A especificação sobre o tempo de acomodação impacta do valor de :math:`\sigma` conforme:
	
	.. math::
		\sigma=\frac{-ln(0,02)}{3}=1,3.
	
	- A especificação da máxima ultrapassagem percentual de :math:`5\%` implicará em um valor mínimo para o :math:`\xi`. Se utilizarmos a aproximação analítica teremos:
	
	.. math::
		\xi^2=\frac{ln(0,05)^2}{\pi^2+ln(0,05)^2},
		
	.. math::
		\xi=0,69.
	
	Com essa especificação, podemos definir qual a posição desejada para as raízes em malha fechada. Podemos obter o valor de :math:`\omega_n` por meio de :math:`\sigma=\xi\omega_n`. Dessa forma, :math:`omega_n=1,89`. A partir de :math:`omega_n` e :math:`\sigma` podemos obter :math:`\omega`, por meio de :math:`\omega_n^2=\sigma^2+\omega^2`. Então, :math:`\omega=1,37`, o que faz com que a posição desejada para as raízes em malha fechada seja :math:`s=-\sigma\pm j\omega=-1,3\pm j1,37`. Podemos então esboçar o lugar das raízes do sistema com :math:`C(s)=k`, para verificar se o lugar passa pela posição desejada para as raízes. Se o lugar passar pela posição desejada, um simples ajuste de ganho é suficiente, porém, caso não passe, será necessário adicionar um compensador. O lugar para este sistema é apresentado em seguida.
	
	.. raw:: html
		:file: charts/ExemploMotorDC.html
	
	Avaliando o lugar, vemos que ele não passa sobre a posição desejada para os polos em malha fechada (em verde). Como esta posição esta à esquerda do lugar, teremos que adicionar um compensador para fazer com que o lugar passe pela posição desejada. A adição do compensador fará com que exista uma nova contribuição de fase, que irá compensar a diferença de fase entre o ponto desejado e o lugar. Dessa forma, a primeira etapa para projeto do compensador avanço consiste em determinar qual o avanço de fase que o compensador deverá introduzir. Relembrando, para um ponto qualquer, :math:`s`, fazer parte do lugar das raízes, ele precisa satisfazer a condição de ângulo, definida como :math:`\angle C(s) G(s)=-180^o(2k+1)`. Então, a contribuição de fase do controlador, :math:`\angle C(s)=\phi_c` deve ser igual à :math:`\phi_c=-180^o(2k+1)-\angle G(s)`. Podemos obter a contribuição necessária na forma:
	
	.. math::
		\phi_c=-180^o(2k+1)-\angle \frac{4}{(s+2)(s+4)s}
		
		\phi_c=-180-(-\angle(s+2)-\angle(s+4)-\angle(s))
		
		\phi_c=-180-(-\angle(-1,3+j1,37+2)-\angle(-1,3+j1,37+4)-\angle(-1,3+j1,37))

		\phi_c=-180-(-\angle(0,7+j1,37)-\angle(2,7+j1,37)-\angle(-1,3+j1,37))		
	
		\phi_c=-180+62,9^o+26,9^o+133,5^o
		
		\phi_c=43,2^o
		
		
	Ou seja, a contribuição de fase do compensador avanço deve ser de :math:`\phi_c=43,2^o`. Teoricamente, é possível avançar até :math:`90^o` com a estrutura :math:`C(s)=k\frac{(s+Z)}{s+P}`, porém, na prática, é possível avançar ângulos até :math:`70^o`. Como desejamos avançar apenas :math:`43,2^o`, podemos alcançar facilmente utilizando a estrutura avanço. 
	
	Partindo da estrutura :math:`C(s)=k\frac{(s+Z)}{s+P}`, precisamos fazer com que:
	
	.. math:: 
		\angle k\frac{(s+Z)}{s+P}=43,2^o
		
		\angle (s+Z)-\angle(s+P)=43,2^o
	
	Como existem duas variáveis, devemos escolher uma delas para calcular o valor da segunda que satisfaça a equação. Geralmente escolhemos a posição do polo, fazendo ele ser entre 2 e 10 vezes mais rápido que o polo mais rápido do processo. Como o polo mais rápido do processo está em :math:`-4`, se escolhermos adicionar um polo 5 vezes mais rápido, teremos :math:`P=20`, o que fará com que a posição do polo seja :math:`-20`. Após escolhermos a posição do polo, nos resta calcular qual a posição do zero que satisfaça a equação, resultando no avanço de fase desejado.

	.. math:: 
		\angle (s+Z)-\angle(s+20)=43,2^o	
	
		\angle (-1,3+j1,37+Z)-\angle(-1,3+j1,37+20)=43,2^o	
	
		\angle (-1,3+j1,37+Z)-\angle(18,7+j1,37)=43,2^o	
		
		\angle (-1,3+j1,37+Z)-4,2^o=43,2^o	
		
		\angle (-1,3+j1,37+Z)=47,4^o	
		
		tg^{-1}(\frac{1,37}{-1,7+Z})=47,^o
		
		\frac{1,37}{-1,7+Z}=1,08
		
		Z=2,58
		
		
	Dessa forma, se utilizarmos o compensador avanço parametrizado como :math:`C(s)=k\frac{(s+2,58)}{s+20}`, alcançaremos o avanço desejado de :math:`\phi_c=43,2^o`. Teoricamente, se escoçarmos o lugar das raízes considerando o compensador, veremos que o lugar passará sobre a posição desejada para os polos em malha fechada. Esse lugar das raízes é apresentado a seguir.
	
	.. raw:: html
		:file: charts/ExemploMotorDC2.html

	A inspeção do diagrama mostra que o objetivo foi alcançado. Ao adicionarmos o compensador avanço, todo o lugar se moveu para a esquerda, fazendo com que a posição desejada para os polos em malha fechada faça parte do lugar. Dessa forma, podemos sintonizar o ganho do controlador, fazendo com que os polos estejam exatamente na posição desejada. O ajuste de ganho pode ser realizado por meio da condição de módulo, da seguinte forma:
	
	.. math::
		|C(s)G(s)|=1
		
		
		|\frac{k(s+2,58)}{(s+20)}\frac{4}{s(s+2)(s+4)}|=1
		
		|\frac{k(-1,3+j1,37+2,58)}{(-1,3+j1,37+20)}\frac{4}{(-1,3+j1,37)(-1,3+j1,37+2)(-1,3+j1,37+4)}|=1
		
		\frac{|k||(1,28+j1,37)|}{|(18,7+j1,37)|}\frac{|4|}{|(-1,3+j1,37)||(0,7+j1,37)||(2,7+j1,37)|}=1
		
		\frac{4k \cdot 1,87}{18,75 \cdot 1,89 \cdot 1,54 \cdot 3,03}=1
		
		k=22,1
	
	Dessa forma, o projeto do controlador foi finalizado, com :math:`C(s)=22,1\frac{(s+2,58)}{s+20}`. Resta simular o resultado, e refazer alguma parte do projeto caso o resultado não seja o esperado. A simulação do sistema em malha fechada é apresentada a seguir:
	
	.. raw:: html
		:file: charts/ExemploMotorDC3.html	
	
	A análise da resposta ao degrau mostra que as especificações foram quase atendidas. A ultrapassagem percentual foi de :math:`6\%`, e o tempo de acomodação foi levemente maior que :math:`3` segundos. O motivo para as especificações não serem completamente atendidas está na condição que assumimos no projeto de que o desempenho será semelhante ao de um par de polos complexos dominantes. Dessa forma, o projeto inteiro foi realizado considerando que se posicionarmos as raízes na posição desejada, o comportamento do sistema será o de um sistema de segunda ordem dominante. Porém, raramente isso irá acontecer, já que temos outros polos em malha fechada, que, apesar de estarem à esquerda do par de polos cuja posição foi alocada, ainda influenciam no comportamento do sistema. Por isso, o desempenho do sistem sempre será um pouco inferior à planejada. Uma forma de compensar isto seria adicionar uma margem no projeto, como por exemplo, compensar :math:`5^o` a mais do que o calculado, fazendo com que exista uma margem no projeto.
	
----------------
Projeto Completo
----------------

	
