1. What is React reconciliation?

React compares the previous and new Virtual DOM and updates only the necessary parts of the real DOM.

2. How does React decide what to update?

It compares element type, props, and keys. Different types usually cause replacement, while keys help identify items in lists.

3. What causes a React component to re-render?

A component re-renders when its state, props, consumed context, or subscribed external store changes, or when its parent renders.

4. Does re-rendering always update the real DOM?

No. React can re-render and then determine that no actual DOM changes are needed.

5. What is React Fiber?

React Fiber is React's internal rendering architecture that allows React to prioritize, pause, resume, and interrupt rendering work.

6. What is the difference between useMemo and useCallback?

useMemo memoizes a computed value, while useCallback memoizes a function reference.

7. What is React.memo?

React.memo prevents unnecessary re-rendering of a component when its props have not changed.

8. When should you use memoization?

Use it for expensive calculations or preventing unnecessary renders, not everywhere because memoization also has overhead.

9. What is a stale closure?

A stale closure happens when a function captures an old state or prop value from a previous render.

10. What is the difference between controlled and uncontrolled components?

A controlled component stores its value in React state, while an uncontrolled component stores it in the DOM, usually accessed using ref.

11. What is lifting state up?

Move state to the closest common parent when multiple child components need to share or update the same state.

12. What is prop drilling?

Prop drilling is passing props through multiple components that don't need them just to reach a deeply nested component.

13. How can you avoid prop drilling?

Use Context, state management libraries, component composition, or restructure the component hierarchy.

14. Context API vs Redux/Zustand?

Context is good for relatively simple global state, while Redux/Zustand is better for complex state and optimized selective updates.

15. What is useRef used for?

useRef stores a mutable value or DOM reference without causing a re-render when it changes.

16. What is useEffect used for?

useEffect is used to synchronize a component with external systems, such as APIs, subscriptions, timers, or browser APIs.

17. What is the cleanup function in useEffect?

It runs before the effect runs again or when the component unmounts, helping clean up timers, subscriptions, or event listeners.

18. What is useLayoutEffect?

It runs synchronously after DOM updates but before the browser paints, mainly for DOM measurements or layout calculations.

19. What is the difference between useEffect and useLayoutEffect?

useEffect runs after painting, while useLayoutEffect runs before painting and can block visual updates.

20. What is React Suspense?

Suspense allows React to show a fallback UI while a component or supported async resource is loading.

21. What is code splitting?

Code splitting breaks the application into smaller JavaScript bundles that can be loaded only when needed.

22. What is React.lazy()?

React.lazy() allows a component to be loaded dynamically, usually together with Suspense.

23. What is concurrent rendering?

Concurrent rendering allows React to prioritize important updates and interrupt lower-priority rendering to keep the UI responsive.

24. What is useTransition?

useTransition marks a state update as non-urgent, allowing urgent updates like typing to remain responsive.

25. What is useDeferredValue?

It allows React to defer updating a value used in expensive UI rendering, helping keep urgent interactions smooth.

26. What is the difference between useTransition and useDeferredValue?

useTransition marks an update as low priority, while useDeferredValue gives you a deferred version of a changing value.

27. Why are keys important in React?

Keys help React identify which list items were added, removed, changed, or reordered, preserving correct component state.

28. Why shouldn't you use array index as a key?

Indexes can cause incorrect state and UI behavior when items are reordered, inserted, or deleted.

29. Why shouldn't you mutate state directly?

React relies on state changes and object references to detect updates, so state should be updated immutably.

30. How do you optimize React performance?

Use React.memo, useMemo, useCallback, code splitting, lazy loading, virtualization, and proper state structure—but only optimize after identifying a real performance problem.
