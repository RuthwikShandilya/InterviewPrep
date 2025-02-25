1. You have a query which is running lot of time how do you optimize this.
Apart from adding cluster keys
partitioning the table in the right way
and using the same cache queries for better perfomance
## Optimizing a Slow-Running Query

### 1. Analyze Query History
- Check **query history page** → Filter based on time & execution
- Identify **compilation time vs execution time**

### 2. Use Query Profiler
- Analyze time spent on:
  - **Processing**
  - **Local Disk I/O**
  - **Remote Disk I/O**
  - **Synchronization**
  - **Initialization**
- Identify **most expensive node** & **bytes/rows scanned**

### 3. Query Optimization Strategies
#### Sorting & Filtering
- Avoid **ORDER BY** in subqueries if outer query already has it
- Use **LIMIT** to reduce unnecessary processing

#### Materialized Views
- Use **materialized views** for precomputed data (single-table, no joins)

#### Partitioning & Clustering
- Ensure proper **partitioning** for efficient pruning
- Use **cluster keys** effectively
- Check clustering health:
  ```sql
  SELECT SYSTEM$CLUSTERING_INFORMATION('table', (col1, col3));
  ```
- Lower **average_depth** and **average_overlaps** for better performance

#### Query Caching
- Reuse **cached queries** to improve speed
