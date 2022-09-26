# W01D01

##### * Tips for success 

###### 1. Ask for help 
###### 2. Put in the hours
###### 3. Take breaks, get proper sleep
###### 4. Don't compare yourself to others
###### 5. Comfortable bering uncomfortable
&nbsp;


#### * `Gist` <br>
What is gist?   Share short code.
1. find a gist that I want to clone
2. click the fork button
3. clone via ssh (copy the address)
4. on terminal at where I want to clone,
`git clone <copied address> <new name>`
5. `rm -rf <Directory Name>` if missed giving new name, delete first and clone again.
<br/>


#### * `code linting & Eslint`<br>
* What is code linting? Tool for writing maintanable, consistent code and analyzes source code to flag errors and bugs. <br>
One of the popular code linting tool is Eslint.<br/>
* how to use? `eslint <FileName>` or `eslint .` on terminal. `eslint <FileName> --fix`.
<br/>


#### * `Markdown`

* What is Markdown? Markdown is a simple markup language that allows a developer to easily `format text`. Markdown can also be parsed into HTML, allowing Markdown to be used in webpages.like `.md / .jsx / . js / . css /`


#### * `How to make ReadMe file`
1. make a new repo `mkdir <folderName>`
2. `git init`
3. make a new file in it `touch README.md`
4. `git add <fileName>` <br/>
`git commit -m ""`
5. make a new repo on github and copy the address <br/>
`git remote add origin <copied address>`<br/> `git push -u origin master`

6. and update the file. and keep commiting!!

7. how to make a link? <br/>
`[Name](url / where the files are(/week-1))`



#### * `Process.argv` <br/>

* `Command line arguments` are a common way of getting user input in a program. <br>

* how to access them  is using the `process.argv` array.

```javascript
> node sum.js 10 25
35
const args = process.argv.slice(2);

```

#### * `console.assert` <br/>
* JavaScript has a built-in console.assert function. <br>

* The console.assert function prints to the console for us, the developer, when an expected outcome is not met (fails) so that we can look into why.

```javascript
// FUNCTION IMPLEMENTATION
console.assert(1 === 1); // => nothing happens because true

console.assert(1 === 1.1); // => prints out "Assertion failed" to the terminal


const sum = function(a, b) { 
  return a + b;
}

// TEST CODE
console.assert(sum(1, 2) === 3);
console.assert(sum(1, 20) === 3); // bad / incorrect assertion, and we see it fail!
```

* [MDN: console.assert](https://developer.mozilla.org/en-US/docs/Web/API/console/assert)




#### * `Template Literal` <br/>
* A neat feature of ES6. <br>

* Template literals (aka template strings) allow us to simplify this process while simultaneously being faster and using up less computer memory.


#### * `shortcut`
* VSCODE <br/>
cmd + p => navigate a file  <br>
cmd + shift + f => to search in all files

* Terminal, Chrome
cmd + t => make a new tab 
    

