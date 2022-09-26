# W01D06

#### `Unit testing`
* Unit testing is just writing code that tests other code.
* Testing that our apps work is a task that can be automated by doing unit testing.

#### `BDD`
* BDD or Behavior Driven Development is a process that emerged from test-driven development in 2006.
* BDD covers the entire life cycle of the app development process, from planning the project to writing the code.

#### `BDD Frameworks`
* One of BDD Frameworks is Mocha.

#### `Mocha and Chai`
* Mocha -> Testing Framework
* Chai -> Assertion Library.
* These are very popular packages for testing javascript.

* steps.
1. Create a new folder. (car)
2. Inside the folder, one file (shouldBuyCar.js) & one more folder called test and in the test, one file (carTest.js)
3. On the car directory,
 * `npm init -y` <br>
 * `npm install mocha@9.2.2 chai --save-dev.`
4. Update the scripts object in the package.json to the following
```js
"scripts": {
  "test": "./node_modules/mocha/bin/mocha"
}
```
5. npm start 
6. on the carTest.js
```js
const chai = require('chai'); // 1
const assert = chai.assert;

const shouldBuyCar = require('../shouldBuyCar.js'); // 2

describe("#shouldBuyCar()", function() { // 3

// Happy Path
it("should return true if the user is old enough", function() {
  const user = {
    age: 18 // Edge Case
  };
  const canSignUp = signUpUser(user);
  assert.isTrue(canSignUp);
});

// Sad Path
it("should return false if the user is not old enough", function() {
  const user = {
    age: 17 // Edge Case
  };
  const canSignUp = signUpUser(user);
  assert.isFalse(canSignUp);
});

});
```
7. npm test 


#### `Modules`

* Every file run by Node has access to a module object.
* Modules are its way of organizing code into individual files
* module.exports tells node what to export from a file -> it defaults to {}
* How to check the value of module? `console.log(module);`

* Module export and require

1. on the file we want to require a module from different file, we can use ``require with relative paths (like ./myModule)` -> it doesn't need the .js extension, as that is implied
```js
const sayHelloTo = require('./myModule');

// Just to check the value of what we just required here
console.log('sayHelloTo: ', sayHelloTo);

sayHelloTo('Bernie');
```
2. on the module file, we need to export `module.exports` 
```js
// myModule.js

const sayHelloTo = function(person) {
  console.log(`Hello, ${person}`);
}
// add this line to the end of the file.
module.exports = sayHelloTo;
```

#### `Packages`
* Packages are self-contained code libraries that we can install and use in our projects.

* npm is Node.js's package manager.

* How to install packages?
```js
//how to install package?
1. mkdir chalk-test && cd chalk-test
2. npm init -y
3. open chalk-test on VScode & open package.json
4. npm install chalk@4.1.2
//check if it's installed properly
5. ls -al node_modules
6. "dependencies": {
  "chalk": "^4.1.2"
}
7. //how to use the installed chalk library? -> require
  const chalk = require("chalk");

const message = `Hello ${chalk.yellow("World")}`;
console.log(message);

```
#### `Typed of testing`
* Unit testing
* Integration testing
* Functional testing

#### `New vocabularies`
* `assert` means very similar to expect.