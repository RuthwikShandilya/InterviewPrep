## Storage Handlers 

Storage handlers allows systems to use other file formats and storage mechanisms which my not be native to hive like hdfs.
Storage handlers introduce a distinction between native and non-native tables. 
A native table is one which Hive knows how to manage and access without a storage handler; a non-native table is one which requires a storage handler.
Storage handlers are associated with a table when it is created via the new STORED BY clause, an alternative to the existing ROW FORMAT and STORED AS clause:


CREATE TABLE hbase_table_1(key int, value string)
STORED BY 'org.apache.hadoop.hive.hbase.HBaseStorageHandler'
WITH SERDEPROPERTIES (
"hbase.columns.mapping" = "cf:string",
"hbase.table.name" = "hbase_table_0"
);
examples : 
org.apache.hadoop.hive.hbase.HBaseStorageHandler
org.apache.iceberg.mr.hive.HiveIcebergStorageHandler
org.apache.hive.storage.jdbc.JdbcStorageHandler

ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
COLLECTION ITEMS TERMINATED BY '|'
MAP KEYS TERMINATED BY ':'
NULL DEFINED AS '\\N';

Here row format defines how the data is written and how the data can be read from the source as this can have diffetnt options 

ROW FORMAT SERDE
Serilizer and Deserializer 

DELIMITED is simple and effective for text-based formats with predictable delimiters.
SERDE is more powerful and flexible for complex or custom data formats.


## Small Files Issue 
When we have lot of small files this will increase the IO since the process has to read the file and process it and everything.We can optimize
this by using coalesce by reducing the number of parititions 


