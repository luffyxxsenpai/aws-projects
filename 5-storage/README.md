# STORAGE
- aws provides 3 main type of storage system

1. Block storage
    a. instance storage
    b. EBS volume

2. File storage
    - EFS (elastic file system) for linux
    - EFX for windows

3. Object storage
    - S3 for unstructured data
    - Glacier (archival storage)

# BLOCK STORAGE
1. Instance Storage
    - physically attached to the host server
    - ephermal storage, data is lost when instance stops or terminates
    - very high performance, low latency
    - included in instance price (no additional cost)

2. Elastic Block Store
    - network attached storage
    - persistent data
    - multiple volume types avalilable (gp3, io2, st1, sc1)
    - additional cost beyond ec2 pricing
    - can be deattached/reattached to different instances
    - supports snapshots and encryption
    - AZ dependent so can only be used in the specific AZ it was created


# PRACTICAL ON BLOCK STORAGE

1. create  a simple ec2 with multiple ebs block attached, i have added an extra 4gb and 2gb block.


2. we can run lsblk in ec2 to see our attached drives

3. create a partiiton and filesystem using fdisk and mkfs
4. mount the filesystem using mount /dev/xvdb1 /test




