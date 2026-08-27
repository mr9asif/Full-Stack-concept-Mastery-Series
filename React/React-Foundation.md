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
