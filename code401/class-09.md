# [Python Classes With Dunder (Magic, Special) Methods](https://dbader.org/blog/python-dunder-methods)
- treat these methods liek a normal language feature
- Dunder methods let you emulate the behavior of built-in types
### Object Initialization: __init__
- To construct objects from a class I need a constructor which in Python is the __init__ dunder
- it sets up the object (creates it?)
### Object Representation: __str__, __repr__
- __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.
- __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.
### Iteration: __len__, __getitem__, __reversed__
- To iterate over transactions in reversed order you can implement the __reversed__ special method
### Callable Python Objects: __call__
- You can make an object callable like a regular function by adding the __call__ dunder method. 

# [Basic Statistics in Python — Probability](https://www.dataquest.io/blog/basic-statistics-in-python-probability/)
- To calculate the chance of an event happening, we also need to consider all the other events that can occur.
- We call a set of tests a *trial*.
- given enough data, statistics enables us to calculate probabilities using real-world observations. 
- Probability provides the theory, while statistics provides the tools to test that theory using data. 
- The descriptive statistics, specifically mean and standard deviation, become the proxies for the theoretical.
- The normal distribution refers to a particularly important phenomenon in the realm of probability and statistics. 
  - The most important qualities to notice about the normal distribution is its symmetry and its bell shape.
  - In probability, the normal distribution is a particular distribution of the probability across all of the events. 
  - The x-axis takes on the values of events we want to know the probability of. 
  - The y-axis is the probability associated with each event, from 0 to 1.  
  