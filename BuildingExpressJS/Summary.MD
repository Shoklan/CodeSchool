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
- 


# User Params

# Body Parser

# Refactoring Routes

## Reference:
