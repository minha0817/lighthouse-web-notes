# W01D04 - Callbacks!
### To Do
- [x] Functions as values
- [x] Callbacks and higher order functions
- [x] Anonymous functions
- [x] Arrow functions
- [x] Make our own higher order function

map, filter, reduce


### `Functions as Values`
- Just like everything else in JavaScript, functions are values
- As a result, they can be stored in variables just like any other value

```js
// function expression 
const myFunction = function() {
  // do something
};
```

2015 ES6 ECMAScript version 6
- They can also be passed around just like any other variable => function expression 

```js
const myFunction = function() {
  // do something
}
array
object
function
const myVar = myFunction;
myVar(); // equivalent to calling myFunction()
```

* Use `for..of` with everything except objects because Of and Object both start with 'O'
- And they can be passed to other functions as arguments

```js
const myFunction = function() {
  // do something
}
```
`Callback` = a function that gets passed to another function to be called by that function
Higher Order Function (HOF) = a function that accepts another function as an argument OR a function that returns another function
```js
const myHigherOrderFunction = function(callback) {
  callback(); // equivalent to myFunction()
}
$()
jQuery.ajax()
myHigherOrderFunction(myFunction);
```

#### `Callbacks and Higher Order Functions`
- A callback is a function that gets passed to another function to be executed by that function
- Callback functions are used all over the place in JavaScript
- They encapsulate reusable code that can be passed around like any other JS variable
- We call the function that accepts another function as an argument a **higher order function**
- Higher Order Function is any functions which operate on other functions.

#### `Anonymous Functions`
- We can pass callback functions _inline_ to a higher order function rather than storing the callback in a variable first

```js
function example() {
  return condition1 ? value1
        : condition2 ? value2
        : condition3 ? value3
        : value4;
const myHigherOrderFunction = function(callback) {
  callback();
}
// the function we pass as an argument has no name
myHigherOrderFunction(function() {});
```

- Anonymous functions are simply functions that do not have a name
- [Naming things is hard](https://martinfowler.com/bliki/TwoHardThings.html)

#### `Arrow Functions`
- Arrow functions give us a syntactic alternative to using the `function` keyword

```js
const myObj = {
  name: 'alice',
  sayHello: function () {
    return `hello ${this.name}`;
  }
// function keyword
const myFunc = function() {
  // do something
};
// arrow function
const myArrowFunc = () => {
  // do something
};
```

- There are some _gotchas_ around using the `this` keyword inside an arrow function, but if you aren't using `this`, arrow functions can be used interchangeably with "regular" functions
- Arrow functions are often used as callbacks because they are shorter/cleaner to type

```js
arr.forEach(function(element) {});
// vs
arr.forEach((element) => {});
```

### Useful Links
* [Wikipedia: Callbacks](https://en.wikipedia.org/wiki/Callback_(computer_programming))
* [MDN: Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

#### `VIM`


#### `New Vocabularies`
* We assign a function to our variable myFn.
* runner.someAttribute = 42; -> .someAttribute is called `attribute`.
* A runner function is defined that runs the argument f that we pass it. `function runner (f) { f() };`
* fat arrow =>
* mutable
* hosting : It takes variable declaration to the top of the document. 