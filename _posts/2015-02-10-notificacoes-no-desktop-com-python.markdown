---
layout: post
title: Notificações no desktop com python
categories: Python
published: true
---

Há quase um ano desde meu último post aqui. Resolvei ressuscitar o blog e comecei por mudar o layout e o gerenciador de conteúdo. De agora em
diante vou começar a usar o [Jekyll](http://jekyllrb.com/) ao invés do wordpress e espero que essa mudança torne ainda mais fácil a elaboração e publicação de novos posts.

Desde que li [esse post](http://zachholman.com/posts/streaks/) do Zach Holman fiquei empolgado em voltar a escrever com certa assiduidade
(pelo menos uma vez por semana), evitando longos períodos sem postar nada por aqui. E para começar, vou escrever sobre um pacote muito legal
para python, o pynotify, que já venho utilizando há algum tempo para receber avisos e notificações no meu desktop.

O pynotify é um binding para a lib [Notify](https://developer.gnome.org/libnotify/) que oferece basicamente formas de notificar o usuário de
forma não intrusiva, ou seja, não precisando que o usuário faça uma ação para que a notificação apareça.

As notificações geralmente são utilizadas para informar usuários sobre algum evento que ocorre no sistema, como por
exemplo, novas mensagens recebidas em programas de chat, alarmes, novos emails e demais avisos.

### Instalação

Para a instalação utilizaremos o repositório oficial do ubuntu, pois até o momento, a pynotify não está disponível no site do PyPi. Dessa forma,
para instalar a lib para python2:

{% highlight bash %}
apt-get install python-notify2
{% endhighlight %}

e para python3:

{% highlight bash %}
apt-get install python3-notify2  
{% endhighlight %}

### Utilização

A lib é realmente simples. Se rodarmos um dir() no objeto do módulo veremos que ele possui poucos métodos.

{% highlight python %}
>>> import pynotify
>>> dir(pynotify)
  [
    'EXPIRES_DEFAULT', 'EXPIRES_NEVER', 'Notification',
    'URGENCY_CRITICAL', 'URGENCY_LOW', 'URGENCY_NORMAL', 'Urgency',
    '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', '_pynotify',
    'get_app_name', 'get_server_caps', 'get_server_info', 'init', 'is_initted', 'uninit'
  ]
{% endhighlight %}

Para criarmos uma notificação basta iniciar o módulo e criar uma instancia de Notification, passando como parâmetro um título e uma mensagem. Dessa forma:

{% highlight python %}
import pynotify

pynotify.init("example")
notification = pynotify.Notification("Notificando", "Hello Pynotify!!!")
notification.show()

{% endhighlight %}

E o resultado desse exemplo fica assim:

![Notify]({{site.url}}/images/notify.png)

A pynotify disponibiliza algumas constantes que mudam o comportamento das notificações, como as `EXPIRES_DEFAULT` e `EXPIRES_NEVER` que
podem ser utilizadas com o método `set_timeout` da classe `Notification`. Outra detalhe interessante é a possibilidade de setar o nível de
urgência da notificação, utilizando as constantes `URGENCY_CRITICAL`, `URGENCY_LOW` e `URGENCY_NORMAL`.

Abaixo um outro exemplo legal para verificar a disponibilidade de um serviço web. Nele é utilizado a constante `EXPIRES_NEVER`, que diz
para nossa notificação nunca fechar sozinha, somente com a ação do usuário, no caso com um clique dele.

{% highlight python %}
#!/usr/bin/env python
#-*- coding: utf-8 -*-
import pynotify
import urllib
import time

pynotify.init("Notifier")
notification = pynotify.Notification("Serviço indisponível")
notification.set_timeout(pynotify.EXPIRES_NEVER)
while(True):
    try:
        areia = urllib.urlopen("http://www.exemplo.com")
        if areia.code != 200:
            notification.show()
    except IOError, e:
        notification.show()
    time.sleep(60)


{% endhighlight %}

Pynotify é uma lib bem simples e muito útil para automatizar tarefas em ambiente Linux. Existem outras configurações possíveis, como por
exemplo, incluir ícones e outros dados.

Não há uma documentação oficial do módulo, mas tudo pode ser descoberto inspecionando as classes da lib utilizando o bom e velho método `dir`
do python.
