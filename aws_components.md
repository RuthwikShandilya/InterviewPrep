## Amazon Red shift

Amazon redshift is a petabyte scale ddata warehoue
uses columner stoage format
massive parallel processing (MPP) and automatic distributin to give high performance analytics

AWS REdshift Architecture 

It has one leader node and multiple compute nodes and when ever it receives a query it processes it parallely

How is it faster
 Columnar storage allows only required columns to be brought and also makes analytics faster
 also can read data from s3 directly 

 Sort and Distributed keys 
 sort defines how data is stored in the database to optimize query performace 
 and distributed keys is how it is distrubted across nodes

 COPY command from s3 

 Vaccum in redshift 

 if delete there are marked for deletion if we vaccum 
 1. Reclaim the disk space
 2. reindxes
 3. Sorts the data

4 types of VACCUM commands 

1. VACCUM FULL
2. VACUM DELETE
3. VACCUM SORT
4. VACCUM REINDEX

Concurrency scaling is basically adding new compute nodes to handle query load
