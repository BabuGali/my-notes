#### Overview
-  is a **relational database** service d**eveloped and offered** by Amazon Web Services
- Compatible API for PostgreSQL / MySQL separation of storage and compute
- **backup retention period** ( 1 to 35 days), default is one day
-  Storage : **data is stored in 6 replicas, across 3 AZ** ( can not change) - high available, self healing, auto scaling
- Compute : Cluster of DB instance across multiple AZ, **auto scaling of read replicas**
- Same security / monitoring / maintenance  feature as RDS
- **Aurora Serverless** - **for unpredictable / intermittent workloads, no capacity planning**
- **Aurora Multi-Master** - **for continuous writes failover** ( high availability )
- **Aurora Global database** - up to 16 DB read instances in each region, <1 second storage replication
- **Aurora Machine Learning** - perform ML using SageMaker & Comprehend on Aurora
- **Aurora Database Cloning** - new cluster from existing one, faster than restoring a snapshot
##### Amazon Aurora has two DB cluster storage configurations
- You can switch from Aurora Standard to Aurora I/O-Optimized once every 30 days.
- **Aurora I/O-Optimized**
- **Aurora Standard**
	- Aurora Standard is the best choice when your I/O spending is less than 25% of your total Aurora database spending.
- ##### Aurora Global Database
	- it support replicating your databases across multiple regions with minimal impact on performance
	- can recover from disaster fairly and quickly
	- you can choose two different approaches to failover
		- Managed planned failover
		- Unplanned failover
##### Aurora Replica
- two main purposes
	- queries read operations ( **to handle any spikes**)
	- to increase availability 
- availability up to 15 low-latency read replicas, point-in-time recovery, continuous backup to Amazon S3 and replication across three availability zones.
- Each read replica associated with a priority tier (0-15). In the event of failover, aurora will promote the read replicate that has highest priority( the lowest numbered tier). It wo are more replicas share the same priority then promote highest in size.
#### Backup And Restore Options
- You **can't disable automated backups** on Aurora
- Aurora backups are **continuous and incremental**  so you can **quickly restore to any point** **within the backup retention period**
- Aurora backups **are stored in Amazon S3**.
- if need backup beyond the backup retention period - **then take the snapshot**
- **Backup Window**
	- daily during the preferred backup window
	- you can't specify a backup window from AWS management console, through API only
	- if you don't specify, then Aurora assigns a **default 30-minute backup window**
#### Cluster Support
- aurora cluster supports FIVE endpoints
	1. cluster endpoint - connect to the primary DB instance of the DB cluster
	2. Reader endpoint - it load the balances between all the available read replicas
	3. custom endpoint - connected to the user defined DB instance
	4. Instance endpoint - connects to the specific DB instance
##### Failover
- If the primary instance in a DB cluster fails, **Aurora automatically fails over** in the following order:
	- If Aurora Read Replicas are available, promote an existing Read Replica to the new primary instance. If there are multiple Aurora Read Replicas, the criteria for promotion is based on the priority that is defined for Read Replicas
	-  If no Read Replicas are available, then create a new primary instance
##### automatic features to enhance reliability
- **Storage auto repair**
	- this helps data loss post disk failure. if any segment of the disk fails, it automatically recovers the data on the segment by using data store in other cluster volumes
- **Survivable page cache**
	- In Aurora, each DB instance's page cache is managed in a separate process from the database, which allows the page cache to survive independently of the database.In the unlikely event of a database failure, the page cache remains in memory, which keeps current data pages "warm" in the page cache when the database restarts. This provides a performance gain by bypassing the need for the initial queries to execute read I/O operations to "warm up" the page cache.
- **crash recovery**
	- it can be used for fast recovery post any crash in the database. with this feature it recovery asynchronously on parallel threads.
#### Use cases
- same as RDS, **but with less maintenance** / **more flexibility** / **more performance** / more features  
