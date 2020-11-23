# Data Analysis

## [What is Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)
- JupyterLab is a next-generation web-based user interface for Project Jupyter.
- JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner.
- You can find and customize the current list of keyboard shortcuts by selecting the Advanced Settings Editor item in the Settings menu, then selecting Keyboard Shortcuts in the Settings tab.

## [NumPy Tutorial: Data Analysis with Python](https://www.dataquest.io/blog/numpy-tutorial-python/)
- [NumPy Cheatsheet](https://s3.amazonaws.com/dq-blog-files/numpy-cheat-sheet.pdf)
- NumPy is a commonly used Python data analysis package.
  - almost every data analysis or machine learning package for Python leverages NumPy in some way

### Numpy 2-Dimensional Arrays
- With NumPy, we work with multidimensional arrays. 
- A 2-dimensional array is also known as a matrix
  - a list of lists 
- A matrix has rows and columns. By specifying a row number and a column number, we’re able to extract an element from a matrix.
- In a NumPy array, the number of dimensions is called the rank, and each dimension is called an axis.
- We can create a NumPy array using the numpy.array function. 
  - If we pass in a list of lists, it will automatically create a NumPy array with the same number of rows and columns. 
  - Because we want all of the elements in the array to be float elements for easy computation, we’ll leave off the header row, which contains strings. 
- One of the limitations of NumPy is that all the elements in an array have to be of the same type, so if we include the header row, all the elements in the array will be read in as strings.
  - Because we want to be able to do computations like find the average quality of the wines, we need the elements to all be floats.

> Import the numpy package:
> 
> - Pass the list of lists wines into the array function, which converts it into a NumPy array.
> - Exclude the header row with list slicing.
> - Specify the keyword argument ***dtype*** to make sure each element is converted to a float.
> - Check the number of rows and columns in our data using the shape property of NumPy arrays


### Alternative NumPy Array Creation Methods
- you can create an array where every element is zero using `numpy.zeros`
  - It’s useful to create an array with all zero elements in cases when you need an array of fixed size, but don’t have any values for it yet
- You can also create an array where each element is a random number using numpy.random.rand
  - Creating arrays full of random numbers can be useful when you want to quickly test your code with sample arrays.
- It’s possible to use NumPy to directly read csv or other files into arrays using the numpy.genfromtxt function.
  - Specify the keyword argument delimiter=";" so that the fields are parsed properly.
  - Specify the keyword argument skip_header=1 so that the header row is skipped.
- NumPy will automatically pick a data type for the elements in an array based on their format.
- We can use array indexing to select individual elements, groups of elements, or entire rows and columns. 
  - just like Python lists, NumPy is zero-indexed, meaning that the index of the first row is 0, and the index of the first column is 0.
- Since we’re working with a 2-dimensional array in NumPy, we specify 2 indexes to retrieve an element. 
  - The first index is the row, or axis 1, index, and the second index is the column, or axis 2, index. 
  - slices work the same way they do on lists in Python using a **:** 
- We can also use indexing to assign values to certain elements in arrays by assigning directly to the indexed value
  - use a slice to overwrite an entire column 

### 1-Dimensional NumPy Arrays
- One of the most common types of multidimensional arrays is the 1-dimensional array, or vector. 
- A 1-dimensional array only needs a single index to retrieve an element. 
  - Each row and column in a 2-dimensional array is a 1-dimensional array. 
  - Just like a list of lists is analogous to a 2-dimensional array, a single list is analogous to a 1-dimensional array. 
- The shape specifies the number of dimensions, and the size of the array in each dimension. 
  - EX : A shape of (10,10) will be a 2-dimensional array with 10 rows and 10 columns. A shape of (10,) will be a 1-dimensional array with 10 elements.

### N-Dimensional NumPy Arrays
- This doesn’t happen extremely often, but there are cases when you’ll want to deal with arrays that have greater than 3 dimensions. 
- One way to think of this is as a list of lists of lists. 
- A three-dimensional array in NumPy is much the same. We now need three indexes to retrieve a single element. 

### [NumPy Data Types](https://numpy.org/doc/stable/reference/arrays.dtypes.html)
- each NumPy array can store elements of a single data type
- NumPy stores values using its own data types, which are distinct from Python types like float and str
- You can find the data type of a NumPy array by accessing the dtype property
- Data types additionally end with a suffix that indicates how many bits of memory they take up. So int32 is a 32 bit integer data type, and float64 is a 64 bit float data type
> - float — numeric floating point data.
> - int — integer data.
> - string — character data.
> - object — Python objects.
- You can use the **numpy.ndarray.astype** method to convert an array to a different type. The method will actually copy the array, and return a new array with the specified data type.
  - We can check the name property of the dtype of the resulting array to see what data type NumPy mapped the resulting array to
    - If you want more control over how the array is stored in memory, you can directly create NumPy dtype objects like numpy.int32

### NumPy Array Operations
- NumPy makes it simple to perform mathematical operations on arrays.
- Single Array Math
  - If you do any of the basic mathematical operations (/, *, -, +, ^) with an array and a value, it will apply the operation to each of the elements in the array and return a new array with the operation applied to each element
  - If we instead did +=, we’d modify the array in place
- It’s also possible to do mathematical operations between arrays. This will apply the operation to pairs of elements. 
- Unless the arrays that you’re operating on are the exact same size, it’s not possible to do elementwise operations. In cases like this, NumPy performs broadcasting to try to match up elements. 
  - Essentially, [broadcasting](https://numpy.org/doc/stable/user/basics.broadcasting.html) involves a few steps:
    - The last dimension of each array is compared.
    - If the dimension lengths are equal, or one of the dimensions is of length 1, then we keep going.
    - If the dimension lengths aren’t equal, and none of the dimensions have length 1, then there’s an error.
    - Continue checking dimensions until the shortest array is out of dimensions.

### [NumPy Array Methods](https://numpy.org/doc/stable/reference/arrays.ndarray.html)
- **numpy.ndarray.sum** method finds the sum of all the elements in an array by default
- We can pass the axis keyword argument into the sum method to find sums over an axis. 
- We can verify that we did the sum correctly by checking the shape. 
> - numpy.ndarray.mean — finds the mean of an array.
> - numpy.ndarray.std — finds the standard deviation of an array.
> - numpy.ndarray.min — finds the minimum value in an array.
> - numpy.ndarray.max — finds the maximum value in an array.