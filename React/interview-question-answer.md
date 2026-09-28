### React Fundamentals

```
Topic: Components, Hooks & State Management
Q31. What is React and what problem does it solve?
Q32. What is JSX and why is it used in React?
Q33. What is the difference between functional and class components?
Q34. What is the virtual DOM and how does React use it?
Q35. Explain the useState hook with an example.
Q36. What is the useEffect hook and what are its use cases?
Q37. What is the difference between controlled and uncontrolled components?
Q38. What are props in React and how are they passed?
Q39. What is prop drilling and how can it be avoided?
Q40. Explain the useContext hook with an example.
Q41. What is the useRef hook and when would you use it?
Q42. What are React keys and why are they important in lists?
Q43. What is the difference between state and props?
Q44. How does conditional rendering work in React?
Q45. What is React.memo and when should you use it?
```

### React Advanced

```
Topic: Routing, Performance & Patterns
Q46. What is the useReducer hook and when is it preferred over useState?
Q47. Explain the useMemo hook and give a use case.
Q48. What is the useCallback hook and when do you use it?
Q49. What is React Router and how do you set up client-side routing?
Q50. What is the difference between useNavigate and Link in React Router?
Q51. What are custom hooks in React? Write a simple example.
Q52. What is lazy loading in React and how is it implemented?
Q53. What are React error boundaries and why are they useful?
Q54. What is the Context API and when should you use Redux instead?
Q55. Explain the concept of reconciliation in React.
Q56. What is the difference between React.Fragment and empty tags (<>)?
Q57. How do you handle forms in React? Explain with Formik or react-hook-form.
Q58. What is code splitting in React and how does it improve performance?
Q59. What are portals in React and when are they useful?
Q60. Explain the lifecycle of a React functional component with hooks.
```

## What is React?

“React is a JavaScript library for building user interfaces, especially single-page applications. It was developed by Meta. React allows us to build reusable UI components and efficiently update the user interface when the application state changes.”

## How does React work?

“React works by using a component-based architecture. We break the UI into small reusable components. Each component can have its own state and props. When the state or props change, React creates a new Virtual DOM representation of the UI and compares it with the previous one. This process is called reconciliation. React then determines the minimum changes required and updates the actual DOM efficiently.”

### Q31. What is React and what problem does it solve?

Core Answer: React is an open-source JavaScript library developed by Facebook for building user interfaces, primarily for single-page applications. The main problem it solves is the unpredictable and complex nature of keeping the UI in sync with underlying data changes. It achieves this using a declarative approach and a Virtual DOM, which efficiently updates only the parts of the actual DOM that have changed.

### Interviewer Counter-Question: Is React a library or a framework?

Answer: It is a library. Unlike a framework (like Angular) that dictates how you structure your entire application (routing, HTTP calls, state), React only cares about rendering the UI components. You have to combine it with other libraries (like React Router) to build a full architecture.

Scenario Challenge: Your team is building a simple static marketing page with no interactivity. Should you use React?
Solution: Probably not. React adds JavaScript bundle size and complexity. For a purely static page with no state changes, basic HTML/CSS (or a static site generator) is more performant and straightforward.

### Q32. What is JSX and why is it used in React?

Core Answer: JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML-like markup directly inside your JavaScript files. It is used because it visually makes writing and understanding complex UI trees much easier than using traditional React.createElement() calls. Under the hood, a compiler like Babel transforms JSX into standard JavaScript functions.

Interviewer Counter-Question: Can the browser read JSX directly?
Answer: No. Browsers only understand standard JavaScript. JSX must be transpiled by a tool like Babel or SWC into React.createElement (or the newer \_jsx runtime) before the browser executes it.

Scenario Challenge: You are trying to return two adjacent <div> elements from a component, but React throws an error. Why, and how do you fix it?
Solution: JSX requires a single parent element because it compiles down to a single function return value. You can fix this by wrapping the divs in a React Fragment (<> ... </>), which groups them without adding an extra node to the actual DOM.

### Q33. What is the difference between functional and class components?

Core Answer:

Class Components are ES6 classes that extend React.Component. They require a render() method and traditionally managed state and side-effects using lifecycle methods (like componentDidMount).

Functional Components are plain JavaScript functions that take props as an argument and return JSX. With the introduction of Hooks in React 16.8, functional components can now manage state and side effects, making them the modern standard.

Interviewer Counter-Question: Why has the React community largely moved away from class components?
Answer: Functional components with hooks allow for better logic reuse (custom hooks), reduce boilerplate (no this binding), and group related logic together rather than splitting it across different lifecycle methods.

Scenario Challenge: You are migrating a legacy Class component that uses componentWillUnmount to clean up a WebSocket connection. How do you handle this in a functional component?
Solution: You use the useEffect hook and return a cleanup function from it. The returned function acts exactly like componentWillUnmount.

### Q34. What is the Virtual DOM and how does React use it?

Core Answer: The Virtual DOM is a lightweight, in-memory JavaScript representation of the actual DOM. When application state changes, React creates a new Virtual DOM tree and compares it against the previous one (a process called reconciliation or "diffing"). It calculates the absolute minimum number of changes needed, and then batches those updates to the real DOM.

Interviewer Counter-Question: How is the Virtual DOM different from the Shadow DOM?
Answer: The Shadow DOM is a browser technology used primarily for scoping CSS and variables in web components. The Virtual DOM is a pattern/concept implemented by React in JavaScript to optimize performance and prevent unnecessary, expensive repaints of the real DOM.

Scenario Challenge: A developer notices that a large list is causing performance lag when rendering. They argue the Virtual DOM should prevent this. What's the misconception?
Solution: The Virtual DOM optimizes updates, but rendering a massive number of nodes in the first place, or unnecessarily re-rendering them, is still expensive. The solution is usually virtualization/windowing (e.g., react-window) or proper use of memoization, not just relying on the Virtual DOM.

### Q35. Explain the useState hook with an example.

Core Answer: useState is a React Hook that allows functional components to hold and update local state. It returns an array containing two elements: the current state value and a function to update it.

JavaScript

```
const [count, setCount] = useState(0);
// 0 is the initial state
// count is the current value
// setCount is the updater function
Interviewer Counter-Question: State updates are asynchronous. If you call setCount(count + 1) three times in a row, what happens?
Answer: Because React batches state updates for performance, if the initial count was 0, the final count will only be 1. To fix this and rely on previous state, you must use an updater function: setCount(prev => prev + 1).
```

Scenario Challenge: You are initializing state with the result of an expensive calculation (e.g., parsing a large JSON string). How do you prevent this calculation from running on every re-render?
Solution: Use lazy initialization by passing a function to useState: useState(() => expensiveCalculation()). This ensures the function only runs on the initial render.

### Q36. What is the useEffect hook and what are its use cases?

Core Answer: useEffect lets you perform side effects in functional components. Use cases include fetching data, setting up subscriptions, manually manipulating the DOM, and starting timers. It takes two arguments: a callback function containing the effect logic, and an optional dependency array that dictates when the effect should re-run.

Interviewer Counter-Question: What happens if you omit the dependency array entirely?
Answer: The effect will run after every single render of the component. This is rarely what you want and can easily lead to infinite loops if the effect also updates state.

Scenario Challenge: Your component starts a setInterval inside a useEffect on mount, but when you navigate away from the page, you get a memory leak warning. How do you fix it?
Solution: Return a cleanup function from the useEffect that calls clearInterval. React will execute this cleanup function when the component unmounts.

### Q37. What is the difference between controlled and uncontrolled components?

Core Answer:

Controlled Components: Form data is handled by React component state. The input's value is bound to a state variable, and changes are handled via an onChange event (e.g., <input value={state} onChange={handleChange} />).

Uncontrolled Components: Form data is handled by the DOM itself. You use a ref (via useRef) to extract the current value from the DOM element only when you need it (like on form submit).

Interviewer Counter-Question: When would you intentionally choose an uncontrolled component over a controlled one?
Answer: Uncontrolled components are necessary for <input type="file"> because its value is read-only and cannot be controlled programmatically by React. They are also useful when integrating React with non-React libraries or optimizing extremely large, complex forms where re-rendering on every keystroke is too costly.

Scenario Challenge: A user complains that they can't type into a text input. You check the code and see <input value={firstName} />. What is wrong?
Solution: It is an incomplete controlled component. By providing a value without an onChange handler, React locks the input to the state value, rendering it read-only.

### Q38. What are props in React and how are they passed?

Core Answer: Props (short for properties) are how data is passed from a parent component down to a child component. They are read-only (immutable) and flow in a strictly one-way, top-down direction. They are passed as attributes in JSX, similar to HTML attributes.

Interviewer Counter-Question: Since props are read-only, how can a child component update data that belongs to the parent?
Answer: The parent must pass a callback function down to the child as a prop. The child can then invoke this function, passing data back up as arguments, which the parent uses to update its own state.

Scenario Challenge: You need to pass 10 different user attributes down to a UserProfile component. Writing them out individually looks messy. Is there a better way?
Solution: You can group them into an object and pass the object (e.g., user={userData}), or use the spread operator to pass all object properties as individual props (e.g., <UserProfile {...userData}/>).

### Q39. What is prop drilling and how can it be avoided?

Core Answer: Prop drilling is the process of passing props through multiple layers of nested components that don't actually need the data, just to get it to a deeply nested child component that does. It makes code harder to maintain and refactor. It can be avoided by using the Context API, state management libraries (like Redux or Zustand), or component composition (passing JSX as children).

Interviewer Counter-Question: Is prop drilling always an anti-pattern?
Answer: No. For small applications or going down just 2-3 levels, prop drilling is perfectly fine and often easier to follow than introducing the complexity of Context or Redux.

Scenario Challenge: You have a deeply nested ThemeToggleButton that needs access to the theme state located in the root App component. How do you solve this without external libraries?
Solution: Create a ThemeContext using React.createContext(), wrap the App in a ThemeProvider, and use the useContext hook inside the ThemeToggleButton to access the theme directly.

### Q40. Explain the useContext hook with an example.

Core Answer: useContext consumes a React Context, allowing you to access global data without passing props down manually at every level.

JavaScript

```
const ThemeContext = React.createContext('light');

function Display() {
// Directly accesses 'light' (or whatever the Provider sets)
const theme = useContext(ThemeContext);
return <div>Current theme: {theme}</div>;
}
```

Interviewer Counter-Question: What is the main performance pitfall of using Context for global state?
Answer: Whenever a Context Provider's value changes, every component consuming that context will re-render, even if they only care about a specific part of the context value.

Scenario Challenge: You have an AuthContext holding user details and a ThemeContext. Should you combine them into one GlobalContext to save time?
Solution: No. Combining unrelated state forces components that only care about the theme to re-render when auth state changes. Keep logically separate contexts separated.

### Q41. What is the useRef hook and when would you use it?

Core Answer: useRef returns a mutable reference object whose .current property is persisted across renders. Crucially, updating a .current value does not trigger a re-render. You use it primarily for two things: directly accessing DOM elements (like focusing an input), and storing mutable variables that shouldn't cause UI updates (like keeping track of a timer ID or previous state).

Interviewer Counter-Question: Why use useRef to store a variable instead of just declaring a let variable outside or inside the component?
Answer: A let variable inside the component gets re-initialized on every render. A variable outside the component is shared across all instances of that component. useRef keeps the variable isolated to that specific component instance while surviving renders.

Scenario Challenge: You want an input field to automatically focus as soon as a modal opens. How do you achieve this?
Solution: Create a ref const inputRef = useRef(null);, attach it to the input <input ref={inputRef} />, and in a useEffect that runs on mount, call inputRef.current.focus().

### Q42. What are React keys and why are they important in lists?

Core Answer: Keys are special string attributes you must include when creating arrays of elements in React. They help the Virtual DOM identify which items have changed, been added, or been removed. Proper keys make the reconciliation process highly efficient by matching children in the original tree with children in the subsequent tree.

Interviewer Counter-Question: Why is using the array index as a key considered bad practice?
Answer: If the list order changes (e.g., sorting, inserting, or deleting items), the indices change. React will mistake an item at index 0 for the previous item at index 0, which can lead to severe bugs, mixed-up component state, and poor performance.

Scenario Challenge: You are rendering a list of to-do items from an API, but the items don't have unique IDs. How do you handle keys safely?
Solution: You should generate unique IDs on the client side when the data is first fetched (e.g., using crypto.randomUUID() or a library like uuid), map those to the objects, and use those as keys.

### Q43. What is the difference between state and props?

Core Answer:

State is internal data managed within a component. It is mutable (using a setter function), and when it changes, the component re-renders.

Props are external data passed into a component from its parent. They are strictly read-only within the child component.

Interviewer Counter-Question: Can a prop be used to initialize state?
Answer: Yes, but it is an anti-pattern if you expect the state to stay in sync with the prop later. If the parent changes the prop, the child's state will not automatically update. It is only safe to do this if the prop is strictly meant as an initial, one-time seed value (e.g., initialCount).

Scenario Challenge: A child component receives a user object via props and needs to edit the user's name locally before sending it to an API. How should this be handled?
Solution: The child should copy the user prop into its own local state upon initialization. The user edits the local state version, and upon save, the child sends the local state to the API.

### Q44. How does conditional rendering work in React?

Core Answer: Conditional rendering in React works exactly like conditional logic in standard JavaScript. You can use if/else statements outside the JSX to determine what to return, or you can use inline operators within JSX, specifically the ternary operator (condition ? trueNode : falseNode) and the logical AND operator (condition && trueNode).

Interviewer Counter-Question: What is the danger of using the && operator like this: {items.length && <List/>}?
Answer: If items.length is 0, JavaScript evaluates 0 as falsy, but it returns the 0 rather than a boolean. React will render a 0 on the screen. It should be cast to a boolean: {items.length > 0 && <List/>}.

Scenario Challenge: You have 4 different roles (Admin, Editor, Viewer, Guest) and want to render a completely different dashboard for each. Should you use a massive nested ternary?
Solution: No, nested ternaries are hard to read. You should either use early returns with if statements, or map the roles to components using an object dictionary or a switch statement for cleaner code.

### Q45. What is React.memo and when should you use it?

Core Answer: React.memo is a Higher-Order Component (HOC) used to optimize performance. If your component renders the exact same result given the exact same props, you can wrap it in React.memo. React will memorize the rendered output and skip re-rendering the component if its props haven't changed, even if its parent re-renders.

Interviewer Counter-Question: If React.memo stops unnecessary renders, why not wrap every component in it?
Answer: Because the prop comparison itself has a performance cost. If a component is lightweight, or if its props change on almost every render anyway, the cost of the comparison is higher than simply re-rendering the component.

Scenario Challenge: You wrapped a Child component in React.memo, but it still re-renders every time the parent updates. The parent passes a prop onClick={() => doSomething()}. Why is memo failing?
Solution: Inline arrow functions create a new reference in memory on every render. React.memo does a shallow comparison, sees a new function reference, and assumes props have changed. You must wrap the function in a useCallback hook in the parent to maintain referential equality.
