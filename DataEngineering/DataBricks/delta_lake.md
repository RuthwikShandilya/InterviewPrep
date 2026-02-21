1. Why is Delta lake better than parquet
Delta Lake is better than parquet because it has some time travel where the users can go to a specific timestamp or version of the parquet they are writing into.
Schema Enforcement
can tun merge updates (Once reverify)
```
spark.read.table("people10m@20190101000000000")
spark.read.table("people10m@v123")

df1 = spark.read.option("timestampAsOf", "2019-01-01").table("people10m")
df2 = spark.read.option("versionAsOf", 123).table("people10m")


SELECT * FROM my_table VERSION AS OF 5;
```
Schema Evolution in delta:

it enables modifying schema of tbles dynamically 

in spark we have to use mergeSchema option to enable this :

df.write.format("delta").option("mergeSchema", "true").mode("append").save("path/to/delta-table")

10. What happens when you delete data in a Delta Table?
The data is not immediately removed but marked as deleted. The VACUUM command must be run to physically delete the data:

from delta.tables import DeltaTable

delta_table = DeltaTable.forPath(spark, "/path/to/delta-table")

delta_table.alias("t").merge(
    updates.alias("u"),
    "t.id = u.id"
).whenMatchedUpdate(set={"amount": "u.amount"}) \
 .whenNotMatchedInsert(values={"id": "u.id", "amount": "u.amount"}) \
 .execute()

 
