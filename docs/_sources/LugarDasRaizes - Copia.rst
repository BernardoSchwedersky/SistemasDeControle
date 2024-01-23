===========================
Lugar Geométrico das Raízes
===========================

Em um sistema de controle realimentado, as raízes do polinômio característico do sistema em malha fechada são os polos do sistema, os quais determinam a sua resposta dinâmica. O polinômio característico é obtido a partir da equação característica do sistema em malha fechada, que é a equação obtida ao igualar à zero o denominador da função de transferência do sistema.

Considerando um sistema de controle realimentado em que o controlador é :math:`C(s)=K`, conforme apresentado no diagrama de blocos a seguir:


os polos do sistema em malha fechada podem ser obtidos ao encontrar as raízes de :math:`1+KG(s)=0`. Como o ganho :math:`K` é uma variável, os polos assumirão valores distintos para cada valor de :math:`K`.

	Exemplo:
	Considerando um processo integrador, descrito pela função de transferência :math:`G(s)=\frac{1}{s(s+10)}`, controlado por um controlador proporcional, :math:`C(s)=K`, podemos obter a função de transferência do sistema em malha fechada conforme:

	..math::
		G_{mf}=\frac{C(s)G(s)}{1+C(s)G(s)}=\frac{K\frac{1}{s(s+10)}{1+K\frac{1}{s(s+10)}=\frac{K}{s^2+10s+K}.

	A posição dos polos do sistema em malha fechada é obtida encontrando as raízes de :math:`s^2+10s+K=0`, existindo polos distintos para cada valor de :math:`K`. Se substituirmos :math:`K` por diversos valores, podemos encontrar a posição dos polos para cada configuração, conforme apresentado na tabela a seguir:
	
+-------+-----------+-----------+
| K     | Polo 1    | Polo 2    |
+=======+===========+===========+
| 0     | -10       | 0         |
| 5     | -9,47     | -0,53     |
| 10    | -8,87     | -1,13     |
| 15    | -8,16     | -1,84     |
| 20    | -7,24     | -2,78     |
| 25    | -5        | -5        |
| 30    | -5+j2,34  | -5-j2,34  |
| 35    | -5+j3,16  | -5-j3,16  |
| 40    | -5+j3,87  | -5-j3,87  |
+-------+-----------+-----------+

	Podemos notar que, quando :math:`K=0`, a posição dos polos do sistema em malha fechada é igual à dos polos do sistema em malha aberta. A medida que que o ganho é incrementado, a posição dos polos em malha fechada se aproxima, até que, para :math:`K=25`, temos um par de polos em :math:`-5`. Ao incrementarmos ainda mais o ganho, é verificado que os polos deixam de ser puramente reais, tornando-se complexos conjugados. 
	
	Podemos apresentar graficamente a variação da posição dos polos do sistema em malha fechada no plano complexo. Para o sistema do exemplo, a variação da posição dos polos é apresentada no diagrama a seguir.
	
	

O lugar das raízes é uma representação gráfica das posições dos polos do sistema em relação a uma variação de um parâmetro (geralmente um ganho). O eixo x do gráfico representa a parte real das raízes (polos), enquanto o eixo y representa a parte imaginária. À medida que o parâmetro varia, o lugar das raízes mostra como as posições dos polos mudam.

A análise do lugar das raízes é útil para entender o comportamento dinâmico do sistema e fazer ajustes no sistema de controle, de forma à atender aos requisitos de desempenho desejados. As aplicações práticas do diagrama do lugar das raízes incluem:

- Projeto de Controladores:
	Ao analisar o lugar das raízes, é possível projetar controladores de forma a garantir a estabilidade e alcançar o desempenho desejado para o sistema. A inspeção do diagrama permite identificar como o ganho do sistema afeta a estabilidade e permite o ajuste para que sejam atendendidos requisitos específicos, como tempo de resposta, coeficiênte de amortecimento e máxima ultrapassagem percentual (sobressinal).

- Análise de Sistemas de Controle:
	Além de auxiliar no projeto, a inspeção do diagrama permite analisar o comportamento do sistema de controle. O lugar das raízes ajuda a visualizar como a estabilidade é afetada por mudanças nos parâmetros do sistema de controle (ganho).


Vetores de Números Complexos
============================


Esboço do Diagrama
==================
