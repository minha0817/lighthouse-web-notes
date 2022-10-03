# W02D05 - How HTTP Servers work, How to build HTTP Servers using Node, Using Express, an HTTP server framework, How domain names works

### How JS actually works 
callstack -> webAPIs -> task queue -> eventloop -> callstack

### Promise
* `Reason why we use it?` Some line of codes are asynchronous, which means `we don't know when they are going to finish executing.` That's why we handle that with promise.
* JS uses callbacks to handle asynchoronous work by default.

`* 4 States of Promise `

1. Fulfilled (it worked!)

2. Rejected (failed)

3. Pending (still waiting...)

4. Settled (something happened)

`* 4 Stages of Promise`
1. Wrapping (syntax, or the Promise structure)

2. Thening (when it works)

3. Catching (recovery, when there's an error)

4. Chaining (where you create long sequences of asynchronous work)

```js
get('example.json')
   .then(resolveFunc)
   .catch(rejectFunc)

```
```js
get('example.json')
   .then(resolveFunc)
   .then(undefined, rejectFunc)
```

### Javascript Style Guide
* `let & const are block - scoped` which they only exist in the blocks they are defined in.
* `function expression >>>>>> function declaration.`
-> function declarations are hoisted which means that it's to easy to reference the function before it's defined in the file. This harms readability and maintability. <br>
[Javascript Style Guide](https://github.com/airbnb/javascript)

### cURL
* It's command line utility that is used to make HTTP request to a given URL and it outputs the response.
* It allows you to see the URL.
* `curl <URL> -i` -> It allows me to inspect the response headers.

### Character encoding
* All characters are stored in computer using a special code. 
* A character encoding provides a key to unlock the code.
* It is a set of mappings between the bytes in the computer and the characters in the character set.
* Without the key, the data looks like a garbage.
* UTF-8 : Predominent character encoding and variable length encoding 1-4 bytes. 

### Domain Name Sysyem (DNS)
* When a URL is typed and press enter(request), website shows up(response).

`* how DNS works? `
*  DNS is translating IP address to certain number (192.18.20...)
1. when we type www.google.com -> it actually is www.google.com`.` (operating system)
2. The resolving name server
3. This dot represents the Root of the Internet's namespace.(The root name server)
4. (.com)TLD name server
5. Authoratative name server
6. The resolving name server
7. Operating system brought to the right certain number (192.18.20...)
8. Browser opens it.

### HTTP server 

* how to create server??
1. use http module 
```js
const  http=require('http')
const server=http.createServer((function(request,response)
  {
    response.writeHead(200,
    {"Content-Type" : "text/plain"});
    response.end("Hello World\n");
  }));
server.listen(7000); //or localhost:3000 
```

2. EXPRESS library 

```js
npm install express --save. //on terminal 

const express  = require("express"); // Import the express library
const app = express(); // Define our app as an instance of express
const port = 3000; // Define our base URL as http:\\localhost:3000

app.get("/", function(req,res){
   res.send("Hello World!");
});

app.listen(port, function () {
  console.log(`Server running on port ${port}`); // Tell yourself the port number to prevent mistakes in the future.
});
```
