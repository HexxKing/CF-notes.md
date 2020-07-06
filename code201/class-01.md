# HTML Notes
## Introduction (pp.2-11)
> DNS = Domain Name System tells the broswer the IP address of the website. 

> ISP = Internet Service Provider connects you to the web.

> A web server is constantly connected to the internet and is set up especially to send web pages.

### How the Web Works:
1) Your ISP connects you to the internet
1) You type in a domain name or web address into the browser
1) The computer contacts DNS servers for the unique IP address for the requested domain name
1) The browser contacts the host via the IP address
1) The web server then sends the page to the browser

## HTML Chapter 1: “Structure” (pp.12-39)
- HTML code is made up of elements and elements are ususally made up of one or two tags: an opening and closing tag

### Tag CheatSheet
```
<html></html> indicates that anything inside is HTML code

<body></body> indicates that anything inside should be shown in the main browser

<h1></h1> indicates that anything inside is a main heading

<p></p> indicates that anything inside is a paragraph

<h2></h2> indicates that anything inside is a sub-heading
```
Attributes reside inside of the opening tag and tell u more about the element. Attributes are made up of a name and a value, seperated by an =

Most attributes can only be used on certain elements, but a few can appear on any element.

Most attributes are pre-defined or follow a special format.

## HTML Chapter 8: “Extra Markup” (p.176-199)

### DOCTYPES tell browsers which version of HTML is being used. HTML5 is the most recent version.

### ``` <!-- and --> ``` allow you to add comments to your code that is not visible in the browser. 
- comments make the code easier to understand when you or someone else has to come back to it later on
- comments can be viewed by anyone by looking at the page's source code
- comments are used on a long page of code to indicate where sections of the page start and end
- canbe used around blocks of code to stop that code from running in the browser

### The id attribute allows you to uniquely identy that elements from other elements on the page. 
- no two elements on a page should be assigned the same id.
- id attributes are used in CSS and JS
- the id attribute is a global attribute bc it can beused on any element.
### The class attribute allows you to identify several elements  as being different from the other elements on the page.
- the class's value should describe the class
- to list several classes, simply seperate the names with a space
- will only change the appearance of the element if CSS is applied 

### Block elements will alwqys appear to star on a new line 
- ex: 
```<h1>```
```<p>```
```<ul>``` 
```<li>```

### Inline Elements will appear to continue on the same line as their neighboring elements
- ex: 
```<a> ```
```<b>```
```<em>```
```<img>```

### The ```<div>``` element allows you to group related elements together in one block-level box.
- ```<div>``` element will start on a new line
- using a class or id on this element means that you can style the ```<div>``` together on the screen, with all the elements contained within it
- ```<div>``` elements also make it easier to follow your code to hold each section of the page.
- comment on your ```<div>``` elements to keep track of the dfferent parts of your page

### The ```<span>``` element is the inline equivalent of the ```<div>```.
- it can contain a secton of text where there is no other suitable element to differentiate it from its surrounding text.
- contain a number of inline elements
- mostly used so we can control the appearance of the content using CSS
- class and id are commonly used with ```<span>``` to explain the purpose of the element

### The ```<iframe>``` tag cuts windows into your web pages through which other pages can be displayed, like a map. 
- aka "inline frame"
- the content of the ```<iframe>``` can be any html page, located either on the same server or on the internet
- Attributes :
    - ***src*** is the URL of the page in the frame
    - ***height*** is the height of the frame in pixels
    - ***width*** is the width of the frame in pixels
    - ***scrolling*** attribute for ```<iframe>``` will not be supported in HTML5? Can we use this? What else can we use?
        - three possible values :
            - yes to show scroll bars
            - no to hide scroll bars
            - auto to show only if needed
    - ***frameborder*** same deal as the scroll bars. 
        - indicates whether the frame should have a border or not
            - a 0 value is no border
            - a 1 value is a border
    - ***seamless*** a new attribute with HTML5 where scroll bars are not needed.

### The ```<meta>``` tag allows you to supply all kinds of information about the web page.
- lives inside the ```<head>``` element 
- tells search engines about the page, who created it, if it's time senstive and set it to expire
- it does not have a closing tag and uses attributes to carry information
- name and content attributes are commonly used together to specify properties. 
    - the value of the ***name attribute*** is the property that is being set 
    - the value of the ***content attribute*** is the value that is given to this property
    - the value of the name attribute can be anything you want. 

### Escape characters are used to include special characters that would normally be used to write code, in your pages
- You can also use these to create symbols such as copyright, trademark, currency symbols, math characters, and some punctuation marks.
- When using these, its important to check your live page because not all fonts support these characters and therefore you might need to specifiy a differnt font rule in CSS

## HTML Chapter 17: “HTML5 Layout” (pp.428-451)

### The new HTML5 elements indicate the purpose of different parts of a web page and help to describe its structure. 

### The new elements provide clearer code (compaured with using multiple ```<div>``` elements).

### Older browsers that do not understand HTML5 elements need to be told which elements are block-level elements. 

### To make HTML5 elements work in IE8 (and older versions of IE), extra JavaScript is needed, which is avaible free from Google

## HTML Chapter 18: “Process & Design” (pp.452-475)

### Know your target audience and their reason for wanting to come to your site, what info they are looking for, and when they are likly to return. 

### Site maps allow yout o plan the structure of a site.

### Wireframes allow you to organize the information that will need to go on each page. 

### Good design is communicaiton. Visual hierarchy helps visitors understand what you are trying to tell them

### You can differentiate between pieces of information using size, color, and style

### You can use grouping and similarity to help simplify the information you present.

# JavaScript Notes

## JS Chapter 1: “The ABC of Programming” (pp.11-52)

### A script is a series of instructions that the computer can follow in order to achieve a goal. 

### Everytime the script runs, it might only use a subset of all the instructions. 

### Computers approach tasks in a different way than humans, so your instructions must let the computer solve the task programmatically

### To approach writing a script, break dow your goal into a series of tasks and then work out each step needed to complete that task 
    - use a flow chart for visual aid

### Computers create models of the world using data.

### The models use objects to represent physical things. Objects can have: properties that tell us about the object; methods that perform tasks using the properties of that object; events which are triggered when a user interacts with the computer. 

### Programmers can write code to say "When this event occurs, run that code"

### Web browsers use HTML markup to create a model of the web page. Each element creates its own node (which is a kind of object). 

### To make web pages interactive, you write code that uses the browser's model of the web page. 

### It is best to keep JavaScript code in its own JavaScript file. JS files are text files (like HTML pages and CSS style sheets), but they have the .js extension. 

### The HTML ```<script>``` element is used in HTML pages to tell the browser to load the JS files (rather like the ```<link>``` element can be used to load a CSS file).

### If you view the sourace code of the page inthe browser, the JS will not have changed the HTML, because the script works with the model of the web page that the browser has created. 