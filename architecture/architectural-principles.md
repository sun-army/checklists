# Architectural principles

## Working with data

name | benefit | examples of usage
--- | --- | ---
hashing | a lot of different values might be decreased to a finite set of values (string to numerical index). Collisions should be resolved via rechecking. Better to fetch from hash structure than to fetch from raw data | PostgreSQL Hash Joins, REDIS Hash data type, Javascript Objects
hash buckets | hash a key and put the related value inside a small array of values instead of putting all values in one big array | PostgreSQL values selectivity statistics
prefetching | Write a bit more than demanded because most of the time a reading process will continue | Disc buffers prefetch, CPU registers prefetch, audio player prefetch (loading a bit more information ahead)
Abstract syntax tree | Easy to modify in comparison to text | V8 compilation process, PostgreSQL query execution process
indexing | create a special structure for the concrete data access case | Relational database indexes

## Data structures

name | description | examples of usage
--- | --- | ---
Bloom filter | an effective method to quickly answer the question 'does a value fulfill some conditions' | Google Chrome malicious URL checker, Apache HBase, PostgreSQL disk lookup reducers


## Application structure

### Libraries and services
* Common library for the features both used by frontend and backend
* Common backend library for the different services

### Raw (initial) data management:
* save both events and result values. For example, save both user follow/unfollow other user in the event table `users_activity` and for quick state selection use a separate `result` table user_activity_follow.
* AFTER triggers for data updates - save the all history of data changing for the desired tables
