=============================
Projeto pelo Lugar das Raízes
=============================

O diagrama do lugar das raízes é uma ferramenta útil, seja para analisar a estabilidade e o desempenho de um sistema de controle, mas também para auxiliar no projeto do controlador. O diagrama apresenta, graficamente, todas as possíveis posições dos polos em malha fechada, alcançáveis ao ajustarmos um parâmetro do sistema de controle, o qual é, geralmente, o ganho do controlador. Utilizando o conhecimento acerca da estrutura do diagrama, e como ele é modificado ao adicionarmos polos e zeros na estrutura do controlador, podemos projetar o sistema de controle de forma a garantir que o desempenho do sistema em malha fechada seja próximo do desempenho desejado.

Neste capítulo, iremos explorar a interrelação entre algumas estruturas de controladores e o impacto de sua utilização na estrutura do diagrama do lugar das raízes. Inicialmente iremos explorar como podemos análisar o sistema de controle a partir do diagrama e como o diagrama se se modifica ao alterarmos a estrutura do controlador. Se baseando no conhecimento da influência de cada estrutura, iremos explorar técnicas para projetar um sistema de controle capaz de atender alguns requisitos de desempenho em malha fechada.

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
  
.. figure:: /figures/nomeFig.png
	:figwidth: 80%
	:align: center


Compensador Atraso de Fase (Lag)
--------------------------------

O compensador atraso de fase consiste na configuração em que o polo está à direita do zero. Isso faz com que a contribuição de fase seja negativa, sendo que, quanto mais distantes estiverem o polo e o zero, maior será a contribuição negativa de fase. Uma contribuição negativa de fase faz com que o lugar das raízes tenda a estar mais à direita em relação a posição inicial, o que faz com que o sistema tenda a ser mais lento, na média. Esse efeito pode ser visto na figura a seguir, na qual temos um compensador atraso no qual o polo é :math:`P=0` e o zero pode ser escolhido.

.. raw:: html
	:file: charts/ExemploAtraso.html
	
O compensador atraso de fase deteriora o desempenho transitório do sistema, fazendo com que os tempos de acomodação alcançáveis sejam menores. Porém, essa estrutura é fundamental para alcançarmos erro nulo em casos onde o sistema não é integrador. Nesse tipo de caso, é necessário adicionar o integrador na estrutura do controlador. Se adicionarmos apenas o integrador, teremos uma grande contribuição de fase negativa, o que tornará o sistema muito lento. Ao adicionarmos um zero à esquerda do polo, podemos amenizar o atraso adicionado pelo polo, sendo que, quanto mais próximo estiver o zero do polo, menor será o atraso adicionado pelo compensador. 



	**Exemplo 3: Filtro passa-baixas ativo:** bi-quad

Compensador Avanço de Fase (Lead)
---------------------------------


.. raw:: html
	:file: charts/ExemploAvanço.html
	
	**Exemplo 4: Controle da posição angular de um motor DC:**

----------------
Projeto Completo
----------------

	
