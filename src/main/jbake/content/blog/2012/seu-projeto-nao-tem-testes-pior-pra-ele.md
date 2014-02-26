status=published
date=2012-05-25
tags=blog
type=post
title=Seu projeto n�o tem testes? Pior pra ele
~~~~~~
Ol� pessoal! Esse � o meu segundo post aqui no blog do T� Safo! e desta vez vou falar sobre testes e TDD que � um tema ainda pouco discutido pela regi�o.

Bem, eu vejo em muitos lugares, inclusive em ger�ncias de projetos por ai que uma tarefa � dividida nos seguintes est�gios: A Fazer, Fazendo, Testando, Homologa��o e Pronto.

A primeira � quando a funcionalidade ainda est� a espera de ser implementada, a segunda � quando alguma criatura come�a a produzir a tarefa (que no nosso caso, � o c�digo). Ent�o, ap�s ser implementado ele ser� testado para depois ser aceito pelo cliente e pronto, fim de papo.

Sempre que assisto a alguma palestra ou converso com algu�m sobre o que este teste realmente quer dizer, ou�o que � algu�m dedicado a usar o software para saber se a funcionalidade feita est� de acordo com o esperado e/ou funcionando.

Cruzes! Toda vez que escuto isso me d� um frio na espinha, s�rio. Primeiramente, existe uma pessoa dedicada para isso. Segundo, o teste � feito manualmente. Terceiro, o teste � feito DEPOIS que o c�digo � escrito.

�bvio, hehe, o terceiro ponto pareceu muito esquisito. N�o tem como testar a fun��o antes dela ter sido implementada. Quebremos, ent�o, este paradigma.

<!-- more -->

Apresento-lhe os testes automatizados. Voc�, desenvolvedor, escreve um teste que valida algum c�digo em produ��o. Este teste deve rodar automaticamente com uma �nica linha de comando ou um clique de um bot�o e deve sempre passar ap�s ele ser implementado.

Perceba que voc� escrever� 2 vezes mais c�digo (mentira, ser�o 4 vezes mais c�digo). Sim, � verdade, e este � uma das in�meras quebras de paradigmas que voc� precisar� passar.

Imagine que todo o seu c�digo foi testado, todos os testes est�o passando e voc� verifica que todo o software est� funcionando como esperado em segundos! Qualquer desenvolvedor, "testador", analista, quem seja, poder� rodar os testes.

Perceba tamb�m que n�o existe mais um papel separado para o testador, o desenvolvedor j� � o testador do c�digo. O caso � que somente testar o c�digo e faze-lo passar n�o � o suficiente para trazer seguran�a no seu c�digo.

� ai que vem o TDD (Test Driven Development) que significa Desenvolvimento Dirigido a Testes. Nele existem tr�s regras b�sicas:

1. Voc� n�o tem permiss�o de escrever qualquer c�digo de produc�o a menos que seja para fazer um teste passar.

2.�Voc� n�o tem permiss�o de escrever mais nenhum teste que o suficiente para falhar.

3. Voc� n�o tem permiss�o de escrever mais nenhum c�digo de produ��o do que o suficiente par afazer o teste passar.

[ [http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd](http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd) ]

As tr�s regras resultam em algo mais resumido que � o chamado ciclo Red Green Refactor (Vermelho Verde Refatorar). Isso significa que voc� deve primeiro, sempre, escrever um teste que falha (Vermelho) para ent�o escrever c�digo de produ��o que fa�a o teste passar (Verde) e com ele passando, refatore o c�digo para que ele fique limpo e mais f�cil de entender.

Se voc� seguir estas regras, seu c�digo ter� sempre 100% de cobertura e no momento que o cliente pedir uma altera��o em uma funcionalidade, voc� poder� saber onde a altera��o quebrou c�digo em qualquer lugar do projeto!

Voc� n�o ter� mais aquele medo enorme�ao mudar o c�digo, pois voc� saber� exatamente onde modificar para que o software funcione sempre como esperado!

Lembre-se dos princ�pios �geis onde a mudan�a � algo esperado e mudar o mais r�pido poss�vel, com c�digo funcionando, � um dos maiores princ�pios que a agilidade nos traz.

Depois desta introdu��o, eu tentarei mostrar mais tecnicamente como criar testes automatizados e o ciclo do TDD em futuros artigos aqui no T� Safo!, ent�o fique ligado!

Al�m disso, eu tenho um [Lightning Talk](http://call4paperz.com/events/t%C3%A1-safo-conf-lightning-talks) no [T� Safo Conf 2012](http://tasafo.org/conf2012) que mostrarei exatamente como trabalho com TDD no trabalho e rodarei os testes ao vivo para voc�s verem como � maneiro! N�o deixe de votar no meu talk e tamb�m de se inscrever no evento! O tempo est� correndo!
