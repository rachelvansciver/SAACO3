# CloudFront
- CDN
- data, videos, application and apis delivery
- global
- regional edge caches
- only http based requests

## Origins

### [[S3]]
- caching
- distributing
- enhanced security with (OAI)
- Cloudfront can be upload point to S3

### Custom Endpoint
- [[ELB]] ALB
- [[EC2]]
- [[S3]] Website
- Any HTTP backend

## Geo Restriction
- whitelist countries
- blacklist countries
- use for copyright laws

## Price Classes
- depends on data transfer, but is different for each edge location
- price goes down if you transfer more data

### All
- all regions - best performance - highest price

### 200
- most regions - excludes most exp

### 100
- only cheapest regions 

## Cache Invalidations
- invalidate via api and path

## Customization at Edge
- serverless
- customize a cdn endpoint
- pay per use

### Use cases
- Website security and privacy
- seo
- intelligent route
- bot mitigation
- real time image transform
- a/b testing
- Dynamic Web Apps at Edge
- User prio
- tracking and analytics
- user auth 

### Cloudfront Edge function
- code attached to cloudfront distributions
- runs closer to users for minimum latency
- lightweight written in js
- high scale latency sensitive cns customizations
- sub ms startup times
- managed in cloudfront
- millions of request per second

#### Price
- Free tier available
- 1/5 of [[Lambda]] @Edge

#### Use cases
- cache key normalization (transform request attributes)
- header manipulation
- url rewrites and redirect
- validate jwt tokens

### [[Lambda]] at Edge
- node.js or python
- 1ks of request per second
- can change every part of the request (viewer and origin)

#### Price
- no free tier

#### Use cases
- longer exec time
- adjustable cpu memory
- code depends on 3rd party (AWS CLI)
- Network access
- File System Access
- Http Body Access

## Availability
- can setup origin failover
- an origin group may have a primary and a secondary origin