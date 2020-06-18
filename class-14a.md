# [CSS Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)
- general layout techniques can be revisited with alternative ways to size, position, and change elements. 
- All of these new techniques are made possible by the transform property.
- The transform property comes in two different settings, two-dimensional and three-dimensional.
  - Each of these come with their own individual properties and values.

# [CSS Transitions & Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/)
- With CSS3 transitions you have the potential to alter the appearance and behavior of an element whenever a state change occurs, such as when it is hovered over, focused on, active, or targeted.
- Animations within CSS3 allow the appearance and behavior of an element to be altered in multiple keyframes. 
- Transitions provide a change from one state to another, while animations can set multiple points of transition upon different keyframes.
- for a transition to take place, an element must have a change in state, and different styles must be identified for each state. 
  - The easiest way for determining styles for different states is by using the :hover, :focus, :active, and :target pseudo-classes.
- There are four transition related properties in total:
  - transition-property
  - transition-duration
  - transition-timing-function
  - transition-delay
- Not all of these are required to build a transition with, but the first three are the most popular.

# [8 simple CSS3 transitions that will wow your users](https://www.webdesignerdepot.com/2014/05/8-simple-css3-transitions-that-will-wow-your-users/)
### Fade In 
- Having things fade in is a fairly common request. 
- It’s a great way to emphasize functionality or draw attention to a call to action.
- Fade in effects are coded in two steps
  - first, you set the initial state
  - next, you set the change
### Change Color
- set the div’s class to “color” and specify the color we want in our CSS
### Grow & Shrink
- To grow an element, use CSS3’s transform to enlarge.
### Rotate Elements
- 
### Square to Circle
- we just transition the border-radius property
### 3D Shadow
- This effect is achieved by adding a box shadow, and then moving the element on the x axis using the transform and translate properties so that it appears to grow out of the screen.
### Swing
- Not all elements use the transition property. We can also create highly complex animations using @keyframes, animation and animation-iteration.
- This animation simply moves the element left and right
### Inset Border
- One of the hottest button styles right now is the ghost button; a button with no background and a heavy border. 
- We can of course add a border to an element simply, but that will change the element’s position. 
- We could fix that problem using box sizing, but a far simpler solution is the transition in a border using an inset box shadow.

### [6 Buttons animated Activity](https://codepen.io/retyui/pen/ByoaXV?__cf_chl_jschl_tk__=b8d3668bef9486c4dd4659c84adf400163633dad-1592493085-0-ASyWWl7cSaYrVkAAB1DPepF3RvEfnvOnhy73BRavTpxpzZRnIS0KzdD8V0uv7hXvaCaSMb9WVl8jfiN4rWaEk4OvgdSq5nO6eqvKNOSxdLG22wL3xlG4FrvG6MUgBdF9hA-rfj2FupP18HgGbfK7GYIBhItET4y5eBzw2WdQJzbHNOZOt7QWN3hK1lCQVI2PJHE4cLy3Uii1iLCSqeZq-yTDgEAn6qa65LXpAx8kKFqLkSFN_ork5hTxSFueODQBSeYY4Zn_oee_sxeBPnV921RrujyF4COgB6iZbEWN7-7D3aTxuDhC1DNjQcGs7heayHsKWFjVGIEbVJ9MuQG3TN9Ni-N2TsexV_KwMhiNw1W2)

### [CSS3 Animations: Keyframes Activity](https://codepen.io/akshaychauhan/pen/oAfae)

### [404 Activity](https://codepen.io/kieranfivestars/pen/MYdQxX)

### [Pure CSS Bounce Animation](https://codepen.io/dp_lewis/pen/gCfBv)