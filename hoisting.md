> https://developer.mozilla.org/en-US/docs/Glossary/Hoisting

# Hoisting

## Function Declaration vs Function Expression

Remember: function declarations are hoisted, not function expressions

### Example: Hoisting (function declaration, works)

```js
catName("Tiger");

function catName(name) {
  console.log("My cat's name is " + name);
}
```

Result: `My cat's name is Tiger`

### Example: No Hoisting (function expression, does not work)

```js
catName("Tiger");

const catName = function (name) {
  console.log("My cat's name is " + name);
};
```

Result: `ReferenceError: Cannot access 'catName' before initialization`

## `var` hoisting vs `let`/`const` hoisting

`var` initializes to default of `undefined` when hoisted
`let`/`const` throws exception, no default initialization

JS only hoists declarations, not initializations, even if declared/initialized on same line

```js
var num; // declaration
num = 6; // initialization
```

```js
console.log(num); // returns undefined
var num;
num = 6;
```

In this example, the `num` being logged is from the declaration `var num`, rather than the initialization `num = 6`.