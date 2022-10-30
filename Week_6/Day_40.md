# Data Structures

## Data structures
- Data structure is a broad term that covers all of the ways that we can store data like using variables 
- could be an array or an object to store Data types like undefined, Boolean, Number, String, BigInt, Symbol which hold only one value.

### How to build Date Structures?
1. Determine what data you need
2. Determine what operations you need to perform on the data
3. Organize the data
4. Determine if certain data is related or independent and decide what kind of substructure is needed
5. Start small, then grow your structure


### Building Bigger Data Structures

```js
//nested objects
  {
    "MURB090909": {
      name: "Buddy Murillo",
      studentId: "MURB090909",
      numberOfClasses: 2
    },
    "TAND060606": {
      name: "Dilan Tanner",
      studentId: "TAND060606",
      numberOfClasses: 5
    },
  }
```

### Building Complex Data Structures
```js
  {
    name: "1084",
    type: "Carbon Steel",
    composition:  ['iron', 'carbon', 'manganese', 'phosphorus', 'sulfur'],
    forgingTemp: { min: 900, max: 1200 }
  }
```

### REACT Props???
- What is Props? In React, we pass data to components as "props" (short for properties) and this is an object.

### Passing Props?
- 2 ways
1. 
```js
<Profile firstName="Amy" lastName="Mansel" avatar="/profile-hex.png" />
```
2.
```js
const user = {
  firstName: "Amy",
  lastName: "Mansel",
  avatar: "/profile-hex.png",
};

<Profile {...user} />;
```

### props.children
- props.children contains anything that is inside the tags of a component.

### Inserting the data
1. Organize the data
2. Create helper function to prepare the data
3. Give them to our components. 

### conditional rendering

- Ternary Operator
```js
function Hello(props) { 

  return ( {props.yourName ? <h1>Hello, {props.yourName}.</h1> : <h1>Sorry, you don't seem to have a name.</h1>} );
}
```
- Short Circuit Evaluation
```js
function Hello(props) { 
  return ( {props.yourName && <h1>Hello {props.yourName}</h1>} );
}
```

### quiz

1. HTML attributes affect the element, JSX props are data given to the component.

2.  You can pass down a prop called onClick, but it will need to be called as an attribute on an HTML element if you want the event listener to work.

3.  we re-render our components each time we have state changes, we don't want to slow down our app by redoing everything. Keys help to only re-render what is needed to re-render.
