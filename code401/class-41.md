# [ES6 Syntax and Feature Overview](https://www.taniarascia.com/es6-syntax-and-feature-overview/)
- ECMAScript 2015, also known as ES6, introduced many changes to JavaScript.
- Variable declaration
  - ES6 introduced the let keyword, which allows for block-scoped variables which cannot be hoisted or redeclared.
- Constant declaration
  - ES6 introduced the const keyword, which cannot be redeclared or reassigned, but is not immutable.
- Arrow function syntax
  - The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods.
- Template literals
  - Expressions can be embedded in template literal strings.
  - Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.
- Implicit returns
  - The return keyword is implied and can be omitted if using arrow functions without a block body.
- Key/property shorthand
  - ES6 introduces a shorter notation for assigning properties to variables of the same name.
- Method definition shorthand
  - The function keyword can be omitted when assigning methods on an object.
- Destructuring (object matching)
  - Use curly brackets to assign properties of an object to their own variable.
- Array iteration (looping)
  - A more concise syntax has been introduced for iteration through arrays and other iterable objects.
- Default parameters
  - Functions can be initialized with default parameters, which will be used only if an argument is not invoked through the function.
- Spread syntax
  - Spread syntax can be used to expand an array.
- Classes/constructor functions
  - ES6 introducess the class syntax on top of the prototype-based constructor function.
- Inheritance
  - The extends keyword creates a subclass.
- Modules - export/import
  - Modules can be created to export and import code between files.
- Promises/callbacks
  - Promises represent the completion of an asynchronous function. They can be used as an alternative to chaining functions.


# [React - Hello World](https://reactjs.org/docs/hello-world.html)
```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```


# [React - JSX](https://reactjs.org/docs/introducing-jsx.html)
- JSX is a syntax extension to JavaScript.
- use it with React to describe what the UI should look like.
- JSX produces React “elements”.
- React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.
- Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both.

### Embedding Expressions in JSX
- You can put any valid JavaScript expression inside the curly braces in JSX.
```
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

### JSX is an Expression Too
- you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions

```
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}

```

### Specifying Attributes with JSX
- You may use quotes to specify string literals as attributes
```
const element = <div tabIndex="0"></div>;
```
- You may also use curly braces to embed a JavaScript expression in an attribute
```
const element = <img src={user.avatarUrl}></img>;
```


### JSX tags may contain children
```
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```


### By default, React DOM escapes any values embedded in JSX before rendering them. 
- Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent XSS (cross-site-scripting) attacks.
```
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```


### Babel compiles JSX down to React.createElement() calls.
- These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.
- It is recommended to use the “Babel” language definition for your editor of choice so that both ES6 and JSX code is properly highlighted.


# [React - Rendering Elements](https://reactjs.org/docs/rendering-elements.html)
- An element describes what you want to see on the screen:
```
const element = <h1>Hello, world</h1>;
```
- Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.
- Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.
- React elements are immutable. Once you create an element, you can’t change its children or attributes. 
- the only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`.
  - In practice, most React apps only call `ReactDOM.render()` once.
- React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.
  - thinking about how the UI should look at any given moment, rather than how to change it over time, eliminates most bugs.


# [React - Components & Props](https://reactjs.org/docs/components-and-props.html)
- One might confuse elements with a more widely known concept of “components”. Elements are what components are “made of”.
- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
- Components are like JavaScript functions. They accept inputs, called “props” (stands for "properties"), and return React elements describing what should appear on the screen.
- The simplest way to define a component is to write a JavaScript function
  - These are called “function components” because they are literally JavaScript functions
- You can also use an ES6 class to define a component
- When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props”.
-  Always start component names with a capital letter. React treats components starting with lowercase letters as DOM tags.
- Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.
- Typically, new React apps have a single App component at the very top. However, if you integrate React into an existing app, you might start bottom-up with a small component like Button and gradually work your way to the top of the view hierarchy.
- It is recommended to name props from the component’s own point of view rather than the context in which it is being used.
- Whether you declare a component as a function or a class, it must never modify its own props.
- All React components must act like pure functions with respect to their props.
  - Such functions are called “pure” because they do not attempt to change their inputs, and always return the same result for the same inputs.


# [React - State & Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- This tutorial explains how to update a clock by adding local state to the class 
- We want to set up a timer whenever the Clock is rendered to the DOM for the first time. This is called “mounting” in React.
  - We also want to clear that timer whenever the DOM produced by the Clock is removed. This is called “unmounting” in React.
  - We can declare special methods, called “lifecycle methods”, on the component class to run some code when a component mounts and unmounts
- The `componentDidMount()` method runs after the component output has been rendered to the DOM. This is a good place to set up a timer
- Note how we save the timer ID right on this (this.timerID).
- While this.props is set up by React itself and this.state has a special meaning, you are free to add additional fields to the class manually if you need to store something that doesn’t participate in the data flow (like a timer ID).
- We will tear down the timer in the componentWillUnmount() lifecycle method
- implement a method called tick() that the Clock component will run every second.
  - It will use this.setState() to schedule updates to the component local state
- There are three things you should know about setState().
  - Do Not Modify State Directly. Instead, use `setState()`. The only place where you can assign `this.state` is the constructor.
  - State Updates May Be Asynchronous. React may batch multiple `setState()` calls into a single update for performance. Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state. To fix it, use a second form of setState() that accepts a function rather than an object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument
  - State Updates are Merged. When you call `setState()`, React merges the object you provide into the current state. You can update them independently with separate `setState()` calls. The merging is shallow, so `this.setState({comments})` leaves `this.state.posts` intact, but completely replaces `this.state.comments`.
- “top-down” or “unidirectional” data flow is any state that is always owned by some specific component, and any data or UI derived from that state can only affect components “below” them in the tree.
  - Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.
- In React apps, whether a component is stateful or stateless is considered an implementation detail of the component that may change over time. You can use stateless components inside stateful components, and vice versa.


# [React - Handling Events](https://reactjs.org/docs/handling-events.html)
- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.
- You cannot return false to prevent default behavior in React. You must call preventDefault explicitly.
- When using React, you generally don’t need to call addEventListener to add listeners to a DOM element after it is created. Instead, just provide a listener when the element is initially rendered.


# Additional Resources
- [React - Installation](https://reactjs.org/docs/create-a-new-react-app.html)
- [React - Comprehensive Guide](https://ui.dev/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)
- [Understanding Variables, Scope, and Hoisting in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-variables-scope-hoisting-in-javascript)
