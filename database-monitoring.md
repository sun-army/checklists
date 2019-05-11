# Database monitoring

## Objects monitoring
* Tables sizes - to catch table bloat in advance. VACUUM is required
* Indexes sizes and consistency - too big and too old index is very ineffective. Rebuild is required. Might be concurrent

## Resources monitoring
* CPU
* Disk I/O and disk space
* RAM
* Compare RAM usage and disk usage
* Network - might be a lot of data is moving from DB to the backend and backward.

## Monitoring of processes
* PostgreSQL log for the errors
* Slow query log
* Autovacuum - does it work always. Should work from time to time.
