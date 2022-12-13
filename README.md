# JavaScript Promises
## 🤷 O que preciso saber primeiro? 

Antes de iniciarmos nossa jornada, precisamos revisar alguns conceitos fundamentais e características do JavaScript, que podem nos ajudar a entender melhor o funcionamento das Promises. Vamos lá? 😉

### 🔃 Callback
Também conhecida como chamada de retorno, uma callback é uma função que possui outra função como parâmetro, logo, ela só consegue finalizar a execução de sua tarefa quando a função mais interna (que foi passada como parâmetro) finalizar e retornar um resultado.

Enquanto isso, o JavaScript não trava a execução do código na espera da resposta da primeira função, ele coloca essa função em modo de espera e parte para a próxima tarefa.

**Vejamos um exemplo:**
```
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
Quando rodamos o exemplo acima, temos a impressão de que a função segundaTarefa() é executada primeiro.

Na verdade, a função **primeiraTarefa()** é a primeira a ser executada de fato, porém, como forçamos a execução do setTimeout de 2 segundos, o JavaScript entendeu que não teria a resposta que precisa a tempo e por isso, deixou a função sendo executada em segundo plano, pulando para a linha de comando seguinte, executando a função **segundaTarefa()**.

Depois que a função **segundaTarefa()** finalizou sua execução, o JavaScript retornou para a fila de tareas pendentes e concluiu a função **primeiraTarefa()**.

### ↔️ Sincrono
Síncrono refere-se a comunicação em tempo real onde cada parte recebe ( e se necessário, processa e responde) mensagens instantaneamente (ou o mais próximo possível do instantâneo).

Vamos entender melhor o sincronismo, imagine que você recebe a ligação de um amigo no seu celular, durante a chamada, você e seu amigo conseguem conversar naturalmente, um respondendo ao outro instantaneamente, sem precisar esperar por outras ações.

Na programação, o processo é o mesmo, os códigos que rodam de forma assíncrona conseguem executar seus comandos em sequência, um após o outro, fazendo com que o prrograma execute de forma fluida.

```
function soma(num1, num2) {
  return num1 + num2;
}

console.log(soma(2, 2)) // 4
```
### Assíncrono
Podemos entender a programação assíncrona como sendo a execução de uma tarefa em segundo plano, ou seja, sabendo que o JavaScript vai tentar executar um comando por vez, ele vai separar as tarefas em duas categorias: 
* as tarefas que ele pode executar agora, sem depender de outras rotinas de código 
* as tarefas que ele vai executar depois, quandoo outras rotinas finalizarem.


### Event Loop
Também conhecida como chamada de retorno, uma callback é uma função que possui outra função como parâmetro, logo, ela só consegue finalizar a execução de sua tarefa quando a função mais interna (que foi passada como parâmetro) finalizar e retornar um resultado.


> 💡 Se você ainda tem alguma dúvida sobre o que acabamos de falar, recomendo que faça uma estudo mais aprofundado sobre o assunto, antes de continuarmos.
> 
> Deixaremos aqui alguns links de materiais gratuítos, disponíveis na internet, que podem te ajudar a compreender melhor todos os conceitos:
> 1. link1
> 2. link2
> 3. link3 

### 

## O que é uma Promise?

O sentido de Promise em JavaScript é similar ao literal: Uma pessoa te passa o contato do Telegram e pede para que você mande uma mensagem pra ela, prometendo que vai responder... O que não temos como saber se vai acontecer.

Quando enviamos uma requisição de dados a uma API, temos uma promessa de que estes dados irão chegar, mas enquanto isso não acontece, o sistema deve continuar rodando. Se, por exemplo, o servidor estiver caído, essa promessa de dados pode não se cumprir, e temos que lidar com isso. As Promises trabalham neste contexto - elas são a ferramenta que o JavaScript utiliza para lidar com código assíncrono.

Uma Promise é um proxy para um valor não necessariamente conhecido quando a promise é criada. Ele permite que você associe manipuladores ao valor de sucesso ou motivo de falha de uma ação assíncrona. Isso permite que métodos assíncronos retornem valores como métodos síncronos: em vez de retornar imediatamente o valor final, o método assíncrono retorna uma promise para fornecer o valor em algum momento no futuro.

## Como criar uma Promise?
--


## Estados de uma Promise
---
Uma Promise está em um destes estados:

pending: estado inicial, nem cumprido nem rejeitado.
fulfilled: significa que a operação foi concluída com sucesso.
rejected: significa que a operação falhou.

O estado eventual de uma promise pendente pode ser fulfilled com um valor ou rejected com um motivo (erro). Quando uma dessas opções ocorre, os manipuladores associados enfileirados pelo método then de uma promise são chamados. Se a promise já tiver sido cumprida ou rejeitada quando um manipulador correspondente for anexado, o manipulador será chamado, portanto, não há condição de corrida entre a conclusão de uma operação assíncrona e a anexação de seus manipuladores.

Uma promise é considerada resolvida se for cumprida ou rejeitada, mas não pendente.

![alt text](image.jpg)

## Métodos de uma Promise
---

## Exercícios
---

## Gabarito
---

## Recursos Adicionais
* [Loupe](http://latentflip.com/loupe) - Loupe é uma pequena visualização para ajudá-lo a entender como a pilha de chamadas/loop/loop/fila de retorno de chamada do JavaScript interage entre si.
* [CodeSandbox](https://codesandbox.io/) - CodeSandbox é uma plataforma online que permite à você testar seus códigos em fiversaslinguagens, sem se preocupar com a instalação ou configuração de pacotes e bibliotecas.


## Referências
https://www.markdownguide.org/cheat-sheet/

https://blog.betrybe.com/tecnologia/callback/

http://rocketseat.com.br

https://www.alura.com.br/artigos/async-await-no-javascript-o-que-e-e-quando-usar

https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/Asynchronous

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Using_promises
