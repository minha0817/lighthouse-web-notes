# W01D05

#### `Objects 'This'`
* `this` points to the object where its function resides.
* `this` refers to the object the method (function) was called on.

```js
const person = {
  firstName: 'Bob',
  lastName:  'Smith',
  fullName: function() {
    return this.firstName + ' ' + this.lastName;
  }
}

// Nice, now I can just say:
console.log('Hello, ' + person.fullName());
// And it's much "cleaner" every time I need their full name!
```

#### `Recursion (재귀함수)`
* This recursion function is calling itself.
* This is a tool we can use as an alternative to traditional iteration using for and while loop.
* Every recursive function must have a base case and a recursive case.
* Each recursive call should break down the current problem into a smaller, simpler one.
* The recursive calls must eventually reach the smallest version of the problem, the base case.
* The base case is when the problem can be solved without further recursion.
```js
let number = 0;
while (number <= 12) {
  console.log(number);
  number += 2;
}
```
```js
1.| function countEvenToTwelve(number) {
2.|   if (number <= 12) { // Recursive Case
3.|     console.log(number);
4.|     // The function will call itself again and get closer to the base case
5.|     countEvenToTwelve(number+2);
6.|   }
7.|   // Base case, do nothing when number > 12
8.| }
9.| countEvenToTwelve(0);
```

