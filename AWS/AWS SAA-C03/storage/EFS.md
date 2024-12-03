- Amazon EFS
	- serverless
	- strong consistence and file locking
	- To access **EFS file systems from on-premises**, you must have an **AWS Direct Connect** or **AWS VPN connection** between your on-premises datacenter and your Amazon VPC.
	- its file storage service , not object storage service
- A **mount target** provides an IP address for an NFSv4 endpoint that you use to mount an Amazon EFS file system.
- Amazon EFS does not support SMB (Server Message Block)
- Amazon FSx for Lustre
	- provides two file system deployment options:
		- **Scratch**
			- supports SSD storage
			- for temporary file storage and short term data process 
			- no data replication
			![[Scratch FSx for Luster.png]]
		- **Persistent**
			- supports SSD storage
			- supports HDD storage
			- these are designed for long term storage and workloads
			- Data is automatically replicated to with the same AZ
			![[Persistent FSX for Luster.png]]
	 
	- serverless
	- high performance file system
	- integrate **with Amazon S3**
	- ability to process cold data and hot data
	- can allow **S3 objects as File system**
	- for applications that required fast storage
	- storage capacity manually increased
	- used for workloads
		- Machine learning
		- High performance computing
		- video processing
		- financial modelling
- Amazon FSx for Windows File Server
	- **does not allow you** to present **s3 objects as File system**
	- Microsoft AD integration
	- support the use of **Distributed File System**
	- Share access possible
	-  can connect your file system to Amazon EC2, Amazon ECS, VMware Cloud on AWS, Amazon WorkSpaces, and Amazon AppStream 2.0 instances
##### EFS Storage Clasess
![[EFS Storage Clasess.png]]
- **EFS Standard-IA Storage** Class
	- to store files that are not accessed every day
	- A regional storage class for infrequently accessed data.
	- High Durable
- **EFS standard storage** class
	- ideal for workloads that require the **highest levels of durability and availability**
	- It offers the highest levels of availability and durability by storing file system data redundantly across multiple Availability Zones in an AWS Region.
	- high durable 
 - **Amazon EFS with One Zone storage classes**
	 -  For frequently accessed files stored redundantly within a single Availability Zone in an AWS Region.
	 - less Durable
 - **EFS One Zone-IA (One Zone-IA)**
	 -  A lower-cost storage class for infrequently accessed files stored redundantly within a single Availability Zone in an AWS Region.
	 - less Durable
##### EFS Lifecycle Management
-  **When enabled,** Lifecycle Management migrates files that haven't been accessed for a set period of time to an infrequent access storage class, Standard-IA or One Zone-IA.
- - Lifecycle management uses an internal timer to track when a file was last accessed and not the POSIX file system attribute that is publicly viewable.
-  **EFS Intelligent‐Tiering**
##### EFS replication
- **When enabled,** Amazon EFS Replication automatically and transparently replicates the data and metadata on your EFS file system to a new destination EFS file system that is created in an **AWS Region that you choose.**
##### EFS Performance Modes
- **General Purpose (Default)**
	- latency-sensitive use cases
	- Ideal for web serving environments, content management systems, home directories, and general file serving, etc.
- **MAX I/O**
	-  ideal for highly parallelized applications and workloads, such as big data analysis, media processing, and genomic analysis
	- is not available for file systems using One Zone storage classes.
##### EFS Throughput Modes
 - Provisioned Throughput Mode
	 -  throughput of the file system (in MiB/s) can be instantly provisioned independent of the amount of data stored.
 - Bursting Throughput Mode
	 - throughput on EFS scales as the size of the file system in the EFS Standard or One Zone storage class grows
##### EFS Security
 - EFS supports two forms of encryption for file systems
	 -  Encryption in transit
		 - Encryption in Transit can be enabled when you mount the file system.
	- Encryption at rest
		- encrypts all the data and metadata
		- can be enabled only when creating an EFS file system.
		- -to encrypt an existing unencrypted EFS file system, create a new encrypted EFS file system, and migrate the data using AWS DataSync.
##### EFS Access Points
- - EFS access points are application-specific entry points into an EFS file system that make it easier to manage application access to shared datasets.


##### LINUX
- POSIX
##### Windows
- SMB
