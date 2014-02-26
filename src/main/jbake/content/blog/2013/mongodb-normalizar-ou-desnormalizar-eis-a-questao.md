status=published
date=2013-09-05
tags=blog
type=post
title=MongoDB - Normalizar ou Desnormalizar, eis a quest�o
~~~~~~
No MongoDB, dados utilizados por m�ltiplos documentos podem ser embutidos (_embedded_) ou referenciados. Quando embutimos um documento em outro, temos dados desnormalizados. Quando referenciamos documentos, temos dados normalizados. Mas quando devemos escolher um ou outro? E qual os seus efeitos no design do banco de dados?

A desnormaliza��o pode gerar dados inconsistentes. Imagine que em um documento **food**, voc� queira mudar o nome de **ma��** para **p�ra**. �Voc� modifica o nome de um documento, mas a aplica��o d� _crash�_antes de atualizar os demais documentos. Voc� ter� dois diferentes valores para frutas em seu banco de dados.

[code language="javascript"]
Documento Food:

{
  _id: x,
  fruit: pear
}

Cole��o Meals:

[
  {
    _id: y,
    fruit: apple
  },
  {
    _id: z,
    fruit: apple
  }
]
[/code]

Para a maioria das aplica��es, inconsist�ncia pode ser ruim, mas para algumas, um breve per�odo de inconsist�ncia pode ser ok. �Se a aplica��o n�o deve possuir inconsist�ncia, a normaliza��o � o mais aconselh�vel. No entanto, normalizar significa uma query extra todo tempo que for necess�rio fazer uma busca por uma fruta. Se sua aplica��o precisa de alta performance, voc� ter� que conviver com dados inconsistentes.

Muitas aplica��es usam mais leitura do que escrita. Se determinados documentos possuem dados referenciados que mudam com uma frequ�ncia baixa, por exemplo, datas de nascimento, endere�os, logs, esse pode ser um bom argumento para o uso da desnormaliza��o. Voc� pode estar pagando um pre�o alto por cada leitura na base de dados para garantir consist�ncia de dados que mudam raramente.

A normaliza��o pode garantir consist�ncia e nos d� outras facilidades. Quando estamos utilizando ferramentas�ODM (Object-Document-Mapper), como [Mongoid](http://mongoid.org/en/mongoid/index.html), o c�digo fica bem mais simples, j� que a desnormaliza��o pode nos trazer uma certa complexidade no c�digo e na administra��o do banco. Para algumas aplica��es seria bem complicado de conciliar insconsist�ncia de dados.

Para sistemas que necessitam da mais alta performance poss�vel, como sistemas de tempo real, a desnormaliza��o � mais indicada. Nesse tipo de aplica��o n�o h� muito o que se pensar sobre isso. Real-time apps, normalmente, devem ser desnormalizados o tanto quanto poss�vel.
