# JavaScript

> Boas práticas

## Sumário

- [JavaScript](#javascript)
    - [Sumário](#sum%C3%A1rio)
    - [Geral](#geral)
    - [Variáveis](#vari%C3%A1veis)
    - [Condicionais](#condicionais)
    - [Objetos](#objetos)
    - [Arrays](#arrays)
    - [jQuery](#jquery)
    - [Referências](#refer%C3%AAncias)

[[⬅ Voltar para Boas Práticas]](https://github.com/CTVoicer/Guidelines/tree/master/boas-praticas)

## Geral

- Use ES6 sempre que seu código for compilado por um pré-processador. ES6 te permite utilizar diversas novas técnicas e recursos [(?)](https://victorvhpg.github.io/2016/11/12/es6.html).

[[⬆ Topo]](#sum%C3%A1rio)

## Variáveis

- Use `var`, `let` ou `const` para declarar variáveis. Quando você declara uma variável sem estas keywords, ela vaza para o escopo global.

```javascript
// ruim
me = 'globalization'

// bom
var me = 'better this way'
```

- Declare variáveis acima de sua chamada. Isto impede o [*variable hoisting*](http://hugobessa.com.br/posts/entendendo-escopo-e-hoisting-no-javascript/).

```javascript
// ruim
var john = person // => null

// ruim
var john = person // => undefined
var person = { age: 23 }

// bom
var person = { age: 23 }
var john = person // => { age: 23 }
```

- Evite variáveis globais. Ao atingirem o escopo global, as variáveis podem ser acessadas por qualquer um. Além disso, uma variável pode tomar o valor de outra se tiverem o mesmo nome. Evite ao máximo expor variáveis globalmente.

- Use *Immediately-Invoked Function Expression* para expor somente as variáveis necessárias ao escopo global. [(?)](http://gregfranko.com/blog/i-love-my-iife/)

```javascript
(function () {
  var Person = {
    // ...
  }

  var PublicPerson = {
    // ...
  }

  window.PublicPerson = PublicPerson

  console.log(Person) // => Person
  console.log(PublicPerson) // => PublicPerson
}())

console.log(Person) // => ReferenceError: Person is not defined
console.log(PublicPerson) // => PublicPerson
```

- Use ao menos o [Module Pattern](http://viralpatel.net/blogs/javascript-module-pattern/). É recomendado que você utilize [AMD](http://requirejs.org/docs/whyamd.html) ou [CommonJS](http://wiki.commonjs.org/wiki/CommonJS) em seus projetos.

- Prefira objetos a muitos parâmetros.

```javascript
// ruim
const setUserInfo = function (user, firstName, lastName, birthDay, gender) {
  user.firstName = firstName
  user.lastName = lastName

  // ...
}

// bom
const setUserInfo = function (user, info) {
  user.firstName = info.firstName
  user.lastName = info.lastName

  // ...
}
```

[[⬆ Topo]](#sum%C3%A1rio)

## Condicionais

- Prefira `===` e `!==` em comparações. [(?)](http://stackoverflow.com/questions/359494/does-it-matter-which-equals-operator-vs-i-use-in-javascript-comparisons)

```javascript
// ruim
5 == '5'        // => true
5 == 6          // => false
5 == 5          // => true

0 == false      // => true
0 == ''         // => true
0 == ' \n\t\r ' // => true
0 == 1          // => false

// bom
5 === '5'       // => false
5 === 6         // => false
5 === 5         // => true

0 === false     // => false
0 === ''        // => false
0 === 0         // => true
```

[[⬆ Topo]](#sum%C3%A1rio)

## Objetos

- Use a sintaxe literal para declarar objetos.

```javascript
// ruim
let item = new Object()

// bom
let item = {}
```

- Não use [palavras reservadas](http://es5.github.io/#x7.6.1) como chaves. Isso não funciona em alguns browsers.

```javascript
// ruim
let superman = {
  default: {
    clark: 'kent'
  },
  private: true
}

// bom
let superman = {
  defaults: {
    clark: 'kent'
  },
  hidden: true
}
```

- Use sinônimos para palavras reservadas.

```javascript
// ruim
let superman = {
  class: 'alien'
}

// ruim
let superman = {
  klass: 'alien'
}

// bom
let superman = {
  type: 'alien'
}
```

[[⬆ Topo]](#sum%C3%A1rio)

## Arrays

- Use a sintaxe literal para declarar arrays.

```javascript
// ruim
var list = new Array()

// bom
var list = []
```

- Use `Array.push()` se você não sabe o `length`.

```javascript
var someStack = []

// ruim
someStack[someStack.length] = 'abracadabra'

// bom
someStack.push('abracadabra')
```

[[⬆ Topo]](#sum%C3%A1rio)

## jQuery

- Utilize jQuery apenas quando for realmente muito necessário [(?)](https://tableless.com.br/considere-nao-usar-jquery/).

- Faça cache de objetos jQuery. Isso evita problemas de performance e facilita a manutenção do código.

```javascript
// ruim
$('.sidebar').hide()
$('.sidebar').css({
  'background-color': 'pink'
})

// bom
var $sidebar = $('.sidebar')

$sidebar.hide()
$sidebar.css({
  'background-color': 'pink'
})
```

- Prefira DOM queries. Use `find` em objetos jQuery já existentes. [Teste no jsPerf](http://jsperf.com/jquery-find-vs-context-sel/16).

```javascript
// ruim
$('ul', '.sidebar').hide()

// ruim
$('.sidebar').find('ul').hide()

// bom
$('.sidebar ul').hide()

// bom
$('.sidebar > ul').hide()

// bom
$sidebar.find('ul').hide()
```

[[⬆ Topo]](#sum%C3%A1rio)

## Referências

- [Coding Style por @LFeh](https://github.com/LFeh/coding-style#js): Uma parte dos exemplos daqui vieram deste ótimo guia por [@LFeh](https://github.com/LFeh).
- [JavaScript por @airbnb](https://github.com/airbnb/javascript): Um guia muito completo sobre como escrever bom JavaScript
- [[Livro] Learning JavaScript Design Patterns](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)
- [[Livro] Build Better Applications with Coding and Design Patterns](http://shop.oreilly.com/product/9780596806767.do)

[[⬆ Topo]](#sum%C3%A1rio)
