# mongodb-crud

### Start mongodb server
start_mongo

### Connect to mongodb server
mongosh -u root -p XXXXXXXXXXXXXXXXX --authenticationDatabase admin local

### List databases
show dbs

### Create a database named training
use training

### Create a collection named mycollection in the database training
db.createCollection("languages")

### List collections
show collections

## Insert documents

### Insert documents into a collection
db.languages.insert({"name":"java","type":"object oriented"})
db.languages.insert({"name":"python","type":"general purpose"})
db.languages.insert({"name":"scala","type":"functional"})
db.languages.insert({"name":"c","type":"procedural"})
db.languages.insert({"name":"c++","type":"object oriented"})

## Read documents

### Count the number of documents in a collection
db.myCollection.countDocuments()

### List the first document in the collection.
db.languages.findOne()

### List all documents in the collection.
db.languages.find()

### List first 3 documents in the collection.
db.languages.find().limit(3)

### Query for “python” language.
db.languages.find({"name":"python"})

### Query for “object oriented” languages.
db.languages.find({"type":"object oriented"})

### List only specific fields.
Using a projection document you can specify what fields we wish to see or skip in the output.
This command lists all the documents with only name field in the output.
db.languages.find({},{"name":1})

### This command lists all the documents without the name field in the output.
db.languages.find({},{"name":0})

### This command lists all the “object oriented” languages with only “name” field in the output.
db.languages.find({"type":"object oriented"},{"name":1})

## Update documents
Update documents based on a criteria.
Add a field to all the documents.

### The ‘updateMany’ command is used to update documents in a mongodb collection, and it has the following generic syntax.
db.collection.updateMany({what documents to find},{$set:{what fields to set}})

### Here we are adding a field description with value programming language to all the documents.
db.languages.updateMany({},{$set:{"description":"programming language"}})

### Set the creater for python language.
db.languages.updateMany({"name":"python"},{$set:{"creator":"Guido van Rossum"}})

### Set a field named compiled with a value true for all the object oriented languages.
db.languages.updateMany({"type":"object oriented"},{$set:{"compiled":true}})

## Delete documents
Delete documents based on a criteria.

### Delete the scala language document.
db.languages.findOneAndDelete({"name":"scala"})

### Delete the object oriented languages.
db.languages.findOneAndDelete({"type":"object oriented"})

### Delete all the documents in a collection.
db.languages.deleteMany({})
    
### Disconnect from mongodb server
exit
