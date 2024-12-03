 #### Overview 
- Managed Reids / Memcached
- In-memory data store, sub-millisecond latency
- Must provision an **EC2 instance type**
- Support for **clustering( redis) and Multi AZ**, Read Replicas (Sharding)
- Security through IAM, Security Grous, KMS, Redis Auth
- Backup / Snapshot / point in time restore feature
- Managed and Scheduled maintenance
- Required some application code changes to be leveraged 
- CloudFront is suitable for website caching , ElastiCache is for application cashing
#### use cases
- Key/Value store, **frequent reads**, less writes, **cache results for DB queries** , **store session data for websites**, cannot use SQL
- for data lookups