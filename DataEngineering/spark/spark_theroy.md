## Basic Spark Questions :

 1. What is RDD and Data Frame and differences between them
    RDD : RDD is Resilient Distributed Dataset is the fundemental data struture that stores and processes data in parallel across cluster of machine.
          1. It is fault toulerent
          2. Lazy Evaluated
          3. it is immutable: ANy transformation creates new records
    
    Data Frame : Dataframe is an API built on top of RDD where it deals with data in rows and columns or strutured data
    it is Schema-based
    Optimized Execution: Uses Catalyst Optimizer for automatic query optimization.
Provides SQL-like operations and functions.

Which one to use when : 
When dealing with strtutuded data and need sql like operations use Dataframes.When using unstrcutyured data and need fine grained control over computations use RDD.Also Dataframes use Catalyst Optimizer to oprtimize query performae

## Architecture of Spark

Spark Uses a Master Slave Architecture wher master is a driver node and slaves are executor nodes
Driver : Driver is the program responsible for cordinating tasks across all worker nodes
Executor : Exectuor Nodes are where the execution happens.They communicate with driver node after each execution 
Cluster Manager : is responsible for allocating resources and managing jobs on cluster.Spark supports various cluster manager like YARN,Mesos,Standalone,Kuberners

Execution Modes : Client mode and Cluster mode 


Optimizations in Spark : 



## WHat happens when you submit a spark job in background
1. when we do a spark submit the first thing is spark context gets crated which is the entry point of spark
2. Based on the deploy mode it runs in the client mode or in any of the clusters as cluster mode
3. the user code is converted into a DAG which represents transformations and actions
4. the DAG scheduler divides the program into stages and each stage is divied into tasks basd on partitioons
5. tasks are sent to executor to run on the worker nodes
6. once the tasks are done they are sent back to driver
7. 
