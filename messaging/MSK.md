# Amazon Managed Streaming
- alternative to Kinesis
- Fully managed apache Kafka on AWS
- cluster
## MSK Serverless
- no provisioning
- automatic scaling

## Difference to Kinesis
- Kinesis 1 MB limit per msg, msk 10 mb
- kinesis shard, kafka topics
- kafka doesn't enforce ssl
- kafka can only add partitions to a topic

## Consumers
- Apps (EC2, ECs, EKS)
- Kinesis Data ANalytics
- GLUE
- Lambda