1. You have a query which is running lot of time how do you optimize this.
Apart from adding cluster keys
partitioning the table in the right way
and using the same cache queries for better perfomance
Steps :
1. Check the query history page (you can generally apply filters based on time and other factors)
2. this gives compilation time vs execution time
3. from query history we can go to query profiler
4. profiler gives us infomration of how much percent each type of query took like
5. 1. processing
   2. local disk io
   3. remote disk io
   4. synchrnizsaation
   5. initialization
  most expensive node 
      and statistics of bytes and rows scanned

use order by properly when dealing with huge data and use limit where ever required
dont use order by inside a sub query when you have a order by outside query 
Use materialized views for data which needs to be computed once in a while 
single table no join 

sno flake maintains the clustering metadata for micropartitions 
total number of mp
no of overlapping micro partitions 
depth of overlapping micro partirions 
select system$clusteringinformation('table',(col1,col3))
the lower the better 
average_depth:
average_overlaps
