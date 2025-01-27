#### Question 1

```
Hello world
Hello from PySpark
PySpark is awesome
Hello PySpark world
```
```
from pyspark.sql import SparkSession
from pyspark.sql.functions import *

spark=SparkSession.builder.getOrCreate()



textFile=spark.sparkContext.textFile("/opt/PysparkInterviewPrep/csvFiles/wordcount.txt")
eleFreq=textFile.flatMap(lambda x:x.split(" ")).map(lambda x:(x,1)).reduceByKey(lambda x,a:x+a)


df=spark.createDataFrame(eleFreq,["ele","freq"])
df.show()
print("print max element")

maxEle=eleFreq.max(lambda x:x[1])
print(maxEle)
df.orderBy(col("freq").desc()).show()



print("++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
num=3
print(f"printng top {num} frequency elements")
print(eleFreq.takeOrdered(num,key=lambda x:-x[1]))
orderedDf=spark.createDataFrame(eleFreq.takeOrdered(num,key=lambda x:-x[1]),["ele","freq"])
orderedDf.limit(num).show()
print("++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")


print("======================================================================================")
maxLength=textFile.flatMap(lambda x:x.split(" ")).map(lambda x:len(x)).max()
print(f"printing maximum length {maxLength}")
textFile.flatMap(lambda x:x.split(" ")).map(lambda x:(x,len(x))).filter(lambda x: x[1]==maxLength).collect()
print("======================================================================================")

maxLength=textFile.flatMap(lambda x:x.split(" ")).map(lambda x:(x,len(x)).reduceByKey(lambda x: x[1],1).collect()

```

#### question 2

```
Sample Data
data = [
 ("Sales", 5000, "John"),
 ("Sales", 6000, "Doe"),
 ("HR", 7000, "Jane"),
 ("HR", 8000, "Alice"),
 ("IT", 4500, "Bob"),
 ("IT", 5500, "Charlie"),
]

df = spark.createDataFrame(data, ["department", "salary", "employee_name"])

```

```
df.groupBy("department").agg(avg("salary").alias("average_salary"),count("employee_name").alias("emp_count")).show()
```

#### Question 3

```
data = [ (1, "Alice", 2000), (2, "Bob", 3000), 
 (3, "Alice", 2000), (4, "David", 4000), 
 (5, "Alice", 5000), (6, "Bob", 3000) ] 
columns = ["ID", "Name", "Salary"]
```

```
df.dropDuplicates(["Name","Salary"]).show()
```

#### question 4

```
data = [("Alice", 30), 
 ("Bob", None), 
 ("Catherine", 25), 
 (None, 35), 
 ("Eve", None)]

columns = ["Name", "Age"]

df = spark.createDataFrame(data, columns)
```

```
df.dropna(subset=["Age"]).show
df.fillna({"Age":0,"Name":"Unknown"}).show()
```

 df.withColumn("country",when(col("City")=="New York",lit("USA")).when(col("City")=="London",lit("UK"))).show()


#### using windowSpec
window_spec=Window.partitionBy("symbol").orderBy("date").rowsBetween(Window.unboundedPreceding,Window.currentRow)
new_df=df.withColumn("running_avg",sum(col("price")).over(window_spec))


