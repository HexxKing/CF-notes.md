# Favorite CSS Resources
- [CSS Tricks](https://css-tricks.com/)
- [Adobe Color Wheel](https://color.adobe.com/create/color-wheel)
- [Useful CSS Links](https://html-css-js.com/css/links/)
- [CSS Zen Garden](http://www.csszengarden.com/)

# HTML/CSS book, Ch. 15, “Layout” 

## Building Blocks
> ***Block-level elements*** start on a new line
> ***Inline elements*** flow in between surrounding text
- to sepratet boxes, you can use borders, margins, padding, and background colors 

## Containing Elements
- ***containing element*** or ***parent element*** is the direct parent of a box nested inside of it.
  - its common to group a number of elements together inside a block-level element.

## Controlling the Position of Elements
- ### Positioning Schemes allow you to control the layout of a page, normal flow, relatie positioning, and absolute positioning
  - #### Normal Flow 
    - Every block-level element appears on a new line, causing each item to appear lower down the page than the previous one. 
    - Even if you specify the width of the boxes, and there is spcae for two elements to sit side-by-side, they will not appear next to each other. 
      - This is the default behavior
  - #### Relative Positioning
    - This moves an element from the position it would be in normal flow, shifting it to the top, right, botton, or left of where it would have been placed
    - This does not affect the position of surrounding elements; they stay in the position they would be in in normal flow.
  - #### Absolute Positioning
    - This positions the element in relation to its containing element. 
    - It is taken out of normal flow, meaning tht it does not affect the position of any surrounding elememts, (they ignore the space it would have taken up)
    - Absolutely positioned elements move as users scroll up and down the page
- ### Box offset will indicate where a box should be positioned and to tell the browser how far from the top or bottom and left or right it should be placed.
  - #### Fixed Positioning
    - this is a form of absolute positioning that positions the element in relation to the browser window, as opposed to the containing element
    - they do not affect the position of surrounding elements and they do not move when the user scrolls up or down the page
  - #### Floating Elememts
    - floating an element allows you to take that element out of normal flow and position it to the far left or right of a containing box
    - the floated element becomes a block-level element around which other content can flow
  - #### WHen you move any element from normal flow, boxes can overlap. The z-index property allows you to control which box appears on top.

