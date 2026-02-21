if the textFile contains punction and you want to remove those 

import scala.util.matching.Regex

val patternmatch="[^a-zA-Z0-9]".r

val textFile=sc.textFile("/opt/dataFiles/sample.txt")
textFile.flatMap(x=>x.split(" ")).map(x => pattern.replaceAllIn(x,"")).filter(x=>x.trim.nonEmpty).map(x=>(x,1)).reduceByKey((a,b)=>a+b)

import re
textFile.flatMap(lambda x:x.split(" ")).map(lambda x:re.sub(r"[^a-zA-Z0-9]","",x)).filter(lambda x:x.strip()!="").map(lambda x:(x,1)).reduceByKey(lambda a,b:a+b)

top 3 frequency elemens 
Scala
textFile.flatMap(x=>x.split(" ")).map(x => pattern.replaceAllIn(x,"")).filter(x=>x.trim.nonEmpty).map(x=>(x,1)).reduceByKey((a,b)=>a+b).takeOrdered(3)(Ordering[Int].reverse.on(_._2))
python
textFile.flatMap(lambda x:x.split(" ")).map(lambda x:re.sub(r"[^a-zA-Z0-9]","",x)).filter(lambda x:x.strip()!="").map(lambda x:(x,1)).reduceByKey(lambda a,b:a+b).takeOrdered(3,key=lambda x:-x[1])
