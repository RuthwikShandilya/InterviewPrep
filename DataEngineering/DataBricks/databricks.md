What are Delta Tables and how do they improve performance.

Delta tables are a storage layer built on top of parquet format.They bring 
a. ACID transactions: Ensures data integrity with atomic commits, rollbacks, and concurrency control.
b. Schema Evolution : automatically handle schema evoltion if we have mergeSchema as True
c. Time Travel(Versioning): For every write it creates a new parquet and we can go back to this parquet using versionOf or based on timestamp
d. Z Order Optimization:
e. Auto Compaction
f. Merge into : supports MERGE into on conflcit 

reason why parquet doesnt support merhge into : 
Parquet files are immutable → You cannot modify a specific row inside a Parquet file
No transaction log → No way to track row-level changes



Auto Compaction:
OPTIMIZE delta.`/mnt/delta/employee`

spark.conf.set("spark.databricks.delta.autoCompact.enabled", "true")

AutoCompaction basically combines all the small files to reduce io load and makes them into a size which improves efficiency by reducing metadata overheda
from delta.tables import DeltaTable

delta_table = DeltaTable.forPath(spark, "/mnt/delta/employee")
delta_table.optimize().executeCompaction()


Z order optimization:
Z order optimization technique basically co locates similar data together so that the amount of data scanned reduces improving efficiency.
Partitioning is basically have same data rows in a pqrquet file but zorder changes the order of rows that are stored to improve the efficiency.
from delta.tables import DeltaTable

delta_table = DeltaTable.forPath(spark, "/mnt/delta/transactions")
delta_table.optimize().executeZOrderBy("customer_id")


Unity Catalog :

Unity catalog is a unified governance system for fine grained access control.data lineage.
It has centralized data access control (Role Based Access Control (RBAC) and ABAC(Attribute Based access control))
Column and Row level security 
Data lineage 

RBAC :
GRANT SELECT ON TABLE clinical_data.patients TO GROUP doctors;
GRANT SELECT (name, diagnosis) ON TABLE patients TO GROUP researchers;

but in ABAC 

CREATE MASKING POLICY mask_ssn AS (val STRING) -> STRING 
USING (current_user() IN ('doctor')) THEN val ELSE 'XXX-XX-XXXX';

CREATE ROW FILTER filter_sensitive_data ON patients
USING (current_user() = 'doctor') THEN TRUE ELSE FALSE;




