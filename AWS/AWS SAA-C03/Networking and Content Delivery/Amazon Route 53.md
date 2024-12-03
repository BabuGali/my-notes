- DNS ( Domain Naming System ) service
- It connects user requests to internet applications which are running on AWS or on-premises
- Route 53 health checks can be used for any endpoint that can be accessed via the Internet ( on-premises also)
> It is recommended to use DNS names or URLs instead of IPs wherever possible 
- Health checks
		- Route 53 do health check then do failover -- **disaster recovery from one region to another region**
		- The health of a specified resource, such as a web server.
		- The status of other health checks.
		- The status of an Amazon CloudWatch alarm
- Route 53 resolver
	1. To create conditional forwarding rules
- Route 53 DNS Firewall 
	1. To control filter inbound traffic to VPC
	2. Firewall manager can be used to centrally configure the rule
- Route 53 **Application Recovery Controller**
	1. Readiness Check - continually audit for recovery readiness
	2.  Routing Controller - its simply ON/OFF switches that enable you to route traffic from one replica to another
	3. Safety Rules 
- Traffic Flow
	1. to build routing system with the combination of geographic location, latency, and availability to route traffic from your users to your cloud or on-premises endpoints.
	2. The geoproximity routing policy is available only if you use traffic flow

- Routing Policies
	 1. **Simple Routing Policy**
		 - route traffic to single resource 
		 - If multiple values returned, the client **choose one at random** ( client side load balancing)
		 - **No health check**, if multiple resources returned, some of them unhealthy
		 - use this policy for records in a **private hosted zone**
	 2. MultiValue Answer Routing Policy
		 - Can return only healthy resources ( max 8)
		 - you can use this  routing policy for records in a private hosted zone.
	 3. Latency Routing Policy
		 - Redirect to resource that has low latency
		 - 
	 1. Geolocation Routing Policy
	 2. Geoproximity Routing Policy
		 - To **use when you want to route traffic based on the location of your resources**
	 3. Weighted Routing Policy
		 1. blue-green deployments
		 2. partial rollouts of software, load balancing, and load-testing.
		 3. 30% vs 70%
	 4. Failover Routing Policy
		 1. active-passive failover configuration
		 2. To use a failover routing policy, you configure active-passive failover, where one resource (the primary resource) handles all the traffic when it’s healthy and the other resource (the secondary resource) only handles traffic when the first resource isn’t healthy.
	 5. IP based  Routing Policy

- Private hosted Zone
	- A private hosted zone is **a container that holds information about how you want Amazon Route 53 to respond to DNS queries for a domain and its subdomains within one or more VPCs that you create with the Amazon VPC service**



- Alias Record
	-  Alias records only support A or AAAA record types
	- Alias records **let you route traffic to selected** AWS resources, such as CloudFront distributions and Amazon S3 buckets
	- When **you use an alias record to route traffic to an AWS resource**, **Route 53 automatically recognizes changes in the resource**.( say IP address changes)
	- create alias record for xxx.com that routes the traffic to www.xxx.com
	- you can create an alias record named acme.example.com that redirects queries to an Amazon S3 bucket that is also named acme.example.com. You can also create an acme.example.com alias record that redirects queries to a record named zenith.example.com in the example.com hosted zone.
- CNAME
    - A CNAME record can redirect DNS queries to any DNS record. For example, you can create a CNAME record that redirects queries from acme.example.com to zenith.example.com or to acme.example.org.
    - You can't create a CNAME record that has the same name as the hosted zone
- non-alias record
- zoneApex
- NS Record