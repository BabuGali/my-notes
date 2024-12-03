#### Overview
- Managed PostgreSQL / MySQL / Oracle / SQL server /Maria DB/ Custom
- Provisioned RDS instance size and EBS Volume Type & Size
- **Auto scaling capability for storage**
- **Support for read replica and Multi AZ** ( for high availability in case of DR)
- Security through IAM, security groups, KMS, SSL in transit
- **Automated backup with point in time restore feature**( up to 35 days)
- Manual DB snapshot for longer-term recovery
- Managed and Scheduled maintenance(**with downtime**)
- Support for **IMA authentication**, integration with Secret Manager
- RDS custom for access to and customise the underlying instance and its OS ( oracle & SQL server)
- Multi-AZ follows **synchronous replication** and spans **at least two availability zones within a single region**. **Read replicas** follows asynchronous replication and **can be within an availability zone, cross-AZ or Cross-region**
- When provision Multi-AZ, then Amazon RDS automatically creates a primary instance and synchronously replicates the data to a standby instance in a different AZ
- Amazon RDS used the engines Native asynchronous replication to update the read replica whenever there is a change to the source DB instance 
##### Failover
- read replicas wont help in case of failover. Read replicas just used to handle read-heavy workloads 
- RDS Proxy
	- Amazon RDS Proxy can improve the application recovery time after database failover
	- use RDS Proxy  to reduce downtime to minimize client disruption when admin planned for failover to do admistrative actions such as rolling upgrade etc
	- During failover RDS proxy automatically connects to a standby database instance 
	- 
##### Snapshots
- For Manual snapshots in an unencrypted format, accounts can directly restore a DB instance from the snapshot
- For manual snapshots in an encrypted format, accounts first need to copy the snapshot and then restore it to a DB instance
- you can not share automated snapshots with other AWS accounts. To share an automated snapshot, copy the snapshot to make a manual version, then share it
- You can share encrypted manual snapshots that don't use the default Amazon RDS encryption key
- You can't restore shared encrypted snapshots directly from the destination account. First, copy the snapshot to the destination account by using an AWS KMS key in the destination account. Then, restore the copied snapshot.
- - To share snapshots that use the default AWS managed key for Amazon RDS (aws/rds), encrypt the snapshot by copying it with a customer managed key. Then, share the newly created snapshot.
- - You can share snapshots across AWS Regions. First share the snapshot, and then copy the snapshot to the same Region in the destination account. Then, copy the snapshot to another Region.
- You can't share manual snapshots of DB instances that use custom option groups with persistent or permanent options. For example, this includes Transparent Data Encryption (TDE) and time zone
- Multi-AZ deployments
	- Main purpose is **high availability**
	- Non-Aurora - **Synchronous replication**; Aurora - asynchronous replication 
	- Non-Aurora - only the primary instance is active, Aurora - all instances are active
	- **automated backups are taken from stand by**
	- **Always span at least two availability zones with in a single region**
	- Automatic failover o standby( non-aurora)
- Multi-region deployments
	- for disaster recovery and local performance
	- **asynchronous replication** 
	- all regions are accessible and can be used for reads
	- Automated backups taken from each region
	- Each region can have a multi-AZ deployments
- Backup
	- RDS snapsshots and automated backups are stored in S3
- Read replicas
	- for scalability
	- asynchronous replication 
	- all regions are accessible and can be used for readscaling
	- no backups configured by default 
	- can be within an availability zone, cross-AZ, or cross-region
#### use cases
- Store relational databases, perform SQL queries , transactions
- 
![[Amazon RDS.png]]
	