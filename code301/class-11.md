# Read: 11 - EJS

## [Watch EJS tutorial from WalkThroughCode on YouTube, Videos 1-5](https://www.youtube.com/watch?v=IqpfBGsALqc&list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt&index=1)
- this is series of videos demostrating how to use EJS

## [Reference: Google Books API Docs](https://developers.google.com/books/docs/v1/using#WorkingVolumes)
- Specifically the section about working with Volumes. Review the sample request and response. Practice making requests using Postman and consider the possible properties of the response that you may want to include in your book application.
### Working with volumes
#### Performing a search
You can perform a volumes search by sending an HTTP GET request to the following URI:

> https://www.googleapis.com/books/v1/volumes?q=search+terms

This request has a single required parameter:

- q - Search for volumes that contain this text string. There are special keywords you can specify in the search terms to search in particular fields, such as:
- intitle: Returns results where the text following this keyword is found in the title.
- inauthor: Returns results where the text following this keyword is found in the author.
- inpublisher: Returns results where the text following this keyword is found in the publisher.
- subject: Returns results where the text following this keyword is listed in the category list of the volume.
- isbn: Returns results where the text following this keyword is the ISBN number.
- lccn: Returns results where the text following this keyword is the Library of Congress Control Number.
- oclc: Returns results where the text following this keyword is the Online Computer Library Center number.

# THIS IS THE MOST HELPFUL REFERENCE ON THIS TOPIC
## [Reference: EJS Docs](https://ejs.co/)
- EJS is a simple templating language that lets you generate HTML markup with plain JavaScript. 
- Fast compilation and rendering
- Simple template tags: <% %>
- Custom delimiters (e.g., use [? ?] instead of <% %>)
- Sub-template includes
- Ships with CLI
- Both server JS and browser support
- Static caching of intermediate JavaScript
- Static caching of templates
- Complies with the Express view system

## [EJS Tutorial](https://scotch.io/tutorials/use-ejs-to-template-your-node-application)
- [Source Code for the EJS Tutorial](https://github.com/scotch-io/node-ejs)
- Like a lot of the applications we build, there will be a lot of code that is reused. We'll call those ***partials*** and define three files we'll use across all of our site: ***head.ejs, header.ejs, and footer.ejs***. 
- The syntax to use an EJS partial is: <% include FILENAME %>. The path to the partial is relative to the current file.
- To echo a single variable, we just use <%= tagline %>.
- To loop over our data, we will use .forEach. 
- Currently, EJS doesn't support the ability to have layouts. So far we have just brought in other partials, but not really used layouts the way we would expect templating to work (extending a layout file and passing a view file into that). 
  - There have been projects in the past to try to bring templating to EJS. The two main projects are EJS Locals and EJS Express Layouts. These provide the ability to define different layouts like a sidebar layout and a full width layout and then call those on the fly. 
  - Sadly, EJS Locals is no longer maintained and EJS Express Layouts doesn't work with Express 4 at the time of this writing.

