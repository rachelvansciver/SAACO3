![[Pasted image 20221101120425.png]]
# Kinesis

## TLDR
Kinesis is a set of services for streaming real time or next to real time data in AWS. Its generally more expensive and more difficult to setup than [[SQS]] but offers more features and higher performance.


## Features
- region scoped
- real time data streaming service
- gigabytes of data per second
- 100ks of sources
- 2MBs/shard default shared between all consumers of kinesis streams
- use enhanced fan out to support multiple consumers, each consumer gets the 2mbs/shard
- 1mbs input per shard 
- shards need to be provisioned ahead of time
- consume records up to 7 days later
- multi applications consume the same stream
- keep order of records
- routing related records to the same consumer

## Kinesis Data Streams Detail
- shards which split data and computing power

### Record
- entry in kinesis
- partition key which targets the shard
- data blob (up to 1mb)
- Producers can set 1mbs and 1000msg per sec per SHARD

#### Consumer
- receives partition key, sequence number and blog
- throughput 2mbs per sec shared for all consumers
- enhances 2mb per sec per consumer
- apps using sdk
- [[Lambda]]
- kinesis firehouse
- kinesis data analytics

### Retention
- between 1 and 365 days
- can replay data
- immutability

### Modes

#### Provisioned Mode 
- choose number of shards, scale manually
- 1mbs in 2 mbs sec out per shard
- pay per shard per hour

#### On demand
- default capacity provisioned (4mbs)
- scales on throughput peak observed within the last 30 days
- pay per hour and data in out per GB

### Security
- [[KMS]] at rest
- https in flight
- [[IAM]] for access
- can also use client side encryption
- [[VPC]] endpoint for access from [[VPC]]
- monitor with [[CloudTrail]]

## Kinesis Streams vs Firehose
- Streams to capture data in real time, and ingest at scale
- Firehose to load streaming into aws data stores
- Firehose is not real time
- Firehose has close ended consumer options
- Firehose has a single target

## Firehose
- load streaming data into data stores/ lakes and analytic tools
- serverless
- scales to data throughput
- aws managed
- batch
- transform
- encrypt
- SINGLE consumer

### Cost
- pay per Data send
- near real time (60 sec minimum)

### Producers
- Clients
- Apps
- SDK
- Kinesis Agent
- AWS IOT
- [[CloudWatch]] logs and events
- kinesis data streams

### Targets
- [[S3]]
- [[Redshift]]
- Elasticsearch
- Splunk
- custom http endpoints

## Data Analytics for SQL Application
- serverless
- pay per consumption rate
- read from Data Streams or Firehose
- use SQL Statements while referencing [[S3]]
- send against to another Kinesis Stream or Firehose
- stores data

### Usage
- Real Time analytics

## Data Analytics for Apache Flink
- Use Flink (Java, Scala or SQL) to process or analyze streaming data
- provision compute resources
- parallel computing
- automatic scaling
- backups
- any apache flink feature
- uses aws managed cluster behind the scenes

## Sources
- Kinesis Data Steams
-  [[MSK]]

## Usage
- more powerful queries
- run complex queries

## Data Ordering in SQS vs Kinesis
- kinesis your producers need to use the same partition/shard key for related data
- in [[SQS]] there is no ordering
- in [[SQS]] FIFO there is only one consumer and order stays the same
- in [[SQS]] FIFO queue if you want to send related data to different consumers you use a group id, which works then similar to kinesis

### [[SQS]] VS [[SNS]] VS [[Kinesis]]

#### [[SQS]] 
- pull data then delete message via api call from consumer
- Message is processed by exactly one consumer (hopefully)
- as many workers at you want
- scales indefinitely
- need fifo for order

#### [[SNS]]
- push same data to multiple subscribers
- data is not persistent
- fan out to combine with SQS

#### Kinesis
- standard 2mb per shard pull data
- consumers can consume data concurrently
- enhanced fan out 2mb per shard per consumer , push data
- limited amount of consumers (by shard)
- replay data
- meant for real time big data
- ordering at shard level
- data will expire after x days