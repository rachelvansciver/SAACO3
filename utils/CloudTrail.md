# Cloud Trail for Cloud Watch
- tracks and logs api requests within the aws account
- used for governance, compliance, operational and risk auditing
- can be used to trigger events on AWS [[EventBridge]]
- enabled by default
- a trail can be one or all regions
- stored for 90 days default
- transfer to [[S3]] for longer retention 

## Management Events
- Configuring Security 
- ...
- enabled by default
- read and write event types
## Data Events
- by default no logged
- e.g. S3 object level activity
- read and write event types

## CloudTrail Insights Events:
- ML
- Detect unusual activity in write events
- send to [[S3]] , [[EventBridge]] and cloudtrail console

## Security
- logs are encrypted by default using [[KMS]] AWS Managed keys