# W03D04 - Security & Real World HTTP Servers
### To Do
- [x] Storing passwords
- [x] Encrypted cookies
- [x] HTTP Secure (HTTPS)
- [x] REST
- [x] More HTTP methods
- [ ] Method Override [Stretch]

### Hashing
* one way process
* plaintext password => hashing algorithm => hash sdfhasd7f9asdfnasdfu83
* (plaintext password + salt) => hashing algorithm => hash 
 'potato' + 'asdjkfghjasd86234' => algo => hash

### Encryption
* two way process
* plaintext cookie => encryption algo => encrypted text => sent to the browser
* request with encrypted cookie => decryption algo => plaintext => route handler

                  encrypted cookie
request => server => middleware => middleware => route handler => middleware
                    cookie-session                                cookie-session
                    req.session                   req.session     res.cookie('whateverIWant', encrypted cookie);



https://localhost:3080/login

Monster in the Middle
MitM

public key/private key (asymetric cryptography)
https://www.google.com/


### REST
* REpresentational State Transfer
* naming convention for routes
* routes used to access a resource represent the underlying data structure
* RESTful

R GET /videos/2/comments
R GET /blogposts/5/replies
R GET /images/10/likes
GET /likes


B  GET   /users
R  GET   /users/:id
E  POST  /users/:id
A  POST  /users
D  POST  /users/:id/delete

B  GET    /users
R  GET    /users/:id
E  PATCH  /users/:id
A  POST   /users
D  DELETE /users/:id


PUT - replaces a resource completely
PATCH - replaces a piece of a resource
DELETE - deletes a resource


### Storing Passwords
* We **never** want to store passwords as plain text
* Passwords should always be _hashed_ 
* **Hashing**:
  * The original string is passed into a function that performs some kind of transformation on it and returns a different string (the _hash_)
  * This is a one way process: a hashed value cannot be retrieved
* We make hashing more secure by adding a _salt_ to the original string prior to hashing
* This [helps to protect against Rainbow Table attacks](https://stackoverflow.com/questions/420843/how-does-password-salt-help-against-a-rainbow-table-attack)

### Encrypted Cookies
* Plain text cookies can be manipulated by users
* It's better practice to use _encrypted_ cookies
* **Encryption**:
  * Similar to hashing, the string is scrambled/transformed by a function
  * This is a two-way process: encrypted strings can be decrypted by the intended recipient

### When to use...
* Plain Text Cookies:
  * Almost never use plain cookies
  * Maybe for:
    * Language selection
    * Shopping cart for non-logged in users
    * Analytics
* Encrypted Cookies:
  * Do this by default
  * Only store a way to uniquely identify the user (eg. `user_id` or `username` can be used to look up values in a database or object)

```js
app.post('/register', (req, res) => {
  const email = req.body.email;
  const password = req.body.password;

  // check if email or password are NOT defined
  if (!email || !password) {
    return res.status(400).send('please include email AND password');
  }

  // check if the email is already in use
  const userFromDb = findUserByEmail(email);

  // if email is duplicated, respond with error message
  if (userFromDb) {
    return res.status(400).send('email is already in use');
  }

  // create a new user object
  const id = generateUniqueId();

  const salt = bcrypt.genSaltSync(10);
  const hash = bcrypt.hashSync(password, salt);

  const user = {
    id,
    email,
    password: hash
  };

  // update the users object with our new user
  users[id] = user;
  console.log(users);

  // do we log the user in (set a cookie) OR do we redirect the user to /login
  // res.cookie('userId', user.id);
  req.session.userId = user.id;

  res.redirect('/protected');
});

```




### HTTP Secure (HTTPS)
* HTTPS uses Transport Layer Security (TLS) to encrypt communication between client and server
* Encrypted using asymmetric cryptography which uses a public key and private key system
* The public key is available to anyone who wants it and is used to encrypt the communication
* The private key is known only to the receiver and is used to decrypt the communication

### REST (REpresentational State Transfer)
* REST means that the path that we are going to should represent the data being transferred
* An API that uses the REST convention is said to be RESTful
* RESTful routes look like:

  | **Method** | **Path** | **Purpose** |
  |:---:|:---|:---|
  | GET | /resources | Retrieve all of a resource (Browse) |
  | GET | /resources/:id | Retrieve a particular resource (Read) |
  | POST | /resources/:id | Update a resource (Edit) |
  | POST | /resources | Create a new resource (Add) |
  | POST | /resources/:id/delete | Delete an existing resource (Delete) |

* RESTful API's have some advantages:
  * If I know that your API is RESTful, then I can easily guess at what endpoints you have defined and I don't need to read your documentation to figure it out
  * Results in clean URLs (ie. `/resources` instead of `/get-my-resource`)
  * The desired action is implied by the HTTP verb
  * This method of specifying URLs is chainable (eg. `/users/123`, `/users/123/resources` or `/users/123/resources/456`)

* Selectors are always plural (eg. `/resources`, `/users`)
* Actions are always singular (eg. `/login`, `/register`)

### More HTTP Methods
- We have more [*verbs*](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) available to us than just `GET` and `POST`
- Popular ones are `PUT`, `PATCH`, and `DELETE`
- `PUT`: used to replace an existing resource
- `PATCH`: update part of an exisiting resource
- `DELETE`: delete an existing resource
- We can access these other methods via AJAX requests (we'll introduce you to AJAX in week 4) or by using the [`method-override`](https://www.npmjs.com/package/method-override) package
- Using these new verbs, our routes table now looks like:

  | **Method** | **Path** | **Purpose** |
  |:---:|:---|:---|
  | GET | /resources | Retrieve all of a resource (Browse) |
  | GET | /resources/:id | Retrieve a particular resource (Read) |
  | PUT | /resources/:id | Replace a resource (Edit) |
  | PATCH | /resources/:id | Update a resource (Edit) |
  | POST | /resources | Create a new resource (Add) |
  | DELETE | /resources/:id | Delete an existing resource (Delete) |

### REST
- REST
- REST is a set of conventions and practices in web development that deals with accessing and manipulating resources over HTTP.

- A resource can be an abstraction of an object or data. In practice resources are referenced using a URL (Uniform Resource Locator).

```js
GET /repos/:owner/:repo/commits
```

### Useful Links
* [Plain Text Offenders](https://github.com/plaintextoffenders/plaintextoffenders/blob/master/offenders.csv)
* [How Does Encryption Work?](https://medium.com/searchencrypt/what-is-encryption-how-does-it-work-e8f20e340537)
* [What is HTTPS?](https://www.cloudflare.com/learning/ssl/what-is-https/)
* [Asymmetric Cryptography](https://searchsecurity.techtarget.com/definition/asymmetric-cryptography)
* [Client Session vs Server Session](http://www.rodsonluo.com/client-session-vs-server-session)
* [Resource Naming](https://restfulapi.net/resource-naming/)
* [Express Middleware](https://expressjs.com/en/guide/using-middleware.html)
* [Method Override Package](https://www.npmjs.com/package/method-override)
* [Express Response Object](http://expressjs.com/en/api.html#res)
* [List of common Express middleware](https://expressjs.com/en/resources/middleware.html)
