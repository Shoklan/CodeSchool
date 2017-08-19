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
- To delete a document use `db.<collection>.remote()`.
- To update a document use `db.<collection>.update( target, {"$set": {"key":"value"}})`.
- The update only works on the first matching document.
- If the update does not contain the `$set` parameter, then data is overwritten.
- To update more than the first hit, use `{"multi": true}`
- You can increment known numeric values using `{"$inc": {"targer": <n_to_increase>}}
- If a document is not matched, then no update.
- To create a document if it does not exist, then use `{"upsert": true}`.
- You can globally remove a field using `{"$unset": {"key": ""}}.
- You can change the name of a field using `{"$rename": { "field":"new_name"}}`.
- You can change an embedded value using a *positional placeholder* declared as `{"$set": {"field.$": value }}`.
- There are a few other special operations:
	1. $max ; iff new value > than current or empty.
	2. $min ; iff new value < than current or empty
	3. $mul ; multiply current value by new value
	4. And, much more.
- You can pop elements off a list using `$pop` with 1 for last element, -1 for first element.
- You can push elements onto a list using `$push`.
- You can pull all values out of an array using `$pull`.

## Level 3

## Level 4

## Level 5