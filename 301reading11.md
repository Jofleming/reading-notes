# Readings: Mongo and Mongoose

## nosql vs sql


Questions:
What kind of data is a good fit for an SQL database?
For complex queries


What kind of data is a good fit a NoSQL database?
Hierarchical data storage. Or for large data sets.


Which type of database is best for hierarchical data storage?
NoSQL.

Which type of database is best for scalability?
Depends. SQL is better for virtical scalability (increasing CPU, RAM, SSD, etc) for a single server, NoSQL is horizontally scalable (adding more servers to share the load).


## sql vs nosql video


Questions:
What does SQL stand for?
Structured Query Language. Database queries generally look like: 
`SELECT id, name, price FROM products`
capitals are SQL syntax/keywords, the others are data/parameters.

What is a realational database?
A database that supports the SQL lanaguage and makes certain assumptions.

What type of structure does a relational database work with?
It works with tables.

What is a ‘schema’?
A plan or outline. 

What is a NoSQL database?
Non-tabular database that stores data differently than relational tables.

How does it work?
It uses 'collections'. They don't have to follow a given schema.

What is inside of a Mongo database?
Collections.

Which is more flexible - SQL or MongoDB? and why.
MongoDB is more flexible since it is not tied to a specific schema. You can also do horizontal scaling with noSQL.

What is the disadvantage of a NoSQL database?
You can easily have duplicate data.


[Back](README.md)