#Data warehousing Concepts

## Fact and Dimension Table

###Dimension tables
Dimension tables have the information about each individual metric like customer information and product information as seprate tables.

### Fact tables

 A fact table is a table that stores the measurements, metrics, or facts related to a business operation. 
Fact tables contain all the keys from the dimnesion table to make the complete sense of the data example a transaction table with customer id and product id with transaction date.
This contains foreign keys from the dimension tables.

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
