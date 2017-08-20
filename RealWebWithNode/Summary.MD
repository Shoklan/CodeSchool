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
## Level 4
## Level 5
## Level 6
## Level 7

## Research:
- V8 Javascript Runtime
- 