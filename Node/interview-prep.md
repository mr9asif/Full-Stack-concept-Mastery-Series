### Q1. What is Node.js and how does it work under the hood?

Core Answer: Node.js is an open-source, cross-platform JavaScript runtime environment built on Chrome's V8 engine. It allows developers to execute JavaScript on the server side. Under the hood, Node.js uses an event-driven, non-blocking I/O model, heavily relying on the libuv library to handle asynchronous operations and the Event Loop, making it highly efficient for data-intensive, real-time applications.

Interviewer Counter-Question: If Node.js is single-threaded, how does it handle thousands of concurrent requests?
Answer: Node.js handles the event loop on a single main thread, but it delegates heavy I/O operations (like file system access or network requests) to a background thread pool (managed by libuv). Once the background task finishes, a callback is pushed back to the main thread's event loop to be executed.

Scenario Challenge: You are building an application that performs heavy video encoding on the server. Should you use Node.js?
Solution: No. CPU-intensive tasks like video encoding will block the single main thread, preventing Node.js from processing other incoming requests. For CPU-bound tasks, languages like C++, Go, or Rust, or using Node's Worker Threads, are better suited.

### Q2. Explain the Node.js Event Loop.

Core Answer: The Event Loop is the mechanism that allows Node.js to perform non-blocking I/O operations. It continuously checks for pending tasks, executes them, and offloads operations to the system kernel whenever possible. It operates in distinct phases: Timers (setTimeout/setInterval), Pending Callbacks, Idle/Prepare, Poll (retrieving new I/O events), Check (setImmediate), and Close Callbacks.

Interviewer Counter-Question: In which phase of the Event Loop are process.nextTick() callbacks executed?
Answer: process.nextTick() is technically not part of the Event Loop itself. Callbacks passed to it are executed immediately after the current operation completes, before the Event Loop moves on to the next phase.

Scenario Challenge: You have a setTimeout with a 0ms delay and a fs.readFile operation. Which callback will execute first?
Solution: The setTimeout callback will execute first because the Event Loop enters the Timers phase before the Poll phase (where I/O callbacks like file reads are handled).

### Q3. What is the difference between process.nextTick() and setImmediate()?

Core Answer:

process.nextTick() fires immediately on the same phase, right after the current operation finishes and before the Event Loop continues to the next phase.

setImmediate() fires in the specific "Check" phase of the Event Loop, which occurs immediately after the "Poll" phase.

Interviewer Counter-Question: Can process.nextTick() cause an application to freeze?
Answer: Yes. If you recursively call process.nextTick(), it will continuously add callbacks to the microtask queue, starving the Event Loop and preventing it from ever reaching the Poll phase to handle incoming I/O.

Scenario Challenge: You need to emit an event from a constructor function immediately upon instantiation, but listeners haven't been attached yet. How do you solve this?
Solution: Wrap the this.emit() call inside process.nextTick(). This guarantees that the constructor finishes and listeners are attached before the event is actually emitted.

### Q4. What is callback hell and how do you resolve it?

Core Answer: Callback hell (or the "Pyramid of Doom") occurs when multiple asynchronous operations are nested inside each other, resulting in heavily indented, hard-to-read, and difficult-to-maintain code. It is resolved by using modern JavaScript features like Promises, async/await, or modularizing callbacks into separate named functions.

Interviewer Counter-Question: How does async/await actually work under the hood?
Answer: async/await is syntactic sugar over Promises. Under the hood, it uses JavaScript Generators to pause the execution of the function (using yield) until the Promise resolves, allowing asynchronous code to look and behave synchronously.

Scenario Challenge: You have an old legacy Node.js library that only exposes callback-based APIs, but you want to use it with async/await in your new codebase.
Solution: Use Node's built-in util.promisify() method to wrap the legacy callback-based function and convert it into a function that returns a Promise.

### Q5. What are Streams in Node.js and why are they used?

Core Answer: Streams are collections of data that might not be available all at once and don't have to fit in memory. They allow you to read data from a source or write data to a destination in small, continuous chunks. The four types are Readable, Writable, Duplex, and Transform streams.

Interviewer Counter-Question: How is a Stream different from a Buffer?
Answer: A Buffer stores the entire chunk of data in RAM before it can be processed. A Stream processes data piece by piece as it arrives without keeping the whole payload in memory, making it far more memory-efficient for large files.

Scenario Challenge: Your Express API allows users to download a massive 5GB log file. Currently, the server crashes with an "Out of Memory" error when 10 users click download at once.
Solution: You are likely using fs.readFile(), which loads the entire 5GB into RAM. Switch to fs.createReadStream() and pipe (.pipe()) it directly to the Express res (response) object to stream the file in small chunks.

### Q6. What is the purpose of the Buffer class?

Core Answer: The Buffer class in Node.js provides a way to handle raw binary data outside the V8 engine. Since standard JavaScript traditionally lacked a way to handle raw binary streams (before typed arrays), Buffers are used to manipulate TCP streams, file system operations, and cryptographic functions.

Interviewer Counter-Question: Are Buffers stored in the V8 heap?
Answer: No. Buffers are allocated in raw C++ memory outside the V8 heap. Node.js manages this memory, which prevents large binary data payloads from clogging up the V8 garbage collector.

Scenario Challenge: You receive binary image data over a WebSocket and need to convert it to a Base64 string to save it to a database.
Solution: You wrap the incoming binary data in a buffer using Buffer.from(data) and then convert it using buffer.toString('base64').

### Q7. Explain the EventEmitter module.

Core Answer: The EventEmitter is a core module in Node.js that facilitates communication between objects in Node. It allows you to create custom events, emit them, and listen for them using .on() or .once() methods. It implements the observer design pattern.

Interviewer Counter-Question: What happens if an error is emitted by an EventEmitter but there is no listener for the 'error' event?
Answer: The Node.js process will crash and exit. EventEmitter treats the 'error' event as a special case. You should always attach an .on('error', ...) listener to prevent the application from crashing.

Scenario Challenge: You have a ChatRoom class extending EventEmitter. You want to trigger a welcome message only the very first time a user joins, but ignore subsequent joins.
Solution: Use this.once('join', callback) instead of .on(). The .once() method automatically removes the listener after it is triggered the first time.

### Q8. What is the difference between CommonJS and ES Modules?

Core Answer:

CommonJS: The traditional module system in Node.js using require() and module.exports. It is synchronous and loads modules dynamically at runtime.

ES Modules (ESM): The official JavaScript module standard using import and export. It is asynchronous, statically analyzed at parse time (allowing tree-shaking), and is the standard for both browsers and modern Node.js.

Interviewer Counter-Question: Can you use ES Modules in a Node.js project without changing the file extensions to .mjs?
Answer: Yes. You can set "type": "module" in your package.json. This tells Node.js to treat all .js files in the project as ES Modules.

Scenario Challenge: You are writing an ES Module, but you need to read a file relative to the current file's directory. **dirname is throwing a ReferenceError.
Solution: **dirname and \_\_filename are not available in ES Modules. You must reconstruct them using import.meta.url and the url module (fileURLToPath(import.meta.url)).

### Q9. What are Worker Threads and when should you use them?

Core Answer: Worker Threads (worker_threads module) allow Node.js to execute JavaScript in parallel across multiple threads. While Node's core event loop is single-threaded, Worker Threads provide a way to offload heavy CPU-bound tasks without blocking the main event loop.

Interviewer Counter-Question: Do Worker Threads share the same memory space?
Answer: No, by default each Worker Thread has its own isolated V8 engine and memory space. However, they can share memory if you explicitly pass a SharedArrayBuffer between them.

Scenario Challenge: Your Node API resizes large images. Traffic is high, and the image resizing is causing the server to stop responding to health checks.
Solution: The CPU-heavy image resizing is blocking the main thread. Move the image processing logic into a Worker Thread, passing the image buffer to the worker and waiting for it to send the resized buffer back asynchronously.

### Q10. How does Node.js handle concurrency despite being single-threaded?

Core Answer: Node.js achieves concurrency through its Event-Driven, Non-Blocking I/O model. It uses the Event Loop to handle lightweight tasks (like network routing) on the main thread, while offloading expensive I/O operations (file reading, network requests, DB queries) to the OS kernel or the libuv thread pool. When the OS finishes the task, it notifies Node.js, which then executes the callback.

Interviewer Counter-Question: If I run a while(true) loop in a Node.js route, will it block other users from accessing the site?
Answer: Yes. A while(true) loop is synchronous CPU work. It will completely block the main thread, preventing the Event Loop from moving forward, and the entire server will hang for all users.

Scenario Challenge: You have a script making 100 API calls using await fetch(). It takes a long time because they run sequentially. How do you make them concurrent?
Solution: Map the requests to an array of Promises and use Promise.all(). This allows all 100 requests to be dispatched concurrently to the background thread pool, drastically reducing execution time.

### Q11. How do you handle unhandled exceptions in Node.js?

Core Answer: Unhandled exceptions can be caught at the process level by listening to the uncaughtException and unhandledRejection events on the global process object.

JavaScript
process.on('uncaughtException', (err) => {
console.error('Unhandled Exception:', err);
process.exit(1);
});
Interviewer Counter-Question: Is it safe to keep the application running after an uncaughtException?
Answer: No. An uncaught exception means the application is in an unpredictable state with potential memory leaks or corrupted variables. The best practice is to log the error, gracefully shut down the server, and let a process manager (like PM2 or Docker) restart it.

Scenario Challenge: A developer forgot to attach a .catch() block to a rejected Promise, but the app didn't crash. Later, in a newer version of Node.js, the same code causes the app to crash. Why?
Solution: Historically, Node.js only printed a warning for unhandledRejection. Since Node 15+, the default behavior changed to terminate the process with a non-zero exit code if a Promise rejection goes unhandled.

### Q12. Explain the cluster module in Node.js.

Core Answer: The cluster module allows you to create child processes (workers) that run simultaneously and share the same server port. Since a single Node.js instance runs on a single core, clustering allows a Node application to fully utilize multi-core server processors by spawning one worker per CPU core.

Interviewer Counter-Question: How does the master process distribute incoming network traffic to the workers?
Answer: By default, the master process listens on the port and uses a round-robin algorithm to distribute incoming connections among the available worker processes.

Scenario Challenge: You implement clustering, but suddenly user sessions (which you stored in a local variable) keep dropping randomly.
Solution: Workers do not share memory. If User A logs in and their session is saved in Worker 1's memory, their next request might be routed to Worker 2, which doesn't know them. You must use a centralized store like Redis for sessions when using clustering.

### Q13. What is the difference between spawn(), exec(), and fork()?

Core Answer: All three are used in the child_process module:

spawn() launches a new process and streams the data back (good for large data/long-running processes).

exec() runs a command in a shell and buffers the output in memory (good for simple, small-output commands).

fork() is a special variation of spawn() specifically designed to spawn new Node.js processes. It establishes an IPC (Inter-Process Communication) channel, allowing the parent and child to exchange messages.

Interviewer Counter-Question: Why is using exec() with user input dangerous?
Answer: Because exec() runs inside a shell, it is vulnerable to command injection attacks. If user input is not sanitized, they could append malicious shell commands (e.g., user_input; rm -rf /). spawn() does not use a shell by default, making it safer.

Scenario Challenge: You need to run a Python script from your Node server and process 10GB of log data that it outputs. Which do you use?
Solution: Use spawn(). Since the output is 10GB, exec() will crash with a maxBuffer exceeded error because it tries to hold everything in RAM. spawn() streams the output piece by piece.

### Q14. How does require() caching work?

Core Answer: When you require() a module in Node.js, it is compiled and executed only once. The resulting module.exports object is cached in memory. Any subsequent require() calls for the same file in the same process will not execute the file again; they will simply return the cached object.

Interviewer Counter-Question: Can you force a module to re-execute and bypass the cache?
Answer: Yes. You can delete the module's cache entry directly from the require.cache object (delete require.cache[require.resolve('./moduleName')]). The next require() will reload it from disk.

Scenario Challenge: You export a database configuration object. Developer A modifies a property on that object in routeA.js. Developer B notices the property is also changed in routeB.js. Why?
Solution: Because require caches the object reference. Both routes are importing the exact same object in memory. Mutating it in one file mutates it globally. Export a factory function instead if you need unique instances.

### Q15. What is middleware in Express.js?

Core Answer: Middleware functions are functions that have access to the request object (req), the response object (res), and the next function in the application's request-response cycle. They can execute code, modify the request/response objects, end the cycle, or call next() to pass control to the next middleware.

Interviewer Counter-Question: How does Express know a middleware function is specifically an error-handling middleware?
Answer: Error-handling middleware is defined by taking exactly four arguments: (err, req, res, next). Express recognizes the arity (number of arguments) and treats it differently.

Scenario Challenge: Your API receives a JSON payload, but req.body is undefined in your route handler.
Solution: You forgot to include a body-parsing middleware. You must add app.use(express.json()) before your routes so Express knows how to parse incoming JSON payloads into req.body.

### Q16. How do you detect memory leaks in a Node.js application?

Core Answer: Memory leaks occur when objects are no longer needed but are still referenced, preventing the Garbage Collector from freeing the memory. You detect them by taking Heap Snapshots using the Chrome DevTools inspector (node --inspect), or by using profiling tools like Clinic.js or PM2. You compare snapshots over time to see which objects are continuously growing in memory.

Interviewer Counter-Question: What is a common architectural pattern in Node.js that accidentally causes memory leaks?
Answer: Heavy reliance on closures or event listeners. If you add an event listener to a long-lived object (like the global process or a database connection) inside a function that runs frequently, and forget to remove it (removeListener), the listeners stack up endlessly in memory.

Scenario Challenge: A specific route on your server is slowly consuming memory until the server crashes. You realize a global array is being appended to on every request for caching purposes.
Solution: Implement a proper caching mechanism like an LRU (Least Recently Used) cache, or use a dedicated store like Redis. Never use unbounded global arrays for caching.

### Q17. What is the difference between dependencies and devDependencies?

Core Answer:

dependencies are packages required for the application to run in production (e.g., Express, Mongoose, Axios).

devDependencies are packages only needed during local development or building/testing pipelines (e.g., Jest, Nodemon, TypeScript, ESLint).

Interviewer Counter-Question: If you deploy your app and run npm install --production, what happens?
Answer: NPM will only install the packages listed in dependencies and will ignore everything in devDependencies, saving deployment time and server disk space.

Scenario Challenge: You wrote a React application and put Webpack in devDependencies. The build fails on your CI/CD server with "webpack command not found".
Solution: The CI/CD server is likely running npm install --production (or NODE_ENV=production), so Webpack is never installed. You need to ensure the CI/CD pipeline runs a standard npm install before running the build step.

### Q18. What is package-lock.json and why is it important?

Core Answer: package-lock.json is a file automatically generated by NPM that locks down the exact versions of every dependency (and their sub-dependencies) installed in the project. It ensures that environments (your laptop, your coworker's laptop, the production server) all install the exact same dependency tree, preventing "it works on my machine" bugs.

Interviewer Counter-Question: Should package-lock.json be committed to Git?
Answer: Yes, absolutely. Committing it ensures that the rest of the team and the deployment pipeline have access to the exact resolved versions needed to build the project identically.

Scenario Challenge: You run npm install and your package-lock.json file changes dramatically, causing massive merge conflicts. You only wanted to install dependencies, not update them.
Solution: You should use npm ci (clean install) instead of npm install. npm ci strictly reads from the package-lock.json without modifying it, and deletes the node_modules folder to ensure a clean slate.

### Q19. How do you secure a Node.js API?

Core Answer: Standard practices include:

Using HTTPS.

Sanitizing input to prevent SQL/NoSQL injection (e.g., using parameterized queries).

Implementing rate limiting (e.g., express-rate-limit) to prevent DDoS.

Using security headers (e.g., via the helmet package).

Avoiding the use of eval() or executing unsanitized shell commands.

Not exposing stack traces in production error messages.

Interviewer Counter-Question: How does the Helmet middleware actually protect an Express app?
Answer: Helmet is a collection of smaller middleware functions that set secure HTTP response headers, such as Strict-Transport-Security (forcing HTTPS), X-Frame-Options (preventing clickjacking), and removing the X-Powered-By: Express header to hide the technology stack.

Scenario Challenge: A malicious user is sending massive JSON payloads (100MB+) to your API endpoint, causing the server to parse it and run out of memory.
Solution: Limit the body payload size in your parsing middleware. In Express, you configure this by passing a limit: app.use(express.json({ limit: '10kb' })).

### Q20. What is the purpose of the fs module and what is the difference between sync and async methods?

Core Answer: The fs (File System) module allows Node.js to interact with the OS file system (reading, writing, deleting files). It provides both synchronous (e.g., fs.readFileSync) and asynchronous (e.g., fs.readFile) methods. Async methods do not block the Event Loop and take a callback or return a Promise. Sync methods block the entire Node process until the file operation completes.

Interviewer Counter-Question: When is it acceptable to use synchronous methods like readFileSync?
Answer: It is acceptable during the initial startup phase of the application (e.g., reading configuration files or SSL certificates before calling app.listen). It is strictly prohibited in route handlers, as it will block incoming requests.

Scenario Challenge: You want to check if a file exists before reading it. The docs say fs.exists is deprecated. How should you approach this safely?
Solution: Instead of checking existence and then reading (which creates a race condition if the file is deleted between the two checks), you should try to open/read the file directly and catch the ENOENT (Error No Entry) error if it fails.
