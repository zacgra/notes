# Functions

## Function declarations

Function declarations: when a function is defined and saved so that we can use it later.

## Invoking

Using a declared function is 'calling' that function, also known as 'invoking' a function.

A function definition consists of

1. a name
2. a list of parameters
3. the code to be run

JavaScript will only run code once it is invoked, as seen here:

```
console.log("First!");

function callMe() {
  console.log("Second!");
  console.log("Third!");
}

console.log("Fourth!");
```

## Returning a value

JavaScript must explicitly be told to return or else it will return `undefined`.

## Naming Conventions

Great code reads like English and almost explains itself. As programmers, our goal is to write code that is not only correct, but also elegant, readable, and maintainable! Hold yourself to this high standard.

As far as syntax goes in JavaScript, we always name our functions and variables camelCase for multiple words. (Ex: tipCalculator, currentNumber, puppyPartyFinder). Other languages use other conventions so it's best to pick up the standard for your chosen language and stick with it.
