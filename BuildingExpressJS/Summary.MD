# Building Blocks of Express.js
## Carlos Souza

# First Steps
- Express is a Web Application Framework for Node.
- It's minimal and Flexible.
- Can be used as teh foundation for other tools.
- To install it use `npm install express`.
```js
var express = require('express');
var app = express();
```
- You can create routes using the `app.get` function.
```js
app.get('/', function(request, response){
  response.send("Hello world");
});

app.listen(3000);
```
- To run the app, you run `node app.js`.
- Express extends Node.js
- You can mix and match Node and Express functions since Express inherits from Node.js.
- If you pass a string the the `send()` function then it changes the header to represent text/html automatically.
- You can redirect after conneection using `response.redirect('<url_or_dir>')`.
- We can use the 301 status code to tell the browser that this is permenant.

# Middleware
- We'll place our *index.html* file in the folder */public/index.html*.
- To return this file, we'll use `response.sendFile(__dirname + '/public/index.html');`
- `__dirname` means *current directory*.
- You can mount midddleware using `app.use(express.static('public'))`.
- This will cause our application to serve *index.html* be default.
- **Middleware** are functions executed sequentially that access request and response.
- This allows us to process what came in in a step-by-step fashion.
- You pass things down the middleware pipe via `app.use( function( request, response, next){ ...; next();})`.
  * Where next must be called to continue down the pipe.
- Everything inside the public folder will be served.
- You can then serve the JS files to communicate back to the server for AJAX.
- To create a custom *middleware* we create a new file with an appropriate name: *logger.js*.
- To export a function outside of the program use `module.exports = function( request, response, next){};.`
- `var start = +new Date();`; `+new` converts into linux epoch time.
- You can gain access to the standard out using `var stream = process.stdout;`.
- You can tell something is a local module when it's of the form `./logger`.

# User Params
- **Query Strings** are a great way to limit the number of results returned from an end point.
- The query strings come in after `?` in the url request.
- You can access the queries using `request.query.<name>`.
- We can use **Meaningful Urls** to return the description for specific types of blocks.
- **Dynamic Routes** are placeholders that can be used to name arguement parts of the url path.
- The formula looks like `'/blocks/:name'`.
- These will be added as `request.params.name`.
- The proper way to deal with requests for objects that don't exists is to return a 404 status code.
- A response for something that does not exist generates a response of `undefined` in Javascript.
- To respond correctly, use `response.status(404).json('Error Messages here!')`.
-


# Body Parser

# Refactoring Routes

## Reference:

## Research:
- Morgan Node Project?
-
