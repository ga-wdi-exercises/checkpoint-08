# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
SQL database, it’s impossible to add data until you define tables and field types in what’s referred to as a schema(relational databases), but  NoSQL database, data can be added anywhere, at any time(non-relational database, but document-based stores).
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Your answer...
```It needs a callback;
results.select('name first');


### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
andy = Instructor.find({name: "Andy"})
@andy.wishlist_items.create({ description: "Resin Laying Deer Figurine, Gold"}, function (err, small) {
  if (err) return handleError(err);
  // saved!
})
```

### Question #4

Convert the following create method in Mongoose to ActiveRecord.

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("authors")
  }
})
```

```rb

Author.create(:name => 'John')
```
## Express

### Question #5

What is module.exports and why do we use it?

```text

module.exports -- is a variable that represents current module and exports is an object that will be exposed as a module
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```
app.use()
app.get('/', function(req, res) {
  res.json('users');
});
app.get('/user/:id', function(req, res) {
  res.json('user')
)};

app.post('/users', function(req, res) {
  res.json('user');

  User.create(req.body.user).then(function(user){
    es.redirect('/users' + user.name);
    })
  });
app.listen(process.env.PORT || 3001);

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Ruby is slow but performs better, Express(Node.js) is very powerfull, however if the application throws an error the whole application can crash.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer here

bodyParser is a part of "Connect", a set of middlewares for node.js.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
