# <img src="https://cloud.githubusercontent.com/assets/7833470/10423298/ea833a68-7079-11e5-84f8-0a925ab96893.png" width="60"> JavaScript Functions

| Objectives |
| :--- |
| Explain what a function is and why we should use functions |
| Create a function definition based on written specifications |
| Implement functions that incorporate conditionals, loops, and other function calls |
| Identify the scope where a variable is defined |

## What are functions?

A [**function**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions) is a concrete implementation of an algorithm in a computer language. *It is a "subprogram" that encapsulates a specific behavior.*

**Algorithm (abstract):**

```
Take a number, multiply it by itself, and return the product.
```

**Function (concrete):**

```js
var square = function(num) {
  return num * num;
}
```

#### Analogy: Dry Cleaner

Your programs can "hand off" some of their work to functions the way you might hand off tasks to another person. When you take your laundry to a dry cleaner, the dry cleaner returns clean clothes to you a day or two later. You don't have to know how to use the dry cleaning machinery, or even exactly what it does (and maybe the dry cleaner wants to protect a secret step in the process!). Plus, many other customers can go to the same dry cleaner. It's so DRY!

```js
var dryClean = function(dirtyClothes) {
  // code that turns dirtyClothes into cleanClothes
  return cleanClothes;
}
```

## Why use functions?

> "Functions are the bread and butter of JavaScript programming.

> The concept of wrapping a piece of program in a value has many uses.

> It is a tool to structure larger programs, to reduce repetition, to associate names with subprograms, and to isolate these subprograms from each other."

> -Marjin Haverbeke, *Eloquent Javascript*

#### Benefits of Using Functions

* **Encapsulation** - Keeping code for the same purpose in the same place makes finding it and updating it easier.

* **Code Reuse** - "Don't Repeat Yourself" is a principle of coding - keep your programs **DRY**! Reusing code makes it easier to change how your program works, since you only have to make updates in one place. If you find yourself writing the same code two or more times, a good rule of thumb is to move it into a function!

## Defining a Function

#### Function declaration

```js
function greet() {
  console.log("Hello, there!");
}
```

*A function declaration is [hoisted](http://www.sitepoint.com/demystifying-javascript-variable-scope-hoisting/#hoisting) to the top of your code. This means you can call your function above its definition, since the definition moves to the top when your code runs.*

```js
greet();

function greet() {
  console.log("Hello, there!");
}

// prints "Hello, there!"
```

#### Function expression

```js
var greet = function() {
  console.log("Hello, there!");
}
```

*When using a function expression, you must define the function above where you call it in your code.*

```js
greet();

var greet = function() {
  console.log("Hello, there!");
}

// Uncaught ReferenceError: greet is not defined
```
---
It is acceptable to use either function declarations or function expressions to define your functions, but make sure to consistently stick to the same convention.

## Components of a Function

The **parameters** are what you declare as being passed into the function in its definition.

```js
var iHaveParameters = function(firstParam, secondParam, thirdParam) {
  // do something with the parameters
}
```

The **arguments** are what is actually passed into the function when called.

```js
iHaveParameters("one", 2, 3.33);
```

The **return statement** is what the function outputs. Only one value returns from a function, and any code after the return statement won't run.

```js
var functionThatReturns = function() {
  return true; // returns true
  var sum = 2 + 2; // doesn't run
}
```

The **function body** is everything inside the actual function.

```js
var whatsInside = function() {
  var sum = 2 + 2; // start function body
  console.log(sum);
  return sum; // end function body
}
```
---
We say that a function **takes in arguments** and **returns** something to us. You can imagine JavaScript control flow as a person talking on the phone with your program. When you call a function, it's like JS puts the main program on hold and contacts the function. If another function is called, JS puts the first function on hold to contact the new one. When the function finishes, JS returns to the previous call.

To keep track of the functions JS has on hold, it uses a **call stack**. As JS calls a new function, it pushes the function onto the call stack. When a function returns, it pops that function off of the call stack.

![](http://i.stack.imgur.com/4Z6xK.png)

* Some computer science languages refer to functions as methods. The same call-stack structure shown in the diagram applies to JavaScript functions.

## Scope

Scope represents the area of your program where a variable is defined. JavaScript has two scopes: **global scope** and **local scope**.

You can think of scope as a rule: *a new function introduces a new scope.*

```js
// global scope
var x = 1;

var changeNum = function (x) {
  // local scope
  x = 2;
}

changeNum(x);

console.log(x)
// logs what?
```

## Callbacks

A **callback** is a function that is passed into another function. A function that can take a callback is known as a **first-class function**.

```js
var consoleMe = function(message) {
  console.log("I'm the callback, now displaying message...");
  console.log(message);
}

var firstClassFunction = function(message, callback) {
  console.log("I'm the first class function, now calling the callback...");
  callback(message);
}

firstClassFunction("Functions are fun!", consoleMe);
```

## Challenges

Fork and clone <a href="https://github.com/sf-wdi-24/functions-basics-challenges">this</a> repo to begin the challenges.




## Evening Challenges

Fork and clone the <a href="https://github.com/sf-wdi-24/functions-challenges" target="_blank">functions-challenges</a> repo, and work through the challenges.  When you are finished, submit a pull request.


## Further Reading

* [Functions - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)
* [Functions - Eloquent JavaScript](http://eloquentjavascript.net/03_functions.html)
* [Demystifying JavaScript Variable Scope and Hoisting](http://www.sitepoint.com/demystifying-javascript-variable-scope-hoisting)