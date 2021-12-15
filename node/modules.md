# Node Module System

## Global Object

The global object is Node’s version of the window object. It is part of the global scope.

Variables and functions we define are not added to the global object. They are scoped to the file.

Some objects and functions available globally in Node:

```js
setTimeout();
clearTimeout();
setInterval(); // repeatedly call a function after delay
clearInterval(); // stop function from being called repeatedly
```

## Modules

Avoid defining variables in the global scope. Use modularity instead.

Every file in a node application is considered a module. The variables and functions we define in the module are private. In order to use them outside the module, they need to be exported and made public.

## Creating a Module

```js
const url = "http://somelogger.com/log";

function log(message) {
  //send an HTTP request
  console.log(message);
}
// add log method to exports in logger.js module
module.exports.log = log;
module.exports.endPoint = url;
```

- if exporting a single function, can set
  export to module.exports like this module.exports = log

- if logger.js exports a single function with module.exports
  then the logger function can be called with logger(message)

## Loading a Module

```js
// load logger.js module from ./logger.js
const logger = require("./logger");
// logger is now an object with the exports from the logger.js file

// if logger is the only exported function, it can be called with
logger(logger);
```

## Module Wrapper Function

At runtime, node converts the module (ie any filename.js) in to a function similar to this:
(immediately invoked function expression, similar to anonymous function, just called when it is encountered by the compiler)

```js
(function (exports, require, module, __filename, __dirname) {
  const url = "http://mylogger.io/log";

  function log(message) {
    //send an HTTP request
    console.log(message);
  }

  module.exports = log;
});
```

**filename = complete path to this file (logger.js)
**dirname = path to the directory that contains the module

Key takeaway: exports and require arts passed to the module wrapper function.

## Path Module

```js
let path = require("path");

let pathObj = path.parse(__filename);

console.log(pathObj);

// logs path object
// {
//   root: '/',
//   dir: '/Users/zach/Code/courses/node',
//   base: 'app.js',
//   ext: '.js',
//   name: 'app'
// }
```

## OS Module

```js
const os = require("os");

var totalMemory = os.totalmem();
var freeMemory = os.freemem();

console.log(`Total Memory: ${totalMemory}`);
console.log(`Free Memory: ${freeMemory}`);
```

## FS Module

Avoid `fs.<method>Sync` (ie Synchronous methods) instead use `fs.<method>` as it is non-blocking
Example: `fs.accessSync` is synchronous/blocking, `fs.access` is async/non-blocking

```js
const fs = require("fs");
```

## Events Module

EventEmitter is a class in the Events module, contains listener methods

```js
const EventEmitter = require("events");
const emmitter = new EventEmitter();

// Register a listener
emmitter.on("messageLogged", function (arg) {
  console.log("Listener called", arg);
});

// Raise an event
emmitter.emit("messageLogged", { id: 1, url: "http://theweb.com" });
```

## Extending

Wrap event emitter inside Logger with extends

```js
// logger.js
const EventEmitter = require("events");

const url = "http://mylogger.io/log";

class Logger extends EventEmitter {
  log(message) {
    //send an HTTP request
    console.log(message);

    // Raise an event
    this.emit("logging", { data: "message" });
  }
}

module.exports = Logger;
```

```js
// app.js
const Logger = require("./logger");

const logger = new Logger();

// Register a listener
logger.on("logging", (arg) => {
  console.log("Logging called", arg);
});

logger.log("message");
```

## HTTP Module

Low-level approach to handling "connection" event

```js
const http = require("http");

const server = http.createServer();

server.on("connection", (socket) => {
  console.log("New connection...");
});
server.listen(3000);

console.log("listening on port 3000...");
```
