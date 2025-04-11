#Data warehousing Concepts

## Fact and Dimension Table

###Dimension tables
Dimension tables have the information about each individual metric like customer information and product information as seprate tables.

### Fact tables

 A fact table is a table that stores the measurements, metrics, or facts related to a business operation. 
Fact tables contain all the keys from the dimnesion table to make the complete sense of the data example a transaction table with customer id and product id with transaction date.
This contains foreign keys from the dimension tables.

Source : https://medium.com/@changuru2023/types-of-fact-tables-data-warehouse-cec3cfaa2efe

#### Types of Fact Tables :
We have 4 types of fact tables : 
1. Transactional Fact tables:
   This type of fact table is used to store business events like transactions where each reocrd is an event.Analysis can be performed on the basic of this records in terms of aggregations.This is used for Customer behaviour,sales patterns and operational efficiency
2. Periodic Snapshot Fact Tables:
Peridic Snap shot tables is used to aggregate values based on data and store  summarized view of the data based on redulat time intervals example month etc
This is used to monitor trends ,performance and make decisions.
3. Accumulating Snapshot Fact Tables :
This kind of fact tables is used to tract the business or a flow like an order status based on order id.Mostly used for process efficiency and identifying bottlenecks in process and optimize supply chain performance.
4. Fact less fact tables
   here the tables dont have any columns which are measures these just have foreign keys from other dimension tables.


First we define dimension tables and then we define fact tables
#### We have a concept of late coming dimension or early arriving fact:
Here having records in few dimension tables but not all then it fact table it might give us an foreign key error.
Example a employee who has not been assigned a team where we have employee and team tables and we have 4 wasy to handle this:

1. Dont process this record
2. I will park the record in some landing table and process it when we have the record in dimension table
3. dummy value
4. INsert a  value in dimension table and update it when we get the correct dimension data


Example:
Transaction table is a fact table containing customer and product ids in it 
Customer table is a dimension table containing customer details location,address,dateof birth and all
Product table is a dimension table containing produt name and description and cost probably


## Slowly Changing Dimension
Where the dimension table is slowly changing and it can be dealt in multiple ways: 
Type 0
No changes in the dimension table
Type 1
1. Just update the current record without any history information example country table just update USA to United States
type 2
3. Here we will have more information by having when it was changed and who changed it has from_date and to_date in the dimension table
type 3
4. Here we have two columns previous and cufrrent value for the table with type 2 tables from_date and to_Date
type 4
more cleaner approach the main dimension table will have just an update on the table we will also have a history dimention table which has an update and an insert 
   

## DataWarehouse vs DataLake vs Database
A database is basically used to record transactions(OLTP) where as warehouse the datawarehouse for analytical (OLAP).Data comes into datawarehouses from multiple databasese usually though an ETL job.

Datawarehouse is designed to just query large amount of data it wount have as amy as updtes as a typical databas

### DataLake 
Data lake is used to store structued unstructured files videos can store any type of data.

## Partition Pruning and Other Concepts 
Spark has this done in Logical plan level
Static Pruning 
Without pruning the partition the read will happen first and then the filter will happen in Spark.
With pruning then then the filter will apply first and then read.This is also called predicate pushdown

Dynamic Pruning 
When we are trying to join multiple tables and has a partition on one of the table the partition pruning applies on the other table to reduce the total scan on all the tables.
It does an broadcase hash join on the fact table when the dimenson table is small
