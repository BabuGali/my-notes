
 ###### Overview
![[VPC Component.png]]

 ###### CIDR - IP4
- A CIDR consists of two components
- Base IP
	- Represents an IP contained in the range
	- Example: 10.0.0.0, 192.168.0.0
- Subnet Mask
	- Defines how many bits can change in the IP
	- Example: /0,/24, /32
	- /32 => allows for 1 IP (2^0)
	- /31 => allows for 2 IP (2^1)
	- /30 => allows for 4 IP (2^2)
	-  ----
	- ---
	-  /24 => allows for 256 IP (2^8)
##### Availability Zones
-  recommend at least two AZs for high availability.
 ##### Subnet
 - Subnet types
	 - public subnet
	 - private subnet
	 - **VPN-only subnet** -The subnet has a route to a Site-to-Site VPN connection through a virtual private gateway. The subnet does not have a route to an internet gateway.
	 -  ** isolated subnet** - The subnet has no routes to destinations outside its VPC. Resources in an isolated subnet can only access or be accessed by other resources in the same VPC.
- Public Subnets
	- if a subnet is associated with a route table **that has a route to an internet gateway** 
	- A NAT instance or a NAT gateway can be used in a public subnet in your VPC to enable instances in the private outbound IPV4 traffic to the innternet
- Private Subnets
	-  if a subnet is associated with a route table **that has  not a route to an internet gateway**
- AWS reserves 5 IP addresses ( first 4 & last 1 ) in each subnet
- These 5 IP addresses are not available for use and can not be assigned to an EC2 instance
-  **Example** : IF CIDR block 10.0.0.0/24, then the reserved IP addresses are:
	- 10.0.0.0 - Network Address
	- 10.0.0.1 - reserved by AWS for the VPC router
	- 10.0.0.2 - reserved by AWS for mapping to Amazon-provided DNS
	- 10.0.0.3 - reserved by AWS for future use
	- 10.0.0.255 - Network Broadcast Address.  AWS does not support broadcast in a VPC, therefore the address is reserved
	- **Exam Tip**
		-  If you need 29 IP addresses for EC2 instances
		- you can not chose a subnet of size /27 ( 32 I address, 32-5 = 27 <29
		- you need to choose a subnet of size /26 ( 64 IP addresses, 64 - 5  = 59 >29 )

- Allows resources (eg EC2 instances ) in a VPC connect to the internet
- It scales horizontally and is highly available and redundant
- Must be created separately from a VPC
- One VPC can only be attached to one IGW and vice versa
- Internet Gateways on their onw do not allow Internet access
- Route tables must also be edited
###### Bastion Hosts
![[bastion host.png]]
- We can use bastion Host to SSH into our private Ec2 instances
- The Bastion is in the public subnet which s then connected to all other private subnets
- Bastion Host security group **must allow inbound from the internet on port 22** from the restricted CIDR, for example the public **CIDR of you corporation**
- Security Group of the EC2 instances **must allow the** Security Group of the Bastion Host, or the private IP of the Bastion Host 
##### Default VPC
- All new AWS accounts have a default VPC
- new EC2 instances are launched into the default VPC if no subnet is specified
- Default VPC has internet connectivity and all EC2 instances inside it have public IPV4 address
- We also get a public and a private IPV4 DNS names
##### VPC in AWS - IPv4
- VPC - Virtual private Cloud
- you can have multiple VPCs in an AWS region ( max 5 per region - soft limit )
- Max CIDR per VPC is 5, for each CIDR:
	- Min. size is /28 ( 16 IP address )
	- Max. Size is /16 ( 65536 IP address )
- Because VPC is private, only the private IPv4 ranges are allowed
- Your VPC CIDR should not overlap with your other networks ( ex. corporate )
##### Route Table
- **Main Route Table** - The route table that automatically comes with your VPC. It controls the routing for all subnets that are not explicitly associated with any other route table. When you create a VPC, it automatically has a main route table. When a subnet does not have an explicit routing table associated with it, the main routing table is used by default.
- By default, when you create a nondefault VPC, the main route table contains only a local route. If you create a VPC and choose a NAT gateway, Amazon VPC automatically adds routes to the main route table for the gateways
- You can't delete the main route table.
- You can't set a gateway route table as the main route table
- **Custom Route Table** - A route table that you create for your VPC.
- **Route table association** -The association between a route table and a subnet, internet gateway, or virtual private gateway.
- **Subnet route table** - A route table that's associated with a subnet.
- **Gateway route table**—A route table that's associated with an internet gateway or virtual private gateway.
- **Transit gateway route table**—A route table that's associated with a transit gateway.
- A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same subnet route table.
##### Internet Gateway ( IGW)
- It serve two purposes
	- to perform network address translation(NAT)
	- enables resources in your public subnets to connect to the internet and vice versa
- supports IPV4 and PV6
- Allows resources in a VPC connect to the internet
- It scales horizontally and is highly available and redundant
-  Must be created separately from a VPC
- One VPC can only be attached to one IGW and vice versa
- Internet Gateways on their own do not allow internet access
- Route table must be edited
- 
![[Internet Gateway.png]]
##### NAT instance
- [[Image1]]
- NAT = Network Address Translation
- Allow EC2 instances in private subnets to connect to the internet
- Must be launched in a public subnet
- Must disable EC2 settings: Source / destination Check
- **Must have Elastic IP** attached to it
- Route table must be configured to route traffic from private subnet to the NAT instance
- NAT instance can be used as a bastion server
- NAT instance supports port forwarding
##### NAT Gateway
- image
- AWS managed NAT, higher bandwidth , higher availability, no administration
- Pay per hour for usage and bandwidth
- NATGW is created in a specific Availability Zone, use Elastic IP
- Can't be used by EC2 instance in the same subnet ( only from the other subnet)
- Requires an IGW(  private Subnet => NATGW => IGW )
- 5 Gbps of bandwidth with automatic scaling up to 45 Gbps)
- No Security Groups to manage/ required
-  NAT Gateway is resilient within a single Availability Zone
- Must create multiple NAT gateways in multiple AZs for fault-tolerance
- There is no cross-AZ failover needed because if an AZ goes down it doesn't need NAT
- public NAT gateway
	- should be in public subnet
	- you can associate elastic IP address to the public NAT gateway 
	- you can route the traffic from public NAT gateway to internet 
	- Alternatively, you can use a public NAT gateway to connect to **other VPCs or your on-premises network**. In this case, **you route traffic from the NAT gateway through a transit gateway** or a virtual private gateway.
- private NAT gateway
	- should be in private subnet
	- private NAT gateway can be used to route traffic between two VPC's having overlapping subnets
	- ![[Communication between two VPCs.png]]
	- you cannot associate elastic IP address to the private NAT gateway
	- Instances in private subnets can connect to other VPCs or your on-premises network through a private NAT gateway. You can route traffic from the NAT gateway through a transit gateway or a virtual private gateway.
	- **You can attach an internet gateway to a VPC with a private NAT gateway**, but if you route traffic from the private NAT gateway to the internet gateway, **the internet gateway drops the traffic.**
##### Security Groups & NACL
- image
-    NACL are like firewall which control traffic from and to subnets
- One NACL per subnet, new subnets are assigned the Default NACL
- you define NACL Rules:
	- Rules have a number ( 1-32766), higher precedence with a lower number
	- First rule match will drive the decision
	- Rule 100 has a higher precedence over 200
	- The last rule is an asterisk(*) and denies a request in case of no rule match
	- AWS recommends adding rules by increment of 100 
	- Newly created NACLs will deny everything
	- NACL are a great way of blocking a specific IP address at the subnet level
- Default NACL
	- Accepts everything inbound/outbound with the subnets its associated with
	- Do not modify the default NACL, instead create custom NACLs
 - Custom NACL
	 - there is default inbound and outbound rule denying all traffic
- Ephemeral Ports
	-  image
	- For any two endpoints to establish a connection, they must use ports
	- Clients connect to a defined port, and except a response on an ephemeral port
	- NACL with Ephemeral Ports
		- image
  - Security Groups
	  - Operate at the instance level
	  - Supports allow rules only
	  - Stateful
	  - We cannot add a Deny Rule, both in Inbound and Outbound Rules as there’s a hidden default Implicit Deny Rule in Security Groups. All we can do is allow which is required, everything else which isn’t allowed by us is blocked.
	  - All rules are evaluated before deciding whether to allow traffic
	  - Applies to an EC2 instance when specified by someone
	  - The reason why a Security Group is called a Stateful Firewall is — Security Group basically maintains the State of a connection, meaning — _if an instance sends a request , the response traffic from outside is allowed back irrespective of the inbound rules, and vice versa._
	  - Default 
		  - allow inbound rules - allow traffic from the security group itself
		  - all outbound traffic is allowed
	- Custom
		- do not have inbound allow rules
		- all outbound traffic is allowed 
- NACL
	- Operates at the subnet level
	- Supports allow rules and deny rules
	- stateless - return traffic must be explicitly allowed
	- Rules are evaluated in order ( lowest to highest)
	- Automatically applies to all EC2 instances in the subnets that its associated with
	###### VPC peering
	![[AWS/AWS SAA-C03/images/vpc peering.png]]
	- Privately connect two VPCs using AWS network
	- Make them behave as if they were in the same network
	- Must not have overlapping CICDRs
	- VPC peering connection is NOT transitive
	- you must update route tables in each VPC's subnets to ensure EC2 instances can communicate each other
	- you can create VPC peering connection between VPC's in different AWS accounts/regions
	- you can reference a security group in a peered VPC's ( works cross accounts - same region )
	##### VPC Endpoints ( AWS private link )
	- image
	- Every AWS service is publicly exposed ( public URL )
	- VPC endpoints ( powered by AWS private link ) allows you to connect to AWS services using a private network instead of using the public internet
	- They are redundant and scale horizontally
	- They remove the need of IGW, NATGW to access AWS services
	- In case of issues
		- Check DNS settings resolution in your VPC
		- Check route tables
	- Types of Endpoints
		- Interface Endpoints ( powered by PrivateLink )
			- Provisions an ENI ( private IP address ) as an entry point ( must attach a security Group)
			- Supports most AWS services
			-  not free
		- Gateway Endpoints
			- Provisions a gateway and must be used as a target a route table ( does not use security groups)
			- Supports both S3 and DynamoDB
			- Free
			- provides connectivity to Amazon S3 without requiring an internet gateway or a NAT device
			- 
	- Gateway or Interface Endpoint for S3
		- Gateway is most likely going to be preferred all the time 
		- Cost - free for Gateway, $ for interface endpoint
		- Interface endpoint is referred access is required from on-premises ( Site to Site VPN or Direct connect ), a different VPC or a different region	
		##### VPC Flow logs
		- Capture information about IP traffic going into your interfaces
			- VPC Flow Logs
			- Subnet Flow Logs
			- Elastic Network Interface (ENI) Flow Logs
		- Helps to monitor & troubleshoot connectivity issue
		- Flow logs data can go to S3, CloudWatch, and Kinesis Data Firehose
		- Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, workspaces, NatGWT, Transit Gateway
		- srcaddrs & dstaddr - help identify problematic IP
		- srcport & dstport - help identify problematic ports
		- Query VPC flow logs using Athena on S3 or CloudWatch Logs insights
- VPC sharing
	- VPC sharing allows multiple AWS accounts to create their application resources such as EC2 instances, RDs databases, redshift clusters and Lambda functions
	- Participants can not view, modify or delete resources that belong to other participants or  the VPC owner
	-  VPC sharing **allows customers to share subnets with other AWS accounts within the same AWS Organization**
	- Sharing resources from a central location instead of building them in each VPC
