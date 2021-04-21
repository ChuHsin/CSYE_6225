## Block Level Storage
Amazon EBS, Amazon EFS
The OS is the intermediary between the application that wants to access files and the underlying file system and block-level storage.

OS provides access to bls

### BLS on AWS
AWS provides 2 kinds of bls
1. Network Attached Storage (NAS) via AWS EBS service
2. Instance Storage

EFS Elastic File Storage
EBS Elastic Block Storage
S3 Object Storage
Instance Store

## Amazon EBS
Provides persistent block storage volumes for use with EC2 instances in AWS.
Think of EBS as disks that you attach to your virtual machine.

Use Cases: databases, data warehousingm, big data app, other low latency interactive app taht demand the gihest IOPS or throughput and lowo latency with consistent, predictable performance.

* EBS volumes are not part of EC2
* attached to your EC2 via a network connection.
* EBS volume can be attached to NO EC2 instance or one EC2 instance at a time. Cannot connect to multiple instances.
* EBS volumes can be used like normal hard disks.

Snapshot for **clone** of EBS volume

Availability 99.999% , only in one zone
automatically replicated within its availability Zone to protect you from component failure.

### Snapshot
stored incrementally: only changed after your last snapshot are saved.

### Encryption
data-at-rest
data-in-transit

## EC2 Instance Store
* provides temporary bls for your isntance;
* this storage is located on disks that are physically attached to the host computer.
* ideal for temporary storage or data taht is replicated from elsewhere.

### Instance store volumes
* An instance store consists of one or more instance store volumes exposed as block devices.
* the virtual devices for instance store volumes are ephemeral[0-23], indexed from 0
ephemeral 暂存的，短生的

### Instance Store Lifetime
* persists only during the lifetime of its associated instance.
* if an instance rebots, data in the instance store persists.
* data in the is is lost under
  * underlying disk failed
  * stop instance
  * terminate instance

## Amazon EFS
 
Elastic File System supports Network File System version 4 (NFSv4) and 4.1, which makes it easy to migrate enterprise applications to AWS or build new ones.
Highly available and highly durable -- stores data and metadata across multiple availability zones in a region.

### Use cases
Media processing workflows
contetn management
web serving
home directories

## Object Storage
Separatino of metadata and data allows clients to work only with the metadata for managing and querying data.

### Amazon Simple Storage Service (S3)
unlimited storage space
available and durable
An object in S3 can be as large as 5TB
S3 is accessed using RESTful APIs.

Since it use RESTful APIs, you don't need a OS to use the data.

### Data Consistency Model
All S3 GET, PUT, and LIST operations, are strongly consistent. (change immediately)
eventually consistent (finally it will change)

### Storage Tiers/Classes
* S3
* S3 - IA (infrequently Accessed) pay for retrieval, cost less than s3
* Reduced Redundancy Storage - 99.99% durability and 9999 availability of objects over a given year.
* Glacier - very cheap but used for archival only, takes 3-5 hours to retrieve data from it.

### S3 Bucket

#### Bucket Logging
detailed access logs delivered to a bucket you choose
An access log record contains details about the request, such as the request type, the resources specified in the request worked, and the time and date the request was processed.

#### Bucket Event Notifications
An object created, removed,a Reduced Redundancy Storage (RRS) object lost event.

#### Bucket Versioning
data version control

#### Cross-Region Replication

#### Querying S3
S3 cannot be used as a database or search engine by itself. You can pair S3 with DynamoDB, CLoudsearch, RDS to index and query metadata about S3 butckets and objects.

S3 is not good to use as file system. Consider EFS.

## Relational Databases (Amazon RDS)
Amazon Relational Database Service

### ACID Transactions
Atomicity, Consistency, Isolation, Durability.

#### Atomicity
Requires that each transaction be "all or nothing": if one part fials, then the entire transaction fails, and the db state is left unchanged.

#### Consistency
any transaction will bring the db from one valid state to another.

#### Isolation
transactions are one after the other, transactions were executed sequentially.

#### Durability
once execute, the results need to be stored permanently (even if the database crashes immediately thereafter)

### Automated Backups of AWS RDS
Automated Backups, Database Snapshots

Snapshots are done manually, they are stored even after you delete the original RDS instance.

## NoSQL

### CAP Theorem
It is impossible for a distributed computer system to simultaneously provide more than two out of three of the following guarentees:
* **Consistency** - Every read receives the most recent write or an error
* **Availability** - Every request receives a (non-error) response - without guarantee that it contains the most recent write
* **Partition tolerance** - the system continues to opearte despite tan arbitrary number of messages being dropped (or delayed) by the network betwwen nodes.

Partition tolerance is always important, so you need to choose between consistency and availability.

 ### No SQL DB & Consistency
 eventual consistency, queries for data might not return uopdated data immediately or mgith result in reading data that is not accurate, a problem known as stale read.

 ### Normalization & Denormalization


 ### Polyglot Persistence
choosing the right persistence option for the task at hand.

 ### Concurrency Control Mechanisms
Optimistic
Pessimistic


