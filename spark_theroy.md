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
