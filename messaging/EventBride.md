![[Pasted image 20221101205129.png]]
# EventBridge

## TLDR
Provides notifications of real time changes in your code, aws services, etc

## Features
- schedule (cron jobs)
- event pattern (email when root user logs in)
- json format
- can archive events
- replay archived events
- event json is typed, can be nice for custom code/lambda
- IAM roles

## Sources
- [[EC2]]
- Code Build
- [[S3]]
- [[TrustedAdvisor]]
- [[CloudTrail]] (any API call)
- schedule (cron)
- 3rd Party
- ...

## Targets
- [[Lambda]]
- [[Batch]]
- [[ECS]]
- [[SQS]]
- [[SNS]]
- [[StepFunction]]
- pipelines
- [[Kinesis]]
- [[SSM]]
- 3rd Party
- ...
## Event Busses
- supports resource based policies
- can allow events from other accounts

### Default
- AWS Services

### Partner Event bus
- supported 3rd party events

### Custom Event Bus
- for custom apps
