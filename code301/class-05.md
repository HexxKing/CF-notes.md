# Read: 05 - Heroku Deployment

## [Heroku: Getting Started with Node](https://devcenter.heroku.com/articles/getting-started-with-nodejs)
- ```$ brew install heroku/brew/heroku```
  - installs heroku onto macOS
- ```heroku login```
  - opens the web browser to the Heroku login page
- ```node --verison```
  - checks what version of node is currently installed
- ```npm --verison```
  - checks what version of npm is currently installed
- ```git --verison```
  - checks what version of git is currently installed
- ```git clone https://blahblahblah.com```
  - works the same way it would for GitHub
- ```heroku create``` 
  - creates an app on heroku and prepares it to recieve the source code
  - Heroku generates a random name for your app, or you can pass a parameter to specify your own app name. 
- ```git push heroku master```
  - deploys the code
- ```heroku ps:scale web=1```
  - you can scale your dyno formation fromt he heroku CLI
  - im not exactly sure what this one does. need more answers.
- ```heroku apps:rename potato```
  - renames the app
- ```heroku open```
  - a shortcut to open the website
- ```heroku logs --tail```
  - views information about the running app
  - Heroku treats logs as streams of time-ordered events aggregated from the output streams of all your app and Heroku components, providing a single channel for all of the events.
  - Press **Control+C** to stop streaming the logs.

## [Deploying a Simple Blog to Heroku](https://howtonode.org/deploy-blog-to-heroku)
- Node.js is an open source, cross-platform runtime environment, which allows you to build server-side and networking applications. It's written in JavaScript and can be run within the Node.js runtime on any platform. 
- There is an acronym created to describe such type of applications Node.js was created for. 
  - It's DIRT. It means Data-Intensive Real-Time applications. 
  - Node allows a server to handle a lot of connections and work with a number of requests at the same time. And you don't need much memory for that. It's designed to be responsive and fast. Just like your web browser! 
  - So, it's useful when you need to create an application that will be able to respond instantly to a large number of users. And Node was built from scratch to provide you with such a functionality.