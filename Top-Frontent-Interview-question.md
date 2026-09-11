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

What is the difference between the cascade and specificity?

Specificity is only one part of the CSS cascade.

The cascade considers things such as:

Origin and importance
Cascade layers
Specificity
Source order

So a rule with lower specificity can sometimes win because of layer priority or other cascade rules.
What is :where() and how is it different from :is()?

The key difference is specificity.

:where(.card, .modal) button {
color: red;
}

:where() always has zero specificity.

:is(.card, .modal) button {
color: red;
}

:is() takes the specificity of the most specific selector in its arguments.

Senior developers often use :where() to create easily overridable base styles.

## What is the :has() selector?

:has() allows selecting an element based on its descendants or related conditions.

.card:has(img) {
padding-top: 0;
}

You can think of it as enabling more relational or parent-aware CSS selection.

### How do you avoid layout thrashing?

Layout thrashing happens when JavaScript repeatedly:

Reads layout information.
Changes styles.
Reads layout again.

For example, repeatedly accessing offsetHeight after modifying styles can force synchronous layout calculations.

To avoid it:

Batch DOM reads.
Batch DOM writes.
Avoid unnecessary layout measurements.
Use requestAnimationFrame when appropriate.
Prefer transform for visual movement.

What is will-change, and why shouldn't you overuse it?

will-change tells the browser that a property may change.

.element {
will-change: transform;
}

The browser may prepare optimization resources in advance.

But overusing it can increase memory usage and hurt performance.

Explain min-content, max-content, and fit-content().

These are intrinsic sizing keywords.

min-content: smallest width without overflowing content where possible.
max-content: width required without wrapping where applicable.
fit-content(): limits intrinsic sizing based on available constraints.

Example:

grid-template-columns:
min-content
1fr
max-content;

They are especially useful in advanced Grid layouts.

What is the difference between auto-fill and auto-fit in CSS Grid?
repeat(auto-fill, minmax(200px, 1fr))

auto-fill creates as many tracks as can fit, including potentially empty tracks.

repeat(auto-fit, minmax(200px, 1fr))

auto-fit collapses empty tracks and allows existing items to expand.

Common use: auto-fit is often preferred for responsive card grids.

Explain subgrid.

subgrid allows a nested grid to inherit the parent grid's track definitions.

.child {
display: grid;
grid-template-columns: subgrid;
}

What is the difference between overflow: hidden, clip, and clip-path?
overflow: hidden: clips overflowing content and creates a scroll container behavior context.
overflow: clip: clips overflow without creating a scroll container.
clip-path: creates custom clipping shapes.
clip-path: circle(50%);

Use them based on whether you need scrolling behavior or complex visual clipping.

What are logical CSS properties?

Logical properties allow layouts to adapt better to different writing directions.

Instead of:

margin-left: 20px;

You can use:

margin-inline-start: 20px;

Other examples:

padding-block
margin-inline
border-inline-start
inset-block

They are useful for internationalized and direction-independent layouts.

What is the difference between 100vh, 100dvh, 100svh, and 100lvh?

Mobile browsers can have dynamic browser UI.

vh: traditional viewport unit.
dvh: dynamic viewport height.
svh: small viewport height.
lvh: large viewport height.

For full-screen mobile layouts, 100dvh is often more appropriate when the layout should react to browser UI changes.

What is CSS @property?

@property allows you to define typed, animatable custom properties.

@property --rotation {
syntax: "<angle>";
inherits: false;
initial-value: 0deg;
}

Then:

.element {
transform: rotate(var(--rotation));
}

This enables more controlled custom-property animation.

How would you architect CSS for a large-scale application?

A strong senior-level answer:

I avoid solving every problem with higher specificity. I establish predictable style boundaries using a consistent architecture, such as component-scoped styles, CSS Modules, BEM, utility classes, or a design system. I use design tokens for colors, spacing, typography, and breakpoints, control global styles carefully, and use cascade layers where they help establish clear priority. The goal is maintainability, low specificity conflicts, predictable overrides, and reusable components.

fsdkflsdkflsdfsd
asdkfsd
