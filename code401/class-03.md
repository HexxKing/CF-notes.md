# [Python Exceptions: An Introduction](https://realpython.com/python-exceptions/)
- A Python program terminates as soon as it encounters an error. In Python, an error can be a syntax error or an exception.
- ***Syntax errors*** occur when the parser detects an incorrect statement.
  - The lil red up arrow (^) indicates where the parser ran into the syntax error.  
- An ***exception error*** occurs whenever syntactically correct Python code results in an error. 
  - The last line of the message indicated what type of exception error you ran into.
  - Python details what type of exception error was encountered.
  - Python comes with various built-in exceptions as well as the possibility to create self-defined exceptions.
### Raising an Exception
- We can use raise to throw an exception if a condition occurs. The statement can be complemented with a custom exception.
- The program comes to a halt and displays our exception to screen, offering clues about what went wrong.
- raise allows you to throw an exception at any time.
- ***The AssertionError Exception***
  - We assert that a certain condition is met. If this condition turns out to be True, then that is excellent! The program can continue. 
  - If the condition turns out to be False, you can have the program throw an AssertionError exception.
  - assert enables you to verify if a certain condition is met and throw an exception if it isn’t.
### The Try and Except Block
- The try and except block in Python is used to catch and handle exceptions. 
- Python executes code following the try statement as a “normal” part of the program. 
- The code that follows the except statement is the program’s response to any exceptions in the preceding try clause.
- The except clause determines how your program responds to exceptions.
- In order to see exactly what went wrong, you need to catch the error that the function threw.
- You can have more than one function call in your try clause and anticipate catching various exceptions. A thing to note here is that the code in the try clause will stop as soon as an exception is encountered.
- Catching Exception hides all errors…even those which are completely unexpected. 
  - This is why you should avoid bare except clauses in your Python programs. 
  - Instead, you’ll want to refer to specific exception classes you want to catch and handle. 
- In the try clause, all statements are executed until an exception is encountered.
- except is used to catch and handle the exception(s) that are encountered in the try clause.
### The Else Clause
- using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.
- You can also try to run code inside the else clause and catch possible exceptions there as well
- else lets you code sections that should run only when no exceptions are encountered in the try clause.
### Finally
- The finally clause implements some sort of action to clean up after executing your code.
- Everything in the finally clause will be executed. 
  - It does not matter if you encounter an exception somewhere in the try or else clauses. 
- finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.
