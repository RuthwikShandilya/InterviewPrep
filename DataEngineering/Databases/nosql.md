#NOSQL 

### sql vs nosql 
1. Relational vs non relational
2. Vertical scaling vs horizontal scaling
   basically i can have more non relational to handle usage using load balancers probably
3. always tables schemas and relatinal ships vs based on documnets keyvale hashes
4. transactions and all unstrocured in json

Four kinds of NOSQL 
5. A. Graph database
B. Key value calculation
C. Document oriented
D. Column view presentatio

## Redis 

We use redis as a nosql database to store out session token linked to tenant_ids 


CAP theorm in DBMS
CAP theroem is basiclly when ever there is a failure of node or a network partition then the system has to choose between consistency and Availability
If the system is consistent then it woont be available until the network error is fixed and if the system chooses Availability there may be some data inconsistencies


Consistency 


Availabilit 

Partition tolerence



Partitioning vs sharding 

Split large data into smaller managable chunks in a single system.

Types of partitioning 
1. Range
2. List
3. Hash

Sharding is also spliting large data into smaller chunks but across multiple system.


Bucketing 
--------------------------------------------
bucketing using a hashfucntion to seperate data into buckets and we define the number of buckets
