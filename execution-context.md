> https://www.freecodecamp.org/news/javascript-execution-context-and-hoisting/

# Execution Context

## Lexical Environment vs Execution Context

The lexial environment is the code written inside of a scope

```js
function doSomething() {
  var age = 7;
  // Some more code
}
```

The block inside doSomething contains the lexical environment where `var age = 7`.

The execution context is how the compiler interprets what is inside the lexical environment.

The execution context manages the lexical environment that the compiler is parsing at any given moment.

## Phases of Execution Context

1 - Tokenizing: chunks code in to tokens, ie `var, age, =, 7, ;`
2 - Parsing: converts tokens in to AST (abstract syntax tree) of nested elements for interpretation by language's grammar
3 - Byte Code: converts AST in to executable byte-code to be optimized by compiler

> AST: https://jotadeveloper.medium.com/abstract-syntax-trees-on-javascript-534e33361fc7
