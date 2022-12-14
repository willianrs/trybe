# Teste Trybe

# JavaScript Promises

## 🤷 O que preciso saber primeiro?

Antes de iniciarmos nossa jornada, precisamos revisar alguns conceitos fundamentais e características do JavaScript, que podem nos ajudar a entender melhor o funcionamento das Promises. Vamos lá? 😉

### 🔃 Callback

Também conhecida como chamada de retorno, uma callback é uma função que possui outra função como parâmetro, logo, ela só consegue finalizar a execução de sua tarefa quando a função mais interna (que foi passada como parâmetro) finalizar e retornar um resultado.

Enquanto isso, o JavaScript não trava a execução do código na espera da resposta da primeira função, ele coloca essa função em modo de espera e parte para a próxima tarefa.

**Vejamos um exemplo:**

```jsx
function primeiraTarefa() {
  //Aqui, o setTimeout atrasa propositalmente a execução da primeira tarefa
  setTimeout(function () {
    console.log("Essa é a 1ª Tarefa");
  }, 2000);
}

function segundaTarefa() {
  console.log("Essa é a 2ª Tarefa");
}

primeiraTarefa();
segundaTarefa();
```

Quando rodamos o exemplo acima, temos a impressão de que a função segundaTarefa() é executada primeiro.

Na verdade, a função **primeiraTarefa()** é a primeira a ser executada de fato, porém, como forçamos a execução do setTimeout de 2 segundos, o JavaScript entendeu que não teria a resposta que precisa a tempo e por isso, deixou a função sendo executada em segundo plano, pulando para a linha de comando seguinte, executando a função **segundaTarefa()**.

Depois que a função **segundaTarefa()** finalizou sua execução, o JavaScript retornou para a fila de tarefas pendentes e concluiu a função **primeiraTarefa()**.

### ↔️ Síncrono

Quando usamos o termo Síncrono nos referimos a uma comunicação que acontece em tempo real, onde cada parte recebe (e se necessário, processa e responde) mensagens instantaneamente (ou o mais próximo possível do instantâneo). Além disso, um código síncrono espera uma ação ser finalizada antes de partir para a próxima ação.

Vamos entender melhor o sincronismo com a seguinte analogia: imagine que você recebe a ligação de um amigo no seu celular, durante a chamada, você e seu amigo conseguem conversar naturalmente, um respondendo ao outro instantaneamente assim que cada um termina sua fala, sem precisar esperar por outras ações.

Na programação com JavaScript o processo é o mesmo, os comandos são executados sequencialmente um após o outro, quase que imediatamente, fazendo com que o programa execute de forma fluida.

**Vejamos um exemplo:**

```jsx
function imprimeNaTela(){
  console.log('Mensagem 01')
  console.log('Mensagem 02')
  console.log('Mensagem 03')
  console.log('Mensagem 04')
}

imprimeNaTela()

console.log('Mensagem 05')
```

No exemplo acima, você pode perceber que ao chamar a função **imprimeNaTela()**, o JavaScript executa os comandos de impressão das mensagens de 01 a 04. Somente depois de finalizar aos comandos internos da função, ele passa para a linha seguinte, imprimindo a mensagem 05.

### ⏳ Assíncrono

Podemos entender a programação assíncrona como sendo a execução de uma tarefa em segundo plano, ou seja, sabendo que o JavaScript vai tentar executar um comando por vez, ele vai separar as tarefas em duas categorias:

- as tarefas que ele pode executar agora, sem depender de outras rotinas de código
- as tarefas que ele vai executar depois, quando outras rotinas finalizarem.

Podemos visualizar isso alterando o exemplo anterior, acrescentando uma função **setTimeout()** que pede ao JavaScript para aguardar alguns segundos antes de prosseguir com a tarefa.

**Vejamos um exemplo:**

```jsx
function imprimeNaTela(){
  console.log('Mensagem 01')
  setTimeout( function espera(){
    console.log('Mensagem 02')
    console.log('Mensagem 03')
    console.log('Mensagem 04')}
    , 2000)
}

imprimeNaTela()

console.log('Mensagem 05')
```

No exemplo acima, encapsulamos as mensagens 02, 03 e 04 em uma função chamada **espera()**, dentro de uma **setTimeout()** que dura dois segundos.

Ao executar esse trecho de código, você perceberá que o resultado exibido no console será:

> Mensagem 01
> 
> 
> Mensagem 05
> 
> Mensagem 02
> 
> Mensagem 03
> 
> Mensagem 04
> 

Ou seja, o JavaScript irá seguir os seguintes passos:

1. imprimir 'Mensagem 01'
2. colocar a função **imprimeNaTela()** em espera por 2 segundos
3. imprimir 'Mensagem 05'
4. retomar a função **imprimeNaTela()**
5. imprimir 'Mensagem 02'
6. imprimir 'Mensagem 03'
7. imprimir 'Mensagem 04'

### 🔄 Event Loop

Até aqui já entendemos que, por padrão, o JavaScript só executa uma tarefa por vez, de forma síncrona. Mas também vimos que podemos programá-lo de forma assíncrona, fazendo com que várias tarefas possam acontecer em tempo e ordens distintas. Mas como o JavaScript consegue fazer isso?

A resposta é simples: o JavaScript consegue organizar as tarefas fazendo o **Event Loop**.

Event Loop é como chamamos o gerenciamento das diversas tarefas que o JavaScript consegue executar de forma assíncrona.

Para isso, o JS faz uso de uma estrutura que empilha as tarefas à medida em que elas são chamadas (Call Stack) e, sempre que uma tarefa não pode ser concluída a tempo, direciona as tarefas pendentes para uma fila de espera (Callback Queue)

Para entender melhor esse conceito, recomendo que você acesse o site: [http://latentflip.com/loupe](http://latentflip.com/loupe). Nele você pode executar o exemplo que acabamos de analisar e acompanhar como o JavaScript gerencia cada passo da execução da tarefa!

> 💡 Se você ainda tem alguma dúvida sobre o que acabamos de falar, recomendo que faça uma estudo mais aprofundado sobre o assunto, antes de continuarmos.
> 
> 
> Deixaremos aqui alguns links de materiais gratuítos, disponíveis na internet, que podem te ajudar a compreender melhor todos os conceitos:
> 
> 1. [https://blog.betrybe.com/tecnologia/callback/](https://blog.betrybe.com/tecnologia/callback/)
> 2. [https://www.javascripttutorial.net/javascript-event-loop/](https://www.javascripttutorial.net/javascript-event-loop/)
> 3. [https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous)

---

## 🤝 O que é uma Promise?

Promise em inglês significa promessa! E quando falamos de Promises no JavaScript, estamos nos referindo a exatamente isso: uma promessa de que algo pode acontecer!

Assim como acontece no mundo real, uma promessa não garante que algo realmanete vá acontecer, afinal, é apenas uma promessa que pode dar certo, ou não.

**Por exemplo:**
Precisamos fazer o upload de fotos para nosso álbum em uma rede social. Ao inciar o processo, você escolhe as fotos que deseja adicionar à sua rede e clica no botão de upload. A partir daí, só nos resta esperar até que todos os arquivos sejam carregados.

Porém, problemas podem acontecer: um dos arquivos pode estar corrompido, a conexão com a internet pode falhar, ou mesmo uma queda de energia em sua casa pode atrapalhar todo o processo. Ou seja, nada garante que o processo vai finalizar com sucesso, o que temos é apenas uma promesa!

Observe que em uma Promise a operação acontece de forma **assíncrona**, pois ela permite que você continue executando outras tarefas enquanto tenta concluir a tarefa que foi 'prometida'. No JavaScript, Promises são objetos e são utilizadas como ferramenta para lidar com as possíveis situações de um código assíncrono.

## Como criar uma Promise?

Como já foi mencionado, Promise é um objeto do JavaScript que permite a execução de códigos de forma assíncrona, logo, sendo um objeto, sua sintaxe de criação é semelhante ao que acontece nas outras linguagens. Para isso, utilizaremos a palavra reservada *new*:

```jsx
  new Promisse ()
```

Todavia, é importante você saber que para funcionar corretamente, uma promise precisa que sejam informadas duas funções como parâmetro, uma para resolver a promise e outra para rejeitá-la:

```jsx
  new Promisse (resolve, reject) => { }
```

As funções **resolve** e **reject**, que são passadas como parâmetro do Objeto Promise, possuem as rotinas que devem ser executadas quando a promise consegue uma resolução, ou sofre algum problema, respectivamente.

## Estados de uma Promise

No momemnto em que lançamos uma promise ela poderá assumir vários estados diferentes ao longo do seu ciclo de execução. Vamos conhecer um pouco sobre esses estados:

- Pending - Estado inicial do objeto quando iniciamos a promise, em espera.
- FulFilled - Estado que indica sucesso na execução da promise.
- Rejected - Estado que indica a rejeição da promise, geralmente causa por algum erro que impeça sua execução.
- Settled - Estado que sinaliza o fim do ciclo de vida da promise, com sucesso ou não.

> Observação: Uma promise é considerada resolvida se for cumprida ou rejeitada, mas não pendente.
> 

## Métodos .then(), .catch() e .finally()
Sempre que uma promise assume o estado **Fulfilled**, significa que ela conseguiu resolver a promessa e possui um resultado, positivo ou negativo.

Nesse caso, podemos utilizar o método **.then()** para tratar esse resultado, exibindo-o no console como segue no exemplo:

```jsx
const promessa = new Promise ((resolve, reject) => {
	setTimeout(() => resolve ('Promessa resolvida'), 2000)
})
 
promessa.then(res => console.log(res))

//Imprime 'Promessa resolvida'
```
Se em todo caso, acontecer algum problema que impeça a execução correta das funções, precisamos definir um tratamento para um possível erro e fazemos isso utilizando o método **.catch()**:

```jsx
const promessa = new Promise((resolve, reject) => {
  //setTimeout(() => resolve("Promessa resolvida"), 2000);
  reject("Ocorreu um problema");
});

promessa
  .then((res) => console.log(res))
  .catch((erro) => console.log(erro));
```
Observe que no código acima, comentamos a linha que define a função 'resolve', simulando uma situação de falha, logo, a função **.catch()** irá executar.

Ao finalizar uma aplicação com promise, podemos utilizar o método **.finally()** para indicar qual ação desejamos executar para confirmar o término da tarefa.

## Exemplo de Aplicação

Podemos entender melhor o uso desses métodos revisando o exemplo que citamos anteriormente, em que você precisa fazer o upload de suas fotos favoritas para sua rede social :

```jsx
let fotos_carregadas = true;

console.log("Upload de fotos");

const promessa = new Promise((resolve, reject) => {
  if (fotos_carregadas) {
    return resolve("Upload completo!");
  }
  return reject("Falha no carregamento!");
});

console.log("aguardando...");

promessa
  .then((result) => console.log(result))
  .catch((erro) => console.log(erro))
  .finally(() => console.log("Fim da Aplicação"));
```
Na primeira linha do nosso exemplo, declaramos uma variável de controle, chamada *fotos_carregdas* que nos dirá se as fotos conseguiram ser carregadas ou não.

Em seguida, exibimos uma mensagem no console para informar a ação que estamos tentando executar.

Na sequência, construímos nossa Promise e utilizamos estruturas de decisão para ajustar o resultado de acordo com a variável de controle, se o valor dela for *true*, significa que as fotos foram carregadas e termos um retorno da função *resolve()*, caso contrário a função *reject()* informará que houve um erro.

Nas últimas linhas do trecho de código, temos a aplicação dos métodos *.then()*, *.catch()* e *.finally()*, imprimindo suas respectivas mensagens no console.


> Existem vários outros métodos que podemos utilizar em conjunto com as promises, porém, os métodos que vimos até aqui já são suficientes para que você consiga desenvovler pequenas aplicações e exercitar os conceitos que vimos hoje!
> 

## Método .all()



# Exercícios

1. Analise o código a seguir:

```jsx
function primeiraTarefa() {
  //Aqui, utilizamos o setTimeout para atrasar propositalmente a execução da primeira tarefa
  setTimeout(function () {
    console.log("Essa é a 1ª Tarefa");
  }, 2000);
}

function segundaTarefa() {
  console.log("Essa é a 2ª Tarefa");
}

primeiraTarefa();
segundaTarefa();
```

Qual função callback é apresentada neste exemplo?

a) primeiraTarefa()

b) setTimeout()

c) function()

d) segundatarefa()

e) console.log()

---

2. Analise o código abaixo e a afirmação que segue?

```jsx
function imprimeNaTela(){
  console.log('Mensagem 01')
  console.log('Mensagem 02')
  console.log('Mensagem 03')
  console.log('Mensagem 04')
}

imprimeNaTela()

console.log('Mensagem 05')
```

Esse código apresenta um modelo de código assíncrono.

a) verdadeiro

b) falso

---

3. Analize o código a seguir para responder à próxima questão:

```jsx
function imprimeNaTela(){
  console.log('Mensagem 01')
  setTimeout( function espera(){
    console.log('Mensagem 02')
    console.log('Mensagem 03')
    console.log('Mensagem 04')}
    , 2000)
}

imprimeNaTela()

console.log('Mensagem 05')
```

Qual a saída será gerada após a execução desse trecho de código?

a)

> Mensagem 05
> 
> 
> Mensagem 01
> 
> Mensagem 02
> 
> Mensagem 03
> 
> Mensagem 04
> 

b)

> Mensagem 05
> 
> 
> Mensagem 04
> 
> Mensagem 03
> 
> Mensagem 02
> 
> Mensagem 01
> 

c)

> Mensagem 01
> 
> 
> Mensagem 05
> 
> Mensagem 03
> 
> Mensagem 04
> 
> Mensagem 02
> 

d)

> Mensagem 01
> 
> 
> Mensagem 02
> 
> Mensagem 03
> 
> Mensagem 04
> 
> Mensagem 05
> 

e)

> Mensagem 01
> 
> 
> Mensagem 05
> 
> Mensagem 02
> 
> Mensagem 03
> 
> Mensagem 04
> 

4. O JavaScript faz uso de uma estrutura que empilha as tarefas à medida em que elas são chamadas (Call Stack) e, sempre que uma tarefa não pode ser concluída a tempo, direciona as tarefas pendentes para uma fila de espera (Callback Queue).

Como chamamos esse recurso do JavaScript?

a) Callback
b) Event Loop
c) Asynchronous
d) Arrow Functions
e) Queue Functions

5. Questão
a) 
b)
c)
d)
e)


---
# Gabarito

Questão 1.

> C
> 

Questão 2.

> B
> 

Questão 3.

> E
> 

Questão 4.

> B
> 

Questão 5.

> C
> 

---

# Recursos Adicionais

- [Loupe](http://latentflip.com/loupe) - Loupe é uma pequena visualização para ajudá-lo a entender como a pilha de chamadas/loop/loop/fila de retorno de chamada do JavaScript interage entre si.
- [CodeSandbox](https://codesandbox.io/) - CodeSandbox é uma plataforma online que permite à você testar seus códigos em fiversaslinguagens, sem se preocupar com a instalação ou configuração de pacotes e bibliotecas.

# Referências

[https://www.markdownguide.org/cheat-sheet/](https://www.markdownguide.org/cheat-sheet/)

[https://blog.betrybe.com/tecnologia/callback/](https://blog.betrybe.com/tecnologia/callback/)

[https://www.javascripttutorial.net/javascript-event-loop/](https://www.javascripttutorial.net/javascript-event-loop/)

[http://rocketseat.com.br](http://rocketseat.com.br/)

[https://www.alura.com.br/artigos/async-await-no-javascript-o-que-e-e-quando-usar](https://www.alura.com.br/artigos/async-await-no-javascript-o-que-e-e-quando-usar)

[https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous)

[https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Using_promises](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Using_promises)

[https://www.devmedia.com.br/programacao-assincrona-em-javascript-com-promises/33184](https://www.devmedia.com.br/programacao-assincrona-em-javascript-com-promises/33184)
