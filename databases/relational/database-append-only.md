# Append only databases (tables)


## AUTOVACUUM
* Poor stats - from time to time it is required to run ANALYZE manually. Append-only table is analyzed rarely.
* autovacuum_freeze_max_age - due to rare ANALYZE.
