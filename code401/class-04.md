# [Classes and Objects](https://www.learnpython.org/en/Classes_and_Objects)
- Objects are an encapsulation of variables and functions into a single entity. 
- Objects get their variables and functions from classes. 
  - Classes are essentially a template to create your objects.
- Classes = cookie cutter / Objects = the cookie
- You can create multiple different objects that are of the same class(have the same variables and functions defined). However, each object contains independent copies of the variables defined in the class. 

# [Thinking Recursively in Python](https://realpython.com/python-thinking-recursively/)
- the typical structure of a recursive algorithm is if the current problem represents a simple case, solve it. If not, divide it into subproblems and apply the same strategy to them.

```
houses = ["Eric's house", "Kenny's house", "Kyle's house", "Stan's house"]

# Each function call represents an elf doing his work 
def deliver_presents_recursively(houses):
    # Worker elf doing his work
    if len(houses) == 1:
        house = houses[0]
        print("Delivering presents to", house)

    # Manager elf doing his work
    else:
        mid = len(houses) // 2
        first_half = houses[:mid]
        second_half = houses[mid:]

        # Divides his work among two elves
        deliver_presents_recursively(first_half)
        deliver_presents_recursively(second_half)
```
- A recursive function is a function defined in terms of itself via self-referential expressions.
  - the function will continue to call itself and repeat its behavior until some condition is met to return a result
- As the large problem is broken down into successively less complex ones, those subproblems must eventually become so simple that they can be solved without further subdivision. This is the base case
- Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case. Then, the stack begins to unwind as each call returns its results
- When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:
  - Thread the state through each recursive call so that the current state is part of the current call’s execution context
  - Keep the state in global scope

```
def sum_recursive(current_number, accumulated_sum):
    # Base case
    # Return the final state
    if current_number == 11:
        return accumulated_sum

    # Recursive case
    # Thread the state through the recursive call
    else:
        return sum_recursive(current_number + 1, accumulated_sum + current_number)

```
- A data structure is recursive if it can be deﬁned in terms of a smaller version of itself. A list, set, tree, dictonary, and others are examples of a recursive data structures.
- The recursive function’s structure can often be modeled after the definition of the recursive data structure it takes as an input. 

```
def list_sum_recursive(input_list):
    # Base case
    if input_list == []:
        return 0

    # Recursive case
    # Decompose the original problem into simpler instances of the same problem
    # by making use of the fact that the input is a recursive data structure
    # and can be deﬁned in terms of a smaller version of itself
    else:
        head = input_list[0]
        smaller_list = input_list[1:]
        return head + list_sum_recursive(smaller_list)
```
- ***lru_cache is a decorator*** that caches the results. Thus, we avoid recomputation by explicitly checking for the value before trying to compute it. 
  - One thing to keep in mind about lru_cache is that since it uses a dictionary to cache results, the positional and keyword arguments (which serve as keys in that dictionary) to the function must be hashable.
- Python doesn’t have support for tail-call elimination. As a result, you can cause a stack overflow if you end up using more stack frames (limit 3000 - i think?) than the default call stack depth
  - a tail call is a subroutine call performed as the final action of a procedure.[1] If the target of a tail is the same subroutine, the subroutine is said to be tail-recursive, which is a special case of direct recursion. Tail recursion (or tail-end recursion) is particularly useful, and often easy to handle in implementations. Tail calls can be implemented without adding a new stack frame to the call stack. 
- Python’s mutable data structures don’t support structural sharing, so treating them like immutable data structures is going to negatively affect your space and GC (garbage collection) efficiency because you are going to end up unnecessarily copying a lot of mutable objects. 

# [Python Testing with pytest: Fixtures and Coverage](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)

### Fixtures
- When you're writing tests, you're rarely going to write just one or two. Rather, you're going to write an entire "test suite", with each test aiming to check a different path through your code. In many cases, this means you'll have a few tests with similar characteristics, something that pytest handles with "parametrized tests".
- You'll want to have some objects available to all of your tests. Those objects might contain data you want to share across tests, or they might involve the network or filesystem. These are often known as "fixtures" in the testing world, and they take a variety of different forms.
- In pytest, you define fixtures using a combination of the pytest.fixture decorator, along with a function definition.
-  in order to avoid the newline character from being placed at the start of the line, you remove it from the string before reversing and then add a '\n' in each returned string. 
- rather than defining global variables in your test file, you can create a fixture that'll provide your test with the appropriate object at the right time.
  - ` @pytest.fixture `
- fixtures are used differently from global variables. 
  - For example, let's say you want to include this fixture in one of your tests. You then can mention it in the test's parameter list. Then, inside the test, you can access the fixture by name. 
- Your fixture might act like data, in that you don't invoke it with parentheses. But it's actually a function under the hood, which means it executes every time you invoke a test using that fixture. This means that the fixture, in contrast with regular-old data, can make calculations and decisions.
- You also can decide how often a fixture is run. For example, as it's written now, this fixture will run once per test that mentions it. That's great in this case, when you want to compare with a list or file-like structure. But what if you want to set up an object and then use it multiple times without creating it again? You can do that by setting the fixture's "scope". For example, if you set the scope of the fixture to be "module", it'll be available throughout your tests but will execute only a single time. You can do this by passing the scope parameter to the @pytest.fixture decorator
  - `@pytest.fixture(scope='module')`
- If your fixture uses "yield" instead of "return", pytest understands that the post-yield code is for tearing down objects and connections. And yes, if your fixture has "module" scope, pytest will wait until all of the functions in the scope have finished executing before tearing it down.

### Coverage
- that there's a package called pytest-cov on PyPI that you can download and install. Once that's done, you can invoke pytest with the --cov option. If you don't say anything more than that, you'll get a coverage report for every part of the Python library that your program used, so I strongly suggest you provide an argument to --cov, specifying which program(s) you want to test. And, you should indicate the directory into which the report should be written.
  - `pytest --cov=mymul .`
- Once you've done this, you'll need to turn the coverage report into something human-readable. Using HTML is suggested, although other output formats are available
  - `coverage html`
  - This creates a directory called htmlcov. Open the index.html file in this directory using your browser, and you'll get a web-based report showing (in red) where your program still lacks coverage.
