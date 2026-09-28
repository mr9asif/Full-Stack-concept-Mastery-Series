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

### Q46. What is the useReducer hook and when is it preferred over useState?

Core Answer: useReducer is a hook used for state management that serves as an alternative to useState. It requires a reducer function (which determines how state changes based on dispatched actions) and an initial state. It is highly preferred when you have complex state logic involving multiple sub-values (like deeply nested objects) or when the next state depends heavily on the previous state.

Interviewer Counter-Question: Can you build a whole application using only useReducer instead of Redux?
Answer: Yes, combined with the Context API, useReducer can manage global state. However, it lacks the ecosystem tools of Redux, like Redux DevTools for time-travel debugging and built-in middleware (like thunks or sagas) for handling complex asynchronous actions.

Scenario Challenge: You are building a complex checkout form where updating the shipping method also needs to recalculate tax, update the total price, and clear the discount code. Managing this with useState requires calling 4 different setter functions.
Solution: Move this logic into a useReducer. You dispatch a single action dispatch({ type: 'UPDATE_SHIPPING', payload: 'express' }), and the reducer centrally handles updating all four state values in one predictable place.

### Q47. Explain the useMemo hook and give a use case.

Core Answer: useMemo is a performance optimization hook that memoizes (caches) the result of a calculation. It takes a calculation function and a dependency array. React will only recalculate the value when one of the dependencies has changed. If no dependencies changed, it returns the cached result from the previous render.

Interviewer Counter-Question: If caching is good, why shouldn't we wrap every variable declaration in useMemo?
Answer: Because the useMemo hook itself has a performance cost. React has to allocate memory for the cached value and run a comparison check on the dependency array on every render. For simple arithmetic or string manipulation, running the calculation is actually faster than using useMemo.

Scenario Challenge: Your component fetches a list of 5,000 users and allows the user to toggle a "Dark Mode" button. Every time they click dark mode, the app freezes for a second. Why?
Solution: The state change for dark mode is causing the component to re-render, which is likely re-running a heavy filtering or sorting operation on the 5,000 users. Wrap the sorting logic in useMemo with the user data as the dependency to prevent it from recalculating on theme toggles.

### Q48. What is the useCallback hook and when do you use it?

Core Answer: While useMemo caches a calculated value, useCallback caches a function definition. In functional components, any function defined inside the component is recreated as a brand new object in memory on every single render. useCallback ensures the function maintains the same referential identity across renders as long as its dependencies stay the same.

Interviewer Counter-Question: What is the primary relationship between useCallback and React.memo?
Answer: React.memo prevents a child component from re-rendering if its props haven't changed. However, if a parent passes an inline function (e.g., onClick={() => doSomething()}) to that memoized child, the child will still re-render because the function is a new reference every time. You must use useCallback in the parent to pass the same function reference.

Scenario Challenge: You wrap a function in useCallback with an empty dependency array []. Inside the function, it logs a state variable, but it always logs 0, even though the UI shows the state is 5.
Solution: You created a stale closure. Because the dependency array is empty, the function was memoized on the first render when the state was 0. You must add the state variable to the dependency array.

### Q49. What is React Router and how do you set up client-side routing?

Core Answer: React Router is the standard library for client-side routing in React applications. Instead of making a request to the server for a new HTML page when navigating, React Router intercepts the URL change and dynamically swaps out the rendered React components in the DOM, creating a seamless Single Page Application (SPA) experience.

Interviewer Counter-Question: How does React Router manipulate the browser URL without triggering a page reload?
Answer: It uses the HTML5 History API (specifically pushState and replaceState) under the hood to update the URL in the browser's address bar and add entries to the browser's history stack without triggering a full page refresh.

Scenario Challenge: Users are visiting [www.yourapp.com/dashboard/settings](https://www.yourapp.com/dashboard/settings), but when they refresh the page, they get a 404 error from the server.
Solution: The server doesn't know about client-side routes. You must configure your server (or static host) to redirect all unknown requests (a "catch-all") back to index.html, where React Router will take over and render the correct component based on the URL path.

### Q50. What is the difference between useNavigate and Link in React Router?

Core Answer:

<Link to="..."> is a declarative component used in JSX. It renders an accessible <a> tag in the DOM and is meant for explicit user navigation (like clicking items in a navigation bar).

useNavigate is an imperative hook. It returns a function that lets you navigate programmatically via JavaScript code (e.g., redirecting after a form submission or a successful API call).

Interviewer Counter-Question: Can you just use a standard <a href="..."> instead of <Link>?
Answer: You can, but you shouldn't for internal links. A standard <a> tag bypasses React Router and causes the browser to perform a full page reload, wiping out all of your React application state (like Redux stores or Context values).

Scenario Challenge: You want a user to be redirected to the login page when their session expires, but you want to ensure they can't click the browser's "Back" button to return to the protected route.
Solution: Use navigate('/login', { replace: true }). The replace flag overwrites the current entry in the history stack rather than adding a new one.

### Q51. What are custom hooks in React? Write a simple example.

Core Answer: Custom hooks are regular JavaScript functions that start with the word use and can call other built-in React hooks. They are the primary mechanism for extracting and reusing stateful logic across different components without copying and pasting code.

JavaScript

```
function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);
    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return width;
}
```

Interviewer Counter-Question: If two different components call the useWindowWidth hook, do they share the exact same state instance?
Answer: No. Custom hooks share stateful logic, not state itself. Each component calling the hook gets a completely independent, isolated instance of the state.

Scenario Challenge: You wrote a utility function fetchUserData() to handle API calls. You want to add useState inside it to handle loading states. React throws an error. Why?
Solution: You can only call Hooks inside React components or custom Hooks. You must rename fetchUserData to useFetchUserData to satisfy the Rules of Hooks.

### Q52. What is lazy loading in React and how is it implemented?

Core Answer: Lazy loading is a technique to defer the loading of non-critical components until they are actually needed (e.g., when a user navigates to a specific route). It is implemented using React.lazy() for dynamic imports and wrapped in a <Suspense> boundary to show a fallback UI (like a spinner) while the component downloads.

Interviewer Counter-Question: Why is lazy loading important for Single Page Applications (SPAs)?
Answer: By default, standard bundlers like Webpack package the entire application into a single massive JavaScript file. Lazy loading splits this bundle up (code splitting), drastically reducing the initial download size and improving the Time to Interactive (TTI) on the first load.

Scenario Challenge: You lazy-loaded a massive charting component. A user with a terrible internet connection tries to view it, but they just stare at a blank white screen for 10 seconds before it appears.
Solution: You forgot the Suspense boundary. You must wrap the lazy-loaded component: <Suspense fallback="{<Spinner"/>}><HeavyChart/></Suspense>.

### Q53. What are React error boundaries and why are they useful?

Core Answer: Error Boundaries are a safety net for React applications. If JavaScript throws an error during rendering, lifecycle methods, or in constructors, it normally crashes the entire React component tree, resulting in a blank white screen. Error boundaries catch these errors, log them, and render a graceful fallback UI instead of crashing the whole app.

Interviewer Counter-Question: Can you write an error boundary using functional components and hooks?
Answer: No, there is currently no hook equivalent for getDerivedStateFromError or componentDidCatch. Error boundaries must be written as Class components (or implemented using a third-party library like react-error-boundary).

Scenario Challenge: A user clicks a "Submit" button, and the API request throws a 500 error inside an onClick handler. You have an Error Boundary at the top of the app, but the app doesn't show the fallback UI. Why?
Solution: Error boundaries do not catch errors in event handlers, asynchronous code (like setTimeout), or server-side rendering. You must handle those manually using standard try/catch blocks.

### Q54. What is the Context API and when should you use Redux instead?

Core Answer: The Context API is a built-in React feature designed specifically to solve prop-drilling by providing a way to pass data deeply through the component tree without passing props manually.
You should reach for Redux (or modern alternatives like Zustand/Redux Toolkit) instead of Context when:

You have high-frequency state updates (Context triggers re-renders on all consumers).

You need complex, asynchronous state transformations (middleware/thunks).

You require deep debugging capabilities (Redux DevTools for time-travel).

Interviewer Counter-Question: If Context causes all consumers to re-render, how can you mitigate performance issues?
Answer: You can split your state into multiple smaller Contexts logically (e.g., ThemeContext and AuthContext separate) or memoize the provider's value using useMemo so it doesn't trigger re-renders unless the underlying data actually changes.

Scenario Challenge: You are building a live dashboard showing real-time stock prices updating every 100 milliseconds. Should you put this data in the Context API?
Solution: Absolutely not. The rapid updates will force every component consuming the Context to re-render 10 times a second, grinding the app to a halt. This requires a dedicated state manager or localized state.

### Q55. Explain the concept of reconciliation in React.

Core Answer: Reconciliation is the internal algorithm React uses to diff (compare) the previous Virtual DOM tree with the newly generated Virtual DOM tree after a state or prop update. It figures out exactly what changed and calculates the most efficient way to patch those exact changes into the real browser DOM. React 16 introduced the "Fiber" architecture to make this process interruptible and prioritized.

Interviewer Counter-Question: Comparing two trees is traditionally an O(n³) operation. How does React do it so fast (O(n))?
Answer: React relies on two heuristics:

Two elements of different types will produce completely different trees (React won't bother diffing their contents; it just unmounts the old and mounts the new).

The developer will provide a unique key prop to hint which child elements are stable across renders.

Scenario Challenge: You have a <div> containing a complex, heavy component. You decide to change the wrapper from <div> to a <section>. What does React do during reconciliation?
Solution: Because the root element type changed from div to section, React assumes the entire subtree is invalid. It will unmount the heavy component entirely and mount it from scratch, destroying its local state in the process.

### Q56. What is the difference between React.Fragment and empty tags (<>)?

Core Answer: Both are used to group multiple sibling elements together without adding an extra, meaningless wrapper node (like an unnecessary <div>) to the actual DOM. <> is simply syntactic sugar for <React.Fragment>.

Interviewer Counter-Question: If they are the same, when are you strictly required to use <React.Fragment>?
Answer: You must use the full <React.Fragment> syntax when mapping over an array to return grouped elements because you need to pass a key prop. The shorthand <> syntax does not accept any attributes, including keys.

Scenario Challenge: You are rendering a description list <dl> and need to dynamically generate <dt> and <dd> pairs from an array. Wrapping the pair in a <div> breaks the HTML validation.
Solution: Use <React.Fragment key="{item.id}"> to group the <dt> and <dd> together cleanly.

### Q57. How do you handle forms in React? Explain with Formik or react-hook-form.

Core Answer: While you can handle forms natively in React using controlled components (useState for every input), it requires massive boilerplate for validation, error handling, and touched states.
Libraries solve this. react-hook-form is the modern standard because it leverages uncontrolled components via refs. It registers inputs without deeply linking them to component state, meaning typing in a field doesn't trigger a re-render of the entire form, resulting in much better performance.

Interviewer Counter-Question: What is the primary difference in philosophy between Formik and react-hook-form?
Answer: Formik relies heavily on controlled state and React Context, causing the entire form to re-render on every single keystroke. react-hook-form isolates renders using refs, re-rendering only when absolutely necessary (like showing an error message).

Scenario Challenge: You have a large registration form. Typing rapidly into the "First Name" field feels incredibly sluggish and delayed.
Solution: The form is likely fully controlled and doing complex validation or triggering deep re-renders on every keystroke. You can fix this by debouncing the validation, or migrating to react-hook-form.

### Q58. What is code splitting in React and how does it improve performance?

Core Answer: Code splitting is the practice of breaking down a large JavaScript bundle into smaller, logical chunks. Instead of downloading the entire application on the first visit, the browser only downloads the chunk needed for the initial route. This dramatically reduces the initial payload, improving the First Contentful Paint (FCP) and Time to Interactive (TTI) metrics.

Interviewer Counter-Question: Besides Route-based code splitting, what is another common boundary to split code?
Answer: Component-based code splitting. You can code-split heavy, user-triggered UI elements that aren't visible immediately—like large Modals, complex rich-text editors, or third-party charting libraries.

Scenario Challenge: You implement React Router and lazy-load all 20 of your routes. However, users complain that every time they click a nav link, they stare at a spinner for 2 seconds.
Solution: You split the code too aggressively without prefetching. You can implement on-hover prefetching (loading the module when the user hovers over the link) so the chunk is already downloaded by the time they click.

### Q59. What are portals in React and when are they useful?

Core Answer: Portals (ReactDOM.createPortal) provide a first-class way to render children into a DOM node that exists entirely outside the DOM hierarchy of the parent component. They are primarily used for UI elements that must break out of their container to avoid CSS constraints like z-index conflicts or overflow: hidden, such as Modals, Tooltips, and Dropdowns.

Interviewer Counter-Question: If a Modal is rendered in a Portal attached to the document.body, how does event bubbling work? Does an onClick event bubble up to the document.body or up the React tree?
Answer: It bubbles up the React tree. Even though the element is physically somewhere else in the DOM, React portals maintain their position in the React component hierarchy. An event fired inside the portal will bubble up to the React parent that invoked it.

Scenario Challenge: You build a Modal component inside a deeply nested sidebar, but it gets cut off because the sidebar has overflow: hidden applied to it.
Solution: Use createPortal to render the Modal's JSX directly into a <div id="modal-root"> located at the very end of your index.html <body>, escaping the sidebar's CSS constraints entirely.

### Q60. Explain the lifecycle of a React functional component with hooks.

Core Answer: Unlike Class components, Functional components don't have explicit lifecycle methods (like componentDidMount or componentWillUnmount). Instead, they execute top-to-bottom on every render. We tap into the component's lifecycle using the useEffect hook:

Mounting: useEffect(..., []) runs once after the initial render.

Updating: useEffect(..., [deps]) runs after the initial render and whenever a dependency changes.

Unmounting: The return () => {} function inside a useEffect runs right before the component unmounts (and before the next effect runs on updates) to clean up subscriptions or timers.

Interviewer Counter-Question: Why does React strict mode in development run useEffect twice on mount?
Answer: React 18 introduced this intentionally to help developers catch bugs. By immediately mounting, unmounting (running the cleanup), and remounting, it forces you to ensure your useEffect cleanup functions are implemented correctly and don't cause memory leaks.

Scenario Challenge: You need to measure the width of a DOM element to position a tooltip accurately before the browser paints it to the screen, otherwise the tooltip flickers. useEffect is causing a flicker.
Solution: useEffect runs asynchronously after the browser paints. For synchronous DOM measurements, you must use useLayoutEffect, which runs synchronously immediately after React performs all DOM mutations but before the browser paints.
