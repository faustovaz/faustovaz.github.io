---
layout: post
status: publish
published: true
title: Aprender programação pode ser divertido...
---
Há alguns meses eu assisti a [entrevista](http://plus.google.com/events/cacqqn90k7hf7tihjbtjn33lktc) com o
[Henrique Bastos](http://henriquebastos.net) no Momento Pythônico e um dos vários pontos que chamaram minha atenção foi sobre a aplicação
do Python como primeira linguagem a ser utilizada por quem quer aprender programação. O Henrique fez algumas observações bem interessantes
sobre como o python e seu conjunto de ferramentas oferecem a oportunidade para quem está aprendendo de construir e rodar algo (um joguinho,
por exemplo) em um intervalo curto de tempo.

Durante o tempo que estudei em Edimburgo tive a oportunidade de morar com uma família escocesa. Essa família era composta por um casal de
idosos e um típico adolescente de 14 anos que adora tecnologia e games.

Um dia enquanto trabalhava em um projeto com um amigo ele veio até mim e perguntou se eu poderia ensinar algo de programação pra ele. Gostei
muito da iniciativa do garoto e influenciado pela excelente entrevista com o Henrique, resolvi mostrar pra ele o quanto programar poderia ser
legal... com Python,  claro!

O primeiro passo foi instalar o Python no laptop dele, que de quebra, já o oferece o Idle, um excelente editor de texto que permite, sem
complicação nenhuma, digitar alguns comandos python e ver o resultado "on the fly".

Depois passamos por alguns pontos básicos de programação como, variáveis, constantes e estrutura de controle. Para auxilia-lo no processo de
aprendizagem usamos como guia de consulta o livro [Learn Python the hard way](http://learnpythonthehardway.org/) do
[Zed Shaw](http://zedshaw.com/), que é uma excelente escolha para quem está começando. Esse livro é excelente e é recheado de exemplos
práticos e interessantes.

Para mostrar pra ele algumas estruturas de dados, nada poderia ser mais prático e simples com a ajuda do Python. É mais fácil entender uma
estrutura se a sintaxe da linguagem te ajuda.

Por exemplo, uma lista em python:

{% highlight python %}
>>> my_list = [1,2,3]
>>> my_list.append(4)
>>> my_list
[1,2,3,4]
>>> my_list.pop()
4
[1,2,3]
>>> len(my_list)
3
{% endhighlight %}

Mais simples? Impossível.

E uma estrutura mais elaborada, como dicionários?

{% highlight python %}
>>> my_dict = {'one' : 1, 'two' : 2}
>>> my_dict.update({'three' : 3})
>>> my_dict
{'three' : 3, 'two' : 2, 'one' : 1}
>>> my_dict.popitem()
('tree', 3)
>>> my_dict
{'two' : 2, 'one' : 1}
{% endhighlight %}

O mesmo! Simples...

Seguindo o progresso do [Jan](https://github.com/jan98), notei o quão python é uma linguagem intuitiva e divertida. Imagino como seria
difícil explicar algumas estrutura de dados como listas, pilhas e filas usando uma linguagem verbosa e complicada como o Java, por exemplo.
E a facilidade em construir pequenos programinhas e ver os mesmos rodando em questão de minutos é um motivador a mais para quem está
começando.

Após aprender o básico necessário do python e seguindo as ideias do Henrique Bastos, decidimos que seria mais legal e desafiador se o Jan
pudesse construir um pequeno game utilizando o que o python já fornece: pygame.

E depois de um pouco mais de três semanas de trabalho eis [aqui](https://github.com/jan98/snake) o resultado:

![Screenshot]({{site.url}}/images/rsz_snake_1.png)
![Screenshot]({{site.url}}/images/rsz_snake_2.png)

Parafraseando o Henrique, realmente, fazer médias de notas de alunos e contas de aritmética não da tesão em ninguém pra aprender programar.

Depois de ver o progresso de um garoto que não sabia nada de programação e quase um mês depois produziu um pequeno game, também acho que Java
e C são péssimas linguagens para serem a primeira linguagem de programação de qualquer pessoa.
