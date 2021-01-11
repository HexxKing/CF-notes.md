# Pythonisms

# [Dunder Methods](https://dbader.org/blog/python-dunder-methods)
Enriching Your Python Classes With Dunder (Magic, Special) Methods
- In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores.
- Initialization of new objects
  - `__init__`
- Object representation
  - `__str__` : The “informal” or nicely printable string representation of an object. This is for the enduser.
  - `__repr__` : The “official” string representation of an object. This is how you would make an object of the class. The goal of `__repr__` is to be unambiguous.
- Enable iteration
  - `__len__`
  - `__getitem__`
  - `__reversed__`
- Operator overloading (comparison)
  - `__eq__`
  - `__lt__`
- Operator overloading (addition)
  - `__add__`
- Callable Python Objects
  - `__call__`
- Context manager support (*with* statement)
  - `__enter__`
  - `__exit__`


# [Iterators](https://dbader.org/blog/python-iterators)
- Objects that support the `__iter__` and `__next__` dunder methods automatically work with for-in loops.
- Iterators provide a sequence interface to Python objects that’s memory efficient and considered Pythonic. Behold the beauty of the for-in loop!
- To support iteration an object needs to implement the iterator protocol by providing the `__iter__` and `__next__` dunder methods.
- Class-based iterators are only one way to write iterable objects in Python. Also consider generators and generator expressions.


# [Generators](https://dbader.org/blog/python-generators)
- Generator functions are syntactic sugar for writing objects that support the iterator protocol. Generators abstract away much of the boilerplate code needed when writing class-based iterators.
- The yield statement allows you to temporarily suspend execution of a generator function and to pass back values from it.
- Generators start raising StopIteration exceptions after control flow leaves the generator function by any means other than a yield statement.


# Additional Resources
- [What are Generators - Video](https://realpython.com/lessons/what-are-python-generators/)
- [Decorators](https://realpython.com/primer-on-python-decorators/)