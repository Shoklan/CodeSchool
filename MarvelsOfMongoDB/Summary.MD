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
- MongoDb has what are called *Common Comparison Operators*:
	1. `$gt` greater than.
	2. `$lt` less than.
	3. `$gte` greater than or equal.
	4. `$lte` less than or equal.
	5. `$ne` not equal to.
- Syntax is `db.<collection>.find( {"price": {"$lt": 20 }})`.
- You can pass more than just one comparison operator.
- To do that same to embedded lists use `"$elemMatch"`.
- The syntax is `db.<collection>.find( {"field": {"$elemMatch" { ... }}}); ... for comparison operators.
- To limit what is returned further, MongoDB allows one to use what are called *Projections*.
- To apply them, pass `{"field": true}`.
- You can also do the reverse and reject data by passing `false` instead.
- For `find` we get back pointers to items.
- Normally, we only get 20 documents.
- You can get the total number of records by appending `.count()` to the end of the call.
- `count()` is called a *Cursor Method*.
- Another cursor method is `sort()`.
- You can tell `sort()` what fields to sort on by passing `{"field": <1,-1>}`; where 1 is asc, -1 is desc.
- Two more cursor methods are `.limit()` and `.skip()` which are self explanatory.

## Level 4
- Lots of duplicate data is a danger to data integrity.
- You can reference other collections like a Relational database.
- If you include `<collection>_id` Mongo will auto-reference the other collection.
- In this setup, we will need two queries to get all data.
- MongoDb has what is called Atomic writes; i.e. either everything is updated or nothing is updated.
- This is not true for references to other collections.
- "Mongo does not support transactions by default."
- If there is a lot of data, then use references.
- If the information is always queried together, then use Embedded.
- If the data rarely changes, then embed it.
- If it changes a lot, then reference it.

## Level 5
- MongoDB has a aggregation framework built in.
- To use them, use `db.<collection>.aggregate()`.
- This is based what are called *Stage Operators*.
- One such operator is `"$group" to group by a field.
- The syntax is `{"$group": {<group_key>: "$field"}}`.
- Anything passed after the group key is called an *Accumulators*.
- Some different accumulators are:
	1. $sum
	2. $avg
	3. $match
	4. $min
	5. $max
	6. $sort
	7. $limit
- `$match` should be used as soon as possible to reduce the compelixity of future filters in the pipeline.
- `$project` should be used as soon as possible to reduce the compelixity of future filters in the pipeline.