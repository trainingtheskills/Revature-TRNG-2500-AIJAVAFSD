1. What is MongoDB, and how is it different from a relational database?
MongoDB is a document-oriented NoSQL database. It stores data as flexible, JSON-like documents in collections, not as rows in fixed tables. You don't need a predefined schema, related data can be stored together in one document, and it scales out across servers with sharding.

2. When would you choose MongoDB over SQL, and when not?
MongoDB is a good fit for evolving or semi-structured data, nested objects, high write volumes and fast iteration. Examples are product catalogues, user profiles, IoT data and content. SQL is better when the data is highly structured, needs complex multi-table joins and heavy reporting, or has strict relational integrity rules such as core banking ledgers.

3. What are the four types of NoSQL databases? Give an example of each.

Document: MongoDB
Key-value: Redis
Wide-column: Cassandra
Graph: Neo4j

4. What is BSON, and why does MongoDB use it instead of JSON?
BSON is a binary encoding of JSON. It supports more types than JSON, such as Date, Int32/Int64, Decimal128, ObjectId and binary data. It is also faster to scan, because each element stores its length, and it encodes numbers efficiently.

5. What is an ObjectId, and what is it made of?
It's the default 12-byte _id value, shown as 24 hex characters. It has a 4-byte timestamp, a 5-byte random value (unique per machine and process) and a 3-byte counter. Because the timestamp comes first, ObjectIds sort roughly by creation time, and getTimestamp() returns when the document was created.

6. Embedding vs referencing: how do you decide?
Data that is read together should be stored together. Embed when the child belongs to one parent, is usually read with it, and stays small, such as a user's addresses. Reference when the data is shared (many-to-many), read on its own, or could grow without limit, such as an order's products or a post's comments. Remember the 16 MB document limit.

7. What's the difference between find() and findOne()?
find() returns a cursor over every matching document, and you can chain .sort(), .limit() and .skip() onto it. findOne() returns only the first matching document, or null if nothing matches.

8. What's the difference between updateOne() with $set and replaceOne()? What is an upsert?
$set changes only the fields you name and leaves the rest of the document alone. replaceOne() swaps the whole document for a new one; only _id stays. An upsert ({ upsert: true }) updates the document if it exists and inserts it if it doesn't.

9. Write a query for CS students with marks above 85, or any student in the EE course.

javascript
db.students.find({
  $or: [
    { course: "CS", marks: { $gt: 85 } },
    { course: "EE" }
  ]
})

Conditions side by side in one object are combined with AND, and $or takes an array of conditions.

10. How do you make a slow query faster, and how do you confirm it worked?
Create an index on the fields you filter and sort by, for example db.students.createIndex({ course: 1, marks: -1 }). Then run .explain("executionStats") on the query: IXSCAN means the index is being used, and COLLSCAN means a full collection scan. Also compare totalDocsExamined with nReturned; the closer they are, the better.
