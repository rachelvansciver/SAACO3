![[Pasted image 20221101212132.png]]
# DynamoDB

## TLDR
NoSQL Serverless DB. Tons of features and can be global.

## Features
- NoSQL
- serverless
- millisecond latency
- key value document db
- single digit millisecond performance
- multi az
- fully managed
- multi-master
- backup and restore
- in memory caching
- transaction capability

##  Capacity Modes
- provisioned capacity with optional autoscaling
- on demand capacity

## Use cases
- can replace elasticache (storing session data with ttl feature)
 - serverless apps
 - rapidily evolve schemas
 - small documents 100bs
 - distributed serverless cache

## DAX cluster
- read cache 
- in memory
- microsecond read latency

## Auth
- [[IAM]]

## Dynamo DB Stream
- event processing
- invoke [[Lambda]] or send to [[Kinesis]]
- 24 hour retention 
- limited number of consumers

## Dynamo DB Kinesis Data Streams
- 1 year retention
- all features of [[Kinesis]]

## Global Tables
- active setup for multi region
- two way replication
- must enable Streams as prerequisite

## Backups
- automated backups up to 35 days with PITR to restore to new table
- on demand backups

## Export
- export import to [[S3]]

## Security
- support [[KMS]] Customer Managed Key

## CLI Created Tabled
- Autoscaling wont be enabled by default
