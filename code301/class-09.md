# Read: 09 - Refactoring

## [Functional Programming Concepts](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)
- Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data

### Pure Functions
- It returns the same result if given the same arguments (it is also referred as deterministic)
- It does not cause any observable side effects
- It returns the same result if given the same arguments
- Pure functions are stable, consistent, and predictable. Given the same parameters, pure functions will always return the same result. 
  - We don’t need to think of situations when the same parameter has different results — because it will never happen.
- If our function reads external files, it’s not a pure function — the file’s contents can change.
- Any function that relies on a random number generator cannot be pure.
- It does not cause any observable side effects
  - Examples of observable side effects include modifying a global object or a parameter passed by reference.
- Mutability is discouraged in functional programming.
- Pure functions are easier to test.
  -  So we can unit test pure functions with different contexts:

  > Given a parameter A → expect the function to return value B
  > Given a parameter C → expect the function to return value D 

### Immutability
- Unchanging over time or unable to be changed.
- When data is immutable, its state cannot change after it’s created. 
- If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.
- With recursion, we keep our variables immutable. 
- It is also very common to build up the final state of an object.

### Referential Transfparency
- Basically, if a function consistently yields the same result for the same input, it is referentially transparent.
> pure functions + immutable data = referential transparency

### Functions as first-class entities
- The idea of functions as first-class entities is that functions are also treated as values and used as data.
- Functions as first-class entities can:
  - refer to it from constants and variables
  - pass it as a parameter to other functions
  - return it as result from other functions
- The idea is to treat functions as values and pass functions like data. This way we can combine different functions to create new functions with new behavior.
- If we can treat functions as values and pass these as arguments, we can build a function that receives the operator function and use it inside our function.

### Higher-order functions
- When we talk about higher-order functions, we mean a function that either:
  - takes one or more functions as arguments, or
  - returns a function as its result

#### Filter
- Given a collection, we want to filter by an attribute. 
- The filter function expects a true or false value to determine if the element should or should not be included in the result collection. 
- Basically, if the callback expression is true, the filter function will include the element in the result collection. Otherwise, it will not.
- A simple example is when we have a collection of integers and we want only the even numbers.
  - An imperative way to do it with Javascript is to:
    - create an empty array evenNumbers
    - iterate over the numbers array
    - push the even numbers to the evenNumbers array
  - We say exactly what our function needs to do 
    - iterate over the collection, compare the collection current item with x, and push this element to the resultArray if it pass the condition.
  - But we want a more declarative way to solve this problem, and using the filter higher order function as well. 

#### Map
- The idea of map is to transform a collection.
- The map method transforms a collection by applying a function to all of its elements and building a new collection from the returned values.
- The whole idea is to transform a given array into a new array.

#### Reduce
- The idea of reduce is to receive a function and a collection, and return a value created by combining the items.
- Using reduce, we can build a function to handle the amount sum and pass it as an argument to the reduce function.

## [Refactoring Javascript for Readability](https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec)
- these are examples of different ways to refactor code using real world coding senarios