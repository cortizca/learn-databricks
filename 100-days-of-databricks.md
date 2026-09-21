# Day 1: ACID Transactions


## What is it?
ACID transactions satisfy ACID properties that ensures each transaction will be fully committed or not at all.
 
## Why does it matter?
Data loading might have issues that could lead to partial writes, deduplication and other data integrity problems.
 
## One real-world example
As a senior data analyst, loading data into the data warehouse is already part of day-to-day responsibility.
 
A simple, clean, formatted csv file can be loaded into Redshift in minutes without any problem.
 
Sometimes, different file types require different configuration and if not configured correctly would lead to data loading issues.
 
These data loading issues could lead to partial writes, deduplication and other data integrity problems.
 
ACID properties help address this issue by ensuring transactions will be fully committed or not at all.
 
ACID properties have the following characteristics:
 
Atomicity - each transaction is treated as independent and mutually exclusive.
Inserting a new row
Updating few column values
Deleting records
 
Consistency - any interruption is the operation or transaction does not create inconsistencies in the data
 
Isolation  - multiple users can run read or write to the table without interruption and without sacrificing the integrity of the data
 
Durable - if a transaction is committed, it will be permanently saved regardless if there is network interruption, etc.
 
## My takeaway
ACID transactions ensure data integrity and data trust by keeping transactions fully committed or not at all.


# DAY 2: Transaction Logs
 
## What is it?
Transaction logs or _delta_logs are JSON files created at the start of table creation. It tracks all transactions applied/operation/committed to the table.
 
## Why does it matter?
Transaction logs play a great role serving as the single source of truth for the table allowing time travel or table restoration. This is also critical in implementing ACID guarantees across Delta Table.
 
## One real-world example
Any insert, update, delete committed to the table are tracked under transaction logs as well as failed transactions. Multiple users can update the same table at the same time and transaction logs handles multiple operations thru optimistic concurrency control. With that, any concurrent non-conflicting transactions will be committed and logged to the table. Most recent commits are reference in the checkpoint transaction for quicker read and implements consistency across multiple users and sessions.
 
## My takeaway
Transaction logs are the backbone of implementing ACID guarantees allowing time travel and table restoration.

# Day 3: Time Travel and Restore

## What is it?
Delta logs or transaction logs implementing ACID guarantees allow time travel and restoration.

## Why is it important?
This allows the ability to query a specific version of the table at a certain point in time. This is important for audit support and in case a specific version of the table needs to be restored.


## One real-world example
Erroneous data was inserted into the table. A data engineer needs to restore the previous state. Time travel makes this possible by querying the specific version and inserting it into the table. Direct table version restoration is possible using the RESTORE syntax as well.

One thing to note though is that do not fully rely on Time Travel feature for restoration. Versions in the last 7 days only are available unless the log retention days is adjusted. 

## My take away 
Time travel is very handy in restoring a previous version and particularly helping in satisfying audit compliance and other table restoration needs.


# Day 4: Schema Enforcement and Schema Evolution

## What is it?

Schema enforcement is like schema validation. It ensures that no other columns will be added to the table.

On the other hand, schema evolution allows adding new columns to the table. 

## Why is it important?
Schema enforcement is important to ensure that no unexpected table will be added to the table. Write operation will fail if new columns are introduced. 

On the other hand, schema evolution is helpful if new columns need to be added to the table. This is extremely helpful if new columns are needed for data enrichment and update.

## How is it implemented? 
Schema evaluation is implemented by making sure that you update the write or write stream operation by indicating that mergeSchema = true.

## My Key Takeaway 
Schema enforcement ensures that table preserved the predefined schema while schema evolution allows introduction of new columns.

# Day 5: Liquid Clustering 

## What is it?
liquid clustering is one of the features of the Delta Lake allowing data partitioning.

## why it is important 
liquid clustering provides way to do data partitioning on an efficient and flexible manner. Before, when we partition a table, we need to do it once and if there’s any updates needed, we need to rewrite the table to include the new column on the partitioning statement. On the other hand, through liquid clustering, we can do the clustering on the fly, such such that we can update the table and then specify then you clustering columns without rewriting the table.

## My Key Takeaway
Liquid clustering plays a great role in optimizing delta tables in a way that it makes partitioning more efficient and in a flexible way.

