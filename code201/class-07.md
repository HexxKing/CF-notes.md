# [Domain Modeling](https://github.com/codefellows/domain_modeling#domain-modeling)

>***domnain modeling*** is the process of creating a conceptual model in code for a specific problem. 
  - it describes the various entites, their attributes and behaviors, as well as the constraints that govern the problem domain
> ***object-oriented***  = an entity that stores data in properties and encapsulates behaviors in methods

### Tips
1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.
1. Model its attributes with a constructor function that defines and initializes properties.
1. Model its behaviors with small methods that focus on doing one job well.
1. Create instances using the new keyword followed by a call to a constructor function.
1. Store the newly created object in a variable so you can access its properties and methods from outside.
1. Use the this variable within methods so you can access the object's properties and methods from inside.


### Define a constructor and initialize properties
> ***constructor function*** defines the same properties between many objects
  - the constructor function is defined using a ***function expression***. 
  
  > example: the variable EpicFailVideoPotato is declared and then assigned a function with two parameters called epicRatingPotato and hasAnimalsPotato.
  - When the function is called, the data inside these parameters are stored inside the this.epicRating and this.hasAnimals properties respectively. Storing data within properties ensures any newly created object can access that data later.
  - After the constructor function definition, two objects are ***instantiated*** with the ***new*** keyword and their properties are ***initialized*** by calling the EpicFailVideo constructor function. After being instantiated and initialized, these objects are stored inside the parkourFail and corgiFail variables.

- This is object-oriented programming in JavaScript at its most fundamental level.
  - The ***new*** keyword instantiates (i.e. creates) an object.
  - The constructor function initializes properties inside that object using the this variable.
  - The object is stored in a variable for later use.

  ### How to Generate Random Numbers
  > ```.prototype.``` 
  [reference](https://www.w3schools.com/js/js_object_prototypes.asp)
  All JavaScript objects inherit properties and methods from a prototype:
  Date objects inherit from Date.prototype
  Array objects inherit from Array.prototype
  Person objects inherit from Person.prototype
  The Object.prototype is on the top of the prototype inheritance chain:
  Date objects, Array objects, and Person objects inherit from Object.prototype.
  > ```Math.floor(x)``` returns the value of x rounded down to its nearest integer
  > ```Math.random()```
returns a random number between 0 (inclusive), and 1 (exclusive):
> ```Math.round()```  rounded to the nearest integer 

### Calculate Daily Likes
- the number of viewers times(*) the percentage of viewers who'll Like a video or, viewers times (*) percentage.


# HTML Book : Chapter 6: “Tables” (pp.126-145)
- The ```<table>``` element is used to add tables to a web page
- a table is drawn out row by row
  - each row is created with the ```<tr>``` element
- Inside each row there are a number of cells represented by the ```<td>``` element 
  - use ```<th>``` if it's in the header
- You can make cells of a table span more than one row or column using the rowspan and colspan attributes
- for long tables, you can split the table into a ```<thread>```, ```<tbody>```, and ```<tfoot>```

# Chapter 3: “Functions, Methods, and Objects” (pp.106-144)
- an object is a series of variables and functions that represent something from the world around you. 
- In an object, variables are known as properties of the object; functions are known as methods of the object
- web browsers implement objects that represent both the browser window and the document loaded into the browser window
- JS has several built-in objects such as String, Number, Math and Date
  - their properties and methods offer functionality that help you write scripts
- arrays and objects can be used to create complex data sets (and both can contain the other)