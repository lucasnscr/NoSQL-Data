# NoSQL Data Structure and Cap Theorem
Repository focused in explain structure of data like, theorem CAP and Scalability

**NoSQL** databases are a class of persistence technology that provide a new storage mechanism that goes hand in hand with normalization and relational databases. Like any other database, it has the same objectives: inserting, updating, retrieving and deleting information, however, with new modeling concepts and storage structure.

The term NoSQL, initially, was related to "not SQL" and later it was controlled to Not Only SQL, that is, "not just SQL", opening the concept of polyglot awareness (the work of dealing with different types of databases to reach the objectives in the application).

These databases have speed and high scalability rates as their main characteristics, such as the ease of increasing the number of database servers. This prevents the bottleneck of operations, avoids a point of failure, in addition to geographically distributing them, making the data closer to the users who respond to the request.

NoSQL databases are being adopted more frequently in different types of applications, including financial institutions. As a consequence, the number of suppliers for this type of database is also growing.

Currently, NoSQL databases are classified into four groups (key-value, column family, document and graphs) defined by their storage model:


## Key Value


![key-value description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c2ydlimhxtibtmxcwqw2.png)

The key-value databases have a structure similar to java.util.Map , that is, the information will be retrieved only by the key. This type of database can be used, for example, to manage the user's session. Another interesting case is DNS, whose key is the address, for example www.google.com , and the value is the IP of that server.

Currently, there are several key-value database implementations, among which the most famous are:

- Redis
- Amazon DynamoDB
- Amazon S3

Comparing the relational database with the key-value type, it is possible to perceive some points. One is that the key-value structure is quite simple.

It is not possible to perform operations such as joining between buckets and the value is composed of a large block of information instead of being subdivided into columns as in the database relational.

| Relational Database       | Key-Value Database |
| ----------- | ----------- |
| Table       | Bucket      |
| Row         | Key/Value   |
| Column      | Not supported        |
| Relationship | Not supported        |



## Column Database


![Column description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ayrcxyuuuwqfk2kj3rub.png)

This model became popular through **Google's BigTable** paper, with the aim of setting up a distributed data storage system, and designed to have a high degree of scalability and data volume. Just like the key-value, to perform a search or retrieve some information within the database, it is necessary to use the field that works as a unique identifier that would be similar to the key in the key-value structure. However, the similarities end there. Information is grouped into columns: a unit of information that is made up of the name and the information itself.

These types of databases are important when dealing with a high degree of data volume, such that information needs to be distributed across multiple servers. But it is worth mentioning that its reading operation is quite limited, similar to the key-value, since the search for information is defined from a single field or a key. There are several databases that use these structures, for example:

- Hbase 
- Cassandra 
- Scylla

Among the types of column family type databases, Apache Cassandra is the most famous. Thus, if an application needs to deal with a large volume of data and with easy scalability, Cassandra is certainly a good option.

By contrasting the column family type database with relational databases, it is possible to notice that operations, in general, are much faster. It is simpler to work with large volumes of information and servers distributed all over the world, however, this comes at a cost: the reading of this type of database is very limited.

For example, it is not possible to perform unions between column families as in the relational database. The column family allows you to have an unlimited number of columns, which in turn are composed of name and information, exactly as shown in the following table:

| Relational Database       | Column Database |
| ----------- | ----------- |
| Table       | Column Family      |
| Row         | Column   |
| Column      | Name and Value to Column        |
| Relationship | Not supported        |



## Document Database


![Document description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lhxhnff15bos36f8tt9l.png)

Document-oriented databases are very similar in structure to a JSON or XML file. They are composed of a large number of fields, which are created at runtime, generating great flexibility, both for reading and writing information. They allow the reading of information by fields other than the key. 

Some implementations, for example, have very high integration with search engines. Thus, this type of database is crucial when performing data analysis or system logs. There are a few implementations of document-type databases, the most famous of which is MongoDB.

When comparing with a relational database, although it is possible to perform a search for fields other than the unique identifier, document-type databases do not support relationships. Another point is that document-type banks, in general, are schemaless.

| Relational Database       | Document Database |
| ----------- | ----------- |
| Table       | Collection      |
| Row         | Document   |
| Column      | Key/Value pair        |
| Relationship | Not supported        |



## Graphs Database

![Graphs description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wapq3o6uwvsj1sw71x93.png)

Graph databases are a data structure that connects a set of vertices through a set of edges. Modern databases in this category support **multi relational** graph structures, where there are different types of vertices (representing people, places, items) and different types of edges. The recommendation systems that take place on social networks are the biggest case for the graph-type bank. Of the most famous database types in the NoSQL world, the graph has a distinct structure with the relational one.

- Neo4j
- HyperGraphDB

| Relational Database       | Document Database |
| ----------- | ----------- |
| Table       | Collection      |
| Row         | Document   |
| Column      | Key/Value pair        |
| Relationship | Not supported        |

## Cap Theorem


![Cap description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rl7nx96useccd1chb05v.png)

One of the great challenges of NoSQL databases is that they deal with distributed persistence, that is, the information is located on more than one server. Several studies have been created to help with this distributed persistence challenge, the most famous being a theory created in 1999, the CAP Theorem.

This theorem states that it is impossible for distributed data storage to simultaneously provide more than two of the following three guarantees:

**Consistency**: A guarantee that every node in a distributed cluster returns the same most recent and successful write. Consistency refers to each customer having the same view of the data. 

**Availability**: each request receives a response (no error) - no guarantee that it contains the most recent write.

**Partition tolerance**: The system continues to function and maintain its consistency guarantees despite network partitions. Distributed systems that guarantee tolerance continue to operate even if there is a failure in one of the nodes, since there is at least one node to operate the same job and guarantee the functioning of the system.

In general, this theorem explains that there is no perfect world. When you choose one characteristic, you lose another as a consequence. In an ideal world, a distributed database would be able to support all three features, but in reality, it is important for the developer to know what he will be missing out on when choosing between one or the other.
