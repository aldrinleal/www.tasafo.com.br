status=published
date=2013-10-01
tags=blog
type=post
title=Verdades inconvenientes sobre agilidade
~~~~~~
O desenvolvimento �gil vem ganhando for�a nos �ltimos anos, tornando-se uma febre. Pap�is como Scrum Master, est�o cada vez mais recorrentes nos curr�culos de profissionais de TI, muitas vezes, em tentativas oportunistas de aproveitar a febre do momento. Isso n�o � errado, mas tem um lado muito ruim, o da n�o compreens�o do que � agilidade. Eu, particularmente n�o gosto de usar o termo agilidade, pois pra mim, s� existe um meio de se desenvolver software, e � com desenvolvimento �gil. Mas algumas vezes, � necess�rio "dar nome aos bois".

**Disclaimer**

Esse post n�o reflete a opini�o do T� Safo e � de total responsabilidade do autor �:P

**Scrum n�o � �gil**

Scrum n�o � metodologia �gil. Scrum � um processo para gest�o e controle. N�o � a toa que gerentes adoram. E como todo _framework_ que se preze, possui alguns padr�es embutidos em si. Ele implementa alguns conceitos �geis, mas n�o � porque possui um processo interativo, que ser� �gil.

N�o sou contra o Scrum. Na verdade acho uma ferramenta fant�stica para equipes que est�o come�ando no desenvolvimento �gil. E, uma evolu��o disso seria abandonar o Scrum � medida que a equipe evolui. Equipes mais experientes em agilidade n�o ir�o tolerar o Scrum por muito tempo. � prefer�vel seguir os princ�pios e valores �geis do que um processo _by the book_.

Tamb�m n�o curto pap�is como Scrum Master e Product Owner. Se existe a grande necessidade de um Scrum Master, talvez a gest�o da empresa n�o seja t�o boa, pois � necess�rio um papel para proteger o time da burocracia. O PO � um papel, que sinceramente n�o sei pra que serve. O stakeholder � mais importante, pois � este quem define o que valor ou n�o. O que ocorre � que, muitas vezes, o stakeholder est� ausente. Agilidade � sobre valor. Se n�o existe stakeholder, n�o existe valor, logo n�o existe agilidade.

**N�o existe agilidade sem testes automatizados**

A verdade � dura. A verdade � �nica. O sistema � bin�rio. Zero ou um. Vivo ou morto. Agilidade � sobre proporcionar _feedbacks_ r�pidos. N�o � poss�vel fazer isso sem uma boa cobertura de testes **automatizados**. Novamente: **automatizados**. De novo: **automatizados**. E ainda n�o estou falando de TDD (que por sinal, esse sim, � um m�todo �gil). Estou falando de receber **feedbacks** r�pidos sobre mudan�as efetuadas no c�digo.

Algu�m pode dizer: _posso proporcionar isso sem testes automatizados. Sou foda_. Talvez, com uma base de c�digo pequena e simples, seja poss�vel. Mas lembrem-se que software � um sistema vivo (de acordo com o dogma m�ximo da ci�ncia moderna, a teoria da evolu��o), ele muda e evolui com o tempo. A tend�ncia � que ele se torne complexo. A n�o ser que ele s� possua CRUDs, nesse caso nem � necess�rio um desenvolvedor.

Em 1981, Barry Boehm, em seu livro Software Engineering Economics, sugeriu que o custo de mudan�as em um projeto de software cresce exponencialmente durante o desenvolvimento. Logo,�seria melhor fazer a maioria das altera��es necess�rias logo no come�o de um projeto, que seriam as fases de levantamento de requisitos e an�lise. Isso � m�todo tradicional, conhecido como **cascata**.

O Extreme Programming�nos d� outra alternativa. Podemos manter esse custo baixo e constante durante o ciclo de vida do software. Esse � um dos grandes benef�cios do TDD. Ele nos proporciona um bom _design_ e de cara nos d� uma cobertura de testes **automatizados**. Ganhamos uma facilidade na compreens�o do c�digo, seguran�a para modific�-lo e uma documenta��o execut�vel. N�o quero mais nada na minha vida.

**A agilidade se desenvolve em torno de indiv�duos motivados.**

N�o consigo descrever muito bem o que � **Management 3.0**. Jurgen Appelo fez, nada mais, que pegar v�rias id�ias e conceitos bons que existiam soltos por a� e escreveu um livro excelente. Esse modelo de gest�o que ele criou, chamada de **Gest�o 3.0** ou **Gest�o �gil**, trabalha com seis vis�es: **energizar pessoas, empoderar times, alinhar restri��es, desenvolver compet�ncias, crescer a estrutura, melhorar tudo**.

Na minha n�o t�o humilde opini�o, este livro deveria ser leitura obrigat�ria para quem quiser adotar agilidade em sua organiza��o. E se voc� tem pregui�a de ler, existe um curso oficial sobre o tema, oferecido pela [Adaptworks](http://www.adaptworks.com.br/treinamento/Management-3-0). Enfim, por que citei isso? Porque agilidade � sobre pessoas. Se n�o existe um desenvolvimento de pessoas, se n�o existe respeito, se n�o existe confian�a, n�o existe agilidade.

Quando tem ser humano no meio, o bicho pega. N�o � exato. N�o existem verdades. O sistema n�o � bin�rio. Quando o fator humano � posto em segundo plano, n�o h� como adotar _agile_. Horas extras, trabalhos em feriados, pontos eletr�nicos, tudo isso �, na verdade, uma tremenda falta de bom senso e, porque n�o dizer, falta de **respeito**. Empresas muito engessadas, departamentais, burocr�ticas em excesso, desorganizadas, com alta rotatividade de funcion�rios ir�o falhar miseravelmente e ir�o dizer que _agile_ n�o funciona. E isso est� acontecendo neste momento.

**tl;tr**

Muitos podem dizer que o importante � entregar software, seja �gil ou n�o. N�o acredito nisso. N�o devemos entregar software a custo do sacrif�cio de outros fatores, como motiva��o, qualidade, satisfa��o pelo seu trabalho. No fim das contas, metodologia n�o desenvolve software. Engenheiros desenvolvem software. **A agilidade � inerente ao bom desenvolvedor**.

A qualidade t�cnica sobrepuja qualquer dogma. Desenvolvedores, talvez n�o precisem de controle, mas sim de liberdade, para criar, para explorar, para desenvolver sua arte. Muitas empresas j� perceberam isso e est�o no caminho certo.
