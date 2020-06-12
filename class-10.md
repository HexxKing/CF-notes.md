# JavaScript book, Ch. 10, “Error Handling & Debugging” pgs 449-486
- Debugging is the process of finding errors and involves the process of deduction

 ## The Console and Dev Tools
- the console helps narrow own the area in which the error is located, so you can try to find the exact error

### Execution Context
- Every statment in a script lives in one of the three execution contexts
  - ***Global Context*** is code that is in the script, but NOT in a function. There can only be one global context in any page 
  - ***FUnction Context*** is code that is being run within a function. Each function has its own function context. 
  - ***Eval Context*** is text that is executed like code in an internal function called eval()
- ***Variable Scope*** is when the first two execution contexts correcspond with scope
  - Global Scope is when a variable is declared outside a function and can be used anywhere because it has global scope. If you do not use the ***var*** keyword when creating a variable, it is placed in global scope
  - Function-Level Scope is when a variable is declared inside of a function and can only be used within that funciton.

## Common Problems
- JS has 7 different types of errors and each create their own object which can tell you its line number and gives a description of the error

## Handling Errors
- If you know that you may get an error, you can give users helpful feedback gracefully using the try, catch, finally statements
