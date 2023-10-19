<h1 align="center"> CheckPoint 6 - Projeto IOT </h1>

<h3> Integrantes do grupo: </h3>

<ul> 
  <li> RM550233 - Fellype Dos Santos Laes </li>
  <li> RM550539 - Guilherme Fazito </li>
  <li> RM551528 - Henrique Lima </li>
  <li> RM98860  - Ian Xavier Kuraoka </li>
  <li> RM98287  - Raí Gumieri dos Santos </li>
</ul>

<h2 align="center"> Introdução </h2>

<p align="justify"> Nesta nova fase do projeto, pretendemos desenvolver um pequeno protótipo destinado à medição de parâmetros relacionados à temperatura, umidade e luminosidade. Para alcançar esse objetivo, será necessário a utilização de sensores de monitoramento, que seriam: </p>
<ul> 
 <li> ESP32; </li>
 <li> Placa de ensaio; </li>
 <li> DHT11 ou DHT22; </li>
 <li> Sensor LDR; </li>
 <li> Resistor 10kΩ. </li>
</ul>

<p align="justify"> Caso você não tenha os equipamentos em mãos, você pode acessar o site Wokwi e realizar o procedimento, assim vai conseguir acompanhar e entender como é feito na prática </p>
<h4> Link do site: https://wokwi.com/ </h4>

<p align="justify"> Para facilitar, vamos seguir o procedimento no próprio site Wokwi. A montagem dos componentes ficará dessa forma: </p>

<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/c94edba7-6598-4eda-9f5f-6c7b6351d346"> 
</div>

<br>


<div align="center"> 
<h2> Análise do Equipamento </h2>

<div align="justify"> 
  <p> O ESP32 desempenha um papel fundamental neste projeto, uma vez que é por meio dele que estabeleceremos a conexão com a Internet e registraremos os valores coletados pelos sensores na nuvem. Isso se mostra particularmente eficaz quando se está distante do protótipo, permitindo o acesso às informações coletadas e a análise do funcionamento adequado do equipamento. </p> 
  <p> Se você conseguir conectar o projeto à sua rede Wi-Fi, terá a capacidade de acessá-lo e executar comandos, como ligar e desligar o LED do ESP32, além de coletar dados dos sensores em uso. Para realizar essas operações, é possível utilizar o aplicativo MyMQTT ou uma aplicação no Google Colab, que fornecerá acesso às medições do dispositivo. </p>
  <p> A placa de ensaio será de extrema importância, já que vai ser ela onde vamos fazer as devidas conexões entre o ESP32 e os sensores. </p>
  <p> Falando em sensores, o DHT22 é utilizado para medir a temperatura e a umidade. No projeto físico, também é possível optar pelo DHT11, que realiza as mesmas medições. Em outras palavras, independentemente da escolha, ambos proporcionarão resultados idênticos. </p>
  <p> Já o sensor LDR será utilizado para fazer a medição da luminosidade, divulgando como resposta a voltagem e o valor em porcentagem. </p>
</div>

<br>

<h2> Montagem do Código </h2>
<p align="justify"> Após ter concluído a montagem da imagem acima, vamos trabalhar no desenvolvimento do código. Você pode usar o que está sendo fornecido neste repositório, porém deve ser feito algumas alterações, envolvendo os tópicos que foram marcados no código. São eles que você terá que usar para acessar a nuvem e visualizar os dados que estão sendo fornecidos (Linhas 21, 22, 23, 24, 25 e 32).  </p>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/5bfc38cb-b5d8-4a14-a04a-d22c77c7000b">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/551e01f0-9944-4e45-827a-5e6090419949">
</div>

<br>

<div align="justify">
  <p> É necessário alterar o lamp108, pois ele é a porta onde será possível acessar a rede. Você pode alterar para lamp109, lamp110, etc...  </p>
  <p> No final dos 3 últimos tópicos, é possível analisar os finais “L, U, T”, essas são as siglas para identificar as portas em que estão os dados de Luminosidade, Umidade e Temperatura. </p>
  <p> Outra alteração importante é na parte do Wifi, é necessário que você coloque o nome e senha da sua internet, para que o ESP32 consiga se conectar à rede. Todavia, se estiver realizando o passo a passo pelo site, é necessário colocar “Wokwi-GUEST” no nome da        rede sem colocar senha, pois o próprio site vai usar uma rede para conectar com o ESP32 (Linhas 41 e 42). </p>
</div>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/9c55c7b1-0c80-4b86-ba66-e658dd19bca2">
</div>

<br>

<p> Após essas modificações, pode ligar o código e esperar aparecer a informação de que o ESP32 está tentando se conectar a uma rede. </p>

<div>
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/d7963852-47e0-4f12-bfc2-1343fac46a70">
</div>

<br>

<p> Caso você esteja fazendo com o material em mãos, é necessário apertar o botão de “BOOT” do ESP32 para fazer a conexão. </p>
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/ad286171-87de-4426-bc58-515b203c7fe7" height=200px>

<br>

<p> Após essa etapa aparecerá a seguinte informação: </p>
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/dda56039-c7bf-466b-b4e0-e1a283edbd84">
<img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/606f9783-6479-4d5e-91ce-ba5a83349e8d">

</div>
<br>

<p align="justify"> Agora vamos trabalhar com o Google Colab, primeiro é necessário instalar a biblioteca Paho MQTT, pois vamos usar ele para se comunicar com o broker (Porta 1883). </p>
<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/77ef62cf-9a0b-419f-a4b5-be549e529aa4">
</div>

<br>

<p align="center"> Após a instalação, vamos realizar a importação do Paho MQTT e acrescentar algumas linhas de código: </p>

<div align="center">
  <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/71851a71-2642-4ba0-86fd-4fbf22ec68f1">
</div>

<br>

<p align="justify"> Antes de você rodar o código, vale ressaltar que ele vai mostrar somente os valores de luminosidade, já que estamos utilizando a porta “/TEF/lamp108/attrs/l”. O resultado disso irá gerar: </p>

<table align="center"> 
  <tr>
    <td align="center"> Dados de Luminosidade </td>
    <td align="center"> Dados de Umidade </td>
    <td align="center"> Dados de Temperatura </td>
  </tr>
  <tr>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/b65a502e-f4dd-4aff-9066-5b9e0078f1a1"> </td>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/2a43ec2e-f519-40dd-9001-86f7df3c2157"> </td>
    <td> <img src="https://github.com/raigumieri/CP6_Edge/assets/127215645/f84d4bec-6da4-473e-9f4f-9a17e0fb8518"> </td>
  </tr> 
</table>

<br> 

<p align="justify"> Após a conclusão destes passos, o projeto estará finalizado. Agora será possível acessar os dados de temperatura, umidade e luminosidade de qualquer local, desde que tenha conexão à Internet para obter as informações. </p>

