# Database optimization

## Profiling
* Profiling. Find a requests which are valuable for the business to optimize - most frequent / most impact to the performance / balance between profit and time required to optimize


## Hardware
* Global database settings like memory limits, write costs (ex. random page costs for PostgreSQL)
* Resources monitoring - RAM and disc consumption, less disc more RAM.
* Separate table spaces for different data - SSD for the hot, HDD - for archives
* Move WAL to a separate SSD disc
* Disc RAID for parallel reading

## Processes
* Actual optimizer statistics and and autovacuum effectiveness.
* Long transactions or too much very short requests (N+1 issue)TODO
* Batch insert/update/select instead of a single big and long request


## Indexes
* New index
* Useless indexes should be deleted
* Composite index instead of two separated
* Functional/partial index
* Too old B-tree index - structure is not optimal, recreation will improve it
* Corrupted indexes
* CLUSTER command to avoid hash index usage and to use index scan
* Unique indexes in order to improve effectiveness of JOINS

## Infrastructure
* Replication
* Partitioning
* Sharding

## Schema
* Normalization - decrease amount of data and a weight of DB objects
* Denormalization - decrease a number of JOINS
* JSON/array data types - decrease amount of JOINED rows
* 
