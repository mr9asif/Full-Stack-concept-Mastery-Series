What is the difference between async and defer in script loading?
async: downloads the script in parallel and executes it immediately when ready.
defer: downloads in parallel but executes after HTML parsing, maintaining script order.

Explain the CSS stacking context.

A stacking context controls how elements are layered on the Z-axis. Properties such as position with z-index, transform, opacity < 1, and isolation can create new stacking contexts.

What are CSS custom properties, and why are they useful?

CSS custom properties (variables) allow reusable and dynamic values.

```
:root {
  --primary-color: blue;
}

button {
  background: var(--primary-color);
}
```

What is the difference between transform, transition, and animation?
transform: changes an element's visual appearance or position.
transition: animates a change between states.
animation: creates multi-step or repeated animations using @keyframes.

What is the CSS cascade, and what are cascade layers?

The CSS cascade determines which style wins based on origin, importance, cascade layers, specificity, and source order. @layer allows developers to organize CSS priority intentionally.

```
Example:

@layer base, components, utilities;

@layer base {
button {
color: black;
}
}

@layer utilities {
.text-red {
color: red;
}
}
```
