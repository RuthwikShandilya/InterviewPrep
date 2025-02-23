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
