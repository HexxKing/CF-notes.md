# HTML: Chapter 7: “Forms” (p.144-175)
- Whenever you want to collect information from visitors you will need a form, which lives inside a ```<form>``` element
- information from a form is sent in name/value pairs
- each form control is given a name, and the text the user types in or the values of the options they select are sent to the server. 
- HTML5 introduces new form elemets which make it easier for visitors to fill in forms

# HTML: Chapter 14: “Lists, Tables & Forms” (pp.330-357)
- in addition to CSS properties, there are several others that are specifically used to control the appearance of lists, tables and forms
- list markers can be given differet appearaces using te list-style-type and list-style image properties
- table cells can have different borders and spacing in different browsers, but there ar eproperties you can use to control them and make them more consistent
- form are easier to use if the form controls are vertically aligned using CSS
- forms benefit from styles that makes them feel more interactive


# JS: Chapter 6: “Events” (pp.243-292)
- Events are the browser's way of indicating when something has happened
  - like when a page has finished loading or a button has been clicked on
- Binding is the process of stating which event you are waiting to happen, and which element you are waiting for that event to happen upon. 
- When an event occurs on an element, it can trigger a JS function. 
  - the function changes the web page in some way and it feels interactive because it is responding to the user
  - ***Event flow*** is the order in which the events fire off. They can flow in two diferent directions:
    - it matters when your code has event handlers on an element ***and** one of its ancestor or descendant elements. 
  - ***Event Bubbling*** is when the events starts at the  most specific node and flows outwards to the least specific one. This is the default for most browers. 
  - ***Event Capturing*** starts at the least specific node and flows inwards to the most specific one
- Use event delegation to monitor for events that happen on all of the children of an element
- the most commonly used events are W3C DOM events, although there are others in HTML5 specification as well as browser-specific events. 
- the ***event object*** tells you where the cursor was positioned when an event was triggered. 
  - the ***screenX*** and ***screenY*** properties indicate the position of the cursor within the entire screen on your monitor measuring from the top left corner of the screen, rather than the browser.
  - the ***pageX*** and ***pageY*** properties indicate the position of the cursor within the entire page. 
  - the ***clientX*** and ***clientY*** properties indicate the position of the cursor within the browser's viewport 