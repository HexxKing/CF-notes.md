# [Pain and Suffering](https://codefellows.github.io/code-401-python-guide/curriculum/class-01/notes/pain_suffering)
- You're not dying, it's just uncomfortable
- pain is just growth


# [Beginners Guide to Big O](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/)
- Big O Notation is:
  - used to describe the performance or complexity of an algorithm or data structure
  - used to specifically describes the worst-case scenario
  - used to describe the execution time or space required to run
  - will always assume the upper limit where the algorithm will perform the maximum number of iterations
- O(1) - (best case senario)
  - describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.
- O(N) 
  - describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set
- O(N2) 
  - represents an algorithm whose performance is directly proportional to the square of the size of the input data set. 
  - This is common with algorithms that involve nested iterations over the data set. 
  - Deeper nested iterations will result in O(N3), O(N4) etc.
- O(2N) 
  - denotes an algorithm whose growth doubles with each additon to the input data set. 
  - The growth curve of an O(2N) function is exponential - starting off very shallow, then rising meteorically. 

- Logarithms - O(log N)
  - The iterative halving of data sets produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase 
    - ex: an input data set containing 10 items takes one second to complete, a data set containing 100 items takes two seconds, and a data set containing 1000 items will take three seconds.  
  - Doubling the size of the input data set has little effect on its growth as after a single iteration of the algorithm the data set will be halved and therefore on a par with an input data set half the size. 
  - This makes algorithms like binary search extremely efficient when dealing with large data sets.


# [Ned Batchelder - Facts and Myths about Python names and values](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation/)
- Names refer to values
- Many names can refer to one value
- Names are reassigned independently
- Values live until no references
- Assignment never copies data
  -  you can have two names referring to the same value but that does not duplicate the value. There is still only one value.
- Changes are visible through all names

> Mutable Aliasing
 > - a mutable value
 > - more than one name
 > - the value changes
 > - all names see the change

- Immutable values can't alias
  - immutable types: ints, floats, strings, tuples

> "Change" is unclear
  > - Changing an int : rebinding
  > - Changing a list : mutating or rebind

- Mutable and Immutable are assigned the same
  - assignment is the same for all values
  - Aliasing can amke it seem different

- Lots of things are assignments
  - x = ...
  - for x in  ...
  - class x(...):
  - def x(...):
  - def fn(x):
  - import x
  - from ... import x
  - except ... as x:
  - with ... as x: