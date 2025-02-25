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


## Optimizing Costs in Snowflake

Snowflake costs can be categorized into two types: **Compute Costs** and **Storage Costs**.

### 1. Compute Cost Optimization
- Choose the right **T-shirt size** for virtual warehouses (avoid over/under-provisioning).
- Use **multi-cluster warehouses** for handling compute spikes:
  - Set `min_cluster_count` and `max_cluster_count`.
  - Enable **auto-suspend** and **auto-resume** to optimize credit usage.
- Implement **resource monitors**:
  - 50% usage → **Notify**.
  - 90% usage → **Suspend**.
  - 100% usage → **Immediate suspend**.
- Define **max concurrency level** and **system queued timeout** to prevent unnecessary compute costs.
- Optimize job execution strategies to reduce redundant compute consumption.

### 2. Storage Cost Optimization
- Reduce **time travel retention** for non-critical tables.
- Use **clones** instead of duplicating tables (clones act as pointers, saving storage costs).
- Move **older tables to external cloud storage** and query via **staging** when needed.
- Store data in **optimized compressed formats** (e.g., **Parquet, ORC**) instead of CSVs to reduce storage size.
