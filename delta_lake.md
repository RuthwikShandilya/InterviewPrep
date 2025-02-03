1. Why is Delta lake better than parquet
Delta Lake is better than parquet because it has some time travel where the users can go to a specific timestamp or version of the parquet they are writing into.
Schema Enforcement
can tun merge updates (Once reverify)

spark.read.table("people10m@20190101000000000")
spark.read.table("people10m@v123")

df1 = spark.read.option("timestampAsOf", "2019-01-01").table("people10m")
df2 = spark.read.option("versionAsOf", 123).table("people10m")

