# W02D05 - Object Oriented Programming (OOP), Class, a fundamental concept in software development.

### OOP
* We use objects to group related variables & functions together. 
* Object's keys === properties
* Object has state & behaviour/ state is property and behavior is method.

* OOP's goals are to help us with code organization, re-use and modularity. 
* Object Oriented Programming (OOP) is a programming paradigm where we use objects to encapsulate (group) data and behaviour.
1. To reduce duplicated code (reusability)
2. To break code up into sensibly-divided units (modularity)


```js
const dog = {
  sound: "woof", //state
  dogBreed: "shih tzu", //state
  speak: function() {
    console.log(`${this.dogBreed} says ${this.dogSound}`);
  } //method
};
```

### this 
* use `this` whenever your method is accessing a property or another method on the same object. 
```js
const dog = {
  sound: "woof",
  speak: function() {
    console.log(this.sound);
  },
  teachMeSomething: function() {
    if (dog === this) {
      console.log('dog === this');
    }
    this.speak();
  }
};

dog.teachMeSomething();
```
### Class
* Class is like a template, blueprints to make a object. 
* It has class, constructor, function .
* Constructor: it's the best place to set up any default property values not a method.  
```js
class Pizza {

  constructor(size, crust) {
    this.size = size;
    this.crust = crust;
    this.toppings = ["cheese"];
  }

  addTopping(topping) {
    this.toppings.push(topping);
  }

}
```
```js
let pizza = new Pizza('large', 'thin');
```

#### `Inheritance`
* we can build a new class based on an existing class.using `extends`.
* When there's repeatition of code in classes, we can make `super class` for repeated code and make another class which is `subclass` and use with `extends`.

```js
class Student extends Person {
  // stays in Student class since it's specific to students only
  enroll(cohort) {
    this.cohort = cohort;
  }
}

class Mentor extends Person {
  // specific to mentors
  goOnShift() {
    this.onShift = true;
  }
```

#### Super

* Using super in the overriding methods in order to avoid repeating code that's already present in the superclass.

* when we want to add more on extends. we can use `super`
```js
class Mentor extends Person {
  // Mentor bios need to include a bit more info
  bio() {
    return `I'm a mentor at Lighthouse Labs. ${super.bio()}`;
  }
}
```
#### Getters and Setters

class Pizza {
* Setters : allow us to validate data before assigning it to a property.

* Getters: allow us to compute a value on the fly instead of simply pulling it out of a property. 


```js
  // replace our custom getters / setters with these ones!
  get price() {
    const basePrice = 10;
    const toppingPrice = 2;
    return basePrice + this.toppings.length * toppingPrice;
  }

  set size(size) {
    if (size === 's' || size === 'm' || size === 'l') {
      this._size = size;
    }
  }
}
```

