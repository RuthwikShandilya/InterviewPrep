# Scala Collections and Functions: Advanced Operations Guide

This document presents an exhaustive exploration of fundamental and advanced operations on Scala's core data structures—Lists, Arrays, Tuples, Maps, and HashMaps—along with functional programming paradigms. These examples are tailored to emphasize precision and best practices in computational design.

---

## 1. List
### Adding Elements
```scala
val list = List(1, 2, 3)
val updatedList = list :+ 4 // Appends an element to the list
println(updatedList)
```

### Removing Elements
```scala
val list = List(1, 2, 3, 4)
val filteredList = list.filter(_ != 3) // Filters out elements not matching the condition
println(filteredList)
```

### Iterating Through Elements
```scala
val list = List(1, 2, 3, 4)
list.foreach(println) // Applies a function to each element
```

---

## 2. Array
### Adding Elements
```scala
val array = Array(1, 2, 3)
val updatedArray = array :+ 4 // Produces a new array with the appended element
println(updatedArray.mkString(", "))
```

### Removing Elements
```scala
val array = Array(1, 2, 3, 4)
val filteredArray = array.filter(_ != 3) // Constructs a new array excluding specific elements
println(filteredArray.mkString(", "))
```

### Iterating Through Elements
```scala
val array = Array(1, 2, 3, 4)
array.foreach(println) // Iterates and applies a function to each element
```

---

## 3. Tuple
### Accessing Elements
```scala
val tuple = (1, "Scala", true)
println(tuple._1) // Retrieves the first element
println(tuple._2) // Retrieves the second element
println(tuple._3) // Retrieves the third element
```

### Iterating Through Elements
```scala
val tuple = (1, "Scala", true)
tuple.productIterator.foreach(println) // Iterates over all elements in the tuple
```

*Note*: Tuples are inherently immutable; modifications such as adding or removing elements are not supported.

---

## 4. Map
### Adding Elements
```scala
var map = Map(1 -> "One", 2 -> "Two")
map += (3 -> "Three") // Adds a key-value pair
println(map)
```

### Removing Elements
```scala
var map = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
map -= 2 // Removes a key-value pair by key
println(map)
```

### Iterating Through Elements
```scala
val map = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
map.foreach { case (key, value) => println(s"$key -> $value") } // Applies a function to key-value pairs
```

---

## 5. HashMap
### Adding Elements
```scala
import scala.collection.mutable.HashMap
val hashMap = HashMap(1 -> "One", 2 -> "Two")
hashMap += (3 -> "Three") // Adds a key-value pair
println(hashMap)
```

### Removing Elements
```scala
import scala.collection.mutable.HashMap
val hashMap = HashMap(1 -> "One", 2 -> "Two", 3 -> "Three")
hashMap -= 2 // Removes a key-value pair by key
println(hashMap)
```

### Iterating Through Elements
```scala
import scala.collection.mutable.HashMap
val hashMap = HashMap(1 -> "One", 2 -> "Two", 3 -> "Three")
hashMap.foreach { case (key, value) => println(s"$key -> $value") } // Iterates over key-value pairs
```

---

## 6. Functions
### Defining and Using Functions
#### Basic Addition Function
```scala
def add(a: Int, b: Int): Int = a + b // Simple binary function
println(add(5, 10))
```

#### Higher-Order Function
```scala
def applyFunction(f: Int => Int, x: Int): Int = f(x) // Function as a parameter
println(applyFunction(x => x * 2, 5)) // Applies a doubling function to the input
```

#### Iterating Through a List Using a Function
```scala
val list = List(1, 2, 3, 4)
list.map(x => x * 2).foreach(println) // Multiplies each element by 2 and iterates through the results
```

---

This document provides a rigorous reference framework for executing standard and functional operations on Scala collections. Use these examples as foundational components for complex application development.

