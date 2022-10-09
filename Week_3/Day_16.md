# Template engine
- Templates are files that define the presentation of a web app's data separately from the server logic. => `EJS`(embedded javascript) with `res.render`
- EJS render data to our web pages.
- Why is helpful? => keeping server logic separate from markup

# render
- when I make res.render("browse-breads"); I was wondering what the render means
- what is `rendering`?? <br> 
Browser can't read ejs file. It has to be changed ejs to HTML so that browser can read. The process is the rendering. 
- When we send variables to EJS template, we need to send them inside an object even if that is only one single variable. <br>
```js
//example
res.render("browser_breads", {breads : database});
```

# CRUD and BREAD
-  what is a `resource` ?????
  1. a "thing" or a "type of data" that a user might want to interact with
  2. a server provides access to all the resrouces in an app
  3. examples: Facebook.com
                              users
                              posts
                              photos

  - do some examples from real websites
- Acroynyms: CRUD and BREAD

- `req` : browser
- `res` : server
- CRUD
  - Create
  - Read
  - Update
  - Delete

- BREAD
  - Browse
  - Read
  - Edit
  - Add
  - Delete

- example : 
1. `bread` => get/breads
2. `Read` breads => get/breads/:id | get/breads/1
3. `Edit` breads => post/breads/:id
4. `Add` breads => post/breads/new
5. `Delete` breads => post/breads/delete/:id

# Build an Express Server
- `npm init`
- `touch server.js`
- `npm i express`
- `const express = require('express')`
- `const app = express()`
- `const PORT = 8080`
- `app.listen(8080, () => console.log('Server listening on port 8080'))`

# Basic Route
- Can we visit the site yet?
- Show what it looks like if you use the browser before the route exists
- Look at requests in Browser tools
- Install morgan to show request
  - `const morgan = require('morgan')`
  - `app.use(morgan('dev'))`
- Simple `/` route with a Hello World
  - `res.send()`

# Database

- Create an object to store data
- Add sample data (at least three)
- Create an object to store data (object of objects with at least three properties, keyed to `id`)
- Add sample data (at least three rows)


# Scaffold

  - body - how does it get data from the form????
  - `name` attribute of the `<input>` tag
- Handle the request on the server
- `npm i body-parser`
- `const bodyParser = require("body-parser")`
- `app.use(bodyParser.urlencoded({extended: true}))`
- `app.use(express.urlencoded({extended: true}))`
- `res.redirect` vs `res.render`
  - Show POST / REDIRECT / GET pattern
  - Show in Morgan/Dev Tools
# Add
- Make new Add view to create a new resource
- Set up GET route to serve it
- Make another form
  - name attributes again
  - get students to build this one together
- set up POST route to handle the request
- `res.redirect` to new resource
  - Show in morgan/Dev Tools
# Delete
- Update Read View to have a delete button
- Another form with POST to delete
  - Why is this a form when there are no inputs?
- Make POST route to handle
- `res.redirect` to Browse
  - Show in Morgan/dev Tools

# Git branches 
- Branching? Project's features, bugs, updates can be sectioned off
```js
git checkout -b bugFix
git commit
git checkout -b main
git commit
git merge bugFix main
```