# Example Code for Data Processing and Analysis

This document contains various examples of data processing techniques and operations using pandas and PySpark.

## Table of Contents

- [Replace Null Values in a DataFrame](#replace-null-values-in-a-dataframe)
  - [Using pandas](#using-pandas)
- [Create DataFrames and Perform Joins](#create-dataframes-and-perform-joins)
- [Drop Duplicates in PySpark](#drop-duplicates-in-pyspark)
- [Sample Window Function Examples](#sample-window-function-examples)
- [Aggregate and Retrieve Top N Products](#aggregate-and-retrieve-top-n-products)

---

## Replace Null Values in a DataFrame

### Using pandas

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', None, 'David', 'Eve'],
    'Age': [25, None, 30, None, 22],
    'City': ['New York', 'Los Angeles', 'Chicago', None, 'San Francisco']
}

df = pd.DataFrame(data)

# Print the original DataFrame
print("Original DataFrame:")
print(df)

# Replace missing values (NaN) with a default value
df_filled = df.fillna({
    'Name': 'Unknown',  # Replace NaN in 'Name' column with 'Unknown'
    'Age': 0,           # Replace NaN in 'Age' column with 0
    'City': 'Unknown'   # Replace NaN in 'City' column with 'Unknown'
})

# Print the updated DataFrame
print("\nDataFrame after replacing NaN values:")
print(df_filled)

# Replace missing values in the 'Name' column with a default value ('Unknown')
df['Name'] = df['Name'].fillna('Unknown')
```

---

## Create DataFrames and Perform Joins

### Using PySpark

```python
from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.appName("JoinExamples").getOrCreate()

# Sample DataFrames
df1 = spark.createDataFrame([
    ('Alice', 1),
    ('Bob', 2),
    ('Charlie', 3)
], ['Name', 'ID'])

df2 = spark.createDataFrame([
    (1, 'New York'),
    (2, 'Los Angeles'),
    (4, 'Chicago')
], ['ID', 'City'])

# Perform inner join on the 'ID' column
inner_join_df = df1.join(df2, df1.ID == df2.ID, how='inner')

# Show the result
inner_join_df.show()
```

---

## Drop Duplicates in PySpark

```python
from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.appName("RemoveDuplicates").getOrCreate()

# Sample DataFrame with duplicates
data = [
    (1, "Alice", 25),
    (2, "Bob", 30),
    (3, "Alice", 25),
    (4, "Charlie", 35),
    (1, "Alice", 25)
]
df = spark.createDataFrame(data, ["ID", "Name", "Age"])

# Remove duplicate rows
df_no_duplicates = df.dropDuplicates()

# Show the result
df_no_duplicates.show()
```

---

## Sample Window Function Examples

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, sum, rank
from pyspark.sql.window import Window

# Initialize Spark session
spark = SparkSession.builder.appName("TopNProductsWindow").getOrCreate()

# Sample DataFrame
data = [
    ("ProductA", 100),
    ("ProductB", 200),
    ("ProductC", 300),
    ("ProductD", 150),
    ("ProductE", 250),
    ("ProductF", 200),  # Example tie with ProductB
]
columns = ["Product", "Sales"]
df = spark.createDataFrame(data, columns)

# Number of top products to retrieve
n = 3

# Define a window specification
window_spec = Window.orderBy(col("Total_Sales").desc())

# Calculate total sales for each product
sales_df = df.groupBy("Product").agg(sum("Sales").alias("Total_Sales"))

# Add a ranking column using the rank() function
ranked_df = sales_df.withColumn("Rank", rank().over(window_spec))

# Filter for the top n ranks
top_n_products = ranked_df.filter(col("Rank") <= n)

# Show the result
top_n_products.show()
```

---

## Aggregate and Retrieve Top N Products

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, sum

# Initialize Spark session
spark = SparkSession.builder.appName("TopNProducts").getOrCreate()

# Sample DataFrame
data = [
    ("ProductA", 100),
    ("ProductB", 200),
    ("ProductC", 300),
    ("ProductD", 150),
    ("ProductE", 250),
]
columns = ["Product", "Sales"]
df = spark.createDataFrame(data, columns)

# Number of top products to retrieve
n = 3

# Calculate top n products based on sales
top_n_products = (
    df.groupBy("Product")
    .agg(sum("Sales").alias("Total_Sales"))  # Aggregate sales
    .orderBy(col("Total_Sales").desc())      # Sort by total sales in descending order
    .limit(n)                                # Get top n products
)

# Show the result
top_n_products.show()
```

from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Initialize a Spark session
spark = SparkSession.builder.master("local").appName("JSONExample").getOrCreate()

# Sample JSON data
json_data = """
[
    {"name": "John", "age": 30, "city": "New York"},
    {"name": "Jane", "age": 25, "city": "Los Angeles"},
    {"name": "Mike", "age": 35, "city": "Chicago"}
]
"""

# Create an RDD from the JSON string
rdd = spark.sparkContext.parallelize([json_data])

# Read the JSON string as a DataFrame
df = spark.read.json(rdd)

# Show the DataFrame
df.show()

# Example transformation: selecting specific columns
df.select(col("name"), col("age")).show()

from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.appName('WordCount').getOrCreate()

# Load the text file into an RDD
rdd = spark.sparkContext.textFile('your_text_file.txt')  # Replace with the path to your text file

# Word count transformation
word_counts = (rdd.flatMap(lambda line: line.split())  # Split each line into words
               .map(lambda word: (word.lower(), 1))  # Convert to lowercase and create (word, 1) pair
               .reduceByKey(lambda a, b: a + b))  # Count the occurrences of each word

# Get the top 5 most frequent words, ordered by frequency (descending)
top_5_words = word_counts.takeOrdered(5, key=lambda x: -x[1])  # Sort by count in descending order

# Print the top 5 words and their counts
for word, count in top_5_words:
    print(f"{word}: {count}")
