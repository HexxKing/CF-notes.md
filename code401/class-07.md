# [Python Scope & the LEGB Rule: Resolving Names in Your Code](https://realpython.com/python-scope-legb-rule/)
- The Python scope concept is generally presented using a rule known as the LEGB rule.
  - Local, Enclosing, Global, and Built-in scopes
  - This summarizes the Python scope levels and the sequence of steps that Python follows when resolving names in a program.
- There’s an important difference between assignment operations and reference or access operations. When you reference a name, you’re just retrieving its content or value. When you assign a name, you’re either creating that name or modifying it.

### Python Scope vs Namespace
- Python scopes are implemented as dictionaries that map names to objects. 
- These dictionaries are commonly called namespaces. 
- These are the concrete mechanisms that Python uses to store names. 
- They’re stored in a special attribute called .__dict__
- Names at the top level of a module are stored in the module’s namespace.
- you can reference a name from a different module in at least two different ways:
  - Using the dot notation on the module’s name 
    - module.name
  - Using a subscription operation on .__dict__ 
    - module.__dict__['name']

### Using the LEGB Rule for Python Scope
- Local, Enclosing, Global, and Built-in
- ***Local (or function) scope***
  - is the code block or body of any Python function or lambda expression.
  - It’s created at function call, not at function definition, so you’ll have as many different local scopes as function calls. 
    - This is true even if you call the same function multiple times, or recursively. Each call will result in a new local scope being created
- ***Enclosing (or nonlocal) scope***
  -  is a special scope that only exists for nested functions. 
  - If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function. 
  - The names in the enclosing scope are visible from the code of the inner and enclosing functions.
- ***Global (or module) scope***
  -  is the top-most scope in a Python program, script, or module. 
  - This Python scope contains all of the names that you define at the top level of a program or a module. 
  - Names in this Python scope are visible from everywhere in your code.
- ***Built-in scope***
  - is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. 
  - This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python and are automatically loaded by Python when you run a program or script
  - Names in this Python scope are also available from everywhere in your code. 
- when you use nested functions, names are resolved by first checking the local scope or the innermost function’s local scope. Then, Python looks at all enclosing scopes of outer functions from the innermost scope to the outermost scope. If no match is found, then Python looks at the global and built-in scopes.
- You can inspect the names and parameters of a function using .__code__, which is an attribute that holds information on the function’s internal code. 
- To inspect the names within your main global scope, you can use dir(). If you call dir() without arguments, then you’ll get the list of names that live in your current global scope.
- you can’t assign global names inside functions unless you explicitly declare them as global names using a global statement
- Good programming practice recommends using local names rather than global names. Here are some tips:
  - Write self-contained functions that rely on local names rather than global ones.
  - Try to use unique objects names, no matter what scope you’re in.
  - Avoid global name modifications throughout your programs.
  - Avoid cross-module name modifications.
  - Use global names as constants that don’t change during your program’s execution.
- If you call dir(), you can see that __builtins__ is always present in the global Python scope. 
  - If you inspect __builtins__ itself using dir(), then you’ll get the whole list of Python built-in names.
  - This returns 152 names that include exceptions, functions, types, special attributes, and other Python built-in objects.
  - You can override or redefine any built-in name in your global scope. If you do so, then keep in mind that this will affect all your code.
    - ex: If you override or re-assign abs, then the original built-in abs() is affected all over your code. Now, suppose that you need to call the original abs() and you forget that you re-assigned the name. In this case, when you call abs() again, you’d get a TypeError because abs now holds a reference to an integer, which is not callable.

### Modifying the Behavior of a Python Scope
- ***The global Statement***
  - With this statement, you can define a list of names that are going to be treated as global names.
  - The statement consists of the global keyword followed by one or more names separated by commas.