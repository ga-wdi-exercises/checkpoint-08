# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```
  - SQL database is a relational database, it has tables, rows and columns. A SQL is better equipped to handle a lot of models/complex domain models.
  - NoSQL database is a nonrelational database, and it has collections, documents and fields.  A NoSQL is more flexible and therefore better suited for less complex associated, no more than three models or it will get ugly.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
good question, I believe is because we set it to the results so there is no need to be redundant.
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

show: function(req){
  Instructor.findOne({"name": req.name}, function(err, docs){
    console.log(docs);
    return docs;
  })
}

instructorsController.show({name: "Andy"});

WishlistItems.create({description: "Resin Laying Deer Figurine, Gold"}, (err, wishlistitems) => {
  if(err){
    console.log(err);
  } else {
    console.log(wishlistitems);
  }
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
def create
  @author = Author.create!(author_params)

  redirect to author_path(@author)
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
Your answer...
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer...
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
