# MongoDB Cheatsheet

|                              COMMANDS |                               THEIR USES |
| --- | --- |
| `show dbs` | To show the databases |
| `use database-name` | To create a new database |
| `db.dropDatabase()` | To delete the database |
| `show collections` | To show the collections in the database |
| `db.createCollection('collection-name’)` | To create a new collection in a database |
| `db.collection-name.drop()` | To delete a collection in a database |
| `db.collection-name.insertOne({ field1:value1,field2: value2,...});` | To insert data in a collection |
| `db.collection-name.insertMany([{ field1: value1, field2: value2, ... },{ field1: value1, field2: value2, ... }])` | To insert many data of objects in to a collection |
| `db.collection-name.insertMany([ doc1, doc2, ... ]);` | This command inserts multiple documents into a specified collection. By default, the ordered option is true i.e. Data before error will be added rest would not be added |
| `db.collection-name.insertMany([ doc1, doc2, ... ], { ordered: false });` | inserts multiple documents into a specified collection but with the ordered option set to false i.e. Data  will be added except the error data |
| `db.collection_name.find({ key: value })` | To find all documents in a collection that match the specified condition |
| `db.collection_name.findOne({ key: value })`| To find a single document in a collection that matches the specified condition |
| `mongoimport Yourjsonfile.json –d database_name –c collection_name` | To import data in your  specified collection  & database in MongoDb |
| `mongoimport Yourfile.json -d <Database-name> -c collection_name --jsonArray` | To import data in your  specified collection  & database in MongoDb as Array document |
| `mongoexport -d database -c collection-name -o <your-directory- where- you-want-to-save-file>` | To export the data from mongo DB to your local machine |
| `db.collection-name.find({ ‘fieldname’ : {$Operator : value}}) comparison operators - $eq , $ne, $gt, $gte, $lt, $lte, $in , $nin` | To find any field using comparison operators |
| `db.collection-name.find({ ‘fieldname’ : {$Operator : value}}).count();` | To find quantity of that field using cursor Method |
| `db.collection-name.find({ ‘fieldname’ : {$Operator : value}}).limit();` | To find specified no. of data of that field using cursor Method |
| `db.collection-name.find({ ‘fieldname’ : {$Operator : value}}).limit().skip();` | To find specified no. of data while skipping some content of that field using cursor Method |
| `db.collection-name.find({ ‘fieldname’ : {$Operator : value}}).sort();` | To sort out field using cursor Method |
| `{$and : [{condition 1}, {condition 2}] }        logical operators -  $and , $or , $not , $nor` | To find the data with an condition logical operator |
| `{ $expr: { operator: [field, value] } }` | To perform query operations using aggregation expressions. |
| `{ field: { $exists: <boolean>} }` | This checks for the existence of a field. If <boolean> is true, it matches documents that contain the field. If false, it matches documents that do not contain the field. |
| `{ field: { $type: "bson-data-type"  }}`| This matches documents where the field is of the specified BSON data type. |
| `{ field: { $size: array-length } }` | This matches documents where the field is an array with the specified length. |
| `db.collection.find({},{field1 :1 , field2 : 1})` | This retrieves documents from the specified collection and projects only field1 and field2 (1 means include the field, 0 means exclude the field). |
| `db.collection.find({"Parent.child" : value})` | This queries for documents where the nested field child under Parent is equal to value. |
| `{ field: { $all: [ value1 , value2 ... ] } }` | This matches documents where the array field contains all the specified values. |
| `{ field: { $elemMatch: { query1, query2, ... } } }` | This matches documents where at least one element in the array field matches all the specified queries. |
| `db.collectionName.updateOne({filter},{$set : {existingField : newValue},{newField : newValue}})` | Updates a single document in the collection that matches the filter criteria. Sets the value of existingField to newValue and adds a new field newField with newValue. |
| `db.collectionName.updateMany({filter},{$set : {existingField : newValue} })` | Updates multiple documents that match the filter criteria. Sets the value of existingField to newValue in all matching documents. |
| `db.collectionName.updateOne({filter},{ $unset: { fieldName: 1 } });` | Updates a single document by removing fieldName. |
| `db.collectionName.updateOne( {filter}, { $rename: { OldfieldName: "NewfieldName" } });` | Updates a single document by renaming OldfieldName to NewfieldName. |
| `db.collectionName.updateOne({ filter },{ $push: { arrayField: "new element" } });` | Updates a single document by adding a new element to the array arrayField. |
| `db.collectionName.updateOne({ filter },{ $pop: { arrayField: value } });` | Updates a single document by removing the first (value: -1) or last (value: 1) element of the array arrayField. |
| `db.collectionName.updateOne({ filter },{ set: { "arrayField.$.text": "Updated text" } });` | Updates a single element within an array arrayField that matches the filter criteria. Sets text to "Updated text" for the matched array element. |
| `db.collectionName.deleteOne({ filter });` | Deletes a single document that matches the filter criteria. |
| `db.collectionName.deleteMany({ filter });` | Deletes all documents that match the filter criteria. |
| `db.collectionName.find({ condition }).explain();` | Returns information on the query plan and execution statistics for the find operation, with a default verbosity of "queryPlanner" |
| `db.collectionName.find({ condition }).explain("executionStats");` | Returns detailed execution statistics for the find operation, including the query plan. |
| `db.collection.createIndex({ field: 1 });` | Creates an ascending index on field in the collection.|
| `db.collection.getIndexes();` | Returns a list of all indexes on the collection. |
| `db.collection.dropIndex({ field: 1 });` | Drops the index on field in the collection. |
| `db.collection.dropIndex(“index_name”);` | Drops the index with the specified name. |
| `db.collection.createIndex({ field: 1 }, { unique: true });` | Creates a unique index on field, ensuring all values in the field are unique. |
| `db.collection.createIndex({ field: "text" });` | Creates a text index on the field to support text search operations. |
| `db.collection.find({ $text: { $search: "keyword" } });` | Searches for documents that contain the specified keyword using a text index. |
| `db.collectionName.aggregate([ {$match : {<query>}}]);` | Filters documents in the aggregation pipeline to only those that match the query criteria. |
| `db.collectionName.aggregate([{ $group: { _id: { expression }, field1: { accumulator1 : expression1 }}} ]);` | Groups documents by a specified _id expression and applies accumulator operations (like sum, avg, etc.) on the grouped documents. |
| `db.collectionName.aggregate([{ $sort: { field: order } }]);` | Sorts documents in the aggregation pipeline by field in the specified order (1 for ascending, -1 for descending). |
| `db.collectionName.aggregate([{ $project: { field: expression1 , ... } } ]);` | Reshapes documents in the aggregation pipeline by including, excluding, or adding new fields. |
| `db.collectionName.aggregate([{ $push: { expression } } ]);` | Adds an expression to an array field in the aggregation pipeline. Typically used within $group. |
| `db.collectionName.aggregate([{  $unwind: array } ]);` | Deconstructs an array field from the input documents to output a document for each element. |
| `db.collectionName.aggregate([{ $addToSet: { field1: value1, ... } } ]);` | Adds a value to an array only if it does not already exist in the array. Used within $group. |
| `db.collectionName.aggregate([ { $size: array }]);` | Returns the number of elements in an array. |
| `db.collectionName.aggregate([ { $skip: positive value }, { $limit: positive value } ]);` | Skips a specified number of documents and limits the number of documents passed to the next stage in the pipeline. |
| `db.collectionName.aggregate([{$filter:{ input: array, as: string,  cond: expression,limit: number expression }}]);` | Filters an array to return only elements that match the specified condition (cond). Optionally limits the number of matching elements. |

Note - for $in operator write value in array form in the command
