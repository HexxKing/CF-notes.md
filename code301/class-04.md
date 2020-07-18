# Read: 04 - Responsive Web Design and Regular Expressions

# [CSS Grid Garden](https://cssgridgarden.com/)
- tutorial

# [RegExr](https://regexr.com/)
- Pay particular attention to the cheatsheet
- RegExr is an online tool to learn, build, & test Regular Expressions (RegEx / RegExp).

#### Character classes
- .	any character except newline
- \w\d\s	word, digit, whitespace
- \W\D\S	not word, digit, whitespace
- [abc]	any of a, b, or c
- [^abc]	not a, b, or c
- [a-g]	character between a & g

#### Anchors
- ^abc$	start / end of the string
- \b\B	word, not-word boundary

#### Escaped characters
- \.\*\\	escaped special characters
- \t\n\r	tab, linefeed, carriage return

#### Groups & Lookaround
- (abc)	capture group
- \1	backreference to group #1
- (?:abc)	non-capturing group
- (?=abc)	positive lookahead
- (?!abc)	negative lookahead

#### Quantifiers & Alternation
- a*a+a?	0 or more, 1 or more, 0 or 1
- a{5}a{2,}	exactly five, two or more
- a{1,3}	between one & three
- a+?a{2,}?	match as few as possible
- ab|cd	match ab or cd

# [Regex Tutorial](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
- Regular expressions (regex or regexp) are extremely useful in extracting information from any text by searching for one or more matches of a specific search pattern

#### Character classes — \d \w \s and .
- Use the . operator carefully since often class or negated character class are faster and more precise.
- \d, \w and \s also present their negations with \D, \W and \S respectively.
- For example, \D will perform the inverse match with respect to that obtained with \d.
- In order to be taken literally, you must escape the characters ^.[$()|*+?{\with a backslash \ as they have special meaning.
- Notice that you can match also non-printable characters like tabs \t, new-lines \n, carriage returns \r.

#### Flags
- A regex usually comes within this form /abc/, where the search pattern is delimited by two slash characters /. At the end we can specify a flag with these values (we can also combine them each other):
  - g (global) does not return after the first match, restarting the subsequent searches from the end of the previous match
  - m (multi-line) when enabled ^ and $ will match the start and end of a line, instead of the whole string
  - i (insensitive) makes the whole expression case-insensitive (for instance /aBc/i would match AbC)

#### Grouping and capturing — ()
- This operator is very useful when we need to extract information from strings or data using your preferred programming language. Any multiple occurrences captured by several groups will be exposed in the form of a classical array: we will access their values specifying using an index on the result of the match.
-  If we choose to put a name to the groups (using (?<foo>...)) we will be able to retrieve the group values using the match result like a dictionary where the keys will be the name of each group.

#### Bracket expressions — []
- Remember that inside bracket expressions all special characters (including the backslash \) lose their special powers: thus we will not apply the “escape rule”.

#### Greedy and Lazy match
- The quantifiers ( * + {}) are greedy operators, so they expand the match as far as they can through the provided text.

# [Regex 101](https://regex101.com/)
- this is a tool used to find the regex expression you want to use

# [CSS Grid Reference](https://css-tricks.com/snippets/css/complete-guide-grid/)
- Grid is the very first CSS module created specifically to solve the layout problems we’ve all been hacking our way around for as long as we’ve been making websites.

#### Important Terms
- Grid Container
  - The element on which display: grid is applied. It’s the direct parent of all the grid items. In this example container is the grid container.
- Grid Item
  - The children (i.e. direct descendants) of the grid container. Here the item elements are grid items, but sub-item isn’t.
- Grid Line
  - The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.
- Grid Cell
  - The space between two adjacent row and two adjacent column grid lines. It’s a single “unit” of the grid. Here’s the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.
- Grid Track
  - The space between two adjacent grid lines. You can think of them like the columns or rows of the grid. Here’s the grid track between the second and third row grid lines.
- Grid Area
  - The total space surrounded by four grid lines. A grid area may be composed of any number of grid cells. Here’s the grid area between row grid lines 1 and 3, and column grid lines 1 and 3.

# [Responsive design with CSS Grid](https://medium.com/samsung-internet-dev/common-responsive-layouts-with-css-grid-and-some-without-245a862f48df)
- CSS grid lets us not only arrange elements in a row or a column, but in multiple rows and columns
- The ‘Holy Grail’ layout describes a page with a header and footer that stick at the top and bottom of the window respectively, and a content section that is split into two sidebars and the main content sits between them. This has been notoriously difficult to solve in an elegant way with CSS due to the need to stretch the content to push the footer down to the bottom of the page. With CSS grid, creating this layout requires very few lines of code.
> body {
    display: grid;
    grid-template-columns: 200px 1fr 200px;
    grid-template-rows: auto 1fr auto;
    height: 100vh;
  }
- This will create a 3 by 3 grid with fixed width columns either side and a center row that stretches to fill the space left after the top and bottom rows take up their content’s space. Setting the header and footer to grid-column: span 3; will make them take up an entire row each