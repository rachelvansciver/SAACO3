![[Pasted image 20221101204757.png]]
# Elastic Block Store

## TLDR
This is network storage attached to an [[EC2]] instance.

## Features
- Network Drive
- persist Data after Termination
- can only be mounted to one instance at once
- limited to AZ which it was created
- can be attached and detached quickly
- need snapshot to move AZ
- uses provisioned capacity (Size and IOPS)
- you get billed even if drive is not full
- delete on termination is an option (defaults to true for root volume, not true for other volumes)
- can be modified while in use (I/O's and capacity)

## Snapshot
- is a Backup, can be done during attachment
- Backups can be copied to different region
- snapshot can be done while the volume is being used

### EBS Snapshot Archive
- cheaper Snapshot storage but longer restore time

### EBS Recycle Bin
- can enable recycle for recovery (retention 1day - 1 year)

### Fast Snapshot Restore (FSR)
- cost a lot
- no latency with restore

## Volume types
- only SSD volumes can be used as boot volumes

### GP2/GP3
- general purpose SSD
- cost effective Storage, low latency
- System boot volumes, virtual desktops, development and test environments
- 1 GiB - 16 TiB

#### gp3
- base line of 3k iops and 125mibs
- can be increased to 16k iops and 1k mibs

#### gp2
- small 
- burst up to 3k iops
- size of volume and iops are linked up to 16k iops max
- 3 iops per gb

### IO1/IO2
- high performance SSD
- mission critical, low latency
- 4GiB - 16TiB
- max Piops 64k for nitro ec2 
- max Piops 32k for non nitro
- io2 ist just better
- iops gb ratio 50:1 (10GB max 500 iops)

#### io2 block express
- sub millisecond latency
- max piops 256k 
- iops gb ratio of 1000:1

### HDDs
- 125mb - 16 Tb
- cannot be boot volume

#### st1 - low cost hdd volume
- designed for frequently access and throughput intensive
- low cost
- bit data workloads , data warehouses, log processing
- max 500mbs and 500 iops

#### sc1
- cold ssd
- hdd less frequently accessed workloads (lowest cost)
- 250mbs and 250 iops

### Provisioned iops ssd (piops)
- critical business application with sustained iops performance
- application which need more than 16k iops
- good for database workloads, good storage pref and consistency
- support ebs multi attach

### Instance Store
- highest performance but ephemeral
- is lost even on hibernation
- cannot be detached and attached to other [[EC2]]

## EBS Multi attach
- Same AZ can attach same volume to multiple instances
- only available for io2 and io1
- each instance has full permissions
- cluster linux applications
- application must manage concurrency
- max of 16 [[EC2]] instances
- file system must be cluster aware

## EBS Encryption
- Data at rest is encrypted
- Data is encrypted in flight between [[EC2]] and [[EBS]]
- Snapshot is encrypted
- Volumes created from encrypted snapshot are encrypted as well
- handles by aws behind the scenes
- minimal impact of latency
- uses keys from [[KMS]] (AES-256)
- copying and unencrypted snapshot enables encryption

### Encrypt currently not encrypted
- created snapshot
- encrypt snapshot
- create volume from snapshot
- attach new volume

## Raid

### Raid 0
- use if I/O is more important than fault tolerance
### Raid 1
- use if fault tolerance is more important than I/O
