#### Overview 
- Global service
- Keywords
	- Requester
	- Edge locations
	- Regional Cache Layer
	- Origin Shield - improve the network performance and cache hit ratio 
	- Origin Server
	- custom Origins
	- closest edge locations
- Content Delivery Network - CDN
- Use CloudFront distribution in front of the application load balancer
- **Edge locations are present outside** of the VPC, so the origin's SG must be configured to allow inbound request from the list of public IPs of the edge locations 
- Improved read performance, content is cached at the edge
- End user requests are served by closet edge location
- Increases lower latency
- Supports DDoS protection, integration with Shield, Web application Firewall
- Supports HTTPS and web sockets
- To improve cache Duration
	- set how long in the **Cache - Control header** in the application
- **To use Amazon CloudFront**
	- Register your origin servers with Amazon CloudFront (bucketname.s3.amazonaws.com)
	-  Include the cloudfront.net domain name, or a CNAME alias that you create, in your web application, Each request made using the cloudfront.net domain name (or the CNAME you set-up) is routed to the edge location best suited to deliver the content with the highest performance
- To **block specific IP at the CloudFront level**, deploy a WAF on CloudFront

==To restrict access to ELB directly when it is being used as the origin in a CloudFront distribution, create a VPC Security Group for the ELB and use AWS Lambda to automatically update the CloudFront internal service IP addresses when they change.==
#### OAC vs OAI
- **CloudFront origin access identity (OAI) provides similar functionality as origin access control (OAC), but it doesn't work for all scenarios**. This is why we recommend using OAC instead. Specifically, OAI doesn't support: Amazon S3 buckets in all AWS Regions, including opt-in Regions.
- OAI wont support integration with SSE-KMS
-  Comprehensive HTTP methods support – OAC supports GET, PUT, POST, PATCH, DELETE, OPTIONS, and HEAD.
- OAC supports accessing S3 in all AWS regions, including existing regions and all future regions. In contrast, OAI will only be supported in existing AWS regions and regions launched before December 2022
#### Cloud front Origins
- different origins for different type of connect on a single site
- S3 bucket
	- cached them at edge
	- Enhanced security with CloudFront - OAC - Origin Access Control - only access by CloudFront
	- OAC replacing Origin access Identity
	- Cloud front can be used as ingress ( to upload files to S3)
- Custom Origin(HTTP)
	- Application Load Balancer
	- ALB must be public
	- EC2 instances can be private
	- EC2 instance
		- EC2 instances must be public
	- S3 website(must first enable the bucket as a static S3 website)
	- Any HTTP backend you want ( including on-premises)

#### Signed Cookies/URLs

- used to make a CloudFront distribution to private ( only to specific users)
	- Signed Cookies => access to multiple files
	- Signed URLS => access to individual files
	- Whenever we create a signed URL / cookie, we attach a policy specifying
	-  URL / Cookie Expiration (TTL)
	- **IP ranges** allowed to access the data
	- Trusted signers (which AWS accounts can create signed URLs)
- CloudFront signed URL - need to change URL for each customer
- S3 presigned URLs - expiration date
- cloudFront signed cookies - no need to change URL for each customer
- there is no s3 signed cookies
#### Multiple Origin
- Route to different origins based on the path in the request
	- /api/** => request goes to ALB
	-  /* =>request goes to S3
#### Origin Groups
- consist of a primary and a secondary origin ( can be in different regions)
- automatic failover to secondary
- Use when getting 504 (gateway timeout) Error
#### Field Level Encryption
- Sensitive information sent by the user is encrypted at the edge close to user which can only be decrypted by the web server (intermediate services can't see the encrypted fields)
-  **Asymmetric Encryption** (public & private key)
-  Max 10 encrypted field
- Supports **Server Name Indication (SNI)** to allow SSL traffic to multiple domain
##### Cost
- **Free** for origin fetches from any AWS origin such as Amazon Simple Storage Service (S3), Amazon Elastic Compute Cloud (EC2), or Elastic Load Balancers.
- **Origin Shield requests**
	- If you set up Origin Shield as a centralized caching layer, request fees are charged based on the AWS Region
- 
#### CloudFront Geo Restirctions
- allowed list 
- blocklist
- No restriction
#### CloudFront Cache Invalidation
- Entire cache refresh
- Partial cache refresh

#### Global Accelerator
- AWS Global Accelerator vs CloudFront
	- Global Accelerator
		- uses edge locations to find an optimal pathway to the nearest regional end point
		- used for non-HTTP like gaming(UDP), IOT(MQTT) and voice over IP
		- HTTP for static IP address
		- TCP and UDP
	- CloudFront
		- Dynamic content
		- HTTP and websockets ( TCP)
		- does not support UDP protocol
		- uses edge locations to cache the content
- Use cases
	- UI and Backend in US region, then what only another UI in India and backed same as in US 
		- then use cloud front with custom origin