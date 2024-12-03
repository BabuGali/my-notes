##### Overview
- AWS proprietary technology,
- managed serverless NoSQL database, 
- **milliseconds latency**
- **Capacity modes**: provisioned capacity with **optional auto-scaling** or **on-demand capacity**
- Can replace ElastiCache as a key/value store ( storing session data for example, using TTL feature)
- Highly Available, Multi AZ by default, **read and writes are decoupled**, transaction capability
- DAX cluster for read, cache, microsecond read latency
- Security, authentication and authorization is done **through IAM**
- Global table feature: active-active setup
- Great rapidly evolve schemas
- on-demand vs provisioned capacity
##### Global tables
- Global tables replicate your DynamoDB tables automatically across your choice of AWS Regions
- Read and write locally, access your data globally
- to support cross-region reads with low latency updated and the ability to quickly failover between regions
- DynamoDB global tables is a much costlier solution than Aurora Global Database
- Useful when you want to have multi-master and multi region database without building a replication solution manually
##### DynamoDB Accelerator ( DAX )
-  DAX is a fully managed and highly available **in memory cache for amazon DynamoDB**
##### DynamoDB Transactions
- useful when you want to accomplish ACID properties in your dynamoDB table
##### Event Processing
- **DynamoDB streams** to integrate with AWS Lambda, or Kinesis Data streams
- DynamoDB Streams are **a time-ordered sequence of events recording all the modifications for DynamoDB tables in near real-time**
##### load
- for unpredict high number of writes and reads
	-  enable auto scaling
- for predict high number of writes and reads
       - choose provisioned capacity
###### Indexes & Kyes
- Primary key
	- 1. Partition Key ( primary key)
	- 2. Sort Key ( composite key )
- **Partition Key (hash attribute)** - composed of one attribute, uses the key value in hash function
-   **Sort Key (range attribute)** - Partition Key + Sort Key,  same partition key but different sort key values
- DynamoDB uses indexes for primary key attributes to improve accesses.
- secondary indexes
	- **Global Secondary Index**
		-  a partition key and an optional sort key that are different from base table's primary key
		- Eventual consistency
		- use DynamoDB Global Secondary Index when you need to support querying non-primary key attribute of a table.
	- **Local Secondary Index**
		- must have the same partition key but a different sort key from the base table.
		- Eventual and strong consistency
		- use DynamodB Local Secondary index when you need to support querying items with different sorting order of attributes.

##### Backups
- **automated backups up to 35 days** with PITR( restore to new table), or **on-demand backups**
- its customer responsibility to turn on PITR ( point in time recovery)
- export to S3 without using RCU ( read capacity units) within the PIR window, import from s3 without using WCU
##### Use Cases
- serverless applications development ( small documents 100s KB)
- **Distributed serverless Cache**