status=published
date=2012-10-13
tags=blog
type=post
title=Controle de vers�o em banco de dados com migrations
~~~~~~
O desenvolvimento de aplica��es em [tr�s camadas](http://en.wikipedia.org/wiki/Three_layer) praticamente tornou ub�qua a persist�ncia de dados em sistemas gerenciadores de bancos de dados. Durante o desenvolvimento, enquanto altera��es em artefatos de c�digo-fonte geralmente s�o controladas com algum sistema de versionamento, altera��es em bancos de dados quase nunca s�o controladas.

Ao codificar, de tempos em tempos o desenvolvedor disponibiliza altera��es nos arquivos em que est� trabalhando para um reposit�rio. Com artefatos versionados � poss�vel se ter um controle sobre todas as altera��es feitas em um dado arquivo, conferir as diferen�as entre vers�es distintas e at� retornar arquivos � como seu conte�do se encontrava num dado momento no passado. Isso tudo al�m, � claro, de se viabilizar o trabalho concomitante de v�rias pessoas num mesmo projeto.

Num cen�rio t�pico, imagine que um desenvolvedor esteja trabalhando numa dada funcionalidade. Ele codifica, submete altera��es ao reposit�rio, codifica novamente. Ent�o o desenvolvedor percebe que ser� preciso incluir uma nova coluna numa das tabelas no banco de dados. O desenvolvedor ent�o acessa o SGBD e realiza diretamente a adi��o da coluna na tabela.

Perceba que, enquanto um arquivo de c�digo-fonte evolui por altera��es que s�o controladas (i.e., sabe-se quem fez, quando fez, e at� se n�o era necess�ria pode-se sempre voltar facilmente � vers�o anterior), geralmente as altera��es feitas em banco de dados n�o. Por mais met�dico que seja o desenvolvedor com respeito �s altera��es a serem feitas em bancos de dados, no fim das contas sempre h� a necessidade de se informar verbalmente a algu�m sobre a execu��o de tais altera��es. V�-se isso muito claramente especialmente quando h� mais de um ambiente de banco de dados e surgem as perguntas: _Aquela_ altera��o j� foi replicada no outro ambiente?

Resumidamente, pode-se dizer que migrations � uma maneira de realizar altera��es em um banco de dados de forma organizada e controlada. Trata-se de uma t�cnica muito comum no desenvolvimento em ambientes modernos de programa��o, como [Ruby on Rails](http://guides.rubyonrails.org/migrations.html) ou [CakePHP](http://docs.google.com/present/embed?id=d922pns_15cpjjwfgc), por exemplo.

<!-- more -->


## Sobre Migrations


Para se contornar esse cen�rio, algumas solu��es s�o poss�veis, cada qual com suas vantagens e desvantagens. Por exemplo:



Versionar um _full dump_ do banco
    Vantagens:



	
  * pode ser simples para bancos de dados pequenos

	
  * pode ter aux�lio de ferramentas gr�ficas



    Desvantagens:



	
  * ainda necessita de intera��o humana

	
  * dif�cil identificar eventuais erros

	
  * o formato do _dump_ deve ser padronizado

	
  * modelagem feita ainda pensando em minimiza��o de impacto de mudan�as

	
  * dificuldade em replicar ou transferir dados

	
  * migra��o de SGBD muito dificultada

	
  * para grandes bancos de dados, pode ser invi�vel por restri��es de espa�o



Versionar cada altera��o no banco de dados em um arquivo separado
    Vantagens:



	
  * solu��o que um desenvolvedor met�dico talvez adotaria

	
  * pode ter aux�lio de ferramentas gr�ficas



    Desvantagens:



	
  * ainda necessita de intera��o humana

	
  * eventualmente muitos arquivos a versionar

	
  * modelagem feita ainda pensando em minimiza��o de impacto de mudan�as

	
  * dificuldade em replicar ou transferir dados

	
  * migra��o de SGBD muito dificultada



Utilizar [_fixtures_](http://en.wikipedia.org/wiki/Test_fixture) (p.ex., [DBUnit](http://www.dbunit.org))
    Vantagens:



	
  * economia de espa�o e quantidade de arquivos versionados

	
  * pode ter aux�lio de ferramentas gr�ficas



    Desvantagens:



	
  * recurso n�o � pr�prio para esta finalidade

	
  * dificuldade em replicar ou transferir dados



[Migrations](http://www.google.com.br/search?q=db+migrations)
    Vantagens:



	
  * f�cil identificar o estado atual do banco de dados

	
  * manipula��o do banco de dados simplificada e estruturada



    Desvantagens:



	
  * muitos arquivos para versionar

	
  * algumas ferramentas n�o proveem abstra��o do SGBD



Neste artigo mostrarei uma abordagem para uso de migrations para controle de vers�o de banco de dados com Maven, adequado para uso em um ambiente de integra��o cont�nua.


### Ferramentas


Pode-se dizer que o conceito de migrations desenvolveu-se juntamente com a populariza��o do framework Ruby on Rails. Mas tamb�m h� iniciativas para implementar ou portar tais ferramentas em outras linguagens. A t�tulo de refer�ncia, seguem links de algumas solu��es semelhantes implementadas ou que poder�am ser utilizadas em Java:



	
  * [http://migrate4j.sf.net/](http://migrate4j.sf.net/)

	
  * [http://code.google.com/p/dbmigrate/](http://code.google.com/p/dbmigrate/)

	
  * [http://autopatch.sf.net/](http://autopatch.sf.net/)

	
  * [http://guilhermechapiewski.github.com/simple-db-migrate/](http://guilhermechapiewski.github.com/simple-db-migrate/)

	
  * [http://www.liquibase.org/](http://www.liquibase.org/)

	
  * [http://www.jroller.com/obie/entry/migrator_activerecord_migrations_in_java](http://www.jroller.com/obie/entry/migrator_activerecord_migrations_in_java)

	
  * [http://code.google.com/p/c5-db-migration/](http://code.google.com/p/c5-db-migration/)


Este guia apresenta uma abordagem voltada � ferramenta [Carbon 5](http://code.google.com/p/c5-db-migration/).


### Afinal, o que s�o migrations?


De uma maneira simplificada, a t�cnica de migrations � implementada a partir de:



	
  1. um conjunto de representa��es das altera��es feitas no banco de dados;

	
  2. um registro informando qual a �ltima altera��o aplicada;

	
  3. um opera��o para avan�o e outra para retrocesso de vers�o.




#### Conjunto de representa��es das altera��es feitas no banco de dados


O conjunto de representa��es de altera��es a serem feitas no banco de dados pode ser simplesmente uma rela��o de arquivos .sql. Esta rela��o precisa estar ordenada, ou seja, deve ser poss�vel identificar qual a primeira a ser aplicada, qual a segunda e assim por diante. Isso � importante para que seja poss�vel aplicar as altera��es sequencialmente de forma consistente.

Implementadas como arquivos, a ordena��o das altera��es pode ser conseguida, p.ex., com um padr�o de nomenclatura de arquivos. Por exemplo, um prefixo num�rico sequencial cumpre perfeitamente este papel.



	
  1. 00001_criar_tabela_usuarios.sql

	
  2. 00002_popular_tabela_usuarios.sql

	
  3. 00003_incluir_coluna_dta_nascimento.sql

	
  4. 00004_definir_usuario_administrador.sql

	
  5. 00005_criar_tabela_perfis_usuario.sql


V�-se que a maioria das ferramentas de migrations utiliza um padr�o de timestamp, tipo yyyyMMhhmmss como prefixo que prov� sequenciamento, identifica��o �nica al�m de n�o ter limita��o quanto � quantidade m�xima de arquivos a serem utilizados. Por exemplo:

	
  1. 20101005220000_criar_tabela_usuarios.sql

	
  2. 20101005221701_popular_tabela_usuarios.sql

	
  3. 20101005233529_incluir_coluna_dta_nascimento.sql

	
  4. 20101006030817_definir_usuario_administrador.sql

	
  5. 20101006031154_criar_tabela_perfis_usuario.sql


Utilizar timestamp como prefixo ainda permite identificar mais facilmente o momento em que o migration foi criado. No caso acima, �s 22:00 em ponto do dia 5 de outubro de 2010, o desenvolvedor gerou o migration respons�vel pela cria��o de uma tabela de usu�rios no banco. �s 22:17 ele decidiu popular a tabela inserindo alguns valores predefinidos. Ap�s passar pouco mais de uma hora implementando (�s 23:35), o desenvolvedor percebeu que seria necess�rio criar mais uma coluna com a data de nascimento na tabela de usu�rios. E assim por diante.

O conte�do dos arquivos .sql s�o, como de se esperar, as opera��es SQL que realizam efetivamente as altera��es em quest�o. Pelo que se depreende ainda no exemplo acima, o primeiro migration (20101005220000_criar_tabela_usuarios.sql) provavelmente deve ter uma instru��o SQL tipo `CREATE TABLE usuarios ...`.

Estamos assumindo que cada migration � implementado diretamente com o dialeto SQL do SGBD correspondente (caso do Carbon 5). Por�m, cabe ressaltar que as ferramentas de migrations mais comuns tamb�m fazem abstra��o do SGBD utilizado, representando defini��es relativas a banco de dados numa representa��o em geral mais simples e uniformizada, como o [YAML](http://pt.wikipedia.org/wiki/YAML), por exemplo. Sem depender
dos dialetos SQL dos diferentes SGBDs, eventuais necessidades de se trocar de um SGBD por outro se tornam tarefas bem mais simples.


#### Registro informando qual a �ltima altera��o aplicada


Apenas manter o conjunto de altera��es realizadas no banco de dados n�o ajuda muito se n�o se sabe quais delas est�o, de fato, aplicadas ao banco de dados. Num ambiente descontrolado essa informa��o acaba ficando na cabe�a do DBA. Sem registro, muitas vezes para obter essa informa��o acaba sendo necess�rio conhecer tudo o que tem sido feito no banco, verificando-o manualmente na tentativa de identificar se seu estado condiz com o desejado. Incertezas advindas desse cen�rio levam a frequentes limpezas no banco de dados. (Quem nunca teve de parar seu desenvolvimento por um instante porque algu�m precisa zerar o banco?)

As ferramentas de migrations geralmente gerenciam a informa��o das altera��es j� aplicadas ao banco de dados tamb�m como uma tabela no pr�prio banco de dados. Todo o controle das altera��es aplicada � feito automaticamente pela ferramenta de migrations, de forma que esse acompanhamento � feito de forma transparente. No caso da ferramenta Carbon 5, a tabela de controle padr�o chama-se `schema_version`.


#### Uma opera��o para avan�o e outra para retrocesso de vers�o


� comum as ferramentas de migratios disponibilizarem ao menos duas a��es: uma que avance a vers�o do banco de dados para o migration imediatamente posterior na sequ�ncia (chamada de **up**) e outra que retrocede a vers�o para o migration imediatamente anterior ao atualmente aplicado (chamada de **down**).

Al�m dessas, � comum haver outras a��es de conveni�ncia derivadas destas, como por exemplo uma que retorne o banco de dados � primeira vers�o e outra que aplique todos os migrations pendentes desde o �ltimo aplicado. Outras a��es dispon�veis s�o combina��es dessas b�sicas. Falaremos com mais detalhes
sobre essas a��es ao abordar o Carbon 5 como plugin do Maven mais � frente.


## Migrations em Java via Maven


Como vimos, existem algumas ferramentas de migrations para Java. Para os fins deste guia, optou-se por abordar o [Carbon 5](http://code.google.com/p/c5-db-migration/) essencialmente porque ela j� est� dispon�vel como [plugin para o Maven](http://code.google.com/p/c5-db-migration/wiki/MavenPlugin), o que facilita seu uso num ambiente de integra��o cont�nua.


### Como configurar


Conforme [descrito no site](http://code.google.com/p/c5-db-migration/wiki/MavenPlugin), configurar o suporte ao Carbon 5 em um projeto Maven � bastante simples. S�o apenas 2 passos no arquivo `pom.xml`:



	
  1. Informar o reposit�rio onde se encontra o plugin:

    
    ...
    <pluginRepositories>
      ...
      <pluginRepository>
        <id>c5-public-repository</id>
        <url><a href="http://mvn.carbonfive.com/public" target="_blank">http://mvn.carbonfive.com/public</a></url>
      </pluginRepository>
    </pluginRepositories>




	
  2. Adicionar o plugin ao build, com a devida configura��o do banco de dados (neste caso, um banco MySQL)

    
    ...
    <build>
       ...
      <plugin>
        <groupId>com.carbonfive.db-support</groupId>
        <artifactId>db-migration-maven-plugin</artifactId>
        <version>RELEASE</version>
        <configuration>
          <url>jdbc:mysql://servidor/meubanco</url>
          <username>admin</username>
          <password>53nh4</password>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.6</version>
          </dependency>
        </dependencies>
      </plugin>
    </build>





Este exemplo de configura��o foi feito para um banco de dados MySQL chamado `meubanco`, hospedado numa m�quina chamada `servidor`, com usu�rio `admin` e senha `53nh4`. H� ainda outras op��es dispon�veis. J� para mais detalhes da configura��o do Maven (por exemplo, como esconder a configura��o de usu�rio e senha no pom), [consulte seu manual](http://maven.apache.org/pom.html) ou pe�a
aux�lio ao gestor de configura��o de seu projeto.

A prop�sito, mostramos neste exemplo uma configura��o para uma banco MySQL, mas o Carbon 5 tem suporte para diversos SGBDs com conex�o via JDBC, entre eles: MYSQL, POSTGRESQL, SQL_SERVER, HSQL, H2, DB2 e ORACLE.


### Como utilizar


Uma vez configurado o suporte ao Carbon 5 em seu projeto, [estar�o dispon�veis](http://code.google.com/p/c5-db-migration/wiki/MavenPlugin#Maven_Plugin_Goal_Reference) os seguintes _goals_ no Maven:



`db-migration:migrate`
    Aplica todos os migrations ainda pendentes
`db-migration:drop`
    Destroi a base de dados
`db-migration:reset`
    Destroi a base de dados e a reconstroi aplicando todos os migrations ainda pendentes (combina��o dos anteriores)
`db-migration:create`
    Cria o esquema do banco de dados se ele ainda n�o existir (caso contr�rio, falha o build)
`db-migration:validate`
    Informa se a base est� atualizada ou informa quais migrations ainda n�o foram aplicados
Destes, o `db-migration:migrate` sem d�vida � o mais importante. Como dito, este _goal_ atualiza o banco de dados aplicando todos os migrations pendentes.

Repare que a vers�o atual Carbon 5 n�o disp�e de _goals_ implementando as a��es `up` e `down` para aplicar ou desaplicar apenas um migration por vez, mas apenas os de voltar o banco � situa��o inicial e aplicar todos os migrations.


#### Cen�rio concreto


Suponha que queiramos come�ar com um novo banco de dados j� configurado. Se tudo estiver funcioando corretamente, podemos come�ar a escrever nossos migrations.

Imagine que queremos criar uma tabela de usu�rios tal como no exemplo ilustrativo do come�o deste guia. Para tal, podemos come�ar a escrever nossos migrations. O local padr�o onde o Carbon 5 procura os migrations � na subpasta `src/main/db/migrations` na raiz de um projeto Maven (lembrando que isto tamb�m pode ser configurado). Para um migration que crie uma tabela de usu�rios, basta criar um arquivo de texto plano contendo a instru��o SQL correspondente. Por exemplo, poderia ser:

    
    CREATE TABLE usuarios (
    	id		integer not null primary key auto_increment,
    	login		varchar(16) not null,
    	password	varchar(40) not null,
    	fullname	varchar(60) not null,
    );


Criado este arquivo, podemos salv�-lo na pasta de migrations padr�o em `src/main/db/migrations` dentro de nosso projeto Maven. Como j� mencionado, o padr�o de nomes envolve um prefixo yyyyMMhhmmss. Enquanto escrevo este trecho deste guia, agora s�o 18:10 do dia 06 de outubro. Podemos salvar nosso arquivo com uma representa��o timestamp deste hor�rio. Portanto, o caminho completo de nosso migration dentro do projeto Maven ser� `/src/main/db/migrations/20101006181000_criar_tabela_usuarios.sql`.

Muito chato salvar arquivos com esse prefixo de timestamp! N�o falamos, mas para auxiliar nisso, voc� poderia ter simplesmente executado o _goal_ `db-migration:new -Dname=criar_tabela_usuarios`. O par�metro `name` � opcional e n�o precisa ser informado, mas � sempre bom para identificar mais claramente o que o migration faz. Este � um _goal_ auxiliar que apenas j� cria um arquivo .sql vazio devidamente nomeado no local padr�o.

Seguindo em frente. Uma vez salvo o arquivo, podemos utilizar a ferramenta para confirmar o estado do banco com `db-migration:validate`. Ao executar um build assim neste momento, obteremos a seguinte sa�da:

    
    $ mvn db-migration:validate
    [INFO] Scanning for projects...
    [INFO] 