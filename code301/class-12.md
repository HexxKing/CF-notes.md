# Read: 12 - Components
# Readings: EJS PARTIALS

## [EJS Partials](https://medium.com/@henslejoseph/ejs-partials-f6f102cb7433)
- Partials come in handy when you want to reuse the same HTML across multiple views. 
- Think of partials as functions
- Define that reusable bundle of code in a file and include it wherever you need it.
- In EJS, any JavaScript or non-HTML syntax you include in your templates is always surrounded by <% %> delimiters
- You use <%- include( PARTIAL_FILE ) %> where the partial file is relative to the template you use it in.
-  The <%- %> tags allow us to output the unescaped content onto the page (notice the -). 
  - This is important when using the include() statement since you don’t want EJS to escape your HTML characters like ‘<’, ‘>’, etc…

## [EJS tutorial from WalkThroughCode on YouTube, Video 7, Partials](https://www.youtube.com/watch?v=3_xEEH4fTEk&t=0s&index=7&list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)
- This is a short, 3-minute video.