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

if the file has punctuaion and you want to remove those:
import re
textFile.flatMap(lambda x:x.split(" ")).map(lambda x:re.sub(r"[^a-zA-Z0-9]","",x)).filter(lambda x:x.strip()!="").collect()

Check if the string in palindrome
str_val="A man, a plan, a canal, Panama"
import re

def isPalindrome(str_val):
    pattern=r"[^a-zA-Z0-9]"
    striped_Str=re.sub(pattern,"",str_val.lower())
    print(striped_Str)
    return striped_Str==striped_Str[::-1]

print(isPalindrome(str_val))


#Check if the string is Anagram
from collections import Counter
str1="silent"
str2="listn"

def areAnagrams(str1,str2):
    return Counter(str1)==Counter(str2)

print(areAnagrams(str1,str2))

#rotate Array

arr=[1,2,3,4,5]
k=9

def rotateArray(arr,k):
    k=k%len(arr)
    return arr[-k:] +arr[:-k]
    
print(rotateArray(arr,9))

#Reverse Words in String (Python)

str_val="hello world"

def reversedWords(str_val):
    return ' '.join(str_val.split(" ")[::-1])
    
print(reversedWords(str_val))

#first occurance of elemtn

str_1="hello world"

match_str="world"


def getStringIndex(str1,match_str):
    index=0
    for ele in str_1.split(" "):
        if match_str!=ele:
            index+=len(ele)
        else:
            return index+1
    return -1
        
print(getStringIndex(str_1,match_str))


str_list=["eat", "tea", "tan", "ate", "nat", "bat"]
from collections import defaultdict
anagrams = {}

for ele in str_list:
    sorted_word=''.join(sorted(ele))
    if sorted_word in anagrams:
        anagrams[sorted_word].append(ele)
    else:
        anagrams[sorted_word]=[ele]

print(list(anagrams.values()))


str="abcdefghabc"
max_sub_str_len=0
i=0
while i<len(str):
    j=i+1
    while j<len(str):
        if str[i]!=str[j]:
            j+=1
        else:
            if j-i > max_sub_str_len:
                max_sub_str_len=j-i
            break
    i+=1

print(max_sub_str_len)

#Write a Python function that finds the largest palindrome in a string. The function should return the palindrome and its length.

str_val="abccba"

def isPalindrome(str_val):
    return str_val==str_val[::-1]

i=0
max_len=0
max_len_str=""
while i<len(str_val):
    j=len(str_val)
    while j>0:
        if isPalindrome(str_val[i:j]) and j-i>max_len:
            max_len=j-i
            max_len_str=str_val[i:j]
            break
        j-=1
    i+=1
print(max_len_str)
print(max_len)
        

                
    
    



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


