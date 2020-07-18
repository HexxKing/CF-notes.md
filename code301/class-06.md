Jul 13 at 7:44am
Read: 06 - Node, Express, and APIs (Links to an external site.)
 (Links to an external site.)What Is Node.js?
Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.
Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.
 (Links to an external site.)Node Is Built on Google Chrome’s V8 JavaScript Engine
The V8 engine is the open-source JavaScript engine that runs in Google Chrome and other Chromium-based web browsers
It was designed with performance in mind and is responsible for compiling JavaScript directly to native machine code that your computer can execute.
V8 is Google’s open source high-performance JavaScript and WebAssembly engine, written in C++. It is used in Chrome and in Node.js, among others. It implements ECMAScript and WebAssembly, and runs on Windows 7 or later, macOS 10.12+, and Linux systems that use x64, IA-32, ARM, or MIPS processors. V8 can run standalone, or can be embedded into any C++ application.
Node programs are NOT executed in a browser.
The creator of Node (Ryan Dahl) took the V8 engine and enhanced it with various features, such as a file system API, an HTTP library, and a number of operating system–related utility methods.
This means that Node.js is a program we can use to execute JavaScript on our computers. In other words, it’s a JavaScript runtime.
 (Links to an external site.)Node.js Has Excellent Support for Modern JavaScript
Compatibility Table (Links to an external site.)
You can write your JavaScript using the latest and most modern syntax.
You don’t generally have to worry about compatibility issues — as you would if you were writing JavaScript that would run in different browsers.
 (Links to an external site.)Introducing npm, the JavaScript Package Manager
Node comes bundled with a package manager called npm.
npm is the world’s largest software registry
To check which version you have installed on your system, type $ npm -v
There are over 1,000,000 packages of JavaScript code available to download, with billions of downloads per week.
use npm to install a package
 (Links to an external site.)Working with the package.json File
the node_modules folder is where npm saves libraries.
A Beginner’s Guide to npm — the Node Package Manager (Links to an external site.)
 (Links to an external site.)What Is Node.js Used For?
installing (via npm) and running (via Node) various build tools designed to automate the process of developing a modern JavaScript application.
They can be used for anything from bundling your JavaScript files and dependencies into static assets, to running tests, or automatic code linting and style checking.
if you want to start developing apps with any modern JavaScript framework (like React or Angular), you’ll be expected to have a working knowledge of Node and npm
it’s because these frameworks (and many, many related packages) are all available via npm and rely on Node to create a sensible development environment in which they can run.
 (Links to an external site.)Node.js Lets Us Run JavaScript on the Server
when you connect to a traditional server, such as Apache, it will spawn a new thread to handle the request.
operations (like interacting with a database) block the execution of your code until the operation has completed.
the server has to wait for the database lookup to complete before it can move on to processing the result.
If new requests come in while this is happening, the server will spawn new threads to deal with them
This is inefficient, as a large number of threads can cause a system to become sluggish and/or crash.
The most common way to support more connections is to add more servers.
 (Links to an external site.)Node.js is single-threaded
It’s also event-driven, which means that everything that happens in Node is in reaction to an event.
Node’s execution model causes the server very little overhead, and consequently it’s capable of handling a large number of simultaneous connections.
For example, when a new request comes in (one kind of event) the server will start processing it. If it then encounters a blocking I/O operation, instead of waiting for this to complete, it will register a callback before continuing to process the next event. When the I/O operation has finished (another kind of event), the server will execute the callback and continue working on the original request. Under the hood, Node uses the libuv library to implement this asynchronous (that is, non-blocking) behavior.

nodes-execution-model

 (Links to an external site.)Are There Any Downsides?
The fact that Node runs in a single thread does impose some limitations.
blocking I/O calls should be avoided
CPU-intensive operations should be handed off to a worker thread
errors should always be handled correctly for fear of crashing the entire process
Some developers also dislike the callback-based style of coding that JavaScript imposes.
But with the arrival of native Promises, followed closely by async await, flow control in modern JavaScript has become easier than it ever was.
 (Links to an external site.)What Kind of Apps Is Node.js Suited To?
Node is particularly suited to building applications that require some form of real-time interaction or collaboration — for example, chat sites
It’s also a good fit for building APIs where you’re handling lots of requests that are I/O driven (such as those needing to perform operations on a database), or for sites involving data streaming, as Node makes it possible to process files while they’re still being uploaded.
 (Links to an external site.)What Are the Advantages of Node.js?
Aside from speed and scalability, an often-touted advantage of using JavaScript on a web server, as well as in the browser, is that your brain no longer needs to switch modes.
You can do everything in the same language
Another of Node’s big pluses is that it speaks JSON. JSON is probably the most important data exchange format on the Web, and the lingua franca for interacting with object databases (such as MongoDB).
JSON is ideally suited for consumption by a JavaScript program, meaning that when you’re working with Node, data can flow neatly between layers without the need for reformatting.
You can have one syntax from browser to server to database.
JavaScript is ubiquitous: most of us are familiar with JavaScript, or have used it at some point.
This means that transitioning to Node development is potentially easier than to other server-side languages
 (Links to an external site.)Other Uses of Node
it can be used as a scripting language to automate repetitive or error prone tasks on your PC
write your own command line tool to scaffold out new projects.
to build cross-platform desktop apps and even to create your own robots