# Snowpipe 
Snow pipe is a continuous data Ingestion service which allows snowflake to automatically load files from cloud stoarage(s3|gcp|azure) into snow flake as soon as the file is added there.

Example :
Given a table created 

CREATE OR REPLACE TABLE orders (
    order_id INT,
    customer_name STRING,
    order_date DATE,
    total_amount FLOAT
);

create storage integration and give for stage
CREATE STORAGE INTEGRATION my_s3_integration
TYPE = EXTERNAL_STAGE
STORAGE_PROVIDER = 'S3'
ENABLED = TRUE
STORAGE_AWS_ROLE_ARN = '<your-iam-role-arn>'
STORAGE_ALLOWED_LOCATIONS = ('s3://your-bucket/path/');



CREATE OR REPLACE STAGE my_s3_stage
STORAGE_INTEGRATION = my_s3_integration
URL = 's3://my-bucket/my-folder/'
FILE_FORMAT = (TYPE = 'CSV' SKIP_HEADER = 1);


Now we create a stage 
CREATE OR REPLACE STAGE my_s3_stage 
URL = 's3://my-bucket/orders-data/'
CREDENTIALS = (AWS_KEY_ID='your-key' AWS_SECRET_KEY='your-secret')
FILE_FORMAT = (TYPE = 'CSV' FIELD_OPTIONALLY_ENCLOSED_BY='"' SKIP_HEADER=1);



CREATE OR REPLACE PIPE my_snowpipe 
AUTO_INGEST = TRUE
AS
COPY INTO orders 
FROM @my_s3_stage 
FILE_FORMAT = (TYPE = 'CSV');

ALTER PIPE my_snowpipe REFRESH;






















Tables 
1. Permanant : exists until explicitly dropped
2. Temporary
3. Transient
4. External

Views :
Standard 
materiralized 
Secure : both for standard materizled query definitioins are only visible to authorized users 

setting data_retention_timeperiood for permanent tables :

ALTER TABLE PERMANENT_TABLE SET DATA_RETENTION_TIME_IN_DAYS= 90;

udfs 
differnt languages of udfs 
external udfs 


Procedures:


Snowpark ....?

Tasks and Streams 

tasks can be linked to form a DAG

Start a task 
alter task minute_task resume;
pause a task :
alter task minute_Task suspend;

Crating dependencies between tasks (DAG):

create task T4 
WAREHOUSE=<>>
AFTER t2,t3
as 
  <<>>>



  Streams :

## VIrtual Warehouses 

Performance Optimization in Virtual Ware house


Resource Monitors 


Query Acceleration Service :
Query_ACCELERATION_ELIGIBLE_VIEW


Performance Optimizations in SQL :

Join operations 

when doing order by put a limit also 
also dont use multiple order by for different columns in the same query

Group BY




Cache

how to check query perfomrance in partitions 

Clustreing concepts
average_overlaps
averaagedepth


Search Optimization Service 

read about stages again


Snowpipe : 

create pipe <<pipe_name>>
AUTO_INGEST=true as 
copy into table from @mystage
file_format=(type=csv)


Estimation functions 
Table sampling





