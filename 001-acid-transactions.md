#Day 1: ACID Transactions
 
What is it?
ACID transactions satisfy ACID properties that ensures each transaction will be fully committed or not at all.
 
Why does it matter?
Data loading might have issues that could lead to partial writes, deduplication and other data integrity problems.
 
One real-world example
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
 
My takeaway
ACID transactions ensure data integrity and data trust by keeping transactions fully committed or not at all.