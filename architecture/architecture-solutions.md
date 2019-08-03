# Architecture solutions

## Raw data and indexes

* Write all events
* For the select purposes create `indexes`

Example:
* `users_activity` table to store all events - insert only, no deleting.
* `users_activity_follow` table to store a last state of related activity
