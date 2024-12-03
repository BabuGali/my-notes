- User Types
	1. Account Owner or Root User
		1.  Root user is account owner and is created when AWS account is created
	2. IAM User
	3. Organization Management Account Owner
	4. Organization Member Account Owner
- Assume role
	- The administrator of the specified account can grant permission to assume this role to any IAM user in that account
	- allows you to **grant temporary credentials** with additional privileges to users as needed, following the principle of least privilege
- Assume Role Vs Pass Role
##### IAM Identity Center
- It helps you securely create or connect your workforce identities and manage their access centrally across AWS accounts and applications.
- IAM Identity Center is the recommended approach for workforce authentication and authorization on AWS for organizations of any size and type.
- Using IAM Identity Center, you can create and manage user identities in AWS, or connect your existing identity source, including Microsoft Active Directory, Okta, Ping Identity, JumpCloud, Google Workspace, and Azure Active Directory (Azure AD).
-  IAM Identity Center allows you to enforce MFA for all your users
- IAM Identity Center makes it easy for you to create and use fine-grained permissions for your workforce based on user attributes defined in your IAM Identity Center identity store
- Successor to Single Sign On
- can access AWS 
- Enable single sign on access to your AWS applications
- Enable single sign on access to Amazon EC2 windows machines
- Enable single sign on access to cloud based applications
##### Resource based policies
- All the resources in AWS could not support resource based policies
- 