# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

NoSQL is non-relational database that stores data into documents and collections， while SQL stores data in a relational model with rows and columns. NoSQL will be better to use if the data needs are changing rapidly, and SQL can be used when the data is not changing in structure.

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
The author model probably does not have the author schema.
var Author = mongoose.model("Author", AuthorSchema)
Author.find({name: "Bob"})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.find_by({name: "Andy"})
Instructor.create({description:"Resin Laying Deer Figurine, Gold"})
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

```
## Express

### Question #5

What is module.exports and why do we use it?

```
module.exports allows us to separate our js files by exposing their contents as one global variable. We assign it when we require the file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", (req, res) => {
  res.render("index")
})

app.post("/candidates", (req, res) => {
  Candidate.create(req.body).then((candidate)=>{
    res.render("new")
  })
})

app.put("/candidates/:name", (req, res) => {
  Candidate.findOneAndUpdate({req.params.name.}, req.body, {new: true}).then((candidate) => {
    res.render("update")
  })
}
})

app.delete("/candidates/:name", (req,res) => {
  Candidate.findOneAndRemove({name: req.params.name}).then(() =>{
    res.render("index")
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
Rails is written in ruby and Express is written in js.
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
