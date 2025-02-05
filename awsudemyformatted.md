# AWS Fundamentals

## Types of Data
1. **Structured Data** - Easily queriable, organized columns, cleanup already (PostgreSQL, Oracle, CSV, and Excel if structured).
2. **Unstructured Data** - Doesn't have a predefined schema, raw text files, videos, audio, emails.
3. **Semi-Structured Data** - XML and JSON.

## Properties of Data
1. **Volume** - Size of data.
2. **Velocity** - Speed at which new data is generated, collected, processed (batch vs. streaming).
3. **Variety** - Types of data (structured vs. semi-structured), source of data, format of data.

## Data Warehouse vs. Data Lake

### Data Warehouse (Extract, Transform, and then Load to Data Warehouse)
A centralized repository optimized for analysis where data from different sources is stored in a structured format.
- Designed for analysis.
- Optimized for read-heavy operations.

**Examples**: Amazon Redshift, Google BigQuery, Azure SQL Data Warehouse.

### Data Lake (Extract, Load, and then Transform when needed)
Do not preprocess, just store all the data in a data lake.

**Examples**: Amazon S3, HDFS.

**Which to choose?**
- **Data Warehouse**: When you have structured data and want to use it for analytics.
- **Data Lake**: When you need raw data for machine learning.

## Data Lakehouse: Combining Data Warehouse and Data Lake

## Data Lineage
### Spline Agent
Stores it in a graph database called **Amazon Neptune**.

## Schema Evolution:
AWS Glue Registry has **backward compatibility**.

### SageMaker

## Database Optimizations:
- **Adding Indexes**
- **Partitioning**
- **Compression**: Use better file formats, also compression techniques (GZIP, LZOP, etc.)

## Data Sampling Techniques:
1. **Random Sampling**
2. **Stratified Sampling**
3. **Systematic Sampling** (e.g., every third record)

## Data Skewing
**Temporal Skew** - Old data has less volume, while new data in the same partition can be huge.

### How do you partition?
1. **Adaptive Partitioning**
2. **Salting**
3. **Regular Repartitioning** (not recommended)
4. **Sampling**
5. **Custom Partitioning**

## AWS S3
1. **S3 bucket names are unique across the globe**.

### Naming Conventions:
- No uppercase, no underscores, no IP addresses.
- Must start with a lowercase letter.
- Must not start with `xn--`.
- Must not end with `-s3alias`.

**Key** is basically the full path of the file without the S3 bucket name.

Example:
```
s3://<bucketname>/folder1/subfolder1/myfile.txt
```
Here, the key is `/folder1/subfolder1/myfile.txt`.
**Value** is the content of the file.

- **Max size**: 5TB.
- If a file is more than 5GB, use **multi-part upload** to upload files.

### Amazon S3 Security
1. **User-based security**
   - IAM policies: Which specific user should be allowed from IAM.
2. **Resource-based security**
   - Bucket-wide policies.
   - Object ACLs (Access Control Lists).
   - Bucket ACLs.
3. **Encrypt objects on S3 using encryption keys**.

### S3 JSON Example:
AWS has a **policy generator** in the console to generate policies.

### S3 Versioning
Used to **protect from unintended deletes** and allows rolling back to a previous version.
- **Enabled at the bucket level**.
- When a file is deleted with versioning enabled, a **delete marker** is added.
- To restore deleted files, **delete the delete marker**.

### S3 Replication
- **Versioning must be enabled** in both source and target buckets.
- **By default, delete markers are not replicated**, but this can be changed in replication rules.
- **If you delete a source object, it is not replicated in the target bucket**.

Types:
- **CRR (Cross-Region Replication)**
- **SRR (Same-Region Replication)**

### S3 Storage Classes
1. **Amazon S3 Standard - General Purpose**
2. **Amazon S3 Standard - Infrequent Access (IA)**
3. **Amazon S3 One Zone - Infrequent Access**
4. **Amazon S3 Glacier Instant Retrieval**
5. **Amazon S3 Glacier Flexible Retrieval**
6. **Amazon S3 Glacier Deep Archive**
7. **Amazon S3 Intelligent Tiering**

**Durability & Availability:**
- Durability: **99.999999999% (11 nines)**
- Availability depends on storage class.

## DynamoDB
A **NoSQL database** that **scales horizontally**.
- Supports **millions of requests per second**.
- Each item can have up to **400KB of data**.

**Other NoSQL databases**: MongoDB

### Primary Keys in DynamoDB
- **Partition Key** (Must be unique for each item).
- **Partition Key + Sort Key** = **Composite Primary Key**.
  
Example:
```
(User_id, game_id) → PK, Score, Result
```

### Creating a DynamoDB Table
- **Select Partition Key**.
- **Select Table Class** (DynamoDB Standard or DynamoDB Standard-IA).

### Read and Write Capacity Modes
1. **Provisioned Mode** (Default)
2. **On-Demand Mode** (Expensive but automatically scales reads/writes)

### Burst Capacity
- Temporarily increases read/write capacity.
- If exceeded, results in **ProvisionedThroughputExceededException** → Need **exponential backoff** retries.

### Read Capacity Units (RCU)
1 RCU = **One strongly consistent read OR Two eventually consistent reads per second for a 4KB item**.

### Write Capacity Units (WCU)
WCU = (Number of writes per second) * CEIL(item size/1KB)

### DynamoDB Partitions

### DynamoDB API Calls
- **PutItem**: Create or update all attributes.
- **UpdateItem**: Update attributes.
- **ConditionalWrites**.
- **GetItem**: Retrieve specific attributes using a projection expression.
- **Query**: Use conditions (>=, <=, between, begins).
- **Filter Expression**: For non-key attributes.
- **BatchWriteItem**: Supports **up to 25 PutItem/DeleteItem operations**.
- **BatchGetItem**: Fetch **up to 100 items or 16MB of data**.

### DynamoDB PartiQL
- **Cannot perform joins**.

### DynamoDB Indexes
- **LSI (Local Secondary Index)**: Additional sort key (must be defined at table creation, max 5 LSIs).
- **GSI (Global Secondary Index)**: Can be created/modified later (speeds up non-key attribute queries).

- **If writes are throttled on GSI, the main table will also be throttled**.
- **For LSI, the main table RCUs are used**.

### DynamoDB TTL (Time To Live)
- **Default TTL is 5 minutes**.

## Elasticache
Used to store **aggregated data** instead of querying the database every time.

---

Let me know if you need any modifications! 🚀
