status=published
date=2009-11-05
tags=blog
type=post
title=Como usamos �gil: SEA
~~~~~~
Dando continuidade � s�rie �Como usamos �gil�, entrevistei o trio Alexandre Gomes, Bruno Pedroso e Renato Willi, da [SEA Tecnologia](http://www.seatecnologia.com.br/). Nesta entrevista eles falam sobre a cultura da SEA e como lidam com o dif�cil mercado de licita��es.

**TaSafo**: Quais metodologias �geis s�o utilizadas na SEA?

**SEA**: N�o abra�amos uma metodologia por completo. Utilizamos Scrum e XP como base para o nosso jeito de desenvolver software. Utilizamos conceitos de Scrum para planejamento e temos pr�ticas do XP como testes autom�ticos, integra��o cont�nua, programa��o em par, entre outras. Na verdade damos muito mais �nfase aos valores. � como se diss�ssemos aos desenvolvedores: "sigam esses valores e fa�am do jeito que acharem melhor".

**TaSafo**: Em rela��o ao Scrum, qual o tempo de uma _sprint_?

**SEA**: O tempo da _sprint_ varia de projeto para projeto, mas costuma ser de 2 semanas a 1 m�s. Esse tempo depende do cliente e da equipe. Em rela��o � equipe, geralmente usamos _sprints_ mais curtas quando temos uma equipe menos experiente.





**TaSafo**: Ap�s definir o tempo da sprint de um projeto, esse tempo permanece o mesmo at� o final?





**SEA**: Depende. Sabemos que o ideal � que se mantenha, mas j� houve casos em que mudamos. Em um projeto passamos a _sprint_ de 2 semanas para 1 m�s, pois a equipe pegou experi�ncia e as reuni�es a cada 2 semanas estavam gerando _overhead_ da ger�ncia. O impacto n�o foi muito grande, pois j� ger�vamos uma _build_ semanal e afer�amos a velocidade semanalmente.







**TaSafo**: Como s�o feitos os contratos entre a empresa e os clientes? Voc�s usam contrato de escopo negoci�vel?







**SEA**: Em contratos com o governo, todos os projetos s�o de escopo fechado, e trabalhamos com m�tricas. Com a iniciativa privada, metade s�o de escopo negoci�vel, metade com m�tricas.







**TaSafo**: Em ambos os casos, como funcionam as estimativas do projeto?

**SEA**: N�s temos coletado m�tricas dos nossos projetos h� dois ou tr�s anos e aprendemos a us�-las para nos auxiliar nas estimativas. Por exemplo, n�s temos uma boa estimativa do intervalo de tempo necess�rio para desenvolver um ponto de fun��o. Para isso, levamos em considera��o principalmente a complexidade do sistema e a equipe de desenvolvimento. Ent�o usamos pontos de fun��o e pontos por caso de uso para nos auxiliar nos projetos de escopo fechado (um exemplo de como essas m�tricas s�o usadas pode ser encontrado no [blog da SEA](http://blog.seatecnologia.com.br/2009/05/11/como-medimos-sistemas-em-pontos-de-casos-de-uso)).

Quando temos escopo aberto, fazemos uma estimativa de alto n�vel, geralmente usando um intervalo de tempo de 1, 2 ou 3 semanas. Se a estimativa passar de 3 semanas, quebramos a funcionalidade e estimamos novamente. Dessa forma temos uma estimativa grosseira do projeto inteiro.







De qualquer forma, sempre procuramos mesclar v�rias t�cnicas para estimar. A converg�ncia (ou n�o) das estimativas, d� no��o do risco do projeto.

<div id="attachment_474" class="wp-caption" align="aligncenter" style="width: 408px"><p class="wp-caption-text"></p></div>
![Coopera��o e sucesso mesmo com escopo fechado com o governo](http://tasafo.files.wordpress.com/2009/11/sea-reuniao.jpg?w=1024) Coopera��o e sucesso mesmo com escopo fechado

<!-- more -->**TaSafo**: Quem � o _product owner_ (PO) e como ele age?

**SEA**: Existe um PO, que pode ser um membro da equipe sempre em contato com o cliente, ou o cliente em si, que � o melhor cen�rio. Na maioria das vezes a nossa equipe inteira fica alocada no cliente. Nesses casos, temos o cliente relativamente presente. Quando isso n�o acontece, tentamos manter um m�nimo de contato com o PO. A medida que ele percebe o retorno dessa presen�a, podemos melhorar a frequ�ncia.




**TaSafo**: Isso (quando o PO n�o est� sempre presente) tem influ�ncia as estimativas?




**SEA**: Sim, de forma negativa. Quanto mais longe, pior. Nesse caso, se a equipe n�o est� em contato direto com o PO, naturalmente o conhecimento sobre o sistema e o _feedback_ do cliente diminui, e as estimativas sofrem com isso.







**TaSafo**: Existem v�rias equipes trabalhando simultaneamente? Quantas pessoas cada equipe possui?







**SEA**: Hoje temos 10 projetos simult�neos, divididos em 7 equipes. Tem uma equipe que chamamos de PPTO (pau pra toda obra), que atende demandas pontuais, pois temos projetos que n�o t�m demanda cont�nua, nos quais recebemos uma ordem de servi�o (para criar uma funcionalidade nova, por exemplo), executamos e passamos para a pr�xima. N�s tentamos fazer com que uma equipe fique 100% focada em um s� projeto, para evitar o problema de multitarefa.

Em rela��o ao tamanho das equipes, temos equipes de 2 a 6 pessoas. Eu (Renato) e o Bruno estamos em todas e em nenhuma, pois n�o ficamos alocados o tempo todo em uma s� equipe. Fazemos mais os pap�is de coordenador e _coach_. Entramos e sa�mos das equipes de acordo com as necessidades. Por exemplo, na equipe da aeron�utica n�s quase n�o interferimos mais, pois est�o maduros o suficiente para caminhar sozinhos. Ent�o voltamos nossa aten��o para outros projetos, novas vendas e novas negocia��es.


![](http://tasafo.files.wordpress.com/2009/11/sea-dashboard.jpg?w=1024)


**TaSafo**: Como � o ambiente f�sico de trabalho?** **

**SEA**: Isso varia muito. Nos clientes sempre tentamos fazer com que a equipe fique na mesma sala, sem baias nem paredes, e que tenha espa�o para 2 pessoas dividirem 1 computador. Na verdade preferimos a rela��o 2 pessoas x 1 computador. J� na SEA temos uma mesona e todo mundo senta ao redor dela. � s� chegar com o seu _notebook_ e trabalhar.



**TaSafo**: Existe algum aspecto que marca seu m�todo? Algum toque especial fora do padr�o das metodologias?

**SEA**: N�o que seja algo inovador ou fora do padr�o, pois as metodologias s�o muito extens�veis, mas uma coisa que fizemos e chamou aten��o de algumas pessoas da comunidade foi o uso do que apelidamos de "mantras". Durante as retrospectivas, surgiam algumas fraquezas que n�o consegu�amos endere�ar com a��es pra serem melhoradas nas pr�ximas itera��es, pois faziam parte de h�bitos ou disciplinas que a equipe deveria se atentar mais o tempo todo, como padr�o do c�digo, comitar, completar o javadoc, etc.

Para as equipes ficarem atentas a essas quest�es, escolh�amos uns 3 h�bitos desses para serem observados na itera��o, faz�amos frases tipo mantras, por exemplo: "eu documentarei mais o c�digo", ou "eu seguirei o padr�o tal", as anot�vamos grandes num papel e deix�vamos no topo do Kanban. Brinc�vamos que todo dia cada um tinha que chegar cedo e ficar repetindo essas frases na frente do Kanban algumas vezes pra n�o esquecer. Era uma brincadeira, claro que ningu�m ficava repetindo as frases rezando na frente do Kanban, mas essas quest�es iam melhorando ao longo das itera��es.





**TaSafo**: Qual � o profissional que a SEA procura?





**SEA**: Essa � uma pergunta boa. O pessoal �s vezes pergunta: "tem que ser gente boa para trabalhar com metodologia �gil? Tem que ser profissional s�nior, muito experiente?". A pessoa tem que ser boa sim, mas o que � ser gente boa para gente?

Eu acho que o bom profissional n�o � necessariamente uma pessoa com anos de experi�ncia e todas as certifica��es poss�veis e imagin�rias. �s vezes isso at� atrapalha devido ao alto comprometimento que a pessoa tem com o passado de sua carreira que leva � resist�ncia a mudan�as. Temos procurado pessoas curiosas, motivadas, que gostem do que fazem e que tenham iniciativa. � nossa leitura para o "safo" que usamos tanto para descrev�-los. Uma pessoa assim, se n�o tiver um determinado conhecimento numa tecnologia ou ferramenta, o adquire facilmente. Experi�ncia � trocada com os mais experientes. Quando a pessoa vem para SEA, vem como um todo, n�o s� para um papel ou para trabalhar num determinado projeto ou tecnologia. Queremos que ela desenvolva todo seu potencial na empresa, e sempre damos chance pra isso. Esse talvez seja um dos grandes chamarizes pra eles.


<div id="attachment_473" class="wp-caption" align="aligncenter" style="width: 422px"><p class="wp-caption-text"></p></div>
![Ambiente de trabalho na sede da SEA](http://tasafo.files.wordpress.com/2009/11/sea-equipe-2.jpg?w=1024) Ambiente de trabalho na sede da SEA

_Uma curiosidade: a SEA surgiu como uma parceira da Rational e era especializada em implanta��o da metodologia de desenvolvimento RUP. Mesmo contando com equipes qualificadas e depois da tentativa de implanta��o de modelos de qualidade de processos como o�MPS.BR, a empresa alcan�ou melhores resultados em termos de estabilidade, satisfa��o, sustentabilidade e rotatividade depois de adotar as metodologias �geis, h� dois anos._
