---
layout: post
status: publish
published: true
title: 'Coding for fun: Implementando um pequeno servidor HTTP para Android'
---
No meu IPod sempre utilizei um [aplicativo](https://itunes.apple.com/en/app/filer/id318884764?mt=8) que me permitia fazer upload de
arquivos do meu computador para meu Ipod sem a necessidade de usar o Itunes. Por vezes, ter que abrir o Itunes para fazer o upload de um
simples arquivo é um baita trabalho e esse aplicativo me permitia fazer isso via wifi, através de um pequeno servidor HTTP que rodava dentro
do Ipod.

Ao adquirir um Android tive a mesma necessidade. Sempre que eu necessitasse transferir arquivos para meu celular eu precisava estar com o
cabo usb para conectar o aparelho ao computador ou usar o bluetooth, mas nem meu computador pessoal nem o computador que uso para trabalhar
possuem bluetooth e não tenho o hábito de carregar o cabo do celular pra cima e pra baixo.

Há tempos venho me interessando por desenvolvimento mobile e usei essa minha pequena necessidade para botar a mão na massa e começar a
aprender um pouco sobre android e desenvolvimento mobile. Como solução, implementei um pequeno servidor HTTP que me permite, através de uma
aplicação web, fazer uploads de arquivo para meu celular via wifi.

Existem vários aplicativos disponíveis na play store que fazem esse trabalho, mas minha intenção era fazer eu mesmo e aproveitar para
aprender um pouco sobre android e entender melhor os detalhes do protocolo HTTP.

### Servidor HTTP

Meu ponto de partida para começar a implementar um pequeno servidor HTTP foi ler o
[documento da especificacao](http://www.ietf.org/rfc/rfc2616.txt) do protocolo HTTP/1.1. Esse documento foi criado em 1999 e define regras
para comportar a transferência de arquivos de mídia, como imagens e videos, e não somente textos ( como era o protocolo HTTP/1.0).  Esse
documento explica várias coisas, desde o que são as mensagens definidas no protocolo, quais sãos as operações, quais atributos fazem parte
das mensagens e o que significa cada uma delas.

Com a leitura pude implementar a primeira parte desse meu pet project e com isso pude descobri coisas bem legais. Coisas que ficam
totalmente abstraídas no nosso dia a dia por conta dos frameworks e servidores de aplicação web.

Descobri como funciona por baixo dos panos o envio de arquivos e como são compostas as mensagens que um servidor envia para um cliente
quando o mesmo requisita um arquivo ou uma imagem.

Enfim, foi um exercício bem bacana que me fez ver servidores e frameworks web com outros olhos.

### Aplicativo Android

Quando iniciei o projeto tive a intenção de fazer o aplicativo em partes separadas, produzindo no final vários jars que pudessem ser
importados e usados no projeto android. Tive alguns problemas com essa abordagem devido a forma como o android permite o acesso aos
arquivos da aplicação, que geralmente ficam no diretório assets do projeto. Ler um arquivo dentro da pasta Assets é um  pouco diferente da
forma como se lê um arquivo em um diretório qualquer do seu computador e além disso, quase todos os arquivos dentro desta pasta (assets) 
são compactados para que o apk final tenha tamanho reduzido. Com isso, se você costuma usar file descriptors para obter informações do
arquivo irá ter  problemas, pois não se pode obter o descriptor de um arquivo comprimido, logo, ao construir uma aplicação android e espera
separa-las em pequenas libs precisa ficar atento a esses detalhes para evitar o trabalho de adaptação do seu código ao sistema android.

Falando um pouco mais sobre a compactação dos arquivos da pasta assets, nem todos os arquivos são comprimidos. Os critérios de escolha de
quais arquivos devem ser compactados são baseados nas extensões dos arquivos. Arquivos jpg, png, mp3 e ogg, por exemplo, não são comprimidos
pois já são formatos compactos. No meu caso, a pasta assets do meu projeto possuí arquivos html, javascript e css que são compactados por
padrão pelo sistema android. Para fazer com que o android não comprima esses arquivos, utilizei de um hack que consiste em alterar as
extensões dos arquivos da pasta assets (no meu caso, htmls e arquivos javascript) para extensões amr, que não são compactadas pelo android. Existe
outra forma (mais elegante) de contornar esse problema.
[Esse post](http://ponystyle.com/blog/2010/03/26/dealing-with-asset-compression-in-android-apps) explica melhor as alternativas e ainda
mostra todos os tipos de arquivos que são compactados pelo apt do android.

Todos os arquivos desse projeto estão no [github](http://github.com/faustovaz/android-ttsserver). Testei em vários telefones (2 Samsungs e
2 LG's) e dois tables (Coby e Samung). Futuramente pretendo adicionar novas funcionalidades como a possibilidade de criar pastas, remover
arquivos pela aplicação, adicionar suporte a self signed SSL e permitir fazer upload de arquivos através de drag n' drop.

O projeto foi construído usando a api level 8 do android, para aparelhos com versão android 2.2+. E a aplicação web foi testada usando os
navegadores Firefox e Google Chrome.

Alguns prints:

![Screenshot]({{site.url}}/images/rsz_screen1.png)
![Screenshot]({{site.url}}/images/rsz_screen2.png)
![Screenshot]({{site.url}}/images/rsz_screen3.png)

### O que aprendi

Seguindo as idéias desse [post](http://www.codinghorror.com/blog/2009/03/sharpening-the-saw.html) do Jeff Atwood, construir projetos como
esse é uma ótima forma para afiar e manter preparadas suas ferramentas e enriquecer ainda mais os fundamentos de tantas tecnologias e
frameworks que fazem parte do nosso dia a dia.
