# Read: 01 - SMACSS and Responsive Web Design

### Other Resources
  - [Don’t Overthink It Grids](https://css-tricks.com/dont-overthink-it-grids/)
  - [CSS Floats Explained By Riding An Escalator](https://www.freecodecamp.org/news/css-floats-explained-by-riding-an-escalator-57fa55232333/)
  - [SMACSS Official Documentation](http://smacss.com/)

## [Shay Howe’s intro to RWD](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)
> Responsive web design aka RWD 
> Responsive web design is the practice of building a website suitable to work on every device and every screen size, no matter how large or small, mobile or desktop.

#### Responsive vs Adaptive vs Mobile
- Responsive generally means to react quickly and positively to any change, while adaptive means to be easily modified for a new purpose or situation, such as change. 
- With responsive design websites continually and fluidly change based on different factors, such as viewport width, while adaptive websites are built to a group of preset factors. 
- A combination of the two is ideal. 
- Which term is used specifically doesn’t make a huge difference.
- NOT BEST PRACTICE : Mobile, on the other hand, generally means to build a separate website commonly on a new domain solely for mobile users. While this does occasionally have its place, it normally isn’t a great idea. 
- Currently the most popular technique lies within responsive web design, favoring design that dynamically adapts to different browser and device viewports, changing layout and content along the way. 
- This solution has the benefits of being all three, responsive, adaptive, and mobile.

> Responsive web design is broken down into three main components, including flexible layouts, media queries, and flexible media. 

#### Flexible Layouts
- the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width
- Flexible grids are built using relative length units, most commonly percentages or em units. 
- Flexible layouts do not advocate the use of fixed measurement units, such as pixels or inches.
  - The formula to help identify the proportions of a flexible layout using relative values is based around taking the target width of an element and dividing it by the width of it’s parent element. The result is the relative width of the target element.
  - target ÷ context = result
- For even more control within a flexible layout, you can also leverage the min-width, max-width, min-height, and max-height properties.

> CSS3 introduced some new relative length units, specifically related to the viewport size of the browser or device. These new units include vw, vh, vmin, and vmax.

#### Media Queries
- Media queries were built as an extension to media types commonly found when targeting and including styles. 
- Media queries provide the ability to specify different styles for individual browser and device circumstances, the width of the viewport or device orientation for example.
- There are a couple different ways to use media queries, using the @media rule inside of an existing style sheet, importing a new style sheet using the @import rule, or by linking to a separate style sheet from within the HTML document. 
- Generally speaking it is recommend to use the @media rule inside of an existing style sheet to avoid any additional HTTP requests.
- Each media query may include a media type followed by one or more expressions. Common media types include all, screen, print, tv, and braille. 
- The HTML5 specification includes new media types, even including 3d-glasses. 
- Should a media type not be specified the media query will default the media type to screen.
- The media query expression that follows the media type may include different media features and values, which then allocate to be true or false. 
- When a media feature and value allocate to true, the styles are applied. If the media feature and value allocate to false the styles are ignored.
- There are three different logical operators available for use within media queries, including **and, not,** and **only**.
- Using the **and** logical operator within a media query allows an extra condition to be added, making sure that a browser or devices does both a, b, c, and so forth. 
  - Multiple individual media queries can be comma separated, acting as an unspoken or operator. 
- The **not** logical operator negates the query, specifying any query but the one identified.
- The **only** logical operator is a new operator and is not recognized by user agents using the HTML4 algorithm, thus hiding the styles from devices or browsers that don’t support media queries. 
  - When using the not and only logical operators the media type may be left off. In this case the media type is defaulted to all. 

#### Mobile First
#### Viewport
#### Flexible Media


## [All About Floats](https://css-tricks.com/all-about-floats/)
