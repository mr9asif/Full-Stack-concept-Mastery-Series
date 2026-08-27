1. React Fundamentals (React Basics)

প্রথমে React-এর একদম বেসিক জিনিসগুলো পরিষ্কার করি। Interview-তে এখান থেকেই অনেক প্রশ্ন আসে।

React কী?

React হলো JavaScript library, যা মূলত User Interface (UI) তৈরির জন্য ব্যবহার করা হয়।

বিশেষ করে Single Page Application (SPA) তৈরিতে React খুব জনপ্রিয়।

সহজভাবে:

ধরো একটি ওয়েবসাইটে আছে:

Navbar
Sidebar
Post
Comment
Footer

React-এ এগুলোকে আলাদা আলাদা Component হিসেবে তৈরি করা যায়।

```
App
├── Navbar
├── Sidebar
├── Post
│ └── Comment
└── Footer
```

এতে code reusable, manageable এবং maintain করা সহজ হয়।

Important Interview Questions

1. What is React?

Answer:

React is a JavaScript library for building user interfaces. It uses a component-based architecture, allowing developers to build reusable and interactive UI components.

সহজে মনে রাখো:

React = JavaScript Library + Component-Based UI

2. Is React a library or a framework?

Answer:

React is a JavaScript library, not a full framework.

It mainly focuses on building the UI layer. For routing, state management, and other features, we can use additional libraries.

3. What is component-based architecture?

Answer:

Component-based architecture means breaking the UI into small, independent, and reusable components.

Example:

```
Website
├── Navbar Component
├── Sidebar Component
├── Product Component
└── Footer Component
```

Benefit:

Reusable
Easy to maintain
Easy to test
Organized code 4. What are the main features of React?

Answer:

The important features of React are:

Component-based architecture
Declarative UI
Virtual DOM
Reusable components
One-way data flow
State management
Efficient UI updates 5. What is declarative programming in React?

Answer:

Declarative programming means we describe what the UI should look like, and React handles how to update the DOM.

Example:

```
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>
{count}
</button>
```

আমরা শুধু বলছি:

Count পরিবর্তন হলে UI-তে নতুন count দেখাও।

কিন্তু DOM কীভাবে update হবে, সেটা React handle করে।

6. Why is React popular?

Answer:

React is popular because it provides:

Reusable components
Fast UI updates using Virtual DOM
Large ecosystem
Easy state management
Strong community support
Good performance for dynamic applications
সবচেয়ে গুরুত্বপূর্ণ মনে রাখার লাইন

React is a JavaScript library used to build user interfaces using reusable components. It follows a declarative and component-based approach.

## 2. JSX

JSX কী?

JSX = JavaScript XML

JSX হলো এমন একটি syntax যা ব্যবহার করে আমরা JavaScript-এর ভিতরে HTML-এর মতো UI লিখতে পারি।

```
Example:

const element = <h1>Hello React</h1>;
```

দেখতে HTML-এর মতো হলেও এটি HTML না। এটি JSX।

React পরে JSX-কে JavaScript code-এ convert করে।

JSX কেন ব্যবহার করি?

JSX ব্যবহার করলে UI code লেখা সহজ এবং readable হয়।

```
Without JSX:

React.createElement("h1", null, "Hello");

With JSX:

<h1>Hello</h1>
```

তাই JSX বেশি সহজ এবং readable।

Important Interview Questions

### 1. What is JSX?

Answer:

JSX is a syntax extension for JavaScript that allows us to write HTML-like code inside JavaScript. React converts JSX into JavaScript that creates React elements.

Short answer:

JSX allows us to write HTML-like UI inside JavaScript.

### 2. Is JSX HTML?

Answer:

No. JSX looks similar to HTML, but it is not HTML. It is a JavaScript syntax extension that is converted into JavaScript code.

3. Can browsers understand JSX directly?

Answer:

No. Browsers cannot understand JSX directly.

JSX must be transformed/compiled into regular JavaScript before the browser can execute it.

4. What is the difference between HTML and JSX?

Important differences:

HTML uses class, JSX uses className
HTML uses for, JSX uses htmlFor
JSX attributes generally use camelCase
JSX expressions use {}

```
Example:

<label htmlFor="email">Email</label>

<input
  className="input"
  onClick={handleClick}
/> 5. How do you write JavaScript inside JSX?

We use curly braces {}.

const name = "Reja";

function App() {
return <h1>Hello, {name}</h1>;
}

Output:

Hello, Reja

You can also use expressions:

<p>{10 + 20}</p>
6. Can JSX return multiple elements?

Yes, but they need to be wrapped inside a single parent element or a Fragment.

function App() {
return (
<>

<h1>Hello</h1>
<p>Welcome</p>
</>
);
}

<> </> হলো React Fragment।
```

সবচেয়ে গুরুত্বপূর্ণ মনে রাখো

JSX is a syntax extension that allows us to write HTML-like code inside JavaScript. Browsers cannot understand JSX directly, so it is transformed into JavaScript before execution.

3. Components
   Component কী?

Component হলো UI-এর একটি ছোট, reusable অংশ।

যেমন:

Navbar
Button
Card
Footer

একটি website = অনেকগুলো Component।

function Welcome() {
return <h1>Hello</h1>;
}
Important Interview Questions

1. What is a Component in React?

Answer:

A component is a reusable and independent piece of UI.

2. What are the types of Components?

মূলত:

Functional Component ✅
Class Component (পুরোনো, এখন কম ব্যবহার হয়)

আজকাল বেশি ব্যবহার হয় Functional Component + Hooks।

3. What is the difference between Functional and Class Components?

Answer:

Functional components are simple JavaScript functions and use Hooks for state and other React features.

Class components use JavaScript classes and lifecycle methods.

👉 Modern React mainly uses Functional Components.

4. Why do we use Components?

Answer:

Code reusable হয়
Code maintain করা সহজ
বড় UI ছোট ছোট অংশে ভাগ করা যায়
মনে রাখো:

Component = Reusable piece of U

4. Props
   Props কী?

Props হলো Parent Component থেকে Child Component-এ data পাঠানোর উপায়।

সহজভাবে:

```
Props = Parent → Child data

function User({ name }) {
return <h1>{name}</h1>;
}

function App() {
return <User name="Reja" />;
}
```

এখানে "Reja" হলো props হিসেবে User component-এ যাচ্ছে।

Important Interview Questions

1. What are Props?

Answer:

Props are used to pass data from a parent component to a child component.

2. Can we modify Props?

Answer:

No. Props are read-only and cannot be modified by the child component.

Props are immutable.

3. What is the difference between Props and State?

Answer:

Props: Parent থেকে data আসে, read-only।
State: Component নিজের data manage করে এবং update করতে পারে।
মনে রাখো:

Props = Data from Parent
State = Component's own data 3. Components
Component কী?

Component হলো UI-এর একটি ছোট, reusable অংশ।

যেমন:

Navbar
Button
Card
Footer

একটি website = অনেকগুলো Component।

```
function Welcome() {
return <h1>Hello</h1>;
}
```

Important Interview Questions

1. What is a Component in React?

Answer:

A component is a reusable and independent piece of UI.

2. What are the types of Components?

মূলত:

Functional Component ✅
Class Component (পুরোনো, এখন কম ব্যবহার হয়)

আজকাল বেশি ব্যবহার হয় Functional Component + Hooks।

3. What is the difference between Functional and Class Components?

Answer:

Functional components are simple JavaScript functions and use Hooks for state and other React features.

Class components use JavaScript classes and lifecycle methods.

👉 Modern React mainly uses Functional Components.

4. Why do we use Components?

Answer:

Code reusable হয়
Code maintain করা সহজ
বড় UI ছোট ছোট অংশে ভাগ করা যায়
মনে রাখো:

Component = Reusable piece of UI

Next: 4. Props

31. React Portals
    React Portal কী?

React Portal ব্যবহার করে একটি component-এর UI তার parent DOM-এর বাইরে অন্য DOM node-এ render করা যায়।

Common use:

Modal
Dialog
Tooltip
Important Interview Questions

1. What is a React Portal?

Answer:

A React Portal allows us to render a component into a different DOM node outside its parent DOM hierarchy.

2. When do we use React Portals?

Answer:

React Portals are commonly used for:

Modals
Dialogs
Tooltips
মনে রাখো:

Portal = Render UI outside the parent DOM hierarchy

next 32. Higher-Order Components (HOC)
HOC কী?

HOC হলো একটি function যা একটি component নেয় এবং enhanced/new component return করে।

সহজভাবে:

Component → HOC → Enhanced Component

Example:

```
const withAuth = (Component) => {
return function EnhancedComponent(props) {
return <Component {...props} />;
};
};
```

Important Interview Questions

1. What is a Higher-Order Component (HOC)?

Answer:

A Higher-Order Component is a function that takes a component and returns a new enhanced component.

2. Why do we use HOC?

Answer:

HOCs are used to reuse component logic across multiple components.

Examples:

Authentication
Authorization
Logging
মনে রাখো:

HOC = Function that takes a Component and returns an enhanced Component

next 33. Render Props
Render Props কী?

Render Props হলো একটি technique যেখানে একটি component অন্য component-কে একটি function দেয়, যাতে logic reuse করা যায়।

সহজভাবে:

Render Props = Share logic using a function prop

Example:

```
<DataProvider
render={(data) => <UserList data={data} />}
/>
```

Important Interview Questions

1. What is the Render Props pattern?

Answer:

Render Props is a pattern where a component shares logic by passing a function as a prop.

2. Why do we use Render Props?

Answer:

It is used to reuse logic between components.

মনে রাখো:

Render Props = Reuse component logic through a function prop
