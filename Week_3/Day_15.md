# W03D01 - Web Servers 101
### To Do
- [x] Web Servers
- [x] Express
- [x] Middleware

### Servers
* server - has data a client wants/needs
* client - wants data

### HTTP
* IP - internet protocol (street address)
* Port - apartment number of the process we are looking for
* 65,535
  * 3000 - 9000 (devs)
  * 80 - HTTP
  * 443 - https
  * 5432 - postgres

* TCP - transport control protocol


                      Move: up
  You ded
client <==== tcp ====> server


* HTTP - HyperText Transfer Protocol
* request/response cycle

### Request
* two parts: verb/action and a path/url/resource
* verb: describes what you want to do
  * GET - retrieve something
  * POST - send something (created/edited/deleted)
* path: describes what you want to do it to
  * http://www.google.com /search
  * http://localhost:3000 /about

* body: may or may not have contents

### Response
* must have a status code
  * 404 - resource not found
  * 200 - everything is okay
  * 500 - internal server error
  * 201 - resource created

  * 1xx - basic routing
  * 2xx - things are going well
  * 3xx - redirection
  * 4xx - bad request
  * 5xx - server errors

* may or may not have a body

                        Response
client <==== tcp/ ====> server

### Web Servers
* From [MDN](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_web_server)
> ...a web server includes several parts that control how web users access hosted files, at minimum an HTTP server. An HTTP server is a piece of software that understands URLs (web addresses) and HTTP (the protocol your browser uses to view webpages).
* Communicates using the HTTP protocol which is a `request -> response` protocol
* A web server listens for incoming requests and responds with a status code and (usually) content of some kind
* Content can be virtually anything: images, videos, static files, dynamically rendered files, or just pure data (usually JSON)
* We have 65,535 ports for each internet connection; we need to choose one for our web server to listen on
```js
cosnt net = require('net');
// a basic web server built using Node's http module
const http = require('http');
const port = 3000;
const server = net.createServer();
server.on('connection', (connection) => {
  console.log('someone has connected');
  connection.write('Move: up');
// create the server
const server = http.createServer((request, response) => {
  response.end('hello world');
});
server.listen(port);
// start the server listening on the specified port
server.listen(port, () => {
  console.log(`server listening on port ${port}`);
});
```

* Instead of responding the same way to every request that comes in, we can program the web server to respond differently depending on the specifics of the request

```js
const http = require('http');
const port = 3000;
// add custom routes to the `createServer` function
const server = http.createServer((req, res) => {
  const route = `${req.method} ${req.url}`;
  switch (route) {
    case 'GET /':
      res.end('This is a GET request to "/"');
      break;
    case 'GET /users':
      res.end('This is a GET request to "/users"');
      break;
    default:
      res.end('Route not found');
  }
});
```

const server = http.createServer();
### Express.js
* A _framework_ for building web servers written in JavaScript
* The main use for _Express_ is to simplify the creation of route handlers

server.on('request', (request, response) => {
  console.log('someone has made a request to the server');
```js
// Express server example
const express = require('express');
const morgan = require('morgan');
const port = 3000;

const app = express();

// middleware
// const morganMiddleware = morgan('dev');
// app.use(morganMiddleware);

app.use(morgan('dev'));

app.use((req, res, next) => {
  console.log('inside the middleware');
  req.secretKey = 'hello world';

  // if (!loggedIn) {
  //   res.redirect('/login');
  // }

  next(); // I'm finished, call the next middleware/route handler in line please
});

// GET /about
app.get('/about', (request, response) => {
  console.log('secretKey', request.secretKey);
  response.send('This is the about page');
});

// GET /home
app.get('/home', (req, res) => {
  // res.send()
  res.json({ message: 'welcome' });
  // res.sendFile()
  // res.render() // `${spotOne}: ${spotTwo}`
  // res.redirect();
});

app.listen(port);
```

### Middleware
* is a function that runs between receiving the request and sending back the response
* parsing incoming data 

                                                      request
client <=====> server => middleware => middleware => route handler
                        cookie-parser  body-parser
                        req.cookies     req.body
* _Middleware_ is code (in the form of functions) that runs between the incoming request and the outgoing response
* ExpressJS on its own has very little functionality; it is through the use of middleware that the real power of Express comes out
* There are many popular middleware packages available to us via NPM (or Yarn), for example:
  * [`body-parser`](https://expressjs.com/en/resources/middleware/body-parser.html): Parses the _body_ of the incoming request, converting it to a JS object and attaching it to the `request` object (accessible with `req.body`)
  * [`cookie-parser`](https://expressjs.com/en/resources/middleware/cookie-parser.html): Parses the _cookie_ header, converting it to an object and attaching it to the `request` object (accessible with `req.cookies`)
  * [`morgan`](https://expressjs.com/en/resources/middleware/morgan.html): A _logger_ that logs all requests/responses to the web servers console
* We let our Express know to use the piece of middleware via the `.use` method

```js
const incomingString = 'message=hello+world'
const incomingObj = {message: 'hello world'};
const express = require('express');
const app = express();
const bodyParser = require('body-parser');
const morgan = require('morgan');
// let Express know to use the middleware
app.use(bodyParser.urlEncoded({ extended: false }));
app.use(morgan('dev'));
```

### Custom Middleware
* We aren't limited to using middleware that someone else has written, we can freely create our own
* To define custom middleware, we pass a callback function to the `.use` method
* The callback function is passed the `request` and `response` objects as well as a special function `next` which our custom middleware will call to indicate that the middleware has finished running

```js
app.use((req, res, next) => {
  // do something with the request and/or response objects
  console.log(`New request: ${req.method} ${req.url}`);
  // call the next step in the middleware chain
  next();
});
```

### Useful Links
- [MDN: What is a web server?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_web_server)
- [Node Docs: http module](https://nodejs.org/api/http.html)
- [ExpressJS](https://expressjs.com/)
- [Popular Express Middleware](https://expressjs.com/en/resources/middleware.html)
- [Writing Custom Middleware](https://expressjs.com/en/guide/writing-middleware.html)