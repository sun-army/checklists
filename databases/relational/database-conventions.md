# Database conventions

## Naming
* snake_case
* lower case
* same naming structure, for example `users_activity`, `users_activity_trust`, `users_activity_follow`, but not
`users_activity` and `users_trust_activity`.

## Logical structure
* do not use public SCHEMA - do use a separate SCHEMA for every group of tables (group is determined by Domain-driven-design principles)
* stats tables/archive tables, etc. must be placed to the separate database for the future sharding


## Migrations
* Migrations under GIT


## Queries
* Always use prefix in order to aviod ambiguous errors in the future when a new column 'suddenly' appears


# Stored procedures and functions
* Use STRICT in order to aviod undefined and null and more than one row issues for the select operators.
* Aviod stored procedures and functions for the simple cases. Use them for the heavy tasks like statistics calculation or for the tasks which include access rules policy.
