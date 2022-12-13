# JavaScript Promises
## 🤷 O que preciso saber primeiro? 

Antes de iniciarmos nossa jornada, precisamos revisar alguns conceitos fundamentais e características do JavaScript, que podem nos ajudar a entender melhor o funcionamento das Promises. Vamos lá? 😉

### Callbacks, Sincrono, Assíncrono e Event Loop no JavaScript
#### Callback
Também conhecida como chamada de retorno,uma callback é uma função que possui outra função como parâmetro, logo, ela só consegue finalizar a execução de sua tarefa quando a função mais interna (que foi passada como parâmetro) finalizar e retornar um resultado.
são funcções que possuem outras funçõ

###Programação Síncrona
O JavaScript funciona de forma síncrona, ou seja, ele só consegue executar uma tarefa por vez

> 💡 Se você ainda tem alguma dúvida sobre o que acabamos de falar, recomendo que faça uma estudo mais aprofundado sobre o assunto, antes de continuarmos.
> 
> Deixaremos aqui alguns links de materiais gratuítos, disponíveis na internet, que podem te ajudar a compreender melhor todos os conceitos:
> 1. link1
> 2. link2
> 3. link3 

### 

## O que é uma Promise?

---
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
