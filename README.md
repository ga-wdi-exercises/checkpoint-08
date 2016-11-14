# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQl databases are also known as Relational Databases and have many tables. No SQL databases are dcoument based, key value pairs. SQL dbs usually have a predefined schema where NoSQL has a dynamic schema for unstructured data. A NoSQL db is preferable when you have a ton of information that doesn't necessarily need relational mapping and can scale horizontally. A SQL db is vertically scalable and can provide clarity when searching for data.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
results is returning as a query object and not hte result. The result can be avaiable in a callback or using a mongoose promise aka .exec

var results = AuthorModel.find({name:"Bob"}).exec()
console.log(results)

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({"name": "Andy"},{$push:{"description": "Resin Laying Deer Figurine, Gold"}})
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
@author = Author.new(name: params[:name])
@author.save!

or @author = Author.create!(name: params[:name])
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports allows us to use variables we've defined in one js file to another js file as long as we require that specific js file that has the exports. It allows for cleaner management of js code within your js application.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", (req, res) => {
  res.render("hello pizza")
})

app.post("/pizza", (req, res) =>{
  Pizza.create(req.body.pizza).then( pizza => {
    res.redirect("/pizza/" + pizza.type)
  })
})

app.post("/pizza/:type", (req, res) => {
  Pizza.findOneAndUpdate({type: req.params.type}, req.body.pizza, {new: true}). then ( pizza =>{
    res.redirect("/pizza/" + pizza.type)
  })
})

app.post("/pizza/:type/delete", (req, res) => {
  Pizza.findOneAndRemove({type: req.params.type}).then (pizza =>{
    res.redirect("/pizza")
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

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
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
