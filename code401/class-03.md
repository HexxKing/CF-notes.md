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

# [Reading and Writing Files in Python Guide](https://realpython.com/read-write-files-python/)
- One of the most common tasks that you can do with Python is reading and writing files. Whether it’s writing to a simple text file, reading a complicated server log, or even analyzing raw byte data, all of these situations require reading or writing a file.
- At its core, a file is a contiguous set of bytes used to store data. This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable. In the end, these byte files are then translated into binary 1 and 0 for easier processing by the computer.
- Files on most modern file systems are composed of three main parts:
  - Header: metadata about the contents of the file (file name, size, type, and so on)
  - Data: contents of the file as written by the creator or editor
  - End of file (EOF): special character that indicates the end of the file
- What this data represents depends on the format specification used, which is typically represented by an extension. 
  - For example, a file that has an extension of .gif most likely conforms to the Graphics Interchange Format specification.
- There are hundreds, if not thousands, of file extensions out there. 
### File Paths
- When you access a file on an operating system, a file path is required. The file path is a string that represents the location of a file. It’s broken up into three major parts:
  - Folder Path: the file folder location on the file system where subsequent folders are separated by a forward slash / (Unix) or backslash \ (Windows)
  - File Name: the actual name of the file
  - Extension: the end of the file path pre-pended with a period (.) used to indicate the file type
  - The double-dot (..) can be chained together to traverse multiple directories above the current directory.
### Line Endings
- One problem often encountered when working with file data is the representation of a new line or line ending. 
- line endings should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n)
  - Windows uses the CR+LF characters to indicate a new line, while Unix and the newer Mac versions use just the LF character. This can cause some complications when you’re processing files on an operating system that is different than the file’s source.  
  - This can make iterating over each line problematic, and you may need to account for situations like this.
### Character Encodings
- Another common problem that you may face is the encoding of the byte data. 
- An encoding is a translation from byte data to human readable characters. 
  - This is typically done by assigning a numerical value to represent a character. The two most common encodings are the ASCII and UNICODE Formats. ASCII can only store 128 characters, while Unicode can contain up to 1,114,112 characters.
  - ASCII is actually a subset of Unicode (UTF-8), meaning that ASCII and Unicode share the same numerical to character values. 
- It’s important to note that parsing a file with the incorrect character encoding can lead to failures or misrepresentation of the character. 
  - For example, if a file was created using the UTF-8 encoding, and you try to parse it using the ASCII encoding, if there is a character that is outside of those 128 values, then an error will be thrown.
### Opening and Closing a File in Python
- When you want to work with a file, the first thing to do is to open it. 
  - This is done by invoking the open() built-in function. 
  - open() has a single required argument that is the path to the file. 
  - open() has a single return, the file object.
- ***You should always make sure that an open file is properly closed.***
  - It’s important to remember that it’s your responsibility to close the file. 
  - In most cases, upon termination of an application or script, a file will be closed eventually. 
    - However, there is no guarantee when exactly that will happen. This can lead to unwanted behavior including resource leaks. 
    - It’s also a best practice within Python (Pythonic) to make sure that your code behaves in a way that is well defined and reduces any unwanted behavior
  - When you’re manipulating a file, there are two ways that you can use to ensure that a file is closed properly, even when encountering an error. 
    - use the try-finally block
    - or use the with statement
      - The with statement automatically takes care of closing the file once it leaves the with block, even in cases of error. 
      - this method is recommended because it allows for cleaner code and makes handling any unexpected errors easier
- the second positional argument is a string that contains multiple characters to represent how you want to open the file. 
  - The default and most common is 'r', which represents opening the file in read-only mode as a text file
    - "r" means open for reading
    - "w" means open for writing or overwriting the file first
    - "rb" or "wb" mean open in binary mode 
      - read/write using byte datd
- There are three different categories of file objects and they are defined in the io module. 
  - Text files (.txt) is the most common
    - open() will return a TextIOWrapper file object
  - Buffered binary files are used for reading and writing binary files.
    - open() will return either a BufferedReader or BufferedWriter file object
  - Raw binary files are not typically used because it is generally used as a low-level building-block for binary and text streams
    - open() will return a FileIO file object:
### Reading and Writing Opened Files
- There are multiple methods that can be called on a file object
  - .read(size=-1) : This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.
  - .readline(size=-1) : This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.
  - .readlines() : This reads the remaining lines from the file object and returns them as a list.
    - can also be done by using list() to create a list out of the file object
- file objects have multiple methods that are useful for writing to a file
  - .write(string) : This writes the string to the file.
  - .writelines(seq) : This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).
### Iterating Over Each Line in the File
- .readlines() returns a list where each element in the list represents a line in the file
- using ***for line in reader:*** is more Pythonic and can be quicker and more memory efficient.
- Some examples contain print('some text', end=''). 
  - The end='' is to prevent Python from adding an additional newline to the text that is being printed and only print what is being read from the file.
### Working With Bytes
- Sometimes, you may need to work with files using byte strings. 
- This is done by adding the 'b' character to the mode argument. 
- All of the same methods for the file object apply. 
  - However, each of the methods expect and return a bytes object instead
### Tips and Tricks
- 



__file__
Appending to a File
Working With Two Files at the Same Time
Creating Your Own Context Manager
Don’t Re-Invent the Snake
You’re a File Wizard Harry!