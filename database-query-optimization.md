# Database optimization

## Profiling
Goal - find a requests which are valuable for the business to optimize - most frequent / most impact to the performance / balance between profit and time required to optimize

### A list of candidates
Candidate | Process
--- | ---
Slow Backend application processing of business tasks | Observe related DB requests
Slow queries | Enable slow query log
Quick but very frequent queries | Automatically grep and parse PostgreSQL main log (or use special extensions, a research is required)

### General tools
* PostgreSQL log with extended request info => parse it automatically
* Extensions like pg_stat_statements
* EXPLAIN directive BUFFERS - I/O profiling


## Optimization strategies

* OLTP requests - index scan instead of Seq. scan for the JOINS, nested loop instead of Merge JOIN and Hash JOIN
* No correlation requests and loops - use JOINS instead or CTE/stored procedures to calculate values beforehand
* More memory I/O, less disk I/O - increase the work_mem, use indexes to decrease amount of data to process
* More accurate statistics for the optimizer - vacuum processes monitoring


## Stored procedures and functions
* IMMUTABLE, STABLE instead of VOLATILE - an ability to call a function at once and beforehand.


## Hardware
* Global database settings like memory limits, write costs (ex. random page costs for PostgreSQL)
* Resources monitoring - RAM and disc consumption, less disc more RAM.
* Separate table spaces for different data - SSD for the hot, HDD - for archives
* Move WAL to a separate SSD disc
* Disc RAID for parallel reading

## Processes
* Actual optimizer statistics and autovacuum effectiveness.
* Long transactions or too much very short requests (N+1 issue)
* Batch insert/update/select instead of a single big and long request
* Decreasing the size of tables (table bloat) due to a lot of updating operations

## Settings
* I/O costs
* Available memory

## Features
* extended statistics

## Indexes
* New index
* Useless indexes should be deleted
* Composite index instead of two separated
* Functional/partial index
* Too old B-tree index - structure is not optimal, recreation will improve it
* Corrupted indexes
* CLUSTER command to avoid hash index usage and to use index scan
* Unique indexes in order to improve effectiveness of JOINS
* Rows visibility stats for the index only scan

## Requests
* Stored procedures to avoid too big network resources consumptions (connections, traffic, etc.)
* CTE to cache a heavy requests in order to reuse results inside the different queries
* CTE to execute a lot of queries at once
* As short as possible transactions - less locks, less bloating
* Background deleting - mark as deleted and actually delete by the separate background worker-process
* INNER JOINs are better than LEFT/RIGHT JOINs (less rows to process)
* Less table scannings (WINDOW functions)

## Infrastructure
* Replication
* Partitioning
* Sharding
* Master-master if it is a high-load processing of data and replication lag time is forbidden
* Tables for the cold, warm and hot data and automatic data archieving

## Schema
* Normalization - decrease amount of data and a weight of DB objects
* Denormalization - decrease a number of JOINS
* JSON/array data types - decrease amount of JOINED rows
* Correct data types 
* Avoid nullable fields if there is no suitable business valuable situation around such null logic
* Separate database for future sharding - for example, separate database with the single table `statistics`
