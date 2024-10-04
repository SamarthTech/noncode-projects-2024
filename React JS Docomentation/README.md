# React JS Documentation

For the official React  documentation, please refer to the [React documentation website](https://react.dev/)
## Table of Contents

1. [Introduction](#1-introduction)
2. [Installation](#2-installation)
3. [Creating a New React App](#3-creating-a-new-react-app)
4. [React Components](#4-react-components)
   - [Function Components](#41-function-components)
   - [Class Components](#42-class-components)
5. [JSX](#5-jsx)
6. [Props](#6-props)
7. [State](#7-state)
8. [Lifecycle Methods](#8-lifecycle-methods)
9. [Handling Events](#9-handling-events)
10. [Conditional Rendering](#10-conditional-rendering)
11. [Lists and Keys](#11-lists-and-keys)
12. [Forms](#12-forms)
13. [Built-in React Hooks](#13-built-in-react-hooks)
    - [State Hook](#131-state-hooks)
    - [Context Hooks](#132-context-hooks)
    - [Ref Hooks](#133-ref-hooks)
    - [Effect Hooks](#134-effect-hooks)
    - [Performance Hooks](#135-performance-hooks)
    - [Other Hooks](#136-other-hooks)
14. [All Hooks](#14-all-hooks)  
    - [useState](#141-usestate)  
    - [useReducer](#142-usereducer)  
    - [useContext](#143-usecontext)  
    - [useRef](#144-useref)  
    - [useImperativeHandle](#145-useimperativehandle)  
    - [useEffect](#146-useeffect)
    - [useLayoutEffect](#147-uselayouteffect)  
    - [useInsertionEffect](#148-useinsertioneffect)  
    - [useMemo](#149-usememo)  
    - [useCallback](#1410-usecallback)  
    - [useTransition](#1411-usetransition)  
    - [useDeferredValue](#1412-usedeferredvalue)  
    - [useDebugValue](#1413-usedebugvalue)  
    - [useId](#1414-useid)  
    - [useSyncExternalStore](#1415-usesyncexternalstore)  
    - [useActionState](#1416-useactionstate)  
15. [Routing](#15-routing)
16. [React Redux](#16-react-redux)
17. [Redux Toolkit](#17-redux-toolkit)

---

## 1. Introduction

React is a popular JavaScript library for building user interfaces, especially single-page applications. It allows developers to create reusable UI components. React was created by Facebook and is maintained as an open-source project. 

---

## 2. Installation

To install React, you'll need Node.js and npm (Node Package Manager).

### Steps:
1. Install Node.js from [Node.js official site](https://nodejs.org/).
2. Verify Node.js and npm installation by running:
   ```bash
   node -v
   npm -v
   ```
   ---
3. React can be installed using npm or Yarn:
```bash
npx create-react-app my-app
cd my-app
npm start
```
## 3. Creating a New React App
The easiest way to start with React is to use create-react-app, a CLI tool to create new React projects with sensible defaults.
###  Steps:
1. Open a terminal and run:
```bash
npx create-react-app my-app
cd my-app
npm start
```
2. Your app will open in a browser at http://localhost:3000.

## 4. React Components
Components are the building blocks of any React application. A component can be a function or a class.
### 4.1 Function Components
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
### 4.2 Class Components
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
## 5. JSX
JSX is a syntax extension for JavaScript that looks similar to HTML. It is used with React to describe what the UI should look like.
```jsx
const element = <h1>Hello, world!</h1>;
```
## 6. Props
Props are inputs to a React component. They are passed to the component via HTML attributes.
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
## 7. State
State is a way to store information that can change over the lifetime of a component.

### Example with Class Component:
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
  
  render() {
    return <h1>Count: {this.state.count}</h1>;
  }
}
```
## 8. Lifecycle Methods
Class components have several lifecycle methods that are called at different stages of the component’s life.
1. componentDidMount: Runs after the component is mounted.
2. componentDidUpdate: Runs after the component is updated.
3. componentWillUnmount: Runs before the component is unmounted.
```jsx
class App extends React.Component {
  componentDidMount() {
    console.log("Component Mounted");
  }
  render() {
    return <h1>Hello World!</h1>;
  }
}
```
## 9. Handling Events
Handling events in React is similar to handling events in DOM elements, but with some differences in syntax.
```jsx
function Button() {
  function handleClick() {
    alert('Button was clicked');
  }

  return <button onClick={handleClick}>Click Me</button>;
}
```
## 10. Conditional Rendering
In React, you can create distinct components that encapsulate behavior you need and render them based on the state of the application.
```jsx
function UserGreeting() {
  return <h1>Welcome back!</h1>;
}

function GuestGreeting() {
  return <h1>Please sign up.</h1>;
}

function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}
```
## 11. Lists and Keys
Rendering lists in React requires a unique key prop to identify elements efficiently.
```jsx
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>{number}</li>
  );
  return <ul>{listItems}</ul>;
}
```
## 12. Forms
Forms in React work similarly to HTML forms, but with controlled components that manage the state.
```jsx
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = { value: '' };
  }

  handleChange = (event) => {
    this.setState({ value: event.target.value });
  }

  handleSubmit = (event) => {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```
## 13. Built-in React Hooks
Hooks let you use different React features from your components. You can either use the built-in Hooks or combine them to build your own.

### 13.1 State Hooks
State lets a component “remember” information like user input. For example, a form component can use state to store the input value, while an image gallery component can use state to store the selected image index.  
To add state to a component, use one of these Hooks:  
1. [`useState`](#141-usestate) declares a state variable that you can update directly.  
2. [`useReducer`](#142-usereducer) declares a state variable with the update logic inside a reducer function.
```jsx
function ImageGallery() {
  const [index, setIndex] = useState(0);
  // ...
```
### 13.2 Context Hooks
Context lets a component receive information from distant parents without passing it as props. For example, your app’s top-level component can pass the current UI theme to all components below, no matter how deep.  
1. [`useContext`](#143-usecontext) reads and subscribes to a context.
```jsx
function Button() {
  const theme = useContext(ThemeContext);
  // ...
```
### 13.3 Ref Hooks
Refs let a component hold some information that isn’t used for rendering, like a DOM node or a timeout ID. Unlike with state, updating a ref does not re-render your component. Refs are an “escape hatch” from the React paradigm. They are useful when you need to work with non-React systems, such as the built-in browser APIs.  
1. [`useRef`](#144-useref) declares a ref. You can hold any value in it, but most often it’s used to hold a DOM node.  
2. [`useImperativeHandle`](#145-useimperativehandle) lets you customize the ref exposed by your component. This is rarely used.
```jsx
function Form() {
  const inputRef = useRef(null);
  // ...
```
### 13.4 Effect Hooks
Effects let a component connect to and synchronize with external systems. This includes dealing with network, browser DOM, animations, widgets written using a different UI library, and other non-React code.  
1. [`useEffect`](#146-useeffect) connects a component to an external system.
```jsx
function ChatRoom({ roomId }) {
  useEffect(() => {
    const connection = createConnection(roomId);
    connection.connect();
    return () => connection.disconnect();
  }, [roomId]);
  // ...
}
  ```
  Effects are an “escape hatch” from the React paradigm. Don’t use Effects to orchestrate the data flow of your application. If you’re not interacting with an external system, you might not need an Effect.  
  There are two rarely used variations of useEffect with differences in timing:  
  1. [`useLayoutEffect`](#147-uselayouteffect) fires before the browser repaints the screen. You can measure layout here.  
  2. [`useInsertionEffect`](#148-useinsertioneffect) fires before React makes changes to the DOM. Libraries can insert dynamic CSS here.

  ### 13.5 Performance Hooks
  A common way to optimize re-rendering performance is to skip unnecessary work. For example, you can tell React to reuse a cached calculation or to skip a re-render if the data has not changed since the previous render.  
  To skip calculations and unnecessary re-rendering, use one of these Hooks:  
  1. [`useMemo`](#149-usememo) lets you cache the result of an expensive calculation.
  2. [`useCallback`](#1410-usecallback) lets you cache a function definition before passing it down to an optimized component.
  ```jsx
  function TodoList({ todos, tab, theme }) {
  const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
  // ...
  }
 ```
 Sometimes, you can’t skip re-rendering because the screen actually needs to update. In that case, you can improve performance by separating blocking updates that must be synchronous (like typing into an input) from non-blocking updates which don’t need to block the user interface (like updating a chart).  
 To prioritize rendering, use one of these Hooks:  
 1.  [`useTransition`](#1411-usetransition) lets you mark a state transition as non-blocking and allow other updates to interrupt it.
 2. [`useDeferredValue`](#1412-usedeferredvalue) lets you defer updating a non-critical part of the UI and let other parts update first.

 ### 13.6 Other Hooks
 These Hooks are mostly useful to library authors and aren’t commonly used in the application code.  
 1. [`useDebugValue`](#1413-usedebugvalue) lets you customize the label React DevTools displays for your custom Hook.
 2. [`useId`](#1414-useid) lets a component associate a unique ID with itself. Typically used with accessibility APIs.
 3. [`useSyncExternalStore`](#1415-usesyncexternalstore) lets a component subscribe to an external store.
 4. [`useActionState`](#1416-useactionstate) allows you to manage state of actions.

## 14. All Hooks
### 14.1 useState
The useState hook in React allows components to store and manage state. Here’s a summary of key points from the documentation:  
1. **Basic Syntax:**
```jsx
const [state, setState] = useState(initialState)
```
2. **Initial State:**
- Can be any value (number, string, object, etc.).  
- If you pass a function, it is treated as an initializer and only runs once during the first render.
3. **State Setter (setState):**
- Used to update state and trigger a re-render.
- You can pass either the new state directly or a function that calculates the new state from the previous one.
4. **Usage Examples:**
- Basic Counter: setCount(count + 1);
- Updating Objects/Arrays: Use a new object/array, don’t mutate the current state:
```jsx
setForm({ ...form, firstName: 'Taylor' });
```
5. **Performance Optimizations**
- Use an initializer function to avoid recalculating expensive initial state on each render.
6. **Common Issues**
- Logging state immediately after setting it returns the old value (as the update happens asynchronously).
- Avoid re-render loops by ensuring setState is not called unconditionally inside the render.  
7. **Caveats**
- React batches state updates for performance.
- In development, React may call state initializers/updaters twice to detect impure functions.  
You can find more details [here](https://react.dev/reference/react/useState)
### 14.2 useReducer
The useReducer hook in React provides a way to manage state using a reducer function. Here are the key points from the documentation:  
1. **Basic Syntax:**
```jsx
const [state, dispatch] = useReducer(reducer, initialArg, init?)
```
- reducer: A pure function that receives the current state and an action, and returns the next state.
- initialArg: The initial state value.
- init?: An optional initializer function for computing the initial state.
2. **Reducer Function:**
- The reducer function defines how the state changes in response to actions.
- It typically uses a switch statement to handle different action types:
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'incremented_age':
      return { ...state, age: state.age + 1 };
    default:
      throw Error('Unknown action');
  }
}
```
3. **Dispatch:**
- The dispatch function triggers state updates by passing actions to the reducer.
- Example:
```jsx
dispatch({ type: 'incremented_age' });
```
4. **Initializer Function:**
- Used to compute expensive initial state and avoid recalculating it on every render:
```jsx
const [state, dispatch] = useReducer(reducer, initialArg, createInitialState);
```
5. **Comparison to useState:**
- useReducer is often preferred for managing complex state logic, especially when multiple actions are needed to update the state.
6. **Common Issues:**
- Logging state immediately after dispatch returns the old value (due to state updates being queued).
- Avoid mutating state directly in the reducer.  
More details can be found [here](https://react.dev/reference/react/useReducer)

### 14.3 useContext
The useContext hook in React allows components to read and subscribe to a context, enabling sharing of values across different parts of the component tree without passing props manually.
1.  **Basic Syntax:**
```jsx
const value = useContext(SomeContext)
```
- SomeContext is a context created using createContext.
2. **Usage:**
- Call useContext in a component to access the nearest context provider’s value. If no provider is found, it falls back to the default value provided in createContext.
3. **Providing Context:**
- Wrap a parent component in SomeContext.Provider to supply the context value to children:
```jsx
<SomeContext.Provider value={someValue}>
  <ChildComponent />
</SomeContext.Provider>
```
4. **Context Updates**
- To update the context value, use a state variable or any dynamic value inside the provider and pass the updated state:
```jsx
const [theme, setTheme] = useState('light');
<ThemeContext.Provider value={theme}>
  <Component />
</ThemeContext.Provider>
```
5. **Default Value**:
- If no provider is found, useContext returns the default value defined during createContext.
6. **Caveats**:
- The useContext call only accesses providers above the component in the tree, not within the same component.
- Changes to the context automatically trigger re-renders for components using that context.  
More details can be found [here](https://react.dev/reference/react/useContext)
### 14.4 useRef
The useRef hook in React allows you to create a mutable reference that persists across renders without causing a re-render. Here are the key points from the documentation:

1. **Basic Syntax**:
   ```js
   const ref = useRef(initialValue);
   ```
   - `initialValue` can be any type.
   - `ref` is an object with a `current` property, initially set to `initialValue`.

2. **Usage**:
   - **Referencing a value**: You can store a mutable value without triggering re-renders:
     ```jsx
     const intervalRef = useRef(0);
     intervalRef.current = setInterval(() => {}, 1000);
     ```
   - **Manipulating the DOM**: `useRef` can reference DOM elements:
     ```jsx
     const inputRef = useRef(null);
     <input ref={inputRef} />;
     inputRef.current.focus(); // Manipulate the DOM node directly
     ```

3. **Caveats**:
   - Changing `ref.current` does not cause re-renders.
   - Avoid reading/writing `ref.current` during rendering; use event handlers or effects instead.

4. **Avoiding Unnecessary Re-initialization**:
   - Initialize complex objects within the ref:
     ```jsx
     const playerRef = useRef(null);
     if (!playerRef.current) {
       playerRef.current = new VideoPlayer();
     }
     ```

More details are available [here](https://react.dev/reference/react/useEffect).
### 14.5 useImperativeHandle
The `useImperativeHandle` hook in React allows you to customize the value or methods exposed to parent components through a `ref`. Key points from the documentation:

1. **Basic Syntax**:
   ```jsx
   useImperativeHandle(ref, createHandle, dependencies?)
   ```
   - ref: The ref passed from the parent.
   - createHandle: A function that returns the methods or values you want to expose.
   - dependencies: Optional list of reactive values that trigger the createHandle to update.

2. **Usage**:
   - **Expose Custom Methods**: Use this hook within a component to customize what the parent can access via the `ref`. For example:
     ```jsx
     useImperativeHandle(ref, () => ({
       focus() {
         inputRef.current.focus();
       },
     }));
     ```
   - This is commonly used in combination with `forwardRef` to allow parent components to access specific methods on a child component.

3. **Examples**:
   - **Exposing DOM methods**: You can expose DOM methods like `focus` or `scrollIntoView` to the parent, without exposing the entire DOM node.
   - **Custom Methods**: You can expose custom methods or behaviors that don’t directly relate to DOM manipulation.

4. **Pitfall**:
   - Avoid overusing refs. Refs are for imperative actions that can't be easily expressed through props.

More details can be found [here](https://react.dev/reference/react/useImperativeHandle).
### 14.6 useEffect
The `useEffect` hook in React lets you perform side effects in function components. Here are key points from the documentation:

1. **Basic Syntax**:
   ```js
   useEffect(setup, dependencies?)
   ```
   - **setup**: Function that contains your effect logic, which can return a cleanup function.
   - **dependencies**: An optional array of values that the effect depends on. If any value changes, the effect re-runs.

2. **Usage**:
   - Commonly used for side effects like fetching data, connecting to external APIs, or managing subscriptions.
   - The cleanup function (if provided) runs when the component is unmounted or before re-running the effect due to dependency changes.

3. **Dependency Management**:
   - Passing dependencies ensures the effect only runs when those values change.
   - If no dependencies are provided, the effect runs after every render.
   - An empty dependency array (`[]`) makes the effect run only once after the initial render.

4. **Common Use Cases**:
   - **Connecting to an external system** (e.g., setting up a WebSocket connection).
   - **Fetching data** on component mount.
   - **Controlling non-React widgets** (like map or video player).

5. **Caveats**:
   - Avoid unnecessary dependencies to prevent excessive re-renders.
   - For effects with frequent updates, `useLayoutEffect` may be more suitable to avoid flickering.
   - Effects run only on the client, not during server-side rendering.

More details are available [here](https://r.1lm.io/p/https://react.dev/reference/react/useEffect).
### 14.7 useLayoutEffect
The `useLayoutEffect` hook in React is similar to `useEffect`, but it runs synchronously **before** the browser repaints the screen. Key points from the documentation:

1. **Basic Syntax**:
   ```js
   useLayoutEffect(setup, dependencies?)
   ```
   - **setup**: A function that runs before the browser repaints. It can return a cleanup function.
   - **dependencies**: An optional array that defines when the effect should re-run.

2. **Usage**:
   - **Measuring Layout**: Useful for measuring DOM elements (e.g., tooltips) before the browser repaints.
   - **Blocking Repaints**: It prevents the browser from showing visual changes until the effect completes, ensuring layout adjustments happen without visual flickering.

3. **Performance Considerations**:
   - **Performance Costs**: It blocks browser rendering, so prefer `useEffect` when layout measurements aren't needed to avoid performance issues.
   
4. **Server-Side Rendering**:
   - `useLayoutEffect` doesn’t run on the server, and may throw an error in server-rendered environments.

More details are available [here](https://react.dev/reference/react/useLayoutEffect).
### 14.8 useInsertionEffect
The `useInsertionEffect` hook in React is intended primarily for authors of CSS-in-JS libraries. It allows styles to be injected into the DOM **before** any layout effects occur. Key points from the documentation:

1. **Basic Syntax**:
   ```js
   useInsertionEffect(setup, dependencies?)
   ```
   - **setup**: Function to inject styles or perform other tasks before layout effects.
   - **dependencies**: Optional array that controls when the effect should re-run.

2. **Use Case**:
   - **CSS-in-JS Libraries**: The hook is useful for injecting dynamic styles into the DOM before layout calculations, ensuring that layout effects can access the correct styles.
   - It is **not recommended** for general use; `useEffect` or `useLayoutEffect` should be used instead for most side effects.

3. **Caveats**:
   - Only runs on the client-side.
   - Avoid state updates inside `useInsertionEffect`.

For more details, visit [here](https://react.dev/reference/react/useInsertionEffect).
### 14.9 useMemo
The `useMemo` hook in React is used to **cache** the result of a computation to avoid recalculating it on every render, improving performance. Here are the key points:

1. **Basic Syntax**:
   ```jsx
   const memoizedValue = useMemo(calculateValue, dependencies);
   ```
   - `calculateValue`: A function that returns the computed value.
   - `dependencies`: Array of values that trigger recalculation when they change.

2. **Usage**:
   - **Skipping Expensive Calculations**: Cache heavy calculations to avoid recomputation.
   - **Preventing Re-renders**: Memoize values passed to child components wrapped in `memo`.
   - **Optimizing Effects**: Prevent effects from triggering too often by memoizing objects or functions.

3. **Caveats**:
   - Only use it for **performance optimization**.
   - In **Strict Mode**, calculations might run twice during development.

For more details, visit [here](https://react.dev/reference/react/useMemo).
### 14.10 useCallback
The [React `useCallback`](https://react.dev/reference/react/useCallback) hook allows you to cache a function between re-renders. It is used primarily for performance optimization in cases where you pass a function as a prop to child components, or use it in an effect. Here's a summary of key points:

1. **Basic Usage**: 
   ```jsx
   const cachedFn = useCallback(fn, dependencies);
   ```
   - **`fn`**: The function to cache.
   - **`dependencies`**: List of values that, when changed, will re-create the cached function.

2. **Use Cases**:
   - **Skipping Re-Renders**: Prevents unnecessary re-renders when passing a function to child components wrapped in `memo`.
   - **Memoized Callbacks**: Helps in scenarios where functions depend on state but should only update when specific dependencies change.
   - **Preventing Frequent Effects**: Avoids frequent re-executions of effects by caching dependent functions.

3. **Best Practices**:
   - **Avoid Overuse**: Only use `useCallback` when necessary for performance; avoid wrapping every function unnecessarily.
   - **Memoization**: Related to `useMemo`, but `useCallback` caches the function itself, while `useMemo` caches the result of a function.

4. **Common Issues**:
   - Functions being recreated every render due to missing dependencies.
   - Avoid calling `useCallback` in loops; instead, extract components where necessary.

For more details, you can visit the [here](https://react.dev/reference/react/useCallback).
### 14.11 useTransition
The [`useTransition`](https://react.dev/reference/react/useTransition) hook in React allows you to mark certain state updates as "transitions," making them non-blocking. This helps maintain a responsive UI during complex or slow updates. Here's a summary:

1. **Usage**:
   - `useTransition()` returns two values: 
     - `isPending`: A boolean indicating whether a transition is in progress.
     - `startTransition`: A function used to wrap state updates that should be marked as transitions.

   Example:
   ```jsx
   const [isPending, startTransition] = useTransition();
   startTransition(() => {
     setState(newState);
   });
   ```

2. **Key Benefits**:
   - Keeps the UI responsive during slow operations (e.g., rendering large components or switching views).
   - Avoids blocking user interactions while state updates are in progress.
   
3. **Common Use Cases**:
   - **Non-blocking state updates**: For example, switching tabs in a UI without freezing the interface.
   - **Handling complex state updates** in components like routers or tab navigations.
   - **Showing pending states**: Using `isPending` to display a loading indicator during a transition.
   
4. **Caveats**:
   - Cannot use transitions for synchronous updates like input fields.
   - Use `startTransition` inside components or custom hooks only.

For detailed examples and troubleshooting, visit the [here](https://react.dev/reference/react/useTransition).
### 14.12 useDeferredValue
The [`useDeferredValue`](https://react.dev/reference/react/useDeferredValue) hook in React lets you defer updates to part of the UI. Here's a concise summary:

1. **Usage**:
   ```jsx
   const deferredValue = useDeferredValue(value);
   ```
   - Returns a "lagging" version of the provided `value`, which updates after the main UI has rendered, keeping the interface responsive.

2. **Key Benefits**:
   - Helps in **deprioritizing expensive UI updates** (e.g., lists or charts) while keeping essential parts (like input fields) responsive.
   - Shows **stale content** while waiting for the deferred value to update in the background.
   - Can be used with **Suspense** to defer rendering without showing a loading state.

3. **Common Use Cases**:
   - **Search interfaces**: Keep showing the old search results while new results load.
   - **Slow components**: Prevent components that take time to render from blocking faster ones, such as text inputs.
   - **Stale indicator**: Add visual indicators when the displayed content is stale compared to the latest input.

4. **Caveats**:
   - Works best with primitive values (e.g., strings, numbers).
   - Not a replacement for debouncing/throttling, but can be used together for network requests.

For more details and examples, visit the [here](https://react.dev/reference/react/useDeferredValue).
### 14.13 useDebugValue
The [`useDebugValue`](https://react.dev/reference/react/useDebugValue) hook in React is used to display custom labels for hooks in React DevTools, helping with debugging. Here's a summary:

1. **Basic Usage**:
   ```jsx
   useDebugValue(value);
   ```
   This allows you to label the hook value in DevTools. 

2. **Optional Formatting**:
   You can provide a custom formatting function as a second argument:
   ```jsx
   useDebugValue(value, formatValue => formatValue.toString());
   ```

3. **Use Cases**:
   - **Custom Hooks**: Add debug labels for hooks that manage complex or internal logic, making it easier to inspect them in DevTools.
   - **Performance**: Avoids expensive computations for formatting unless the hook is being inspected.

4. **Best Practices**:
   - Only use `useDebugValue` for hooks that benefit from additional labeling in DevTools, especially in shared libraries.

For more details, visit the [here](https://react.dev/reference/react/useDebugValue).
### 14.15 useSyncExternalStore
The [`useSyncExternalStore`](https://react.dev/reference/react/useSyncExternalStore) hook allows React components to subscribe to an external store, ensuring synchronization between the store's state and the component.

### Key Points:

1. **Basic Usage**:
   ```jsx
   const snapshot = useSyncExternalStore(subscribe, getSnapshot, getServerSnapshot?);
   ```
   - **`subscribe`**: Subscribes to the store and provides a callback for when the store updates.
   - **`getSnapshot`**: Returns the current state of the store.
   - **`getServerSnapshot`** (optional): Used for server rendering.

2. **Use Cases**:
   - **External state management**: Useful for third-party state management libraries (e.g., Redux) or browser APIs (e.g., `navigator.onLine`).
   - **Server-side rendering**: Ensures data consistency between server and client when rendering.

3. **Best Practices**:
   - **Immutability**: Ensure that the snapshot returned by `getSnapshot` is immutable to prevent unnecessary re-renders.
   - **Custom Hooks**: Typically wrapped in custom hooks to abstract the subscription logic for reuse across components.

4. **Caveats**:
   - **Avoid suspense with stores**: Suspending based on store values can cause poor user experience.
   - **Subscribe outside components**: Prevent unnecessary resubscription by moving `subscribe` outside the component or using `useCallback`.

For detailed examples and implementation, visit the [here](https://react.dev/reference/react/useSyncExternalStore).
### 14.16 useActionState
The [`useActionState`](https://react.dev/reference/react/useActionState) hook in React (currently in experimental channels) allows you to update a component's state based on the result of a form action. Here's a summary:

### Key Points:
1. **Basic Usage**:
   ```jsx
   const [state, formAction] = useActionState(fn, initialState, permalink?);
   ```
   - **`fn`**: The function triggered when the form is submitted.
   - **`initialState`**: Initial state value.
   - **`permalink`** (optional): Used for server actions to specify a unique page URL.

2. **Use Case**:
   - Tracks and updates form state after form submissions, allowing interactive updates.
   - Compatible with **React Server Components**, making form submissions interactive before JavaScript has loaded.

3. **Parameters**:
   - The action function receives the current form state as its first argument and the form data as the second.

4. **Returns**:
   - **Current state**: Starts with `initialState`, updated with the action's return value.
   - **Form action**: Used in the `action` or `formAction` prop to trigger state updates.

For more details, visit the [here](https://react.dev/reference/react/useActionState).

## 15. Routing
To handle routing in a React app, the react-router-dom package is commonly used.
### Installation:
```bash
npm install react-router-dom
```
### Example:
```jsx
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li><Link to="/">Home</Link></li>
            <li><Link to="/about">About</Link></li>
          </ul>
        </nav>

        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}
```
## 15. React Context API
The Context API provides a way to pass data through the component tree without manually passing props at every level.
### Example:
```jsx
const MyContext = React.createContext();

function App() {
  return (
    <MyContext.Provider value="Hello World">
      <Child />
    </MyContext.Provider>
  );
}

function Child() {
  const value = React.useContext(MyContext);
  return <h1>{value}</h1>;
}
```
## 16. React Redux
Here's a concise and practical section on **React Redux** that you can include in your README documentation:

---

## React Redux Integration

**React Redux** is a library that provides seamless state management by integrating Redux with React. It allows you to manage and access global state efficiently across your components.

### Installation

To install React Redux and Redux:
```bash
npm install redux react-redux
```

### Setup

1. **Create Redux Store**: Define a reducer and create a store to hold the global state.
   ```javascript
   // store.js
   import { createStore } from 'redux';

   const initialState = { counter: 0 };

   function counterReducer(state = initialState, action) {
     switch (action.type) {
       case 'INCREMENT':
         return { ...state, counter: state.counter + 1 };
       default:
         return state;
     }
   }

   const store = createStore(counterReducer);
   export default store;
   ```

2. **Provide the Store to React**: Wrap your root component with the `Provider` component to make the Redux store available throughout your app.
   ```javascript
   // index.js
   import React from 'react';
   import ReactDOM from 'react-dom';
   import { Provider } from 'react-redux';
   import App from './App';
   import store from './store';

   ReactDOM.render(
     <Provider store={store}>
       <App />
     </Provider>,
     document.getElementById('root')
   );
   ```

3. **Access Redux State and Dispatch Actions**:
   - Use `useSelector` to read from the state.
   - Use `useDispatch` to dispatch actions.

   ```javascript
   // CounterComponent.js
   import React from 'react';
   import { useSelector, useDispatch } from 'react-redux';

   function CounterComponent() {
     const counter = useSelector(state => state.counter);
     const dispatch = useDispatch();

     return (
       <div>
         <p>Counter: {counter}</p>
         <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
       </div>
     );
   }

   export default CounterComponent;
   ```

### Core Concepts
- **Store**: Holds the application state.
- **Reducer**: A pure function that updates the state based on the action type.
- **Actions**: Describes events that modify the state.
- **Dispatch**: Sends actions to reducers to update the state.
- **Provider**: Makes the Redux store available to your app.
- **useSelector**: Reads state from the Redux store.
- **useDispatch**: Dispatches actions to the store.

For more details, refer to the [here](https://react-redux.js.org/).


## 17. Redux Toolkit

Redux Toolkit is the official, recommended way to write Redux logic. It provides a set of tools to simplify common Redux tasks like store setup, creating reducers, and handling immutable updates. Redux Toolkit helps improve developer experience by removing boilerplate and enabling better patterns for writing Redux logic.

### Concept of Slice in redux toolkit:

**1. Combining Reducers and Actions in One Place:** The createSlice function simplifies Redux by automatically generating both the action creators and reducers. This reduces the boilerplate typically involved in manually writing action types, action creators, and reducers separately.

**2. Handling Immutable State Updates with Immer:** Redux Toolkit uses Immer under the hood, which allows you to write "mutative" code in reducers, but behind the scenes, Immer ensures the state is updated immutably. This means you can directly update state properties without worrying about immutability rules.

**3. Supports Initial State:** createSlice takes an initialState argument, which defines the starting point for the slice's state. This helps keep the state structure consistent and easy to follow.

### Key Features of Redux Toolkit:

- Simpler store setup with `configureStore`
- slice reducers created with `createSlice`
- Built-in **Redux DevTools** integration
- Thunks for handling asynchronous logic with `createAsyncThunk`
- Immutability is ensured using **Immer** under the hood

### Installation

Install Redux Toolkit and React-Redux:

```bash
npm install @reduxjs/toolkit react-redux
```

### Setup

1. **Create a Redux slice:** Redux Toolkit uses createSlice to combine action creators and reducers.
   ```javascript
   // counterSlice.js
   import { createSlice } from '@reduxjs/toolkit';

   const counterSlice = createSlice({
     name: 'counter',
     initialState: {
       value: 0,
     },
     reducers: {
       increment: (state) => {
         state.value += 1;
       },
       decrement: (state) => {
         state.value -= 1;
       },
       reset: (state) => {
         state.value = 0;
       },
     },
   });
   
   export const { increment, decrement, reset } = counterSlice.actions;
   export default counterSlice.reducer;
   ```
   
2. **Create Redux Store**: Define a reducer and create a store to hold the global state.
   ```javascript
   // store.js
   import { configureStore } from '@reduxjs/toolkit';
   import counterReducer from './counterSlice';
   
   export const store = configureStore({
     reducer: {
       counter: counterReducer,
     },
   });
   ```

3. **Provide the Store to React**: Wrap your root component with the `Provider` component to make the Redux store available throughout your app.
   
   ```javascript
   // index.js
   import React from 'react';
   import ReactDOM from 'react-dom';
   import { Provider } from 'react-redux';
   import App from './App';
   import store from './store';

   ReactDOM.render(
     <Provider store={store}>
       <App />
     </Provider>,
     document.getElementById('root')
   );
   ```

3. **Access Redux State and Dispatch Actions**:
   - Use `useSelector` to read from the state.
   - Use `useDispatch` to dispatch actions.


   ```javascript
   // CounterComponent.js
   import React from 'react';
   import { useSelector, useDispatch } from 'react-redux';
   import { increment, decrement, reset } from './counterSlice';

   function CounterComponent() {
     const count = useSelector((state) => state.counter.value);
     const dispatch = useDispatch();
   
     return (
       <div>
         <h1>{count}</h1>
         <button onClick={() => dispatch(increment())}>Increment</button>
         <button onClick={() => dispatch(decrement())}>Decrement</button>
         <button onClick={() => dispatch(reset())}>Reset</button>
       </div>
     );
   }

   export default CounterComponent;
   ```

   For more details, refer to the [here](https://redux-toolkit.js.org/).
