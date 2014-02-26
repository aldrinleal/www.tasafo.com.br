status=published
date=2009-09-13
tags=blog
type=post
title=Como usamos �gil: OnCast
~~~~~~
Este � o primeiro artigo de uma s�rie intitulada "Como usamos �gil". Tendo como inspira��o o livro "Scrum e XP direto das trincheiras" (Scrum and XP from the trenches), de Henrik Kniberg, no qual ele conta em detalhes como usa Scrum e XP, pretendemos entrevistar algumas empresas brasileiras que usam metodologias �geis no seu dia-a-dia.

Sabemos que a principal dificuldade encontrada por iniciantes em �gil � justamente p�r em pr�tica tudo o que estudou. Principalmente porque a grande maioria das empresas ainda n�o adotou tais metodologias, somos muitas vezes pioneiros em adotar �gil na empresa em que trabalhamos.

Diferente dos livros que dizem **o que** devemos fazer, mostrar de forma pr�tica **como** as empresas usam as metodologias pode ajudar a diminuir a dist�ncia que separa a teoria da pr�tica, e de repente evitar que alguns erros sejam cometidos devido � inexperi�ncia. Esse � o principal objetivo desta s�rie.

A primeira empresa entrevistada foi a [OnCast](http://www.oncast.com.br/), de Florian�polis, Santa Catarina. Entrevistei Samuel Cresc�ncio, um dos fundadores da empresa. Segue o resultado dessa entrevista:

<!-- more -->**TaSafo: **Quais metodologias �geis s�o utilizadas na OnCast?**
**

**OnCast: **Usamos um _mix_ de pr�ticas baseadas nos nossos princ�pios que s�o adaptadas ao contexto dos projetos. Temos como base da nossa cultura os princ�pios de Lean e do manifesto �gil. Para implementar os conceitos �geis, n�s temos uma figura que � parecida com uma pir�mide: no topo, temos Lean e os nossos valores, que � o que define nossa cultura; na parte intermedi�ria, temos a �rea de gest�o de projetos, onde normalmente usamos Scrum, e em alguns casos um modelo parecido com Lean; na base da pir�mide, temos a engenharia de software, que � onde utilizamos algumas pr�ticas do XP, como os testes automatizados, integra��o cont�nua, simplicidade e refatora��o constante, que d�o sustentabilidade para que possamos obter os valores das metodologias que utilizamos.

**TaSafo: **Quais pr�ticas desse mix Lean + Scrum + XP s�o utilizadas por voc�s?

**OnCast: **Utilizamos o Scrum na �ntegra. J� do XP, fazemos programa��o em par para transfer�ncia de conhecimento para um novo membro da equipe e para tarefas complexas; fazemos _move people around _para promover um conhecimento amplo sobre o c�digo para todos dentro das equipes. Al�m disso, utilizamos c�digo coletivo; integra��o cont�nua; testes em todos os n�veis (unidade, integra��o, funcionais, aceita��o), em sua maioria automatizados; em alguns casos, utilizamos TDD.

**TaSafo:** Em rela��o ao Scrum...
Como fazem o _product backlog_?

**OnCast:** Uma pessoa respons�vel pelos projetos da OnCast se re�ne com o cliente para viabilizar e estimar o projeto. Salientamos nesse momento que essa estimativa � muito crua, e que uma estimativa mais real e detalhada ser� feita pela equipe de desenvolvimento. Nesse momento criamos algumas est�rias de alto n�vel, que far�o parte do product backlog. Durante o desenvolvimento o backlog geralmente � alterado.

**TaSafo: **Qual o tempo de um _sprint_?

**OnCast:** Isso varia de projeto para projeto. Mais al�m: temos projetos que o tempo do _sprint_ � fixo; em outros � vari�vel. Usamos _sprints_ menores em projetos pequenos para aumentar o _feedbak_, o aprendizado e a corre��o de problemas. Em projetos mais longos, podemos usar _sprints_ maiores.

**TaSafo:** Quem � o _product owner_ (PO) e como ele age?

**OnCast:** Nesse caso o Scrum � bem interessante para n�s. Como fornecemos _outsourcing_, o Scrum promove uma boa separa��o de pap�is e responsabilidades: o PO fica respons�vel pelo neg�cio, enquanto que a equipe cuida da tecnologia. Muitas vezes o cliente possui v�rios _stakeholders_ para um projeto, ent�o a centraliza��o de um �nico PO como o representante deles no projeto � muito importante. Esse PO � quem participa das reuni�es de planejamento, nas quais o PO vai at� a sede da OnCast ou a nossa equipe vai at� o cliente. Al�m disso, temos comunica��o direta com o PO pessoalmente ou atrav�s de telefone, e-mails, etc.

**TaSafo:** O que acontece se o time percebe que n�o vai conseguir entregar o _sprint backlog_?

**OnCast:** N�s sempre trabalhamos de forma colaborativa com o nosso PO, ent�o sempre informamos os problemas a ele, deixando o projeto com boa visibilidade. De qualquer forma, quando acontece um problema cr�tico, utilizamos uma t�cnica do Lean, que se chama_ stop-the-line_, que significa: parar a linha de produ��o, corrigir o problema pela raiz, para ent�o voltar � linha de produ��o. Ent�o, quando usamos _stop-the-line_, dependendo do problema a itera��o inteira pode ser cancelada, mas o que geralmente acontece � que tomamos algumas a��es para mitigar aquele risco ou para diminuir o impacto daquele problema no final da itera��o, objetivando manter o prazo da itera��o inalterado e entregando software com valor agregado ao cliente. Pode ser que precisemos cortar escopo, ent�o fazemos isso junto ao PO. Assim como n�s podemos querer alterar o _product backlog_, o cliente �s vezes identifica que suas prioridades mudaram no meio do _sprint_. Fazemos ent�o o _stop-the-line_, damos a oportunidade para ele substituir funcionalidades por outras de mesmo valor. N�s n�o pegamos mais capacidade do que aquela que podemos produzir. Conhecemos nossa velocidade e o esfor�o das est�rias, ent�o permitimos que o PO altere as est�rias de modo que elas se adequem a nossa velocidade.

**TaSafo: **E quanto aos _bugs_ encontrados ap�s o t�rmino do _sprint_, o que acontece com eles?

**OnCast: **Ao ser notificada de um _bug_, a equipe imediatamente cria um item no _backlog_ (est�ria), que ser� priorizado pelo PO. Dependendo da prioridade esse item pode entrar no _sprint_ em andamento, ou nos pr�ximos _sprints_. Como os _bugs_ sempre entram no _product backlog_, n�o usamos ferramentas de _bug tracking_ para gerenciar isso.

**TaSafo:** Existem v�rias equipes trabalhando simultaneamente? Quantas pessoas cada equipe possui?

**OnCast:** Isso depende das necessidades de cada projeto. Hoje temos 5 equipes trabalhando em projetos diferentes. Em geral as equipes t�m de 4 a 6 pessoas, mas j� tivemos equipes de 2 e 3 pessoas para projetos menores.

**TaSafo:** Ao t�rmino de um projeto, o que acontece com a equipe de desenvolvimento?

**OnCast:** Como trabalhamos com presta��o de servi�os, estamos sempre preocupados com a demanda de projetos e relacionamos isso com a nossa capacidade produtiva. Ent�o estamos sempre prospectando novos projetos, constantemente visitando clientes e avaliando oportunidades. O que tem acontecido ultimamente � que as equipes n�o t�m ficado desalocadas. No dia seguinte ap�s o t�rmino de um projeto, tem outro esperando para come�ar.
Mas quando ocorre de uma equipe ficar ociosa entre um projeto e outro, ela fica livre para inovar, adquirir conhecimento ou mesmo para trabalhar nos nossos projetos _open-source_.

**TaSafo:** Como � o ambiente f�sico de trabalho? As equipes ficam distribu�das geograficamente?

**OnCast:** N�s temos 2 laborat�rios de desenvolvimento: um deles possui um ambiente todo aberto e grande, n�o possui divis�rias entre as mesas, todo mundo fica no mesmo c�modo; o outro � uma casa que foi transformada em laborat�rio. Nele, as equipes se instalam nas depend�ncias da casa. Nessa casa, temos um _lounge_ com uns puffs onde o pessoal costuma relaxar, tirar uma soneca depois do almo�o, etc. O pessoal est� at� querendo botar um videogame l�. Temos uma cultura de liberdade e tentamos deixar o pessoal bem � vontade. Por exemplo, no ver�o, as pessoas gostam de ir trabalhar de bermuda e chinelo de dedo; temos um hor�rio de trabalho flex�vel, desde que respeite as necessidades do time. Tentamos deixar as pessoas confort�veis, porque o objetivo � promover a criatividade, ent�o o ambiente l� � bem aberto.

<div id="attachment_361" class="wp-caption" align="alignleft" style="width: 259px"><p class="wp-caption-text"></p></div>
![Daily meeting de uma equipe](http://tasafo.files.wordpress.com/2009/09/daily-meeting-oncast.jpg?w=300)

Com rela��o ao _daily meeting_, sempre fazemos na frente do _dashboard_. Cada equipe possui um _dashboard_ e um _burndown chart_ e � l� que ocorre o _daily meeting_. N�o existe a obrigatoriedade de ficar em p�, mas seguimos a regra de 15 minutos para a reuni�o, nos quais as pessoas devem responder as 3 perguntas do _daily Scrum__ meeting_.

**TaSafo:** Como s�o feitos os contratos entre a empresa e os clientes? Voc�s usam contrato de escopo negoci�vel?

**OnCast:** No in�cio foi dif�cil vender o primeiro projeto de escopo aberto. O cliente n�o queria e acabamos fechando um projeto com escopo fechado. Trabalhamos utilizando pr�ticas �geis, estimando com _story points_ e oferecemos ao cliente a possibilidade de mudar o escopo, contanto que n�o alterasse o custo final do projeto, ou seja, ele poderia trocar uma funcionalidade que custasse 3 _story points_ e colocar outra que tamb�m custasse 3 _story points_.

Depois disso n�s conseguimos estabelecer um relacionamento muito interessante com os clientes e passamos a usar um modelo de contrato de escopo negoci�vel. Nesse caso, n�s fechamos o custo por hora, sem cobrar valores diferenciados para os membros da equipe. Dessa forma n�s fechamos um valor por equipe, e n�o por pessoa. Funciona assim: o cliente tem um projeto e pede uma equipe de 4 pessoas para desenvolv�-lo. Fazemos ent�o uma estimativa na qual achamos que, por exemplo, 6 meses de desenvolvimento para a equipe de 4 pessoas s�o suficientes. A partir de ent�o o cliente paga mensalmente o que foi gasto em esfor�o naquele m�s. J� ocorreram casos de projetos menores, em que fizemos uma estimativa e gastamos menos esfor�o. Nesses casos, n�s s� cobramos pelo esfor�o entregue, mesmo que a estimativa tenha sido maior. Com isso o cliente adquiriu confian�a na empresa, o que nos permitiu usar contratos de escopo negoci�vel.

Hoje s� usamos esse tipo de contrato (de escopo negoci�vel) e at� recusamos alguns contratos de escopo fechado. Com o tempo, n�s adquirimos uma certa habilidade em conversar sobre os processos �geis e mostrar os nossos casos de sucesso, ent�o quando um cliente aparece com um projeto de escopo fechado, geralmente acabamos convencendo-o de que o modelo de escopo negoci�vel ser� muito mais interessante para ele.

**TaSafo:** Existe algum aspecto que marca seu m�todo? Algum toque especial fora do padr�o da metodologia (nesse caso, fora do Scrum)?

**OnCast:** Sim, utilizamos a an�lise SWOT para as retrospectivas. Avaliamos as for�as e fraquezas daquilo que est� sob o controle do time (aspectos internos) e as oportunidades e amea�as do que � externo ao time. � muito legal fazer isso e tem sido um ponto fundamental no nosso processo de melhoria cont�nua.

<div id="attachment_360" class="wp-caption" align="alignright" style="width: 259px"><p class="wp-caption-text"></p></div>
![Dashboard](http://tasafo.files.wordpress.com/2009/09/dashboard.jpg?w=300)

Utilizamos o Scrum tamb�m para gerenciar outras �reas da empresa, como o marketing e o administrativo-financeiro. Nesses casos utilizamos um _dashboard_ diferenciado, que tamb�m � um _kanban_, com as tarefas a fazer, o que est� sendo feito e o que j� foi feito, mas criamos um esquema de prioriza��o diferenciado, que � distribu�do ao longo das datas. Com isso, temos visibilidade e n�o corremos o risco de esquecer de fazer alguma coisa a ser feita em determinada data. O interessante � que estamos conseguindo aumentar bastante a produtividade desses 2 setores utilizando Scrum, isso � bem legal.
