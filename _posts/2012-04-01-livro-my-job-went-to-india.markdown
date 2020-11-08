---
layout: post
status: publish
published: true
title: My job went to India.
categories: Books
---
Há um  bom tempo, perambulando pela [loja de livros](http://pt-br.facebook.com/LivrariaSeboAmadeus) do meu tio, encontrei esse livro jogado num canto, todo empoeirado e sujo. Na época eu já tinha escutado alguém falar da editora [The Pragmatic Programmers](http://pragprog.com/) mas nem conhecia e não tinha a menor idéia de quem era [Chad Fowler](http://www.chadfowler.com/), o autor do livro. O que chamou a minha atenção foi a capa cômica da obra e o título: My job went to India.  

![My job went to india]({{site.url}}/images/myjobwenttoindia.jpeg)

Quando li o livro eu estava trabalhando como estagiário na prefeitura municipal de Foz do Iguaçu e naquele tempo muita coisa escrita no livro não fazia parte do meu cotidiano. Coisas como offshoring, body shop, equipes remotas com fuso horários diferentes eram coisas que eu sabia o que eram, mas nunca tinha vivido na pele seus efeitos. Esses termos começaram a fazer parte da minha vida quando entrei para o time da EITS.

A [EITS](http://www.eits.com.br/) é uma empresa de TI que presta serviços para Europa, Estados Unidos e Brasil, além de desenvolver produtos próprios. Meu primeiro projeto offshore na EITS foi para um grande cliente americano que tem seus negócios focados em educação a distância. É um cliente realmente grande que atua em quase todo Estados Unidos e Canadá. O time desse projeto era dividido em três equipes: uma americana, uma indiana e uma brasileira (nós da EITS). Trabalhar em um projeto assim é muito interessante, visto que você entra em contato com culturas diferentes, com jeitos diferentes de pensar e resolver problemas, tem a oportunidade de se comunicar em outro idioma (e logo nota que é preciso estudar inglês muito mais do que se imagina) e saber que agora você tem colegas de trabalho no mundo todo. É realmente uma experiência profissional muito bacana, muito legal. Mas tem um outro lado da moeda, para que possamos fazer parte de um projeto assim, uma equipe de lá (EUA) deixa de atuar (deixa de fazer parte do projeto) e além do trabalho deles já estar indo para India  agora está vindo para o Brasil também. Isso é muito bom para nós, afinal, temos mais oportunidades, temos bons profissionais e o país está em plena ascensão. No entanto, a crise que passa por lá pode chegar aqui e o nosso trabalho pode sair daqui para ir para a Índia ou a China (que são mais baratos e muito bons também). E é ai que vale a pena conferir cada uma das dicas do Chad Fowler no livro dele.

Todas as dicas do livro são interessantes. Elas são tiradas da experiência do autor em montar times de desenvolvimento de software na Índia e por consequência desempregar times de desenvolvedores nos Estados Unidos. Lendo o livro é possível ver que o mercado de TI brasileiro tem algumas semelhanças com o indiano. Todos os capítulos e temas são interessante e valem a pena ler. Desde que terminei a leitura do livro tento aplicar no meu dia a dia os conselhos do autor.

Abaixo resumo alguns:

### Entenda o negocio para o qual você está trabalhando.


É importante aprender os aspectos não técnicos do negocio para o qual está trabalhando (no nosso caso, desenvolvendo software) Muitos problemas podem ser resolvidos se os aspectos não técnicos forem absorvidos pelos responsáveis técnicos. Vivi essa experiência no projeto que referi acima. Estávamos com uma feature complicada de ser implementada no tempo que tínhamos. Como o time tentou absorver ao máximo o negocio, conseguimos apresentar ao cliente uma solução alternativa, que não era como o cliente idealizou mas resolvia o problema. Isso foi possível graças ao esforço do time em entender o negocio. Nos poderíamos ter ignorado o negocio, por consequência não teríamos outra solução e implementaríamos a feature ignorando o prazo e comprometendo o negocio do cliente. Foque no negocio e depois na tecnologia, a tecnologia só importa se o negocio tem sentido.

### Pratique


Pratique programação. Desenvolva sua caixa de ferramentas, faça seus próprios produtos, vá além dos seus limites. Quer aprender TDD? Pratique. Quer aprender BDD? Pratique. No livro Chad da várias dicas de como praticar programação. Ele compara praticar programação com praticar música. Quanto mais, melhor. Desde que li isso, tento aplicar essa dica [resolvendo os problemas](https://github.com/faustovaz/projecteulerO) matemáticos do [project Euler](http://projecteuler.net), um site que reune uma série de problemas matemáticos que vão do básico aos mais complexos. É muito bacana e você ainda pode mostrar sua solução e receber feedbacks dos outros usuários do site.

### Nos ombros de gigantes


Você já parou para ver como funciona aquele framework que você utiliza no seu dia a dia? Já viu como ele é implementado? Quais técnicas os criadores do seu framework favorito utiliza para solucionar o problema que ele propõe resolver? Essa dica do Chad Fowler fala sobre como aprender com os gigantes. Estar no ombro deles vendo e aprendendo com a forma como eles trabalham. Hás uns dois anos, eu e o
[Leandro Quingerski](http://quinja.wordpress.com) trabalhávamos num projeto utilizando o Flex com Spring. Estávamos enfrentando alguns problemas e então decidimos debugar o código fonte do framework para flex que estávamos utilizando. Em uma tarde aprendemos várias técnicas que ajudaram a entender como os frameworks (no caso, pra Adobe Flex) utilizavam o Event.onStage para ler metadados dos componentes que você utiliza na sua aplicação. Essa técnica aprendida foi utilizada mais tarde, quando tivemos que implementar nosso próprio modelo de metadados.

### Avalie seu conceitos e livre-se dar armadilhas


No livro tem um exemplo bem interessante de como alguns conceitos e valores que levamos como verdade pode nos prejudicar. Em algumas regiões da India, moradores são frequentemente incomodados por macacos que invadem suas casas em busca de alimentos. Para solucionar esse problema, os indianos começaram a [cavar alguns buracos](http://www.peeniewallie.com/2011/06/the-south-india.html) no quintal de suas casas e colocar alimentos dentro deles. As cavidades criadas eram bem estreitas de modo que a mão de um macaco só penetrava a cavidade se ela estivesse totalmente aberta. Como os macacos agarravam os alimentos, suas mãos não poderiam mais sair de dentro daquelas cavidades. Eles tinham duas opções, deixar o alimento lá e irem embora ou morrer tentando tirar o alimento da cavidade. Como macacos tinham conceitos rígidos e colocavam alto valor no alimento ali encontrado, a segunda opção era a que eles escolhiam com mais frequência. Falando de TI, quantos projetos já falharam por escolhas tecnológicas baseadas em valores pessoais e conceitos rígidos? Eu já vi alguns. Já vi bons produtos não serem lançados por escolhas e decisões baseadas em valores pessoais que para ocasião eram errados. Repense seus conceitos e avalie seu valores constantemente.


Esse livro é dividido em 6 partes contendo 52 temas. Cada tema descreve a experiência de um CIO americano responsável por montar times de desenvolvimento de software na India. Ao ler o livro o autor nos faz refletir sobre várias coisas, mas a principal mensagem é se temos algo a mais para oferecer do que simplesmente o baixo custo, afinal somos mais baratos, mas além do bom preço existe algo a mais que nos diferencia?
