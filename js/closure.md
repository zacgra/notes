> https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures

# Closure

## Lexical scoping

How the parser resolves variable names when functions are nested.

### Nested functions

```js
function init() {
  var name = "Mozilla"; // name is a local variable created by init
  function displayName() {
    // displayName() is the inner function, a closure
    alert(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

displayName() is only available within init(), but has access to name, since it is declared in its outer scope

## Closure Examples

Compare this example to the one Nested functions

### Example 1

```js
function makeFunc() {
  var name = "Mozilla";
  function displayName() {
    alert(name);
  }
  return displayName;
}

var myFunc = makeFunc();
myFunc();
```

The displayName function is returned before being executed.

**How does this still work if it only exists inside the local scope?**

When myFunc() is called, makeFunc() returns a reference to the displayName function. Together with the lexical environment where displayName was declared, this forms a closure. Inside of the lexical environment, name still exists.

### Example 2

```js
function makeAdder(x) {
  return function (y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2)); // 7
console.log(add10(2)); // 12
```

makeAdder is essentially a factory function (returns object without new keyword). It creates functions that add a value to the argument.

```js
let add5 = makeAdder(5); // creates a new function named add5 which takes an argument and adds 5 to it
add5(2); // passes 2 to add5, 2 + 5 = 7
```

add5 is a closure, with the add5 function and the lexical environment of 5 passed as the value for x.

### Practical Example

```js
function makeSizer(size) {
  return function () {
    document.body.style.fontSize = size + "px";
  };
}

var size12 = makeSizer(12);
var size14 = makeSizer(14);
var size16 = makeSizer(16);
```

> add functionality on a page to adjust text size

makeSizer takes a number (int) and returns a function that takes no args and sets the dom style to that specific font size.

## Performance Concerns

Due to not triggering garbage collection, closures will negatively affect memory
