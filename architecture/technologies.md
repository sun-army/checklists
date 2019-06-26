# Technologies

## Existing solutions to use

name | when to use | when not to use
--- | --- | ---
PostgreSQL | Main project database | OLAP tasks to aggregate on data on the fly (real time metrics), a very big (more than 1 TB collections of id + TEXT documents
ClickHouse | OLAP tasks when it is required to aggregate and show data on the fly | Small amount of data, for ex. less than 100 mln, no real-time aggregation required
NGINX | almost for all regular tasks | Not determined yet (not enough experience)
RabbitMQ / Kafka | Queue-related processes when one of the processes is a lot heavier than another | If it is possible to make a sync call between the servers - debugging and error processing will be much easier
GraphQL | An interface for the well-controlled services, for ex. backend + frontend of the same company | As an API for third-party usages - most of the external cliends are not able to implement it
Docker containers | For stateless services like backend applications, server-side renderers, microservices | Production databases (not possible to scale on-demand because of the state), other stateful services
Typescript | always, because it is fully backward compatible with the Javascript | Use always, it is not required to use all the features at one time - from time to time improve typing

## Existing solutions not to use

name | why | alternatives
--- | --- | ---
MongoDB | This is a mix of SQL and NoSQL features and every such feature has a quality lower than another solutions | PostgreSQL JSONB, Cassandra
MySQL | Pluggable engine architecture is unsuccessful - optimizer is very bad | PostgreSQL
Apache web server | tread pattern is outdated and not effective any more | NGINX
NodeJs web server without NGINX, blockchain nodes web servers | thread pattern is not enought effective, lack of good SSL features, etc | Place a NGINX beforehand
REDIS for queue-related tasks | Lack of features specified to queue processing | RabbitMQ, Kafka
Amazon containers different from well-known ones like Docker | Vendor-lock | Docker containers
