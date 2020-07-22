# Read: 13 - Update/Delete

## [Sending Form Data](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data)
- Once the form data has been validated on the client-side, it is okay to submit the form. And, since we covered validation in the previous article, we're ready to submit! 

### Client/server architecture
- a client (usually a web browser) sends a request to a server (most of the time a web server like Apache, Nginx, IIS, Tomcat, etc.), using the HTTP protocol. The server answers the request using the same protocol.
- An HTML form on a web page is nothing more than a convenient user-friendly way to configure an HTTP request to send data to a server. 
  - This enables the user to provide information to be delivered in the HTTP request.

### On the client side: defining how to send the data
- The ```<form>``` element defines how the data will be sent. All of its attributes are designed to let you configure the request to be sent when a user hits a submit button. 
  - The two most important attributes are ***action*** and ***method***.

#### The action attribute
- The action attribute defines where the data gets sent. Its value must be a valid relative or absolute URL. If this attribute isn't provided, the data will be sent to the URL of the page containing the form — the current page.
- It's possible to specify a URL that uses the HTTPS (secure HTTP) protocol. 
  - When you do this, the data is encrypted along with the rest of the request, even if the form itself is hosted on an insecure page accessed using HTTP. 
  - On the other hand, if the form is hosted on a secure page but you specify an insecure HTTP URL with the action attribute, all browsers display a security warning to the user each time they try to send data because ***the data will not be encrypted***.
- The names and values of the non-file form controls are sent to the server as name=value pairs joined with ampersands. 
- The action value should be a file on the server that can handle the incoming data, including ensuring server-side validation. 
  - The server then responds, generally handling the data and loading the URL defined by the action attribute, causing a new page load (or a refresh of the existing page, if the action points to the same page).

#### The method attribute
- The method attribute defines how data is sent. 
- The HTTP protocol provides several ways to perform a request; HTML form data can be transmitted via a number of different methods, the most common being the GET method and the POST method
- This is how HTTP works. 
  - Each time you want to reach a resource on the Web, the browser sends a request to a URL. 
  - An HTTP request consists of two parts: a header that contains a set of global metadata about the browser's capabilities, and a body that can contain information necessary for the server to process the specific request.

##### The GET method
- The GET method is the method used by the browser to ask the server to send back a given resource: "Hey server, I want to get this resource."

##### The POST method
- It's the method the browser uses to talk to the server when asking for a response that takes into account the data provided in the body of the HTTP request: "Hey server, take a look at this data and send me back an appropriate result." 
- If a form is sent using this method, the data is appended to the body of the HTTP request.

##### Viewing HTTP requests
- HTTP requests are never displayed to the user 
  - if you want to see them, you need to use tools your Chrome Developer Tools.









## [HTML5 Forms Reference](https://htmlreference.io/forms/)
- Pay special attention to the “action” and “method” attributes.

## [Video Series on Styling HTML5 Forms](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g5_p_BVUGWykHfqx6bb7qK)
- Note that this video series is approximately 40 minutes long. 