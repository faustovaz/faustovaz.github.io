---
layout: post
status: publish
published: true
title: Breve introdução ao ecossistema python
author:
  display_name: faustovaz
  login: faustovaz
  email: faustovaz@gmail.com
  url: ''
author_login: faustovaz
author_email: faustovaz@gmail.com
wordpress_id: 313
wordpress_url: http://www.faustovaz.com/blog/?p=313
date: '2014-02-18 02:17:32 -0300'
date_gmt: '2014-02-18 05:17:32 -0300'
categories:
- python
tags: []
comments:
- id: 150
  author: Fernando Geraldo Mantoan
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100001820390284
  date: '2014-02-18 14:55:09 -0300'
  date_gmt: '2014-02-18 17:55:09 -0300'
  content: Apavorou Faustinho, ótimo artigo.
- id: 151
  author: Jan Palach
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100006915254617
  date: '2014-02-18 15:11:20 -0300'
  date_gmt: '2014-02-18 18:11:20 -0300'
  content: "      Gostei muito do seu post. Sou usuário de Python desde a versão 2.3
    e este post trás um overview bacana. Lá na parte de virtualenv, vale um comentário
    de que a partir da versão 3.3.3(acho), já existe um virtualizador embutido chamado
    pyvenv. E na parte de implementações existe o Stackless Python http://www.stackless.com/.
    \ Vale ressaltar também, que quando se deseja fazer paralelismo massivo usando
    threads as implementações CPython, PyPy são afetadas por questões referentes ao
    GIL - Global Interpreter Lock que permite executar uma thread(CPU-Bound) por vez
    por interpretador, o que impede o 100% de aproveitamento em ambientes multicore
    ou multiprocessor. Mas com as implementações IronPython e Jython isso não ocorre,
    pois tiram proveito do ambiente de execução destas VMs."
- id: 152
  author: Marcos Castro
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100004030372353
  date: '2014-02-18 16:25:13 -0300'
  date_gmt: '2014-02-18 19:25:13 -0300'
  content: "Ótimo artigo"
- id: 153
  author: Eric Hideki
  author_email: ''
  author_url: http://facebook.com/profile.php?id=1771225884
  date: '2014-02-18 20:26:01 -0300'
  date_gmt: '2014-02-18 23:26:01 -0300'
  content: Muito bom artigo, parabéns! E obrigado por citar o meu blog :D
- id: 154
  author: Bruno Pinna
  author_email: ''
  author_url: http://facebook.com/profile.php?id=1713414282
  date: '2014-02-18 21:55:06 -0300'
  date_gmt: '2014-02-19 00:55:06 -0300'
  content: 'parabéns excelente artigo, apavorou '
- id: 155
  author: Elton Hadriel Paula
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100002831256364
  date: '2014-02-18 23:46:15 -0300'
  date_gmt: '2014-02-19 02:46:15 -0300'
  content: Muito bom o artigo, parabéns
- id: 157
  author: Adriano Pinheiro
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100001157135223
  date: '2014-02-19 00:24:42 -0300'
  date_gmt: '2014-02-19 03:24:42 -0300'
  content: |
    Show o artigo. Expert em Python... ai sim. Parabéns cara... !
- id: 158
  author: Guilherme Louro
  author_email: ''
  author_url: http://facebook.com/profile.php?id=100000507957621
  date: '2014-02-19 00:40:07 -0300'
  date_gmt: '2014-02-19 03:40:07 -0300'
  content: 'Muito bom! '
---

Já faz mais de um ano que tomei a decisão de aprender de vez python. Vi algumas coisas de python durante a faculdade e sempre ouvia alguns
professores mencionar a linguagem com certo gosto pessoal. Porém nunca havia tomado a decisão de investigar a tecnologia e começar a usa-la
como ferramenta no meu dia-a-dia.

![Python]({{site.url}}/images/python_logo_without_textsvg.png)

Desde que comecei a estudar python, decidi usar a linguagem sempre que fosse conveniente e sempre que eu tivesse a liberdade de escolher
a tecnologia dos trabalhos que adquiria. Também passei a usar python em meus projetos pessoais, testando o que a tecnologia oferece para
aplicativos desktop, aplicativos web e automatização de tarefas. Porém, aprender e usar uma tecnologia não se resume somente a entender os
mecanismos, a sintaxe e os pontos fortes e fracos da linguagem. Envolve também entender todo o ecossistema que envolve a tecnologia, bem
como, a comunidade e quem são os mentores por trás desse sistema.

O objetivo desse post é introduzir, de forma breve, o ecossistema python e auxiliar os amigos que estão interessados em começar com a
tecnologia. Também pretendo descrever os recursos que utilizei, e utilizo, para continuar estudando e aprendendo a linguagem e seu
ecossistema.

Existem muitos outros itens a serem considerados, mas vou destacar somente os abaixo:

### Versões e implementações

Existem duas versões de python que são bem utilizadas: a versão 2.7 e a versão 3+. Há algumas diferenças entre as duas versões, algumas
diferenças bem sutis tanto sintaticamente quanto semanticamente. A comunidade python está trabalhando para portar as bibliotecas e pacotes
disponíveis  na linguagem para a versão 3 e também existe um grande esforço de programadores para portar seus frameworks e bibliotecas.

Apesar da versão 2.7 ser a mais utilizada e normalmente distribuída em muitos sistemas Unix-like por ai, é aconselhável fazer o update e
utilizar a versão 3+. Algumas bibliotecas ainda não estão totalmente adaptadas para a versão 3, mas as mais populares já estão disponíveis
nessa versão. Você pode checar no [Python 3 Wall of super powers](https://python3wos.appspot.com) se o pacote ou framework que você quer utilizar já está adaptado para o python 3. Se você está começando e não precisa de nada tão especifico, vá direto para o python 3.

Em relação as diferentes implementações, existem hoje 4 implementações conhecidas (pelo menos que eu conheço): Cpython, PyPi, Jython e
IronPython.

A CPython (Common Python) é a implementação mais popular, mais conhecida e mais utilizada (é essa versão que normalmente vem com sua
distribuição Linux). Ela também é referência para as outras implementações da linguagem e é a implementação que você encontra para fazer
download no [site](http://www.python.org/) ofícial do python.

O [Jython](http://www.jython.org/) e [IronPython](http://ironpython.net/) são, respectivamente, implementações de python em java e python
para a plataforma Microsoft.net CLR. Já [PyPy](http://pypy.org/) é uma implementação de Python desenvolvida em Python, e segundo o site do
PyPy, roda programas python mais rapidamente que a versão oficial, a CPython.

Por fim, ao menos que você tenha um requisito ou objetivo específico, use a versão oficial CPython que pode ser baixada no
[site](http://www.python.org/download/) ofícial.

####Módulos e pacotes

Todo código em Python é organizado através de módulos. Um módulo pode ser um arquivo python com uma ou varias funções.
Também pode ser um diretório contendo um ou vários arquivos python. Um módulo pode ser importado em outro módulo através do comando
`import` ou do comando `from... import`.

Quando se é importado um módulo dentro de um programa python o interpretador importa esse módulo como um objeto (tudo em python é objeto) e
suas funcionalidades são acessadas através desse objeto  criado. Exemplo:

{% highlight python %}
#importando o modulo os
>>> import os
>>> os.mkdir('dir_exemplo')
{% endhighlight %}

Ou com o comand from...import

{% highlight python %}
#importando somente a função mkdir
>>> from os import mkdir
>>> mkdir('dir_exemplo')
{% endhighlight %}

Para saber onde o python busca por esses pacotes, existe um módulo chamado sys que possui uma lista com todos os diretórios onde o
interpretador busca por pacotes. Essa lista é configurada no momento que o python é instalado e pode ser manipulada afim de incluir
dinamicamente novos diretórios onde o interpretador poderá procurar por novos módulos.

No meu laptop, rodando Ubuntu 12.04, a lista está configurada como segue:

{% highlight python %}
>>> import sys
>>> print sys.path
  ['',
    '/usr/lib/python2.7',
    '/usr/lib/python2.7/plat-linux2',
    '/usr/lib/python2.7/lib-tk',
    '/usr/lib/python2.7/lib-old',
    '/usr/lib/python2.7/lib-dynload',
    '/usr/local/lib/python2.7/dist-packages',
    '/usr/lib/python2.7/dist-packages']
{% endhighlight %}

Assim como em outras linguagens, o python importa automaticamente um módulo chamado builtins que contém algumas funções e classes uteis como str, open, len, Exception, etc.

A lista de módulos da biblioteca padrão é vasta. E por esse motivo, a comunidade python se refere a linguagem como sendo "Batteries
Included" já que existe uma variedade de módulos disponíveis para as mais diversas tarefas.

### Pacotes de terceiros e pip

Mesmo que a biblioteca padrão do python seja tão vasta, em algum projeto sempre vamos precisar de uma biblioteca ou framework de
terceiros que facilite nosso trabalho. Eu conheço três modos de instalar novos pacotes para o python:

* utilizando o gerenciador de pacotes do seu sistema operacional;
* utilizando o pip (Python Installer Package);
* instalando através do código fonte da biblioteca;

Os três modos fazem praticamente a mesma coisa: instalam os pacotes e suas dependências em algum dos diretórios que o interpretador usa para procurar módulos.

Particularmente eu uso mais o [pip](http://www.pip-installer.org/). Acho ele muito pratico e ainda possui algumas funcionalidades
interessantes quando se está trabalhando em um ambiente virtual (o que veremos mais adiante).O pip pode ser instalado baixando o
pip-installer ou usando o gerenciador de pacotes do sistema operacional. Uma vez instalado, para baixar uma nova biblioteca basta utilizar
o comando:

{% highlight bash %}
$pip install <nome_do_pacote>
{% endhighlight %}

Para instalar o framework flask por exemplo, basta rodar o comando:

{% highlight bash %}
$pip install flask
{% endhighlight %}

Outras funcionalidades do pip incluem instalar bibliotecas com versões específicas, fazer upgrades e downgrades de pacotes, buscar
bibliotecas por nome ou palavra chave, instalar dependências baseando-se em um arquivo
[comumente](https://github.com/faustovaz/odecarvalho-kindle/blob/master/requirements.txt)
[encontrado](https://github.com/grangier/python-goose/blob/develop/requirements.txt) em projetos python chamado de requirements.txt
e gerar esses mesmos arquivos com todas as dependências e versões de um projeto.
No site do [pip](http://www.pip-installer.org/en/latest/quickstart.html) é possível ver os comandos disponíveis pela ferramenta.

Existem muitas formas de encontrar pacotes Python. Você pode procurar por pacotes no github ou no site do
[Python Package Index](http://pypi.python.org/), que é uma das melhores formas de encontrar bibliotecas python e é a fonte de pacotes
utilizado pelo pip.

### VirtualEnv

O [VirtualEnv](http://www.virtualenv.org/) é uma ferramenta utilizada para criar ambientes de desenvolvimento Python isolados.

A necessidade de isolar ambientes surge com a necessidade que muitas vezes temos de usar versões de pacotes e bibliotecas diferentes em
cada projeto. Por exemplo, digamos que você instalou a versão mais recente do BeautifulSoup no path principal do Python, no entanto, a
versão mais recente trás algumas incompatibilidades com a versão anterior que você usou em um projeto qualquer. Como fazer para utilizar a
versão anterior do pacote se você atualizou a biblioteca  no ambiente padrão do python?

Para solucionar esse problema, podemos utilizar o virtualenv e criar um ambiente python isolado. Nesse ambiente isolado você pode utilizar
o pip para instalar a versão necessário da biblioteca. Para criar o ambiente isolado basta digitar:

{% highlight bash %}
$virtualenv meu_ambiente_isolado
{% endhighlight %}

Note que ao rodar o comando, o virtualenv cria um diretório. Dentro desse diretório , além de outras pastas, existe uma pasta chamada
bin onde se encontra o interpretador do python que será utilizado ao ativar o ambiente virtual.

Com o ambiente criado, é preciso ativa-lo:

{% highlight bash %}
$source meu_ambiente_isolado/bin/active
{% endhighlight %}

Ao ativar, podemos perceber que o python do ambiente isolado utiliza um novo path para procurar e instalar pacotes e libs python.

{% highlight python %}
>>>
>>> import sys
>>> print sys.path
  ['',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7/plat-linux2',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7/lib-tk',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7/lib-old',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7/lib-dynload',
    '/usr/lib/python2.7',
    '/usr/lib/python2.7/plat-linux2',
    '/usr/lib/python2.7/lib-tk',
    '/home/vagrant/python-env/meu_ambiente_isolado/local/lib/python2.7/site-packages',
    '/home/vagrant/python-env/meu_ambiente_isolado/lib/python2.7/site-packages']
>>>
{% endhighlight %}

Agora, com o ambiente isolado ativo, podemos instalar novas bibliotecas e pacotes com versões específicas sem alterar a instalação
padrão do python.

O uso do virtualenv e do pip são muito divulgados pela comunidade Python. É de boa prática sempre utilizar virtualenv e desenvolver em
ambientes isolados afim de evitar conflitos de versões e gerenciar efetivamente as dependências de um projeto.

### Ferramentas e Frameworks

Python é uma linguagem de propósito geral. Ela é usada para construir aplicações web, aplicações desktop, games e automatizar tarefas.
Quando se trata de aplicações web a comunidade python apresenta inúmeros frameworks. Vou limitar esse post a somente dois frameworks que
conheço, o Flask e o Django.

### Flask

O [Flask](http://flask.pocoo.org/) é um microframework web que permite criar aplicações rapidamente. Ele é integrado  a um sistema de
template engine simples e prático (Jinja2) e possui um  wrapper que facilita a integração com o orm SqlAlchemy.

Ele é muito parecido com os frameworks Slim(PHP) e Sinatra(Ruby). Uma aplicação simples, teria a seguinte estrutura:

{% highlight python %}
#-*- encoding: utf-8 -*-
#file: main.py

from flask import Flask
aplicacao = Flask(__name__)

@aplicacao.route('/')
def main():
    return 'Olá, mundo'

if __name__ == '__main__':
    aplicacao.run()

{% endhighlight %}

E para iniciar a aplicação:

{% highlight bash %}
$ python main.py
{% endhighlight %}

Para acessar essa aplicação exemplo, basta ir até seu navegador e abrir o endereço http://locahost:5000.

### Django

O [Django](http://www.djangoproject.com), ao contrário do Flask, é um framework full stack. Ele possui vários módulos e libs que facilitam
e agilizam o desenvolvimento de aplicações web. O Django trás, entre outras coisas, um ORM e engine de templates próprio, filtros contra
XSS, filtro contra CSRF e um admin pronto para sua base de dados.

Ambos podem ser instalador através do pip. Há inúmeros [cursos](http://www.welcometothedjango.com.br) e
[tutoriais](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world) na internet para aprender a desenvolver
aplicações web com esses dois frameworks web.

### Pygame

[Pygame](http://www.pygame.org/) é um wrapper para linguagem Python da biblioteca gráfica [SDL2](http://www.libsdl.org/). Possui uma
comunidade bem ativa e você pode tirar dúvidas e até participar em implementações de alguns games e
[desafios](http://www.pyweek.org/) que a comunidade promove.

É uma forma divertida de conhecer e usar a linguagem a fundo. Também é uma maneira interessante de começar a desenvolver e entender algumas
técnicas por trás de games 2D. Para aprender um pouco e desenvolver alguns
[pet projects](http://github.com/faustovaz/rock-shooter) comecei lendo o livro gratuito
[Making Games with Python and Pygame](http://inventwithpython.com/pygame/index.html) de Al Sweigart.

Sem dúvida, depois de aprender um pouco de PyGame seu aprendizado de python vai ser muito mais divertido.

### Onde começar

Existem muitas fontes disponíveis para aprender python e você pode usar a forma que mais se adequa ao seu estilo de aprendizado.
Se você gosta de aulas, existem iniciativas bem legais como o [Google Class](http://developers.google.com/edu/python/), o
[Python Pro](http://www.python.pro.br/) e o curso do [Henrique Bastos](http://www.welcometothedjango.com.br) de Django.
Particularmente, já assisti algumas aulas no google class. Além de serem gratuitas, são excelentes e valem muito a pena. Também já fiz o
curso do Henrique Bastos de Django e gostei muito também.

Se você gosta de livros, existem dois livros gratuitos (para ler online) que usei e uso: o
[Learn Python the Hard Way](http://learnpythonthehardway.org/) e o [Dive Into Python 3](http://www.diveintopython3.net/).
Ambos os livros são excelentes e trazem uma série de exercícios interessantes que ajudam a entender e praticar o jeito pythonico de
resolver problemas.

O Eric Hideki, [compilou](http://ericstk.wordpress.com/2013/05/30/por-onde-eu-comeco-a-aprender-python/) no blog dele,  uma lista de sites
que são úteis para quem quer aprender python. Vale a pena conferir.

Por fim, para entender bem a filosofia da linguagem, basta digitar no interpretador python o comando import this e ler o famoso poema
de Tim Peters, o Zen of Python:

{% highlight python %}
>>> import this
The Zen of Python, by Tim Peters
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
>>>
{% endhighlight %}
