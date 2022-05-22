# Arrays

## Array.protoype.splice()

```js
array.splice(index, next_n_elements);
```

```js
array.splice(index, next_n_elements, elements_to_insert);
```

Using splice to remove:
Notice that it mutates the original!

```js
let colors = ["red", "yellow", "blue", "green", "orange", "brown", "gray"];
let returnVal = colors.splice(2, 3);
console.log(returnVal); // [ 'blue', 'green', 'orange' ]
console.log(colors); // [ 'red', 'yellow', 'brown', 'gray' ]
```

Using splice to insert:

```js
let colors = ["red", "yellow", "blue"];
let returnVal = colors.splice(1, 0, "RebeccaPurple", "CornflowerBlue");
console.log(colors); // [ 'red', 'RebeccaPurple', 'CornflowerBlue', 'yellow', 'blue' ]
console.log(returnVal); // []
```

Combining removal and insert:

```js
let colors = ["red", "yellow", "blue", "green", "black", "beige"];
let removed = colors.splice(2, 3, "Gainsboro", "Ivory", "Khaki");
console.log(colors); // [ 'red', 'yellow', 'Gainsboro', 'Ivory', 'Khaki', 'beige' ]
console.log(removed); // [ 'blue', 'green', 'black' ]
```

## str.split()

```js
"yellow".split(); // ["yellow"]
"yellow".split(""); // [ 'y', 'e', 'l', 'l', 'o', 'w' ]
```

## arr.join()

```js
let words = ["run", "around", "the", "block"];
let sentence = words.join(" "); // 'run around the block'
```

## Find/Replace with .split() and .join()

```js
let str = "I don't know what I want to eat";
let newStr = str.split("I").join("we");
console.log(newStr); // 'we don't know what we want to eat'
```
