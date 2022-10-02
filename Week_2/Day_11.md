# W02D04 - Promise, HTTP, HTTP APIs, JSON data format 

### Review aboout asynchronous programming & callback 
* When we do asynchronous programming, `we use call back a lot to make sure that we are in the proper scope` when we receive information or data. 

* We use callback for code `reusability and modularity `
* Callback chaining -> The reason why we use callback chaining is that sometimes we have multiple asynchornous functions working together. So, one function gives its result to the other one, and so on and so on. 
====> why we use callback? 1. Asynchronous programming 2. modularity.

### Promise
* for handling errors and handling asynchronous functions. 


### JSON
* Javascript Object Notation.
* JSON is built on 2 structures. 1. A collection of name/value pairs. 2. An ordered list of values.
```js
//JSON file looks like this. the keys are always double-quoted "strings".
{
  "name": "New York City",
  "boroughs": [
    "Manhattan",
    "Queens",
    "Brooklyn",
    "The Bronx",
    "Staten Island"],
  "population": 8491079,
  "area_codes": [212, 347, 646, 718, 917, 929],
  "position": { "lat": 40.7127, "lng": -74.0059 }
}
```
* Serialization : converts Object -> String. `JSON.stringify()`
* Deserialization: converts String -> Object. `JSON.parse()`
* Objects are an easy way to store key-value data, So, this JavaScript Object Notation is used to store configuration/setting information in files (such as package.json) and how we can easily use two methods on the JSON object to convert between actual object and string representation of that data.


### APIs
* Application Programming Interface.
* It allows systems to work together. 
* APIs are sets of requirements that govern how one app can talk to another. 
* APIs can access to a specific set of features. 
* APIs are great time saver. 