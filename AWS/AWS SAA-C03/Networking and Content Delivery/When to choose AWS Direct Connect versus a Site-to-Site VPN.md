**Connectivity requirements**
- While the network in AWS Direct Connect is stable and offers a constant experience, the network in AWS VPN is connected to shared and public networks, which causes bandwidth and latency to change.
**Security:**
	- Your traffic is not automatically encrypted in transit when using AWS Direct Connect. The connection between the client network and the AWS VPC is encrypted when using AWS Site-to-Site VPN. For businesses that demand stronger security requirements, AWS Direct Connect is the primary option since it offers higher security. Because the communication is carried over the public Internet network rather than a private dedicated network, VPN raises greater security concerns.
**Cost:**
- An AWS VPN is less expensive than AWS Direct Connect. In addition, AWS Direct Connect does not offer a VPN option that is priced by the hour.
**Time to execution:**
- VPN can use whatever network transport the customer has. On the other hand, AWS Direct Connect it’s a private physical connection, either the connection is hosted or dedicated, this translates to human intervention and provisioning that makes these options somehow slower.
** Other **
- - Since VPN tunnels can only have a maximum bandwidth of 1.25 Gbps, AWS VPN connectivity is not scalable. AWS Direct Connect bandwidth starts at 50 Mbps and goes up to 100 Gbps.
- - High-scalability connections are available up to 100 Gbps. Since the connections are dedicated, you enjoy better and more reliable network speed as well as more inherent security while accessing your AWS services.
	- A site-to-site vpn has a maximum throughput of 1.25 Gbps. To scale throughput beyond 1.25 GBPS, equal-cost- multi-path support can be used over multiple VPNs
	- 