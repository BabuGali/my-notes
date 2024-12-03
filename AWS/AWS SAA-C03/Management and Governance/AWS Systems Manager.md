- Manage your resources on AWS and in multi-cloud and hybrid environments
- AWS Systems Manager is a secure end-to-end management solution for resources on AWS and in multi-cloud and hybrid environments.
-  **AWS Systems Manager VS Application Manager**
-  Application Manager, a capability of AWS Systems Manager, helps DevOps engineers investigate and remediate issues with their AWS resources in the context of their applications and clusters
- Application Manager reduces the time it takes for DevOps engineers to detect and investigate issues with AWS resources.
- **AWS Systems Manager Parameter Store**
	- to store secret keys, instead of in source code
- AWS Systems Manager is the operations hub for your AWS applications and resources, and is broken into four core feature groups.
	- Operations Management
	-  Application Management
	-  Change Management
	-  Node Management
##### AWS Systems Manager Parameter Store Vs Secret Manager
- Both services have a versioning feature
- **Secret Manager**
	- Secrets Manager was designed specifically for confidential information that needs to be encrypted
	- You can’t store data in plaintext in Secrets Manager.
	- Can have ability to rotate the secret
	- cross-account access.
	- Built in Password Generator

- **Parameter Store**
	- Parameter Store was designed to cater to a wider use case, not just secrets or passwords, but also application configuration variables like URLs, DB hostnames, custom settings, product keys, etc.
	- can not have ability to rotate the secret
	- Costs nothing to use it.
##### AWS System Manager Run Command
- Run command allows you to automate the administrative tasks like update package all EC2 instances