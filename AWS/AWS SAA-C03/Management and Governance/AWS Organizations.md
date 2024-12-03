- It is an account management service. you can consolidate multiple AWS accounts into an AWS organization that you can create and centrally manage.
- It is global server, not specific to any region
- It is a free service
-  An Organization has one management account with zero or more member accounts. You can organize the accounts in a hierarchical, tree-like structure with **a root at the top and organizational units nested under the root**. Each account can be directly in the root, or placed in one of the OUs in the hierarchy.
- It is **collection of AWS accounts** that you can organize into a hierarchy and **manage centrally**.
- key words
	1. **Management account**
		-  It can attach policies to entities such as administrative roots, organizational units (OUs), or accounts within your organization
		- You **cannot change** which account in your organization is the **management account**.
		- Cost allocation tags manages is only accessible from the management account of the AWS organization
	1. **Member account**
		-  Member account belongs to only one organization at a time
	2. Organization Unit ( OU) - group of AWS accounts
- It offers
	1. **Centralized account management** of all AWS accounts 
	2. **Consolidate billing** of all member account
- Organization of administrator can **create accounts** or **invite existing accounts** to join the organization
- **AWS organizations enable**
	1. view and manage costs with consolidate billing
	2. Configure AWS services across multiple accounts
	3. Centrally manage policies across multiple AWS accounts
- When member account leaves the organization, the member account can not access cost explore data, that was created when account was in the organization. The data is not delete, and the management account can access it. If member re-joins then the member account can access again
- **AWS control tower**
	 1. offers the easiest way to setup the govern a secure, multi account environment
	 2. create, orchestrate and monitor your multi account environment
	 3. No additional charge, you pay only services enabled by using it
	 4. Use cases
		 1. Setup and manage a multi account environment
		 2.  Govern at with pre-configured controls
		 3. It is for customers who want to **create or manage their multi-account** AWS environment **with built-in best practices**
- **Service Control Policies**
	1. These are organization policies that can be used to manage the permission in your organization
	2. SCP's do not effect **users or roles** in the management account. They affect the only member accounts in your organization
	3. No permissions are granted by SCP's
	4.  **Service control policies vs IAM policies**
		 -  SCPs mainly used along with Organisational unit
		 -  IAM policies **can not restrict the AWS account user**. But with SCPs you can limit the permissions of the root user account
		 - 
