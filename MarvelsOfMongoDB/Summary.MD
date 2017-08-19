## The Magical Marvels of MongoDB
### Joel Taylor

## Level 1
- MongoDB is an Open source NoSQL database.
- NoSQL are databases that doesn't have a query language like SQL.
- Collections vs Tables.
- Documents vs Rows.
- Document-oriented vs Relational.
- We can store completely different documents in a collection.
- This is refered to as a *Dynamic Schema*.
- To get into the shell type `mongo`.
- MongoDB is basically just javascript.
- Select which database to use using `use <database>`.
- View current database using `db`.
- You don't store a document in the database; you store it in a collection first.
- To insert the docuement, you use `db.<collection>.insert( variable_or_JSON )`.
- To get a document, you use `db.<collection>.find( )`
- Mongo requires all documents to have a unique id; will create one if not specified.
- It's better if Mongo makes ids.
- You can request `find()` locate a specific entry by passing the key,value pair.
- `find()` will return the whole document as opposed to just the single field.
- It will return all documents that match.
- Queries are case sensitive.
- Mongo saves files in a format called BSON.
- To access embedded documents, you use dot notation.
- Ex: `db.potions.find({"ratings.flavor": 5})`.
- MongoDB doesn't force values into an explicit type.
- Verifying data is our responsibility.


## Level 2


## Level 3

## Level 4

## Level 5