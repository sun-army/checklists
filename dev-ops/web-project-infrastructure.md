# Web project infrastructure


## Monitoring
* Basic monitoring (Zabbix)
* Alerting
* Business metrics - orders amount per hour, last activity datetime, etc.

## Principles
* Dedicated servers for production and for production replication servers
* Expensive VPS for critical production systems like monitoring
* Cheaper VPS for staging/release-candidate infrastructure

## Logging
* Log aggregation system (Sentry) and proper log rotation
* Logging for frontend (console errors)
* Logging for backend - errors/warnings/info
* Errors alerting to the Slack/Telegram for the required severity level

## Database
* Master
* Slave for the requests about statistics (for analytics) and for backups
* Slave as a reserve - always uptime
* Backups - to the separate storage - two storages, separated data centers
* Scripts to check backups.
* From time to time - manual backups checkings (for ex. on the staging infrastructure)
* Backups storage disc space monitoring
* An ability to make and download a backup via Jenkins for development purposes
* An ability to sync release candidate and production databases via Jenkins

# Deployment
* playbook scripts
* Jenkins as an example of automatization
* Deployment alerting

## Other
* Docker images, Docker conductor - Swarm, Rancher, etc.
* CI with autotests running (both backend and frontend like Selenium)
* Deployment scripts ruled by Jenkins
* Staging servers
* Release-candidate servers
* Database migrations under the GIT
* All servers configurations under the GIT (or docker images)
* Documentation at least about infrastructure and about the basic workflows
* Static content CDN
* IP and DOS protection CDN like CloudFlare
* Queue services like RabbitMQ
* 3rd party services and API like blockchain
* Load balancing and availability balancing via HAProxy (custom business rules)

