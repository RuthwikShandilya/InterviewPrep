#40 Real Data Architect Interview Questions & Answers - Part I
### How do you improve Data Architecture:
  1. If the data is dealing with bad data issues. We need to revist validation processes that we have and establish them if we dont have.Simple validation checks like NOT NULL constraints.Data cleaning
     filling bad values with mean and mode values.Also checking the timestampz values.
  2. Not able to gettimely data => consider having streming approches.or use checkpoining approach
###how to choose Datalake vs Data warehouse
We choose datalakes when we are dealing with semi structured and unstrutured data mostly and there is no clear defined use case.When speed to innovate is crucial we use Data lakes
We choose data warehouse when the use case of the data is defined and is strutured also when data goverance is very important we use data warehouses.

### Different types of datastores used
Datastore is basically where we store data and based on the complexity how are we dfining and storing this data:

Relational Databases: Store structured data (e.g., MySQL, PostgreSQL).
NoSQL Databases: Handle semi-structured or unstructured data (e.g., MongoDB, DynamoDB).
File Systems: Manage data in file formats (e.g., NTFS, HDFS).
Cloud Object Storage: Store large amounts of unstructured data (e.g., AWS S3, Google Cloud Storage).
In-Memory Datastores: Provide ultra-fast access (e.g., Redis, Memcached).

### how do you choose a relational vs non relational DB
We choose relational db when struture is important and data integrity and consistency is important
we choose non relational (nosql) db when scalability is a factor and dealing with semistrutured and unstrutured data

### where do you use an index and where does it fail

Use index on the columns we are doing a joins 

### How do you improve Database performance

First max_connections

### datalake house 
=> datalake and dataarehouse



















