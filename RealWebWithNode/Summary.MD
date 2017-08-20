# Real Time Web With Node

## Level 1
- Node allows you to build scalable Netowrk Applications using Javascript on the server side.
- Node is a wrapper around the V8 Javascript Runtime.
- Node is all written in C.
- Types of servers you could build:
	1. Websocket server; chat server.
	2. File upload client.
	3. Ad server.
	4. Real time data apps.
- Node.js is not a web framework.
- Not really for beginners since it's so low level.
- It's not multi-threaded.
- Blocking is where execution stops while it waits for an original command to finish.
- Non-blocking is where a step is ignored until a *callback* is sent.
```js
var contents = fs.readFileSync('target/file', function( err, contents){
	// stuff to do.
})
// other stuff.
```
- Alternatively, we could define the function and parameters and pass that to the function call.
- You can tell node what you need using `var http = requires('http');`
- Worth knowing: `http.createServer( function( request, response){})` is how you start server in Node.js.
- Node uses what is called the *Event Loop* to continue checking for requests.
- Most other languages require blocks; this is, in Python, called the *Mutex Lock*.
- `readFileSync()` is blocking; `readFile()` is non-blocking.
- Issueing commands in node using `node`.
- `writeHead()` can do more than send the 200 code.
- `response.end()` can also return a string response.

## Level 2
- Focused on events this level.
- Types of events include click, submit and hover.
- Just like the DOM, many objects in Node emit events.
- This being the case, they almost certainly inherit from **EventEmitter**.
```js
var EventEmitter = require('events').EventEmitter;
var logger = new EventEmitter(); // error, warn, info events.

logger.on('error', function( message ){
	console.log('ERR: ' + message);
});

logger.emit('error', 'Spilled Milk');

// These next two lines are the same:
http.createServer( function( request, response){});

var server = http.createServer(); server.on('request', function( request, response){});
```

## Level 3
- Talking about streams this level.
- Streams allow us to process data as soon as it is received.
- Streams are like channels were data just flows through.
- There are two types:
	1. Readable.
	2. Writable.
- ReadableStream inherits from EventEmitter.
```js
request.on( 'reabale', function(){
	var chunk = null;
	while( null !== (chunk = request.read())){
		console.log(chunk.toString());
	}
});
request.on('end', function(){
	response.end();
});
```
- This block deals with each sent chunk of data piece by piece in non-blocking fashion.
- Node has a function called `request.pipe( //response )` that behaves like a pipe between two clients.
- To read files, you need `var fs = require('fs');`.
- Then, `var file = fs.createReadStream("readme.md");`.
- To write contents to a file, use `var newFile = fs.createWriteStream("readme_copy.md");`
- You can pipe any read stream into any write stream.
- You can access how large the file is supposed to be using `var fileBytes = request.headers['content-length'];
- Instead of all that low level code, you could just call `file.pipe( process.stdout);`.
- To force a pipe to remain open until an end is received, pass `{ end: false }` to `*.pipe()`.

## Level 4
- To allow external access to a function, one must include `module.exports = <namespace>`.
- In the file **app.js**, we then can include `var hello = require('./custom_hello');`
- You can export a function explicitely using `exports.<function_name> = function(..){}`.
- You can call the second using `gb.goodbye();` but the first as `hello();`.
- The options passed to `http.request()` are:
	1. host.
	2. port.
	3. path.
	4. method
- If a path is not specified, then node looks in the node_modules directory of the app.
- Then, it checks node_modules in the home directory.
- npm is the package manager for Node.
- To install a package use `node install <module_name>`.
- To install a module globally, pass the flag `-g` at the end of the command.
- If you think you know the name, node comes with a `search` command.
- When building a node project, the packages.json file tells node lots of important information.
- The three most important are:
	1. name
	2. version
	3. dependencies.
- Calling `npm install` will have node check to insure all dependencies are installed.
- If you include the package name with a `~n` then node will only install the lastest version of n instead of n+1.
- `module.exports.warn = warn;` for reference.


## Level 5
- This level is about Express
- `npm install --save express`
- `--save` will add the package to our dependencies.
- Require express -> assign express to new app.
- You can pass parameters to express using `:etc`.
- You can access those from the `get()` call using `req.params.<parameter>`.
- You make json data not look like shit, install prettyjson.
- Package ejs stands for embedded javascript.
- `<% = %>` for print data.
- `<% %>` for running code.
- `res.render('template.ejs')` to render a template to a request.
- `render()` can be passed a json object 

## Level 6
- This level is about Socket.io.
- Web servers nowadays have web sockets.
- Not all browsers have this capacity.
- Since some don't, we'll need a fall back like Socket.io.
```js
var express = require('express');
var app = express();
var server = require('http').createServer(app);
var io = require('socket.io')(server); // what is this?

io.on('connection', function(client){
	console.log('Client connected... ');
	client.emit('messages', {hello: "world"});
});

app.get('/', function( req, res){
	res.sendFile( __dirname + "/index.html");
});

app.listen(8080);
```
- Make sure to includde the socket.io.js file in the html file.
- As well as calling `var socket = io.connect('<server_address>');`
- Inside the client side data, you can then call any responses from socket.io.
- Socket.io has a broadcast category for emits.
- `socket.broadcast.emit( 'messages', <messages>)`.
- You can assign any variable


## Level 7

## Research:
- V8 Javascript Runtime
- Gulp.js
- Sinatra