##### pricing options
- On-Demand
	- hour/second 
	- Use cases
		-  **no longer-term commitments or upfront payments**
		- applications with **short-term** , **spiky, unpredictable workloads** that can not be interpreted 
		- Application being developed or tested on Amazon EC2 **for the first time**
- Reserved Instances
	-  up to 75 % discount compared to on-demand instance pricing
	- provide the **capacity reservation**
	- Use cases
		- Applications with **steady state usage**
		- Applications that required reserved capacity
		- **commit to using 1 or 3 years**
- Metadata
	- http://169.254.169.254/latest/meta-data
- Saving plans
	- offers low prices, in exchange for a commitment to a consistent usage for 1 or 3 year term
	- Savings Plans offer significant savings over On-Demand Instances, just like EC2 Reserved Instances, in exchange for a commitment to use a specific amount of compute power (measured in $/hour) for a one or three-year period
	- You can sign up for Savings Plans for a one- or three-year term and easily manage your plans **by taking advantage of recommendations, performance reporting and budget alerts** in the **AWS Cost Explorer**.
- Saving plans vs RI
	- Reserved Instances are built on the commitment to utilize an instance **at a specific price over a specific term**. Whereas, Savings Plans are built on the commitment **to spend a specified dollar amount per hour over a defined period**.
- Dedicated instances
	- are virtual machines
	- may share hardware with other instances
	- dedicated instances cannot be used for existing software licenses
	- 
- Dedicated hosts
	- its costlier than dedicated instances
	- physical server
	- when you have own software licences
- Spot instances
	- **unused instance**, that available for less price than on demand
	- spare EC2 computing capacity up to 90% of the on demand instances
	- let you take advantage of unused EC2 capacity in the AWS Cloud
	- spot instances can be taken by AWS **with two minutes of notice**
	- Spot fleet is the set of spot instances
	- **Spot fleet** - it selects the spot instance pools
	-  **spot instance pools**
	- **spot price** - current price per hour
	- **spot instance request** 
	- **spot instance interruption** - its a notice
	- Spot blocks are **designed not to be interrupted**
	- When you cancel an active request, it does not terminate the associated instance
	- if the spot request is persistent, then it is opened again after your spot instance is interrupted
	- **Spot Blocks are Spot instances that run continuously for a finite duration (1 to 6 hours)**
	- Use cases
		-  Applications that have **flexible start and end times**
		- at very low compute prices
		-  for stateless , fault-tolerant or flexible applications
		- users with **urgent computing needs for large amount of additional capacity**
- **Elastic Fabric Adapter**
	- Enables customers to run applications requiring high levels of inter-node communications at scale on AWS
	- EFA is available as an optional **EC2 networking feature** that you can enable on any supported EC2 instance **at no additional cost**.
	- EFA provides all of the functionality of an ENA
	- EFA not supports in windows machines
	- Provides all of the functionality of an ENA, with additional **OS-bypass**
	- can attach one EFA per instance
- **Elastic Network Adapter**
	- Next generation of network interfaces
	- provides enhanced networking on EC2 instance
##### Placement Groups
- Placement groups **help us to launch a bunch of EC2 instances close to each other physically within the same AZ**
- placement groups provides high-performance networking
- Being close physically and within the same AZ helps it take advantage of high-speed connectivity to provide low latency, high throughput access.
- you **cannot merge** placement groups
- you **cannot launch dedicated hosts** in a placement groups
- you can migrate instance from one placement group to another
- placement groups cannot span multiple regions
- placement strategies
	- **Cluster**
		- single availability zone
		- for low-latency
		- High performance computing applications
	- **Partition**
		- No partition within a placement group share the same stacks
		- each partitions comprises multiple instances
		- isolate the impact of **hardware failures** within your application
		- used to deploy large distributed and replicated workloads
			- for hadoop, Cassendra and kafka
	- **Spread**
		- across distinct underlying hardware to reduce **correlated failures** 
		- are recommended for applications that have a smaller number of instances that should be kept separate from each other  
##### EC2 Instance life cycle
![[EC2 instance life cycle.png]]

- Pending
	- The instance is preparing to enter the `running` state. An instance enters the `pending` state when it is launched or when it is started after being in the `stopped` state.
	- Not billed
- Running
	- The instance is running and ready for use.
	- Billed
	- The instance store volume erased
- Stopping 
	- The instance is preparing to be stopped.
	- Not billed
	- The instance store volume erased
- stopped
	- The instance is shut down and cannot be used. The instance can be started at any time.
	- Not billed
	- The instance store volume erased
- Rebooting
	- Rebooting an instance doesn't start a new instance billing period because the instance stays in the `running` state.
	- The instance store volume is preserved
- Hibernate
	- Supports only if the EC2 instance is EBS-backed instance
	- When you hibernate your instance, it enters the `stopping` state, and then the `stopped` state. We don't charge usage for a hibernated instance when it is in the `stopped` state, but we do charge while it is in the `stopping` state
	- it pre-warms the instance and after resuming it, it quickly brings the applications to a running state
	- The instance store volume erased
	- All the content of the memory RAM save to EBS volume
	- Once the instance started from the hibernate state, then the following activities are performed
		- The EBS root volume and attached EBS volumes are reattached
		-  The instance ID is not changed
	![[EC2 Hibernate.png]]
- AMI
	- can copy across AWS regions
	- can share with another AWS account
	- coping an AMI backed by encrypt snapshot cannot result in an unencrypted target snapshot
	- you can copy both EBS backed AMIS and instance store Backed AMIs
	- you can copy AMI with encrypted snapshots and also change encryption status during the copy process 
	- unencrypted to unencrypted - yes
	- Encrypted to encrypted - yes
	- unencrypted to Encrypted - yes
	- Encrypted to unencrypted - No