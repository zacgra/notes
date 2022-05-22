# Introduction to JavaScript

## The Number Data Type

Basic math operations:

```
+ (addition)
- (subtraction)
* (multiplication)
/ (division)
% (modulo)
```

- Integer divided by Integer = Floating point number
- Order of operations holds

---

## The Boolean Data Type

Logical operators

```
! (not)
&& (and)
|| (or)
```

De Morgan's Law

```
!(A || B) is equivalent to !A && !B
!(A && B) is equivalent to !A || !B
```

---

## Variables

Declaring a variable

```
let bootcamp;
console.log(bootcamp); // undefined
```

Assigning a variable

```
let bootcamp;                   // declared
console.log(bootcamp);          // logs undefined
bootcamp = "App Academy";       // assigned
console.log(bootcamp);          // logs 'App Academy'
```

Shorthand number assignments:

```
let number = 0;
number += 10; // equivalent to number = number + 10
number -= 2; // equivalent to number = number - 2
number /= 4; // equivalent to number = number / 4
number *= 7; // equivalent to number = number * 7
console.log(number); // 14

let year = 3004;
year++;
console.log(year); // 3005
year--;
console.log(year); // 3004
```

NaN - Not a Number
NaN is the result of trying to perform and arithmetic operation on an undefined value.

```let num;
console.log(num + 3); // NaN
```

## Strings

```
// valid string
'Shakespeare wrote, "To be or not to be"';

// invalid string
'That's a bad string'
```

Calculating length

```
console.log("ramen".length); // => 5
```

Indexing a string

```
console.log("bootcamp"[3]); // => 't'
```

indexOf returns -1 if character not in string.

```
console.log("bagel".indexOf("l")); // => 4
console.log("bagel".indexOf("z")); // => -1
```

Concatenation using `+`

```
console.log("hello" + "world"); // => 'helloworld'
console.log("goodbye" + " " + "moon"); // => 'goodbye moon'
```
