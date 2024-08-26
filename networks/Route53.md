![[Pasted image 20221101114116.png]]
# Route 53

## TLDR
AWS Name server and Domain Name Registration Service.

## Features
- managed
- scalable
- authoritative DNS (can be updated by customer)
- registrar ( can register own names)
- 100% availability
- health checks


## DNS Record
- domain name
- record Type
- value (ip)
- routing policy
- time to live (TTL)

### Record types

#### A
- hostname to IPv4

#### AAAA
- hostname to ipv6

#### CNAME
- maps DNS queries to another domain or subdomain
- AAAA
- CNAME
- NS

#### Alias
- can target a root domain (cname can not)
- can only be used for aws resources

## Endpoint types

### Outbound
- used by resources in [[VPC]] to resolve DNS queries to resources outside of the [[VPC]]  (e.g. on premise)

## Inbound
- used by resources outside of aws to resolve DNS name to resources inside a [[VPC]]

## Routing Types

### Weighted
- split traffic % to a % to b

### Latency based
- route to record with least latency for user