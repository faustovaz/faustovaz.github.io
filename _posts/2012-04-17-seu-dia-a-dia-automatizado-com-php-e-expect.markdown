---
layout: post
status: publish
published: true
title: Seu dia a dia automatizado com PHP e Expect.
---
Em 2010 tive a oportunidade de ir ao [Latinoware](http://www.latinoware.org) e assistir a uma palestra do Rogério Ferreira sobre automatização de tarefas rotineiras, aquelas que sempre fazemos no nosso dia a dia como desenvolvedores (ou sys admins). Na palestra do Rogério ele apresentou uma extensão da linguagem de script [TCL](http://www.tcl.tk/) chamada
[Expect](http://www.tcl.tk/man/expect5.31/) que permite que você faça interações com um shell de forma automática. Assim, você pode criar um script que fará automaticamente toda aquela interação com o shell que necessite de intervenção humana. Por exemplo, você pode criar um script para logar em um servidor qualquer, executar alguns comandos e enviar alguns arquivos. Tudo isso de forma automática. Todo o trabalho que você faria para logar no servidor e digitar os comandos necessários para cumprir uma tarefa como essa o script com Expect faz pra você.

A palestra foi muito interessante e o Rogério disponibiliza até hoje os slides da apresentação no
[site dele](http://rogerioferreira.objectis.net/).

Nesses últimos meses estou trabalhando como freelancer nos horários vagos com um amigo que presta serviços fazendo consultoria em recursos humanos. Em um dos clientes nosso trabalho envolvia integrar o sistema de cartão ponto do cliente com o sistema que estávamos desenvolvendo. Esse cliente era grande e por consequência disso tinha máquinas de cartão ponto espalhadas em vários locais para facilitar o registro de horários dos funcionários. Devido a limitação dos aparelhos que esse cliente possuía, todos os horários eram registrados em arquivos texto e embora os computadores fossem ligados em rede eles não tinha uma estrutura que permitisse que esses arquivos fossem enviados ou centralizados em um único local, tornando difícil armazenar os registros no nosso sistema afim de calcular salários e horários extras. Como já conhecíamos o Expect, tínhamos uma carta na manga para solucionar esse problema. No entanto, precisávamos de uma solução rápida e não tínhamos disponível no time uma pessoa que entendesse de TCL. Foi aí que descobrimos, fuçando no site da [pecl](http://pecl.php.net) a extensão do
[expect](http://pecl.php.net/package/expect) para PHP.

![]({{site.url}}/images/php-300x300.jpg)

Essa extensão é bem bacana e apesar de estar na versão beta, funciona muito bem. Com a extensão instalada você programa em php e aproveita toda a funcionalidade que o expect oferece. Abaixo mostro a instalação e alguns scripts que dão uma idéia do que pode ser feito com o expect.

### Instalação

Aqui usamos o pacote [xampp](http://www.apachefriends.org/pt_br/xampp.html) para desenvolver nossos trabalhos e para instalar a extensão do expect basta baixar o pacote de desenvolvimento do xampp, que vem os fontes do PHP e outros arquivos mais. Uma vez com os arquivos devidamente instalados basta usar o aplicativo pecl para instalar a extensão. Se você não tem o expect-dev e o autoconf instalados siga os seguintes passos:

{% highlight bash %}
apt-get install expect-dev;
apt-get install autoconf;
pecl install expect-0.3.1
{% endhighlight %}

Se você já tiver o autoconf e o expect-dev instalados, basta executar a última instrução.
Logo após a instalação do pacote basta incluir no seu arquivo php.ini a extensão do expect:

{% highlight bash %}
extension=expect.so;
{% endhighlight %}

### Exemplos

A extensão expect possui somente duas funções, uma para abrir o stream do shell e outra que comparar a saída do shell após um comando dado com os patterns passados. Para exemplificar melhor, segue um script com expect:

{% highlight php %}
#!/opt/lampp/bin/php
<?php

$servers = array(
        array("ip" => "192.168.1.22", "user" => "adminuser", "password" => "adminuser", "path" => "/home/adminuser/punto/punto_comercial.txt"),
        array("ip" => "192.168.1.45", "user" => "adminuser", "password" => "adminuser", "path" => "/home/adminuser/punto/punto_admin.txt"),
        array("ip" => "192.168.1.37", "user" => "adminuser", "password" => "adminuser", "path" => "/home/adminuser/punto/punto_vendas.txt"),
        array("ip" => "192.168.1.15", "user" => "adminuser", "password" => "adminuser", "path" => "/home/adminuser/punto/punto_info.txt"),
);
$localPath = "/home/fausto/files/";

ini_set("expect.loguser", "Off");
$options = array(
        array("password:", "PASSWORD"),
);

foreach ($servers as $server)
{
    $params = $server['user'] . '@' . $server['ip'] . ":" . $server['path'] . " " .$localPath;
    $stream = expect_popen("scp -r $params");
    switch(expect_expectl($stream, $options))
    {
        case "PASSWORD"        :    fwrite($stream, $server['password']."\n");
                                    while($line = fgets($stream));
                                    break;
    }
    fclose($stream);
}

echo "Done!\n";
?>
{% endhighlight %}

Esse é o script que usamos para resolver o problema que citei acima. Ele é bem simples e tudo que ele faz é copiar os arquivos textos de cada um dos servidores relacionados para um diretório local qualquer.

Para entender melhor, na linha 12, começamos setando uma opção de configuração do Expect, o expect.loguser, para off. Dessa forma não serão gerados log do que estiver acontecendo no shell. Para que você possa ver o output que é gerado ao executar o expect, basta retirar esse trecho de código, uma vez que a opção padrão dessa configuração é On. O expect tem outras três opções de configurações que podem ser consultadas [aqui](http://www.php.net/manual/en/expect.configuration.php)

Logo abaixo, na linha 20, temos uma chamada a função [expect_popen](http://www.php.net/manual/en/function.expect-popen.php).
Esse método executa o comando passado no shell e retorna o stream do terminal. Com esse stream você pode usar a função
[fwrite](http://br2.php.net/manual/en/function.fwrite.php") do php para escrever dados no terminal, como uma senha, uma resposta de yes / no ou outros comandos.

Mas como saber o momento de escrever um password ou uma resposta de yes / no para o shell? Para isso temos a função
[expect_expectl](http://www.php.net/manual/en/function.expect-expectl.php). Essa função compara a saída que o shell disponibiliza após a execução de um comando com um array de array de opções.

Explicando melhor, quando o script acima é executado ele chama a função expect_popen e passa para ela o comando
[scp -r](http://linux.die.net/man/1/scp) que copia recursivamente, via ssh, arquivos de um local qualquer para um destino
qualquer. Assim que esse comando é executado, o shell espera pelo password que autorizará a execução da instrução. Assim a função [expect_expectl](http://www.php.net/manual/en/function.expect-expectl.php) compara a saída disponibilizada pelo shell (que no caso será "password:") com o array de array de opções. Ao encontrar o pattern, ele executa os métodos associados, que no caso está dentro de um bloco switch case. Ao executar, a  função fwrite escreve o password requerido no shell e executa a tarefa.

Segue abaixo um outro exemplo que uso no dia a dia para deployar rapidamente uma aplicação em um servidor de testes. Executo esse script sempre que preciso enviar para nosso servidor de testes a versão corrente da app que estou trabalhando e atualizar o banco de dados para os testes.

{% highlight php %}
#!/opt/lampp/bin/php
<?php
//Configurações do servidor e aplicação.
$host = "192.168.1.5";
$user = "adminuser";
$password = "adminuser";
$destino = "/home/adminuser/bagual/";
$projeto = "/opt/lampp/htdocs/codeigniter/";
//Configurações do banco de dados
$mysqlUser = "root";
$mysqlPassword = "";
$mysqlDB = "dev1";
$arquivoSQL = "agritrad_extranet.sql";
//Parametros de configuração e comportamento do expect
ini_set("expect.loguser", "Off");
$shell = fopen("expect://scp -r $projeto $user@$host:$destino", "r");
$opcoes = array (
    array("password:","PASSWORD"),
    array(" $" ,"SHELL", EXP_EXACT)
);
switch (expect_expectl ($shell, $opcoes)){
    case 'PASSWORD': fwrite ($shell, "$password\n");
                     break;
    default        : die ("Eita, deu um erro.\n");
}
while($line = fgets($shell)){
echo $line; //Mostra os arquivos enviados.
}
fwrite($shell, "exit");
fwrite($shell, "\n");
fclose ($shell);

// Atualiza banco de dados
$done = false;
$stream = expect_popen("ssh $user@$host");
while(true){
    switch (expect_expectl ($stream, $opcoes)){
        case 'PASSWORD': fwrite($stream, "$password\n");
                         break;
        case 'SHELL'   : if($done == false){
                             fwrite($stream,"cd $destino");
                             fwrite($stream, "\n");
                             fwrite($stream, "mysql -u $mysqlUser -p $mysqlDB < $arquivoSQL");
                             fwrite($stream, "\n");
                             while(true){
                                 switch(expect_expectl($stream, $opcoes)){
                                     case 'PASSWORD': fwrite($stream, "$mysqlPassword\n");
                                                      $done = true;
                                                      break 2;
                                 }
                             }
                         }else{
                              break 2;
                         }
    }
}
echo "Concluido!\n";
fclose ($stream);
?>
{% endhighlight %}

O script é bem semelhante ao primeiro. Uma coisa interessante para notar é o uso da constante EXP_EXACT, que indica ao PHP que o pattern fornecido é uma string exata. [Há outras constantes](http://www.php.net/manual/en/expect.constants.php) que você pode usar para facilitar na construção dos seus scripts.

Outro ponto, é o uso de uma chamado adicional ao método fwrite com o parametro "\n", para simular o ENTER. Por algum motivo desconhecido se usarmos o "\n" concatenado ao final do comando, o script imprime exatamente a cadeia de caracteres "\n" ao invés de simular um ENTER. Deve ser algum problema com a extensão do expect. Por isso forcei a chamada do fwrite com somente o "\n" como parâmetro.

O Expect abre uma gama de possibilidades de automatização em casos onde há a necessidade de intervenção humana. Tentar automatizar sempre é bom. No final das contas, quando você automatiza tarefas sempre sobra tempo para coisas mais
[legais](http://www.youtube.com/watch?v=s8qCXutbVU0) e [produtivas](http://www.youtube.com/watch?v=fr2mB3gzsYQ).
