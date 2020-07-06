# [EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)
- Chart.js, a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page. It’s a well documented plugin that makes using all kinds of bar charts, line charts, pie charts and more, incredibly easy.
- The first thing we need to do is download Chart.js. Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in. Then create a new html page and import the script.

### Drawing a Line Chart
- ```<canvas>```  : To draw a line chart, the first thing we need to do is create a canvas element in our HTML in which Chart.js can draw our chart
- Next, we need to write a script that will retrieve the context of the canvas, so add this to the foot of your body element

### Drawing a Pie Chart
- The data is a little different than the line chart because the pie chart is simpler, we just need to supply a value and a color for each section

### Drawing a Bar Chart
- the syntax for the bar chart is very similar to the line chart

# [Chart.js Install and Creating a Chart](https://www.chartjs.org/docs/latest/)
- You can download the latest version of Chart.js from the GitHub releases or use a Chart.js CDN. 
- Detailed installation instructions can be found on the installation page.
- It's easy to get started with Chart.js. All that's required is the script included in your page along with a single <canvas> node to render the chart.

# [Basic Usage of Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage)

### The ```<canvas>``` Element
- the ```<canvas>``` element has only two attributes, width and height. These are both optional and can also be set using DOM properties. 
- When no width and height attributes are specified, the canvas will initially be 300 pixels wide and 150 pixels high. 
- The element can be sized arbitrarily by CSS, but during rendering the image is scaled to fit its layout size: if the CSS sizing doesn't respect the ratio of the initial canvas, it will appear distorted.
- If your renderings seem distorted, try specifying your width and height attributes explicitly in the ```<canvas>``` attributes, and not using CSS.
- The id attribute isn't specific to the ```<canvas>``` element but is one of the global HTML attributes which can be applied to any HTML element (like class for instance). 
  - It is always a good idea to supply an id because this makes it much easier to identify it in a script.
- The ```<canvas>``` element can be styled just like any normal image (margin, border, background…). 
  - These rules, however, don't affect the actual drawing on the canvas. 
  - When no styling rules are applied to the canvas it will initially be fully transparent.
- Providing fallback content is very straightforward: just insert the alternate content inside the ```<canvas>``` element. 
  - Browsers that don't support ```<canvas>``` will ignore the container and render the fallback content inside it. 
  - Browsers that do support ```<canvas>``` will ignore the content inside the container, and just render the canvas normally.
  - If fallback content is not needed, a simple ```<canvas id="foo" ...></canvas>``` is fully compatible with all browsers that support canvas at all.

### The Rendering Context
- The ```<canvas>``` element creates a fixed-size drawing surface that exposes one or more rendering contexts, which are used to create and manipulate the content shown.
- The canvas is initially blank. To display something, a script first needs to access the rendering context and draw on it. 
- The ```<canvas>``` element has a method called getContext(), used to obtain the rendering context and its drawing functions. getContext() takes one parameter, the type of context. 
  - For 2D graphics you specify "2d" to get a CanvasRenderingContext2D.
- The first line in the script retrieves the node in the DOM representing the ```<canvas>``` element by calling the document.getElementById() method. 
  - Once you have the element node, you can access the drawing context using its getContext() method.

# [Drawing Shapes with Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes)
- Working with paths is essential when drawing objects onto the canvas and we will see how that can be done.
- ```<canvas>``` only supports two primitive shapes: rectangles and paths or lists of points connected by lines

### The Grid or Coordinate Space
- Normally 1 unit in the grid corresponds to 1 pixel on the canvas. 
- All elements are placed relative to the origin.

### Drawing Rectangles
- There are three functions that draw rectangles on the canvas:
  - ***fillRect(x, y, width, height)***
    - Draws a filled rectangle.
  - ***strokeRect(x, y, width, height)***
    - Draws a rectangular outline.
  - ***clearRect(x, y, width, height)***
    - Clears the specified rectangular area, making it fully transparent.
- Each of these three functions takes the same parameters. 
- ***x*** and ***y*** specify the position on the canvas (relative to the origin) of the top-left corner of the rectangle. 
- ***width*** and ***height*** provide the rectangle's size.
- all three rectangle functions draw immediately to the canvas.

### Drawing Paths
- A path is a list of points, connected by segments of lines that can be of different shapes, curved or not, of different width and of different color. 
  - A path, or even a subpath, can be closed.
- First, you create the path.
  - call the beginPath()
  - Internally, paths are stored as a list of sub-paths (lines, arcs, etc) which together form a shape. Every time this method is called, the list is reset and we can start drawing new shapes.
- Then you use drawing commands to draw into the path.
- Once the path has been created, you can stroke or fill the path to render it.
  - call closePath()
  - This method tries to close the shape by drawing a straight line from the current point to the start. 
  - If the shape has already been closed or there's only one point in the list, this function does nothing.
- When the current path is empty, such as immediately after calling beginPath(), or on a newly created canvas, the first path construction command is always treated as a moveTo(), regardless of what it actually is. 
  - For that reason, you will almost always want to specifically set your starting position after resetting a path.
- When you call fill(), any open shapes are closed automatically, so you don't have to call closePath(). This is not the case when you call stroke()

### moveTo(x, y)
- Moves the pen to the coordinates specified by x and y.
- When the canvas is initialized or beginPath() is called, you typically will want to use the moveTo() function to place the starting point somewhere else. 
- We could also use moveTo() to draw unconnected paths

### lineTo(x, y)
- Draws a line from the current drawing position to the position specified by x and y.
- This method takes two arguments, x and y, which are the coordinates of the line's end point. 
- The starting point is dependent on previously drawn paths, where the end point of the previous path is the starting point for the following, etc. 
- The starting point can also be changed by using the moveTo() method.

### arc() or arcTo() methods
- arc(x, y, radius, startAngle, endAngle, anticlockwise)
  - Draws an arc which is centered at (x, y) position with radius r starting at startAngle and ending at endAngle going in the given direction indicated by anticlockwise (defaulting to clockwise).
- arcTo(x1, y1, x2, y2, radius)
Draws an arc with the given control points and radius, connected to the previous point by a straight line.
- the arc method, takes six parameters: 
  - x and y are the coordinates of the center of the circle on which the arc should be drawn. 
  - radius is self-explanatory. 
  - The startAngle and endAngle parameters define the start and end points of the arc in radians, along the curve of the circle. 
    - These are measured from the x axis. 
  - The anticlockwise parameter is a Boolean value which, when true, draws the arc anticlockwise; otherwise, the arc is drawn clockwise.

### Bezier and Quadratic Curves
- quadraticCurveTo(cp1x, cp1y, x, y)
  - Draws a quadratic Bézier curve from the current pen position to the end point specified by x and y, using the control point specified by cp1x and cp1y.
- bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
  - Draws a cubic Bézier curve from the current pen position to the end point specified by x and y, using the control points specified by (cp1x, cp1y) and (cp2x, cp2y).
- The difference between is that a quadratic Bézier curve has a start and an end point and just one control point while a cubic Bézier curve uses two control points.

### Rectangles
- rect(x, y, width, height)
  - Draws a rectangle whose top-left corner is specified by (x, y) with the specified width and height.

### Path2D Objects
- Path2D()
  - The Path2D() constructor returns a newly instantiated Path2D object, optionally with another path as an argument (creates a copy), or optionally with a string consisting of SVG path data.

# [Applying Styles and Colors](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)
- color is a string representing a CSS ```<color>```, a gradient object, or a pattern object. We'll look at gradient and pattern objects later. By default, the stroke and fill color are set to black
- fillStyle = color
Sets the style used when filling shapes.
- strokeStyle = color
Sets the style for shapes' outlines.
  - strokeStyle property to change the colors of the shapes' outlines. 
- globalAlpha = transparencyValue
  - Applies the specified transparency value to all future shapes drawn on the canvas. The value must be between 0.0 (fully transparent) to 1.0 (fully opaque). This value is 1.0 (fully opaque) by default.
  - The globalAlpha property can be useful if you want to draw a lot of shapes on the canvas with similar transparency, but otherwise it's generally more useful to set the transparency on individual shapes when setting their colors.

> When you set the strokeStyle and/or fillStyle property, the new value becomes the default for all shapes being drawn from then on. For every shape you want in a different color, you will need to reassign the fillStyle or strokeStyle property.

#### Line Styles
- lineWidth = value
  - Sets the width of lines drawn in the future.
- lineCap = type
  - Sets the appearance of the ends of lines.
- lineJoin = type
  - Sets the appearance of the "corners" where lines meet.
- miterLimit = value
  - Establishes a limit on the miter when two lines join at a sharp angle, to let you control how thick the junction becomes.
- getLineDash()
  - Returns the current line dash pattern array containing an even number of non-negative numbers.
- setLineDash(segments)
  - Sets the current line dash pattern.
- lineDashOffset = value
  - Specifies where to start a dash array on a line.
- lineCap property determines how the end points of every line are drawn
  - butt: The ends of lines are squared off at the endpoints.
  - round: The ends of lines are rounded.
  - square: The ends of lines are squared off by adding a box with an equal width and half the height of the line's thickness.
-  lineJoin property determines how two connecting segments (of lines, arcs or curves) with non-zero lengths in a shape are joined together (degenerate segments with zero lengths, whose specified endpoints and control points are exactly at the same position, are skipped)
  - There are three possible values for this property: round, bevel and miter. By default this property is set to miter. Note that the lineJoin setting has no effect if the two connected segments have the same direction, because no joining area will be added in this case.
  - round: Rounds off the corners of a shape by filling an additional sector of disc centered at the common endpoint of connected segments. The radius for these rounded corners is equal to half the line width.
  - bevel: Fills an additional triangular area between the common endpoint of connected segments, and the separate outside rectangular corners of each segment.
  - miter: Connected segments are joined by extending their outside edges to connect at a single point, with the effect of filling an additional lozenge-shaped area. This setting is effected by the miterLimit property which is explained below.
- createLinearGradient(x1, y1, x2, y2)
  - Creates a linear gradient object with a starting point of (x1, y1) and an end point of (x2, y2).
- createRadialGradient(x1, y1, r1, x2, y2, r2)
  - Creates a radial gradient. The parameters represent two circles, one with its center at (x1, y1) and a radius of r1, and the other with its center at (x2, y2) with a radius of r2.
- gradient.addColorStop(position, color)
  - Creates a new color stop on the gradient object. The position is a number between 0.0 and 1.0 and defines the relative position of the color in the gradient, and the color argument must be a string representing a CSS <color>, indicating the color the gradient should reach at that offset into the transition.
- createPattern(image, type)
  - Creates and returns a new canvas pattern object. image is a CanvasImageSource (that is, an HTMLImageElement, another canvas, a <video> element, or the like. type is a string indicating how to use the image
    - repeat: Tiles the image in both vertical and horizontal directions.
    - repeat-x: Tiles the image horizontally but not vertically.
    - repeat-y: Tiles the image vertically but not horizontally.
    - no-repeat: Doesn't tile the image. It's used only once.
- shadowOffsetX = float
  - Indicates the horizontal distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- shadowOffsetY = float
  - Indicates the vertical distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- shadowBlur = float
  - Indicates the size of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0.
- shadowColor = color
  - A standard CSS color value indicating the color of the shadow effect; by default, it is fully-transparent black.

# [Drawing Text](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)
- fillText(text, x, y [, maxWidth])
  - Fills a given text at the given (x,y) position. Optionally with a maximum width to draw.
- strokeText(text, x, y [, maxWidth])
  - Strokes a given text at the given (x,y) position. Optionally with a maximum width to draw.
- font = value
  - The current text style being used when drawing text. This string uses the same syntax as the CSS font property. The default font is 10px sans-serif.
- textAlign = value
  - Text alignment setting. Possible values: start, end, left, right or center. The default value is start.
- textBaseline = value
  - Baseline alignment setting. Possible values: top, hanging, middle, alphabetic, ideographic, bottom. The default value is alphabetic.
- direction = value
  - Directionality. Possible values: ltr, rtl, inherit. The default value is inherit.
- measureText()
  - Returns a TextMetrics object containing the width, in pixels, that the specified text will be when drawn in the current text style.