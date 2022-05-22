# Arrays

Declaring and assigning array

```js
let myArray = [1, 2, 3, 4, 5];
```

Array index starts at 0.

`indexOf` returns -1 in value not in array.

Concatenation

```js
// Don't use plus!  This will convert the array to a string
console.log([1, 2, 3] + [4, 5, 6]); // => 1,2,34,5,6
```

```js
console.log([1, 2, 3].concat([4, 5, 6])); // => [1, 2, 3, 4, 5, 6]
```

`push` and `pop`

```js
let arr = [1, 2, 3];
arr.push(4);
arr.push(5);
console.log(arr); // => [1, 2, 3, 4, 5]
arr.pop();
console.log(arr); // => [1, 2, 3, 4]
```
