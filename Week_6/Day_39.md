# How REACT & Javascript XML (JSX) works? 

## The difference between Library and Framework

- Framework has all the structure to build an app (like UI, Rounting, HTTP clients, State Management) ex) Angular -> 정해진 틀안에서 정해진 룰만 따라가야한다는 단점이 있다.

- Library is a solution to solve smaller parts like REACT. REACT helps to build UI for other parts, we can use different libraries for that. 리액트가 UI만을 핸들하지만 유명한 라이브러리니만큼 강력한 커뮤니티가 있어서 리액트랑 쓸수있는 다른 라이브러리들이 정말 잘 구성되어있다. 

## what is Javascript XML (JSX)
- It's a special syntax.
- JSX looks like HTML on the surface, but it's a way to write JavaScript.
- Allowing us to easily combine JS with HTML mark up. 
- JSX is a powerful language that allows us to declare how an interface looks.
- It is not a template language but it shares the declarative benefits of one.

- Rules : 
1. All JSX expressions must result in one root level element.
2. All tags must be closed
3. no html comments allowed like <!--- Not allowed --->
4. A child tag must close before its parent.
5. The keywords are camelCase (onClick).


- onClick, onChange, onSubmit
- ***onClick Event Handler***
This event handler will listen to click events on clickable elements, like a ***button***. Using the event parameter will give access to information about the event, like mouse position, timestamp, etc.

- ***onChange Event Handler***
This event handler will listen to change events on input elements, like an ***input or a textarea element***. Using the event parameter will give access to information about the event, like the name of the input and the value that the user typed or selected.

- ***onSubmit Event Handler***
This event handler will listen to submit events on submittable elements, like a ***form***. Using the event parameter will give access to information about the event, like the content of the form, and a method to prevent the default behavior of a form submission.

## what is REACT?

- A javascript library for building user interfaces.
- React has a way to manage the state (the current status of each view) in our application.
- Renders ***UI*** and responds to (reacts to) ***events***
- REACTS === COMPONENTS (box)
- COMPONENTS? A highly cohensive building block for UIs loosely coupled with other components. Isolted, independent, reusable

- 리액트를 잘 만든다는것은 컴포넌트를 잘 만든다는것과 같다. 이 컴포넌트는 독립적이고 재사용이 가능해야한다.

- Always start component names with a capital letter.

- 함수형 컴포넌트는 jsx를 return 한다. - 이 컴포넌트는 이 jsx룰 보여주는 컴포넌트야 라고 알려주는거임.
- Components has state, render and props.
1. STATE : 내부상태 
- 컴포넌트가 가지고 있는 상태값(state)는 useState()라는 함수를 이용해서 변수형태로 상태값을 저장한다. 
2. PROPS : 외부로부터 전달받은 상태
- 외부에서 상태값을 전달할수 있다면 props를 이용해서 함수의 인자로 전달해주면 된다. 
3. RENDER : 상태를 나타냄
4. RERENDER : 상태가 변경될때마다 re-render


- 우리가 html로 작성한 코드가 브라우저에 표기가 되기 위해서는 DOM TREE로 구성이 된다. 
- 이는 리액트도 마찬가지인데 리액트는 가상의 돔트리를 가지고 있다. 
- state가 업데이트가 되었을때 : 리액트는 이전의 트리와 virtual DOM TREE를 비교해서 
변화가 이루어진 node만 DOM TREE에 업데이트를 해줘서 속도가 아주 빠르다. 

5. 실제로 변경된 부분만 화면에 업데이트 된다. 

- REACT HOOKS ? : Hooks are functions that let you hook into React state and lifecycle feature from function component.
- 훅은 커스텀을 하기도 하고 리액트에서 제공된것도 있다. 
- Hooks are starting with USE : useState, useEffect, useRef, useMemo, useCallback, useContext......
- 주의할점: Hooks는 값의 재사용이 아니라 로직의 재사용을 위한것이다. 

### React.createElement

### ReactDOM.render

- Most applications call ReactDOM.render(element, container) a single time to render the application.


```js
ReactDOM.render(
  <Tweet
    name="React"
    avatar="https://api.adorable.io/avatars/64/react@adorable.png"
    content="A JavaScript library for building user interfaces"
    date="May 29th, 2013"
  />,
  document.getElementById("root")
)
```

### Making react app
1. Create HTML file for each component like navigation.html

2. "npx create-react-app react-version" -> to use create-react-app

3. Making js file for each component like Navigation.js

4. npm start in the react-version folder (which is automatically created when we use create-react-app)

5. Delete unnecessary css from css files and jsx from App.js

6. Importing Our Components to App.js
```js
import Navigation from './components/Navigation'
```

7. Showing Our Components 
```js
function App() {
  return (
    <div className="App">
      <Navigation /> 
      <Profile />
      <TweetForm />
      <TweetList />
    </div>
  );
}
```

8. Summary so far : cleaned our App component, imported our newly made components and called them inside its return statement

9. Import the sliced HTML files like taking html part from navigation.html to Navigation.js

10. Importing Styles like Copy the content of original.css into App.css

11. Apply that original structure to our elements in our App component.

```js
//original structure
  <body>
    <nav> ... </nav>
    <aside> ... </aside>
    <main class="container">
      <section class="newtweet"> ... </section>
      <section class="tweets"> ... </section>
    </main>
  </body>
```

12. Copy the additional stylesheet links in the <head> tag of the index.html file 

13. 
```js 
import './App.css';
```

14. Remove hardcoded values and use JSX to show data stored in variables.

```js
  function Profile() {
    const firstName = "Amy"
    const lastName = "Mansell"
    const avatar = "/profile-hex.png"

    return (
      <aside>
        <div className="profile">
          <img className="profile__image" src={avatar} />
        </div>
        <br />
        <div className="profile__name">
          <h2><span className="profile--bold">{firstName}</span> {lastName}</h2>
        </div>
      </aside>
    )
  }



//Tomorrow we will learn about how to pass properties to the component
//to make it more dynamic
```

