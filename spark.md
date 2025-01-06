## Spark Optimizations 
What effects perfomrance 
1. Shuffle operations : it causes network IO and will effect performance
2. Transformations : Wide(effects) and Narrow
3. Memory configurations
4. Use proper Disks : ssds and pther disk types

1. Check Spark UI and check different Garbage Collectors<<<<<<<<<<<<<<<<<<<Read about this >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
2. Minimize scans
   1. Paritition
   2. Bucketing
   3. filtering
   4. Avoid Data skewness
3. Join Optimizations
    1. For both datasets latger use default sortMerge join strategy
    2. for one dataset larger and othger small then 10MB(default broadcase join threshold) use a broadcast join
       spark.sql.autoBroadcastJoinThreshold
4. Coalesce Repartition : Coalesce decreses partition and doesnt shuffle data and Reparttion increses it and shuffles data
5. DropDuplicates before Join to optimize joins
6. Cache or persists(Cache is in INMEMORY onlt where as persissts can be MEMORY /DISK) if the data is frequently accesses
7. Broadcase variables has readonly variables copied to all nodes
8. Accumulators
9. Avoid Spark UDF
   Spark optimizations will not work on UDFS.UDFS are applied on each row.
10 While using file processions use parquet file which has snappyy compression
11. Increase parallelism if the data is huge
12. Garbage Collection :
13. Dynamic Allocation : 
spark.dynamicAllocation.enabled	
spark.dynamicAllocation.minExecutors	
spark.dynamicAllocation.maxExecutors
14. Offheap memory
15. 
