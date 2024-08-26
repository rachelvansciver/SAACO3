![[Pasted image 20221030232125.png]]
# Kubernetes

## TLDR
Kubernetes in AWS. [[ECS]] Default options are not Kubernetes, but AWS own tech.

## Options

### Managed Node Groups
- Creates [[EC2]] instances for you
- [[ASG]] managed by [[EKS]]
- Supports on demand and spot instances

### Self Managed
- [[EC2]] are created by the user and registered to the cluster
- Can use prebuilt [[EKS]] optimized [[AMI]]
- Supports on demand or spot instances

### Fargate
- No nodes, instances or maintenance required

## Data volumes
- Need to specify storage class
- [[EBS]] (for [[EC2]] version only)
- [[EFS]] (works with fargate)
- [[FSxLustre]]
- FSx for NetApp ONETAP

## Authentication
- Need a config map to map IAM to Kubernetes RBAC System (is automatically created)