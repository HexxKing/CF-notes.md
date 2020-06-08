# [Understanding the problem domain is the hardest part of programming](https://simpleprogrammer.com/understanding-the-problem-domain-is-the-hardest-part-of-programming/)
- understanding the problem is the most critical piece. It is very difficult to solve a problem before you know the question. 
- extreme amount of specification that is done before anything is built makes it easier to write the code for a feature
- essnetially, you want to map out the entire problem domain in the form of a spec that is clear and unambiguous.
  - It makes it easy to learn the problem domain and therefore, the code will be easy to write as well.
- to make programming easier, do three things:
  - Make the problem domain easier
  - Get better at understanding the problem domain
  - cut out cases and narrowing your focus to a particular part of the problem.
    - it is often beneficial to take a part of the problem and fully understand that part before expanding the problem domain.
-  It is easy to fall into the trap of thinking you understand enough of the problem to get started coding it. 

# Chapter 3: “Object Literals” (pp.100-105)
- Objects group together a set of variable and functions to create a moel of something you would recognize from the real world.
- Varibles and functions take on new names in an object
  - when a varible is part of an object, its called a ***property***.
    - properties tell us about the object
    - the value of a property can be a string, number, Boolean, array, or another object
  - when a function is part of an object, its called a ***method***
    - Methods reporesent tasks that are associated with the object
    - the value of a method is always a function
- properties and methods have a name and a value
  - in an object, that name is called a ***key***
  - objects consist of a set of name/value pairs, but the names are referred to as ***keys***
- an object CANNOT have two keys with the same name
  - keys are used to access their corresponding values

### Literal Notation
- easiest and most popular way to create objects
  - when setting properties, treat the values like youwold do for variables: strings live in quotes and arrays live in square brackets
- access the properties or methods of an object using dot notation and/or square brackets.
  - ***dot notation:*** to access a property or method of an object, use the name of the object, followed by a period, then the name of the property or method you want to access
  - ***member operator*** is the period. The property or method on its right is a member of the object on its left.
  - you can also use the square brackets syntax. The object name is followed by square brackets, with the property or method inside them
     - use when:
       - the name of the property or method contains special characters (like a dash)
       - the name of the property is a number (technically  allowed but not best practice)
       - a variable is being used in place of the property name 


# Chapter 5: “Document Object Model” (pp.183-242)