status=published
date=2009-05-14
tags=blog
type=post
title=Se voc� n�o testa, voc� n�o � �gil!
~~~~~~
O colega Robson Pelegrini [reportou na lista [scrum-brasil]](http://br.groups.yahoo.com/group/scrum-brasil/message/3348) uma situa��o que � comum, principalmente em equipes que est�o iniciando no desenvolvimento �gil de software e que (com a devida autoriza��o) transcrevo abaixo:


> Pessoal,

Gostaria de saber como voc�s tratam a quest�o dos bugs que surgem dentro do SPRINT, por exemplo:

> 
> 
	
>   * Criam um item no SPRINT BACKLOG, �corre��o de bugs�
> 
	
>   * Bugs � responsabilidade do time concertar, n�o podendo esse impactar na entrega do SPRINT
> 

Acredito que a partir da 1� entrega feito ao PO, temos o que podemos chamar de �legado�, e ent�o come�am a surgir bugs e mudan�as de requisitos e funcionalidades que geralmente afetam o planejamento feito para o pr�ximo SPRINT.

- Isso costuma ocorrer com voc�s ? Como voc�s lidam com essas situa��es ?


Necess�rio pontuar algumas coisas num cen�rio como este.� Vamos a elas.

**O QUE VEM A SER UM "BUG" DE SOFTWARE?![software-bug-03](http://tasafo.files.wordpress.com/2009/05/software-bug-03.jpg?w=150)**

Como seres humanos, todos estamos sujeitos a erros.� Assim, mais ainda quando estamos lidando com um produto em desenvolvimento, ou seja, que est� sendo construindo.� Muitos projetos de software mant�m dois ramos do produto --um est�vel e um em desenvolvimento-- justamente para diferir a quantidade de bugs em potencial que podem estar contidos no produto.

Se por um lado tudo isso � verdade, por outro, quando tratamos de desenvolvimento �gil de software, deve-se partir da premissa de que a cada itera��o no ciclo de desenvolvimento um item de valor deve ser entregue ao cliente.� S�o os releases curtos.

Isto posto, cabe nos perguntarmos: afinal o que � um "bug" de software?

<!-- more -->Apesar de geralmente chamarmos a qualquer problema com software de "bug", no livro _"Qualidade de Software"_, [Koscianski e Soares](http://www.novateceditora.com.br/livros/qualidadesoftware2/) fazem uma boa diferencia��o destes em DEFEITOS e FALHAS.� Um _defeito_ costuma ser uma imperfei��o do software.� Uma situa��o que deveria ser considerada mas n�o o �.� De uma maneira simples, **defeituoso � aquilo que simplesmente n�o funciona como deveria**.� J� uma _falha_ � a manifesta��o de um problema.� Mesmo que contenha defeitos, um software pode funcionar sem apresentar necessariamente uma falha.� Enquanto defeito � uma situa��o n�o prevista pelo software, uma falha geralmente se apresenta por problemas no tratamento de erros do software.

**DEFINI��O DE PRONTO**

Pois bem. A quest�o ent�o passa a ser como identificar e isolar defeitos do produto na busca por corrig�-los, evit�-los ou trat�-los adequadamente, sempre de forma a atender �s necessidades do cliente.

![checklist](http://tasafo.files.wordpress.com/2009/05/checklist2.jpg?w=150)Voltando ao cen�rio do come�o do post.� Se a equipe deu como conclu�do um item do _backlog_ em um sprint anterior e, algum tempo depois percebeu-se que tal item est� defeituoso (ou seja, uma dada hist�ria sobre aquele item n�o funciona como esperado), vem a pergunta: **ser� que o item estava de fato pronto?** Ou melhor**: como se sabe se um item est� de fato pronto?**

A resposta a tal pergunta pode estar relacionada a um conceito essencial mas que pode ser negligenciado em algumas equipes (principalmente as mais inexperientes em metodologias �geis) que � a DEFINI��O DE PRONTO (_Definition of Done_).� Como de se supor, a_ [defini��o de pronto](http://agilesoftwaredevelopment.com/2006/05/definition-of-done)_ deve ser um crit�rio objetivo, inequ�voco e facilmente verific�vel e que possa servir de marco para se considerar uma determinada tarefa, um item ou uma funcionalidade do software como conclu�da.

**TESTES AUTOMATIZADOS**

� comum nas equipes com pouca experi�ncia em desenvolvimento �gil, que o desenvolvedor "entenda" o que deve ser feito ap�s uma orienta��o ou uma conversa com o l�der do projeto ou do cliente.� E ent�o implemente o que entendeu.� E ent�o que execute o sistema para testar o que fez.� Nessa desfavor�vel situa��o, as coisas facilmente saem dos eixos por v�rios motivos:



**O desenvolvedor nunca entende toda a demanda, por mais simples que ela seja.**
    No contexto do desenvolvimento, a pessoa que melhor entende do neg�cio. A especialidade do desenvolvedor s�o as linguagens, as t�cnicas, os algoritmos e aspectos da constru��o do software. A priori, o desenvolvedor n�o deve ter obriga��o de conhecer a fundo toda a l�gica de neg�cio do cliente.� Al�m disso, sem conhecer toda a l�gica do neg�cio, o desenvolvedor pode ter dificuldades em executar o software de forma a disparar certas situa��es espec�ficas e/ou incomuns;
**O desenvolvedor pode estar (e comumente est�) sob press�o.**
    Prazos, custos e produtividade s�o algumas das cobran�as �s quais o desenvolvedor est� sujeito. N�o se deve estranhar que tais press�es resultem em alguma pressa ou ansiedade. Em equipes muito heterog�neas que n�o adote algumas padroniza��es ou revis�es de c�digo, isto pode resultar em grande risco � qualidade do produto;
**O desenvolvedor busca naturalmente pelo "caminho feliz".**
    Basicamente, buscando reduzir tempo dispendido no uso para averigua��o do sistema, conforme vai avan�ando em suas atividades, � natural que desenvolvedor limite-se a executar os cen�rios que sabe com que o sistema funcionar�. Testes que o desenvolvedor executa no sistema sobre aquilo que desenvolveu tendem a ser viciados e podem n�o ser muito confi�veis. A preocupa��o acaba sendo "ver o software funcionar" e n�o propriamente "testar o software";
O ponto chave aqui � que o desenvolvedor nunca � a melhor pessoa para testar o que ele mesmo escreveu.� Para distanciar o elemento humano da atividade de teste � que se recomenda fortemente que seus testes de software sejam realizados de forma automatizada.� A escrita de testes ([unit�rios](http://pt.wikipedia.org/wiki/Teste_unit�rio), [de integra��o](http://thinkabouttests.blogspot.com/2008/02/teste-de-integrao.html), [de aceita��o](http://gc.blog.br/2007/09/26/voce-automatiza-seus-testes-de-aceitacao/)... enfim, todos os poss�veis) e sua execu��o de forma automatizada s�o um excelente ponto de partida para o estabelecimento de defini��o de pronto: um item ou tarefa est� conclu�do se passou no teste correspondente.

Al�m do que, com a escrita de testes automatizados, voc� tamb�m mant�m registro documental das l�gicas de neg�cio de sua aplica��o, refor�ando o entendimento do neg�cio e facilitando a integra��o de novos membros de trabalho � equipe.

Assim, se voc� n�o quiser terminar com um sistema de [bugtracking](http://en.wikipedia.org/wiki/Bug_tracking_system) cheio de itens "teoricamente prontos" mas repletos de defeitos, teste sempre seus software de forma automatizada.� Testes automatizados s�o imprescind�veis, de forma que...


> **SE VOC� N�O TESTA, VOC� N�O � �GIL!**

**
**





* * *



Testes de software, ferramentas, relatos de experi�ncias com Scrum e muito mais sobre desenvolvimento �gil estar�o nos pr�ximos posts.� Acompanhe os [feeds do T� Safo](http://tasafo.wordpress.com/feed/) e n�o perca!

Comentem!� Participem!� Nos vemos no [Academic Meeting!](http://tasafo.wordpress.com/2009/04/30/evento-visao-agil-academic-meeting-2009/) At� a pr�xima!****


