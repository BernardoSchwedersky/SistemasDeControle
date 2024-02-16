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

Projeto pelo Lugar das Raízes
=============================


------------------------
Controlador Proporcional
------------------------


--------------------------------------
Compensador Atraso de Fase (Lag)
--------------------------------------



---------------------------------------
Compensador Avanço de Fase (Lead)
---------------------------------------




--------------------------------------------
Compesador Avanço-Atraso (Lead-Lag)
--------------------------------------------

	
