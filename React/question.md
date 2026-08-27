1. What is React?

Answer:
React is a JavaScript library used to build user interfaces using reusable components.

2. Is React a library or a framework?

Answer:
React is a JavaScript library, mainly focused on building UI.

3. What is a Component?

Answer:
A component is a reusable and independent piece of UI.

4. What is JSX?

Answer:
JSX is a syntax that allows us to write HTML-like code inside JavaScript.

5. Is JSX HTML?

Answer:
No. JSX looks like HTML, but it is JavaScript syntax that gets transformed into JavaScript.

Props and State 6. What are Props?

Answer:
Props are used to pass data from a parent component to a child component.

7. Can we modify Props?

Answer:
No. Props are read-only and should not be modified by the child component.

8. What is State?

Answer:
State is data managed by a component that can change over time.

9. What happens when State changes?

Answer:
React re-renders the component and updates the UI where necessary.

10. What is the difference between Props and State?

Answer:

Props: Data comes from the parent and is read-only.
State: Managed by the component and can be updated.
Rendering 11. What is Conditional Rendering?

Answer:
Conditional rendering means showing different UI based on a condition.

12. How do you render a list in React?

Answer:
Usually by using the .map() method.

13. What is a Key in React?

Answer:
A key is a unique identifier that helps React identify list items when they change, are added, or removed.

14. Why should we avoid using array index as a key?

Answer:
Because when items are added, removed, or reordered, it can cause incorrect UI or state issues.

15. What causes a component to re-render?

Answer:
A component can re-render when:

State changes
Props change
Its parent re-renders
Hooks 16. What is a Hook?

Answer:
A Hook is a special React function that allows functional components to use React features like state and effects.

17. What is useState?

Answer:
useState is a Hook used to create and manage state in functional components.

18. What does useState return?

Answer:
It returns:

The current state
A function to update the state 19. How do you update state based on the previous state?

Answer:

setCount(prev => prev + 1);

Use this when the new state depends on the previous state.

20. What is useEffect?

Answer:
useEffect is a Hook used to handle side effects such as API calls, timers, and event listeners.

21. What is the dependency array in useEffect?

Answer:

No dependency array → Runs after every render
[] → Runs after the initial mount
[value] → Runs when value changes 22. What is a cleanup function?

Answer:
A cleanup function removes or cleans up side effects before the effect runs again or when the component unmounts.

23. What is useRef?

Answer:
useRef is used to access DOM elements or store mutable values without causing a re-render.

24. What is the difference between useState and useRef?

Answer:

useState update → Causes re-render
useRef update → Does not cause re-render 25. What is useContext?

Answer:
useContext allows components to access shared data from Context without passing props through every level.

26. What is useReducer?

Answer:
useReducer is a Hook used for managing complex state logic using a reducer function and actions.

27. When should you use useReducer instead of useState?

Answer:
Use useReducer when state logic is complex or multiple related state updates need to be handled.

28. What is a Custom Hook?

Answer:
A Custom Hook is a reusable function used to share stateful logic between components.

29. What are the Rules of Hooks?

Answer:

Call Hooks only at the top level.
Call Hooks only inside React function components or Custom Hooks. 30. Why can't Hooks be called conditionally?

Answer:
Because React depends on Hooks being called in the same order on every render.

State Management 31. What is Props Drilling?

Answer:
Props drilling means passing data through multiple intermediate components to reach a deeply nested component.

32. How can you avoid Props Drilling?

Answer:
You can use:

Context API
Redux
Zustand 33. What is Context API?

Answer:
Context API allows us to share data between components without manually passing props through every level.

34. What is Lifting State Up?

Answer:
It means moving shared state to the closest common parent so multiple child components can use the same state.

35. What is a single source of truth?

Answer:
It means keeping shared data in one central place instead of duplicating the same state in multiple components.

Virtual DOM & Rendering 36. What is the Virtual DOM?

Answer:
The Virtual DOM is a lightweight JavaScript representation of the Real DOM.

37. Why does React use Virtual DOM?

Answer:
React compares the previous and new Virtual DOM and updates only the necessary parts of the Real DOM.

38. What is Reconciliation?

Answer:
Reconciliation is the process where React compares the old and new Virtual DOM to determine what needs to change.

39. Does re-render mean the whole DOM updates?

Answer:
No. React determines the necessary changes and updates only the required parts of the DOM.

40. What is React Fiber?

Answer:
React Fiber is React's internal architecture that helps manage, prioritize, and schedule rendering work efficiently.

Performance Optimization 41. What is React.memo?

Answer:
React.memo memoizes a component and can prevent unnecessary re-renders when its props have not changed.

42. What is useMemo?

Answer:
useMemo memoizes a calculated value to avoid unnecessary recalculation.

43. What is useCallback?

Answer:
useCallback memoizes a function and keeps the same function reference until its dependencies change.

44. What is the difference between React.memo, useMemo, and useCallback?

Answer:

React.memo → Memoizes Component
useMemo → Memoizes Value
useCallback → Memoizes Function 45. Should you use useMemo and useCallback everywhere?

Answer:
No. Use them only when there is a real performance benefit because memoization also has a cost.

Other Important Questions 46. What is a Controlled Component?

Answer:
A controlled component is a form element whose value is controlled by React state.

47. What is an Uncontrolled Component?

Answer:
An uncontrolled component manages its own data in the DOM, usually accessed using a ref.

48. What is an Error Boundary?

Answer:
An Error Boundary catches errors in its child component tree and displays a fallback UI.

49. What is a React Portal?

Answer:
A React Portal allows rendering a component into a different DOM node outside its parent DOM hierarchy.

Common use: Modals and dialogs.

50. What is the difference between Client State and Server State?

Answer:

Client State: UI-related data managed on the client, such as theme or modal state.
Server State: Data that comes from and is synchronized with a server, such as users or products.

Examples: React Query is commonly used for server state.

🔥 If you have very little time, master these first

Top Priority:

Component
JSX
Props vs State
useState
useEffect
useRef
useContext
useReducer
Props Drilling
Component Re-rendering
Virtual DOM
Keys
React.memo
useMemo vs useCallback
Controlled vs Uncontrolled Components

These 15 topics are the core ones I would master first for a React interview.
