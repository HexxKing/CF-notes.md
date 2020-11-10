# Testing and Modules

## [In Tests We Trust — TDD with Python](https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932)
- Unit tests are some pieces of code to exercise the input, the output and the behaviour of your code. You can write them anytime you want.
- Test-Driven Development is a strategy to think (and write!) tests first.
  - be ok with the possibility of the beginning to be hard sometimes — and it’s totally fine.
- what is the smaller test that we can do against a function (method/class) that will return what I am looking for?
- what are the parameters? arugments? 
- the test name needs to be descriptive about it and to say what is expected and what we are testing.
  - The test file name should follow the same name of module name. For instance, if our module is gender.py, our test name should be test_gender.py. 
  - It’s ideal to separate the tests folder from production code (the implementation) 
- A convention widely used for structure is the ***AAA: Arrange, Act and Assert***.
  - Arrange: you need to organize the data needed to execute that piece of code (input);
  - Act: here you will execute the code being tested (exercise the behaviour);
  - Assert: after executing the code, you will check if the result (output) is the same as you were expecting
- The Cycle - go through this cycle every time you add or modify a new feature in your code.
  - Write a unit test and make it fail (it needs to fail because the feature isn’t there, right? 
  - Write the feature and make the test pass!
  - Refactor the code — the first version doesn’t need to be the beautiful one
- Implementing the feature should follow the same rules.
  - What is needed to make this test pass? Think about just the test
  - think about software design first
  - when writing tests we are forced to think abut the desig first and how it can be broken into smaller pieces


## [Recursion](https://www.geeksforgeeks.org/recursion/)
- recursion is the process in which a function calls itself directly or indirectly 
  - the corresponding function is called as recursive function
- A recursive function definition has one or more base cases, meaning input(s) for which the function produces a result trivially (without recurring), and one or more recursive cases, meaning input(s) for which the program recurs (calls itself).
  - In the recursive program, the solution to the base case is provided and the solution of the bigger problem is expressed in terms of smaller problems. 
- The idea is to represent a problem in terms of one or more smaller problems, and add one or more base conditions that stop the recursion.
- If the base case is not reached or not defined, then the stack overflow problem may arise.
  -  If the memory is exhausted by these functions on the stack, it will cause a stack overflow error. 
- A function is called direct recursive if it calls the same function. A function is called indirect recursive if it calls another function and that 2nd function calls the first function directly or indirectly.
- A recursive function is tail recursive when recursive call is the last thing executed by the function.
  - The tail recursive functions considered better than non tail recursive functions as tail-recursion can be optimized by compiler. The idea used by compilers to optimize tail-recursive functions is simple, since the recursive call is the last statement, there is nothing left to do in the current function, so saving the current function’s stack frame is of no use 
- When any function is called from main(), the memory is allocated to it on the stack. A recursive function calls itself, the memory for a called function is allocated on top of memory allocated to calling function and different copy of local variables is created for each function call. 
  - When the base case is reached, the function returns its value to the function by whom it is called and memory is de-allocated and the process continues.
- Note that both recursive and iterative programs have the same problem-solving powers, i.e., every recursive program can be written iteratively and vice versa is also true. 
  - The recursive program has greater space requirements than iterative program as all functions will remain in the stack until the base case is reached. 
  - It also has greater time requirements because of function calls and returns overhead.
- Recursion provides a clean and simple way to write code.
  - We can write such codes also iteratively with the help of a stack data structure.  
