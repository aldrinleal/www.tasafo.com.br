status=published
date=2013-08-23
tags=blog
type=post
title=Integrando backbone.js e devise
~~~~~~
Imagine o seguinte cen�rio: queremos implementar uma autentica��o de usu�rio em um sistema rails que utiliza o _devise_. No front-end, estamos utilizando o _backbone.js_. N�o � uma tarefa das mais complicadas, mas que requer alguns artif�cios e um bom conhecimento da api do _devise_.




[Devise](https://github.com/plataformatec/devise) � uma gem desenvolvida pela galera da [plataformatec](http://plataformatec.com.br/), que nos proporciona uma api completa e flex�vel para solu��es de autentica��o em rails. Sua api j� abstr�i para o desenvolvedor funcionalidades como encripta��o senha,�Omniauth, confirma��o por email, esqueceu sua senha, bloqueio de conta, entre outras coisas.




O [backbone.js](http://backbonejs.org/)�� uma biblioteca javascript para cria��o de web apps. Ele nos auxilia a trabalhar em aplica��es javascript de maneira desacoplada do DOM. Com estruturas de **model**, **collections**, **views** e **templates**, nos proporciona uma melhor organiza��o e modulariza��o do c�digo javascript, facilitando a compreens�o e a manuten��o. Chega de javascript macarr�nico. Backbone trabalha nativamente com REST, logo, casa muito bem com aplica��es rails, restful.




<!-- more -->




**M�o na massa**




Como vamos usar o backbone para montar a interface com o usu�rio, n�o iremos utilizar os helpers do rails e do devise para montar os formul�rios. Em um projeto rails j� pr�-configurado com o devise, vamos instalar o backbone.js. Como sou pregui�oso, vou usar a gem [banckone-on-rails](https://github.com/meleyal/backbone-on-rails).**<!-- more -->**




Criei a view user_login.js para a tela como formul�rio de login:



[code language="javascript"]
BackDevise.Views.UserLogin = Backbone.View.extend({
  template: JST["users/login"],

  events: {
   "submit #user_login" : "auth"
  },

  initialize: function(){
    this.user = new BackDevise.Models.User();
    this.render();
  },

  auth: function(e){
    e.preventDefault();
    var $form = $(e.target);
    var self = this;

    $.ajax({
      url: "/users/sign_in.json",
      data: $form.serialize(),
      dataType: "json",
      type: "post",
      error: function(response){
        var result = $.parseJSON(response.responseText);
        $(".box-content").prepend("<div class="alert alert-error">"+ result['error'] +"</div>");
      },
      success: function(res){
        self.user.set(res);
        new BackDevise.Views.Dashboard({user: self.user});
      }
   })
 },

 render: function(){
   $(this.el).html(this.template());
   $("#main").html(this.el);
 }
})

[/code]

Abaixo, a view do cadastro de usu�rio:

[code language="javascript"]
BackDevise.Views.UserRegistration = Backbone.View.extend({
  template: JST["users/signup"],

  events: {
    "submit #user_registration" : "signup"
  },

  initialize: function(){
    this.user = new BackDevise.Models.User();
    this.render();
  },

  signup: function(e){
    e.preventDefault();
    var $form = $(e.target);
    var self = this;

    $.ajax({
      url: "/users.json",
      data: $form.serialize(),
      dataType: "json",
      type: "post",
      error: function(response){
        var result = $.parseJSON(response.responseText);

        _(result.errors).each(function(errors,field) {
          var $controlGroup = $('.user_'+field);

          $('.user_'+field).addClass('error');
          _(errors).each(function(error, i) {
            $controlGroup.children(".controls").find("span.help-inline").remove();
            $controlGroup.children(".controls").append('<span class="help-inline">'+ error +'</span>');
          });
      });
    },
    success: function(res){
      self.user.set(res);
      window.location = "/";
    }
  })
 },

  render: function(){
    $(this.el).html(this.template());
  }
})
[/code]

Como pode ser notado, n�o utilizei os m�todos do _backbone_ para fazer as requisi��es _ajax_. Ao inv�s disso, usei **jquery** puro, pois assim evitei utilizar mais uma depend�ncia no projeto para mapear os atributos do formul�rio para o _model_ _user_. No entanto, � recomend�vel utilizar os m�todos do _backbone_, como [model.save()](http://backbonejs.org/#Model-save), pois deixa o c�digo bem mais sem�ntico.

Pulo do gato

A partir da vers�o **2.2.0**, o _devise_ n�o aceita mais, por _default_, solicita��es no formato **json**. Logo, � necess�rio setar o m�todo **respond_to** no _controller_ do _devise_. Para isso, adicionamos no **application.rb** o seguinte c�digo:

[code language="ruby"]
  config.to_prepare do
    DeviseController.respond_to :html, :json
  end

[/code]

Segue o link para o sistema: http://enigmatic-reaches-7294.herokuapp.com/

C�digo no github: https://github.com/paulociecomp/backbone-devise
