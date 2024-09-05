---
type: "docs"
title: Mongo DB
draft: false
url: "docs/db/mongodb/"
---

# MongoDB

- [MongoDB Download](https://www.mongodb.com/download-centerjmp=nav#community)
- MongoDB is a document database. It is open-source and cross platform.
- It stores data in a type of JSON format called **BSON**. A record in MongoDB is a document, which is a data structure composed of key value pairs similar to the structure of JSON objects.
- Records in a MongoDB database are called documents, and the field values may include numbers, strings, booleans, arrays, or even nested documents.

---

## Database Management Systems

A special software program that helps users create and maintain a database

- Makes it easy to manage large amounts of information
- Handles security
- Backups
- Importing/Exporting Data
- Concurrency
- Interacts with software applications
- **CRUD** - Create Read Update Delete
- Non-Relational (noSQL / not just SQL)
- Data is organized in a non-traditional way, using data structures other than tables, which are used in Relational Database Management Systems.
- Example of Relational Database Management Systems:
  A. Key-Value stores
  B. Documents (JSON, XML etc)
  C. Graphs
  D. Flexible Tables
- **Query** -- A request made to Database Management system for specific information. **Eg** : A Google Search is a query.

---

## Basic Commands

| Command                  | Action                                                                                                                      | Command            | Action                                                                                            |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------- |
| `mongosh`                | Open a connection to your local MongoDB instance. All other commands will be run within this mongosh connection             | `use <db>`         | Switch current database to <db>. The mongo shell variable db is set to the current database.      |
| `db.help()`              | Text output listing common methods on the db object.                                                                        | `show collections` | Print a list of all collections for the current database                                          |
| `db.users.help()`        | Shows help for database methods.                                                                                            | `show users`       | Print a list of all users for the current database                                                |
| `db.<collection>.help()` | Show help on collection methods. The **collection** can be the name of an existing collection or a non-existing collection. | `show roles`       | Print a list of all roles, both user-defined and built-in, for the current database               |
| `show dbs`               | Print a list of all databases on the server.                                                                                | `show profile`     | Print the five most recent operations that took 1 ms. or more on databases with profiling enabled |
| `show databases`         | Print a list of all existing databases available to the current user.                                                       | `exit`             | Exit the mongosh session                                                                          |

---

## CRUD Operations

**CRUD** - Create Replace Update Delete

**Create Documents**

| Command                                                                                            | Description                                                                                                                       |
| -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `show dbs`                                                                                         | Shows all the available databases                                                                                                 |
| `bd`                                                                                               | Lists the currently active database                                                                                               |
| `use blog`                                                                                         | Creates and activates a database named **blog**. **Note** : In MongoDB, a database is not actually created until it is populated. |
| `db.collectionName.insertOne({att1 : "attr1", att2 : "attr2"})`                                    | Inserts single record into the collection. collectionName = name of the collection in the active database                         |
| `db.collectionName.insertMany({att1 : "attr1", att2 : "attr2"}, {att1 : "attr1", att2 : "attr2"})` | Inserts multiple records into the collection                                                                                      |

> Whenever a record is successfully entered into the collection, _"acknowledged : true"_ will be displayed along with ID for the entry. Each entry has an ID allotted to it unless custom ID is entered, like below :

```js
db.collectionName.insertOne({ _id: 4, att1: "attr1", att2: "attr2" });
```

**Update, Delete and Replace Documents**

| Command                                                                                                | Description                                                                                   |
| ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| `db.students.updateOne({major:"Biology"}, {$set: {major:"BioScience"}})`                               | Updates only one record no matter how many records exist with same value for the chosen field |
| `db.students.updateMany({gpa:3.5}, {$set:{gpa:3.1}})`                                                  | Updates all records matching the field value                                                  |
| `db.posts.updateMany({}, { $inc: {likes:1} })`                                                         | Updates all the records of collection posts, by incrementing likes field by 1                 |
| `db.students.replaceOne({major : "BioScience"}, {major : "Gender Studies", gpa : 3.2, name : "Eric"})` | Replaces a documents values with others (major category from BioScience to Gender Studies)    |
| `db.students.deleteOne({gpa : {$lte : 3.2}})`                                                          | Deleting only one record using the criteria (gpa <= 3.2)                                      |

**Query Commands**

| Syntax                                                                       | Description                                                                                                                           |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `db.collectionName.find({})`                                                 | Returns all records                                                                                                                   |
| `db.collectionName.find({}, {_id : 0})`                                      | Returns everything except \_id field                                                                                                  |
| `db.collectionName.find({}, {_id : 0}).limit(3)`                             | Returns everything except \_id field but limits records to 3                                                                          |
| `db.collectionName.find({}, {_id : 0}).skip(2).limit(3)`                     | Returns everything except \_id field but skips 2 records & limits records to 3                                                        |
| `db.students.find({}, {_id: 0}).sort({gpa : -1, name : 1})`                  | Returns records and sorts them first by gpa in desc (-1) and by name                                                                  |
| `db.students.find({major : "Biology"}, {_id: 0})`                            | Filters the records by major, in this case that would be Biology                                                                      |
| `db.students.find({$or: [{major : "Medicine"}, {name : "Jack"}]}, {_id: 0})` | Returns records which either have major as Medicine or have name as Jack (OR Condition)                                               |
| `db.students.find({gpa : {$gt: 3.0}}, {_id: 0})`                             | Returns records where gpa is greater than ($gt ; $lt for less than) 3.0                                                               |
| `db.students.find({gpa : {$lte: 3.5}}, {_id: 0})`                            | Returns records where gpa is less than or equal to 3.5                                                                                |
| `db.students.find({name: {$in: ['Mike', 'Pike']}}, {_id:0})`                 | Returns records that match any of the names in the list ($in:)                                                                        |
| `db.students.find({awards:{$exists: true}}, {_id:0})`                        | Returns all records for which the entry for awards field exists. Boolean True/False                                                   |
| `db.students.find({name:{$type : 2}}, {_id:0})`                              | Returns all records where the name field is of data type 2 (string) **Note** : MongoDB databases have various datatypes of same field |
| `db.students.find({"grades.0": 90}, {_id:0})`                                | Returns all records where the grades field has its first element(index : 0) equal to 90                                               |
| `db.students.find({grades: {$elemMatch: {\$gte: 90}}}, {_id:0})`             | Returns all records where the grades field has any of its elements grater than or equal to 90                                         |
| `db.students.find({grades : {$size : 4}}, {_id:0})`                          | Returns records where the No. of elements in the grades field = 4                                                                     |

**Upsert Documents**

**Upsert** : Updates a document, but if the entry is not found, inserts it.

```js
db.posts.updateOne(
  { title: "Post Title 5" },
  {
    $set: {
      title: "Post Title 5",
      body: "Body of post.",
      category: "Event",
      likes: 5,
      tags: ["news", "events"],
      date: Date(),
    },
  },
  { upsert: true }
);
```

---

## MongoDB Operators

**Comparison Operators**

| Sign   | Description                      |
| ------ | -------------------------------- |
| `$ne`  | Not Equal to                     |
| `$eq`  | Equal to                         |
| `$gt`  | Greater Than                     |
| `$lt`  | Less Than                        |
| `$gte` | Greater Than or equal to         |
| `$lte` | Less Than or Equal to            |
| `$in`  | Value is matched within an array |

**Logical Operators**

| Sign   | Description                                        |
| ------ | -------------------------------------------------- |
| `$and` | Returns documents where both queries match         |
| `$or`  | Returns documents where either query matches       |
| `$nor` | Returns documents where both queries fail to match |
| `$not` | Returns documents where the query does not match   |

**Evaluation Operators**

| Sign     | Description                                                        |
| -------- | ------------------------------------------------------------------ |
| `$regex` | Allows the use of regular expressions when evaluating field values |
| `$text`  | Performs a text search                                             |
| `$where` | Uses a JavaScript expression to match documents                    |

**Update Operators**

| Sign           | Description                              |
| -------------- | ---------------------------------------- |
| `$currentDate` | Sets the field value to the current date |
| `$inc`         | Increments the field value               |
| `$rename`      | Renames the field                        |
| `$set`         | Sets the value of the field              |
| `$unset`       | Removes the field from the document      |

**Array Operators**

| Sign        | Description                                             |
| ----------- | ------------------------------------------------------- |
| `$addToSet` | Adds distinct elements to an array                      |
| `$pop`      | Removes the first or last element of an array           |
| `$pull`     | Removes all elements from an array that match the query |
| `$push`     | Adds an element to an array                             |

---

## DataTypes In MongoDB

```bson
{
    string : "Text String",
    int : 420,
    double : 3.654,
    boolean : True, // False
    array : [1, 2, 3],
    object : {att1 : "attr1", att2 : "attr2", att3 : "attr3" },
    date : new Date("<YYYY-mm-dd>"),
    object_id : <ObjectId>
    no_value : null

}
```

**Additional Datatypes**

```bson
    Timestamp
    Binary data
    Regular expressions
    JS Code
```

---

## BSON Data Identifiers

| Type                       | Number | Alias                 | Notes                      |
| -------------------------- | ------ | --------------------- | -------------------------- |
| Double                     | 1      | "double"              |                            |
| String                     | 2      | "string"              |                            |
| Object                     | 3      | "object"              |                            |
| Array                      | 4      | "array"               |                            |
| Binary data                | 5      | "binData"             |                            |
| _Undefined_                | 6      | "undefined"           | Deprecated.                |
| ObjectId                   | 7      | "objectId"            |                            |
| Boolean                    | 8      | "bool"                |                            |
| Date                       | 9      | "date"                |                            |
| Null                       | 10     | "null"                |                            |
| Regular Expression         | 11     | "regex"               |                            |
| DBPointer                  | 12     | "dbPointer"           | Deprecated.                |
| JavaScript                 | 13     | "javascript"          |                            |
| Symbol                     | 14     | "symbol"              | Deprecated.                |
| JavaScript code with scope | 15     | "javascriptWithScope" | Deprecated in MongoDB 4.4. |
| 32-bit integer             | 16     | "int"                 |                            |
| Timestamp                  | 17     | "timestamp"           |                            |
| 64-bit integer             | 18     | "long"                |                            |
| Decimal128                 | 19     | "decimal"             |                            |
| Min key                    | -1     | "minKey"              |                            |
| Max key                    | 127    | "maxKey"              |                            |

---
