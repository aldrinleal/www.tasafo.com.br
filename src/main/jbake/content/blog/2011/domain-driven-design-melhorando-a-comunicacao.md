status=published
date=2011-10-19
tags=blog
type=post
title=Domain Driven Design - Melhorando a comunica��o
~~~~~~
Software � complexidade. E tal complexidade vem diretamente do dom�nio do problema ao qual o software se destina a resolver. � aqui que entram uma s�rie de pr�ticas voltadas a tentar combater ou mesmo amenizar tal complexidade. A cria��o de um modelo de dom�nio � uma delas.

Um modelo � uma simplifica��o, uma interpreta��o de algo mais complexo no qual gostar�amos de mostrar os aspectos mais relevantes. Um modelo de dom�nio serve como base para uma comunica��o entre as pessoas que participam de um projeto. Esta comunica��o deve ser realizada atrav�s de uma linguagem que facilite a intera��o entre pessoas que possuem vis�es diferentes sobre o dom�nio.

Em um projeto de software podemos encontrar v�rios perfis de profissionais. Os especialistas de neg�cio possuem sua pr�pria linguagem, seus pr�prios jarg�es t�cnicos sobre o dom�nio. Diferente dos desenvolvedores que, por sua vez, possuem seus pr�prios conceitos para se referenciar ao dom�nio, muitas das vezes mais voltado para a solu��o.

Para os desenvolvedores torna-se dif�cil entender o dom�nio, algo novo, algo complexo, passado a eles atrav�s de uma linguagem que n�o compreendem muito bem. Alguns at� se destacam e conseguem falar as duas linguagens, mas isso � mais um problema do que solu��o. A comunica��o torna-se uma via de m�o dupla. Tendo de ser traduzida a todo instante. Esse � o grande mal que aflige os projetos de software. Uma tradu��o mal interpretada pode colocar tudo a perder.

<!-- more -->

Por isso a necessidade de uma linguagem ub�quoa de alto n�vel que esteja�presente em todos os cantos do projeto. E que seja capaz, n�o s� de descrever artefatos de sistema, mas tamb�m, tarefas e funcionalidades. Essa linguagem deve atender a desenvolvedores e especialistas no dom�nio para que possam se comunicar uns com os outros e entre si. Pelo menos, no mundo ideal seria assim. N�o � t�o f�cil manter uma linguagem ub�qua. � preciso um compromisso forte por parte dos membros da equipe para o uso da linguagem baseada no modelo.

**Diagramas**

A maioria das pessoas s�o visuais e os diagramas auxiliam na obten��o e no entendimento de informa��es. A [UML](http://pt.wikipedia.org/wiki/UML) � uma ferramenta muito boa nesse aspecto. Diagramas [UML](http://pt.wikipedia.org/wiki/UML) podem ajudar a ententer fluxos e intera��es. No entanto, a [UML](http://pt.wikipedia.org/wiki/UML) n�o � a melhor forma de se modelar um dom�nio. Diagramas [UML](http://pt.wikipedia.org/wiki/UML) complexos podem vir a ser de dif�cil compreens�o. H� muito trabalho para interpret�-los e muito para constu�-los e modific�-los. S�o completos demais e mesmo assim deixam muita coisa de fora. Sobrecarregam o leitor com muitos detalhes e pouco significado.

Detalhes relevantes do design ficam no c�digo.� Diagramas devem abordar os pontos principais como complemento ao modelo de dom�nio. O diagrama n�o � o modelo, n�o deve ser encarado como modelo. Ele � s� uma forma de ajudar na comunica��o. C�digo bem escrito � t�o explicativo quanto um diagrama.

**Documentos de texto**

A comunica��o _face to face_ vem sendo cada vez mais enfatizada, principalmente com a for�a que os m�todos �geis vem adquirindo ao longo dos anos. No entanto, documentos escritos s�o uma necessidade. Mas criar documentos que realmente agreguem valor a equipe � um desafio.

O grande problema com rela��o a isto � que software evolui. Software muda, a linguagem do projeto muda, c�digo muda e os documentos s�o deixados para tr�s. Vendo dessa forma, o [Extreme Programming](http://www.extremeprogramming.org/) prega que a melhor documenta��o que existe � o c�digo. Pois o c�digo dificilmente vai mentir. Documentos mentem e at� coment�rios no c�digo mentem. Isso acontece pois documentos e coment�rios n�o afetam o comportamento do software por isso eles sempre saem de sincronia com o c�digo. Logo ficamos altamente dependentes do c�digo como meio de comunica��o. Dai a import�ncia do [c�digo limpo](http://www.infoq.com/br/articles/clean-code-book-review).

Mas c�digo como documento tem alguns problemas. Possui muitos detalhes. Mesmo que ele seja limpo, pode n�o ser t�o �bvio. E os desenvolvedores n�o s�o os �nicos que precisam entender o modelo de dom�nio. Dai a import�ncia de bons documentos e bons diagramas. Mas diagramas e documentos n�o devem tentar fazer o que o c�digo j� faz bem. Eles devem se complementar.

Os termos presentes no documento devem aparecer nas conversas face a face, nos diagramas e no c�digo. Isso caracteriza a linguagem onipresente. No entanto a linguagem onipresente pode evoluir. Os documentos devem sobreviver a esta evolu��o e estar sempre em sintonia com o projeto. Caso contr�rio, tornam-se mais um desperd�cio.

**C�digo**

C�digo precisa transmitir significado. Tamb�m precisa estar em sintonia com o projeto. A linguagem ub�qua precisa estar presente no c�digo. Este � o cerne do [Domain Driven Design](http://en.wikipedia.org/wiki/Domain-driven_design). No entanto, isso requer um alto grau de disciplina. Porque at� mesmo o c�digo pode mentir. Por exemplo, o nome de um m�todo que n�o condiz com o seu comportamento. O c�digo n�o deve somente fazer a coisa certa, mas tamb�m, deve dizer a coisa certa.

Apesar de o c�digo mentir, ele sem d�vida, � o artefato que mais se aproxima da realidade do dom�nio. Por isso deve utilizar a mesma linguagem usada nos requisitos e nas conversas. A linguagem ub�qua, onipresente, voltada ao modelo de dom�nio.

[Domain Driven Design](http://en.wikipedia.org/wiki/Domain-driven_design) � um assunto muito extenso. Esta foi s� uma r�pida abordagem sobre fatores que afetam a comunica��o. Vamos esperar os pr�ximos posts.
