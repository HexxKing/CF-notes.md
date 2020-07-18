# Read: 10 - The Call Stack and Debugging

## [The Call Stack defined on MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
- A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.
- When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.
- Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.
- When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.
- If the stack takes up more space than it had assigned to it, it results in a "stack overflow" error.

## [Understanding the JavaScript Call Stack](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)
- At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).
  - LIFO: When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.
- The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.
- An understanding of the call stack will give clarity to how “function hierarchy and execution order” works in the JavaScript engine.
- The call stack is primarily used for function invocation (call). Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. It means the call stack is synchronous.
- In Asynchronous JavaScript, we have a callback function, an event loop, and a task queue. The callback function is acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop.
- Temporarily store: When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a stack frame. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.
- Manage function invocation (call): The call stack maintains a record of the position of each stack frame. It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.
- A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

> In summary
The key takeaways from the call stack are:
1. It is single-threaded. Meaning it can only do one thing at a time.
2. Code execution is synchronous.
3. A function invocation creates a stack frame that occupies a temporary memory.
4. It works as a LIFO — Last In, First Out data structure.

## [JavaScript error messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c?gi=70ebca2441e6)
- Being able to read error messages and practising debugging is one of your biggest weapons has a developer, do it frequently and with enough time you will notice a great decrease in the time you spend on each error that you find along the way. And remember, before a commit/push, remove all the debugging stuff from your code, we don’t want the client or another developer to get stuck on a debugger now do we?

### Reference Errors
- This is as simple as when you try to use a variable that is not yet declared you get this type os errors.
- This is also a common thing when using const and let, they are hoisted like var and function but there is a time between the hoisting and being declared so when you try to access them a reference error occurs, the fact that this happens to let and const is called Temporal Dead Zone (TDZ).
  - Whatever you are using (var, let or const) the fix is as simple has declaring the variable before any declaration is made.
### Syntax Errors
- I know it’s in the name of the errors, but like it says itself, this occurs when you have something that cannot be parsed in terms of syntax.
- Some syntax errors like sending a trailing comma when calling a function are handled without error by most recent browsers, but older ones you have to be careful.

### Range Errors
- Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.
- I prefer not to mutate my variables whenever possible (making them constants and not variables) but this is a method that is available and now you know it.

### Type Errors
- Like the name indicates, this types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.
- There are also warnings, for instance telling you about a deprecated method, which can be found more frequently in firefox developer tools.

## Debugging
- To debug your JS code, the easiest and maybe the most common way its to simply console.log() the variables you want to check or, by using chrome developer tools, open your page with your JS code (press cmd+o in macOS) and choose your file to debug, click the line you wanna debug and refresh your page again.
- If the line you selected was run you will be able to see what has happened before that point and you can try and evaluate the next lines to check if everything is outputting what you are expecting.
- The breakpoint can also be achieved by putting a debugger statement in your code in the line you want to break.
- You can also add conditional breakpoints by right-clicking a previous set breakpoint, which will make your program stop at that point only if a condition is met, this is awesome for when you want to debug huge cycles for specific values.

## Call Stack
- is the path that your program has taken to reach the point were you set a breaking point or were you have an error
- Paired with breakpoints it is easier to create a code execution in scenarios like this by taking into account the call stack which is available, for example, in chrome developer tools “sources” tab.
  - You can add a debugger statement and when running the code above you can see the “history” before reaching that breakpoint
- The call stack it’s better to navigate when you have names to your functions, meaning that if you use anonymous functions you will most probably have an harder time since the call stack will not show the name of the parent function.
- Another way to see the stack trace at any given point in your code is to just write console.trace() were you want to log it.

## Handling Errors
- meaning anything after this error will not be executed.
- To avoid this we usually try to catch the errors so we can gracefully fallback to a default state of our application in case of an error (this fallback can be a 404 page which is normally not that graceful but is better than a page to just stop working).
- An alternative it’s to encapsulate our problematic function code with a try…catch which would make an error be thrown but this time, not “uncaught” so we can send it to a error logging to be checked later and send a fallback to the function so that our code continues without problems
- This will make your error message show up slightly different and instead of a console.error you could have some kind of logging system as pointed before so you can check your client errors and fix them without waiting for a report.
- The worthiest outcome of using try…catch tough is the fact that your application will keep on running, maybe with some side effects due to the fact that the function doesn't just crash onto itself (just make sure the code you have afterwards is bearing in mind the default values of the errors).
- I would recommend using try…catch when the type checks are becoming “longer than your function logic”, when a request is made and you aren’t sure if the response might change or temporarily when a code is continuously giving you problems and you still haven’t got around to refactor it.

## Tools to avoid runtime errors
- JS is not a compiled language like Java so your errors will happen at runtime, that means that you can only see whatever is wrong with your code after your run it.
- [quokka](https://quokkajs.com/) to evaluate your code as you type
- [eslint](https://eslint.org/) to make sure your style guide is consistency and it will grab you an error or two along the way and
- For those of you looking to make JS a more strong typed experience you can check out stuff like [TypeScript](https://www.typescriptlang.org/) (like I said in a previous article, when learning I rather avoid libraries that abstract the core language so I wouldn’t recommend this last one when starting).

## [JavaScript errors reference on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors)
- this is a list of errors which are thrown by JavaScript. 
- These errors can be a helpful debugging aid, but the reported problem isn't always immediately clear. 
- This page will provide additional details about these errors. 
- Each error is an object based upon the Error object, and has a name and a message.
- Errors displayed in the Web console may include a link to the corresponding page below to help you quickly comprehend the problem in your code.

## [Troubleshooting JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_went_wrong)