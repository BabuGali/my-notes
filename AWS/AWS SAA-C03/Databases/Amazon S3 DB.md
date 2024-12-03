###### Overview
- S3 is a Key / Value store objects
- Great for **bigger objects, not so great for many small objects**
- Serverless, scales infinitely, max object size is 5 TB, versioning capability
##### Tiers
- S3 standard
- S3 infrequent Access
- S3 Intelligent
- S3 Glacier +  life cycle policy
##### Features
- Versioning, Encryption, Replication, MFE-Delete, Access Logs
###### Security
- IAM, Bucket Policies, ACL, Access Points, Object Lambda, CORS, Object/Vault Lock
##### Encryption
-  SSE-S3, SSE-KMS, SSE-C, client-side, TLS in transit, default encryption
##### Performance
- Multi-part upload, S3 Transfer Acceleration, S3 select
#### Batch Operations
- On objects using S3 batch, listing files using S3 Inventory
##### Automation
- S3 event notifications ( SNS, SQS, Lambda, EventBridge)
##### Use Cases
- static files, key value store for big files, website hosting
