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

App
├── Navbar
├── Sidebar
├── Post
│ └── Comment
└── Footer

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

Website
├── Navbar Component
├── Sidebar Component
├── Product Component
└── Footer Component

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

const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>
{count}
</button>

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

Example:

const element = <h1>Hello React</h1>;

দেখতে HTML-এর মতো হলেও এটি HTML না। এটি JSX।

React পরে JSX-কে JavaScript code-এ convert করে।

JSX কেন ব্যবহার করি?

JSX ব্যবহার করলে UI code লেখা সহজ এবং readable হয়।

Without JSX:

React.createElement("h1", null, "Hello");

With JSX:

<h1>Hello</h1>

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

সবচেয়ে গুরুত্বপূর্ণ মনে রাখো

JSX is a syntax extension that allows us to write HTML-like code inside JavaScript. Browsers cannot understand JSX directly, so it is transformed into JavaScript before execution.
