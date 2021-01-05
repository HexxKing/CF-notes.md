# [React - Conditional Rendering](https://reactjs.org/docs/conditional-rendering.html)
- In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.
- Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.
- You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change.
- You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical `&&` operator. It can be handy for conditionally including an element
  - It works because in JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false.
  - Therefore, if the condition is true, the element right after && will appear in the output. If it is false, React will ignore and skip it.
  - Note that returning a falsy expression will still cause the element after && to be skipped but will return the falsy expression. In the example below, <div>0</div> will be returned by the render method.
- Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.
- In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.


# [React - Lists & Keys](https://reactjs.org/docs/lists-and-keys.html)
- You can build collections of elements and include them in JSX using curly braces {}.
- A “key” is a special string attribute you need to include when creating lists of elements.
- Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity
- The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys
- When you don’t have stable IDs for rendered items, you may use the item index as a key as a last resort
- We don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.
- If you choose not to assign an explicit key to list items then React will default to using indexes as keys.
- Keys only make sense in the context of the surrounding array.
- A good rule of thumb is that elements inside the `map()` call need keys.
- Keys used within arrays should be unique among their siblings. However they don’t need to be globally unique. We can use the same keys when we produce two different arrays.
- Keys serve as a hint to React but they don’t get passed to your components. If you need the same value in your component, pass it explicitly as a prop with a different name
- JSX allows embedding any expression in curly braces so we could inline the `map()` result
- Sometimes this results in clearer code, but this style can also be abused. Like in JavaScript, it is up to you to decide whether it is worth extracting a variable for readability. Keep in mind that if the `map()` body is too nested, it might be a good time to extract a component.


# [React - Forms](https://reactjs.org/docs/forms.html)
- HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state.
- In most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. The standard way to achieve this is with a technique called “controlled components”.
- In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().
  - We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.
- Since the `value` attribute is set on our form element, the displayed value will always be `this.state.value`, making the React state the source of truth. Since `handleChange` runs on every keystroke to update the React state, the displayed value will update as the user types.
- With a controlled component, the input’s value is always driven by the React state. While this means you have to type a bit more code, you can now pass the value to other UI elements too, or reset it from other event handlers.
- In React, a `<textarea>` uses a `value` attribute instead. This way, a form using a `<textarea>` can be written very similarly to a form that uses a single-line input.
  - `this.state.value` is initialized in the constructor, so that the text area starts off with some text in it.
- React, instead of using this `selected` attribute, uses a `value` attribute on the root `select` tag. This is more convenient in a controlled component because you only need to update it in one place. 
- Overall, this makes it so that `<input type="text">`, `<textarea>`, and `<select>` all work very similarly - they all accept a `value` attribute that you can use to implement a controlled component.
  - You can pass an array into the `value` attribute, allowing you to select multiple options in a `select` tag
- In HTML, an `<input type="file">` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API. Because its value is read-only, it is an uncontrolled component in React. 
- When you need to handle multiple controlled `input` elements, you can add a `name` attribute to each element and let the handler function choose what to do based on the value of `event.target.name`.
- Specifying the value prop on a controlled component prevents the user from changing the input unless you desire so. If you’ve specified a `value` but the input is still editable, you may have accidentally set `value` to `undefined` or `null`.


# [React - Lifting State](https://reactjs.org/docs/lifting-state-up.html)
- Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor.
- In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called “lifting state up”.
- There should be a single “source of truth” for any data that changes in a React application. Usually, the state is first added to the component that needs it for rendering. Then, if other components also need it, you can lift it up to their closest common ancestor. Instead of trying to sync the state between different components, you should rely on the top-down data flow.
- Lifting state involves writing more “boilerplate” code than two-way binding approaches, but as a benefit, it takes less work to find and isolate bugs. Since any state “lives” in some component and that component alone can change it, the surface area for bugs is greatly reduced. Additionally, you can implement any custom logic to reject or transform user input.
- If something can be derived from either props or state, it probably shouldn’t be in the state.
- When you see something wrong in the UI, you can use React Developer Tools to inspect the props and move up the tree until you find the component responsible for updating the state. This lets you trace the bugs to their source


# [React - Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)
- React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.
- Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”. We recommend that such components use the special children prop to pass children elements directly into their output
- React elements like `<Contacts />` and `<Chat />` are just objects, so you can pass them as props like any other data. This approach may remind you of “slots” in other libraries but there are no limitations on what you can pass as props in React.
- Sometimes we think about components as being “special cases” of other components. In React, this is also achieved by composition, where a more “specific” component renders a more “generic” one and configures it with props
- Composition works equally well for components defined as classes
- Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.
- If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.


# [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)
- Start With A Mock, JSON API
- Step 1: Break The UI Into A Component Hierarchy
  - The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names. 
  - But how do you know what should be its own component? Use the same techniques for deciding if you should create a new function or object. One such technique is the single responsibility principle, that is, a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.
  - Since you’re often displaying a JSON data model to a user, you’ll find that if your model was built correctly, your UI (and therefore your component structure) will map nicely. That’s because UI and data models tend to adhere to the same information architecture. Separate your UI into components, where each component matches one piece of your data model.
  - Now that we’ve identified the components in our mock, let’s arrange them into a hierarchy. Components that appear within another component in the mock should appear as a child in the hierarchy
- Step 2: Build A Static Version in React
  - The easiest way is to build a version that takes your data model and renders the UI but has no interactivity. It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing. 
  - To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. props are a way of passing data from parent to child. If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.
  - it’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.
  - At the end of this step, you’ll have a library of reusable components that render your data model. The components will only have render() methods since this is a static version of your app. The component at the top of the hierarchy (FilterableProductTable) will take your data model as a prop. If you make a change to your underlying data model and call ReactDOM.render() again, the UI will be updated. You can see how your UI is updated and where to make changes. React’s one-way data flow (also called one-way binding) keeps everything modular and fast.
- Step 3: Identify The Minimal (but complete) Representation Of UI State
  - Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand.
  - Ask three questions about each piece of data:
    - Is it passed in from a parent via props? If so, it probably isn’t state.
    - Does it remain unchanged over time? If so, it probably isn’t state.
    - Can you compute it based on any other state or props in your component? If so, it isn’t state.
- Step 4: Identify Where Your State Should Live
  - we need to identify which component mutates, or owns, this state.
  - For each piece of state in your application:
    - Identify every component that renders something based on that state.
    - Find a common owner component (a single component above all the components that need the state in the hierarchy).
    - Either the common owner or another component higher up in the hierarchy should own the state.
    - If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
- Step 5: Add Inverse Data Flow
  - Now it’s time to support data flowing the other way: the form components deep in the hierarchy need to update the state 


# Additional Resources
- [React - Comprehensive Guide](https://ui.dev/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)