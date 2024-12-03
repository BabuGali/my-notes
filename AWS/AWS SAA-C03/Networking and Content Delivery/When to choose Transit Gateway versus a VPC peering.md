- VPC Peering and Transit Gateway are used to connect multiple VPCs
- VPC Peering
	- **VPC Peering provides Full-mesh architecture**
	- inter region and intra region
	- Advantages
		- Low cost since you need to pay only for data transfer.
		- No bandwidth limit.
	- Disadvantages
		- Complex at scale. Each new VPC increases the complexity of the network. Harder to maintain route tables compared to TGW.
		- No transit routing.
		- - Maximum 125 peering connections per VPC.
- Transit Gateway
	- **Transit Gateway provides hub-and-spoke architecture**
**Connectivity Options**
	- Peering: VPC to VPC. Hybrid connectivity is not supported.
	- TGW: VPC to VPC. Supports hybrid connectivity using VPN or Direct Connect Gateway attachments. Reuse same VPN/DX connection for multiple VPCs
**Architecture**
- Peering: Full Mesh (One to one mapping).  
 - TGW: Hub and Spoke.
 **Transitive Routing**
	 - Peering: Not supported.
	 - TGW: Supported.
**Network Connectivity**
 - Peering: Supports Inter-region and Intra-region VPCs connectivity.
 - TGW: Supports Inter-region and Intra-region VPCs connectivity.
**Complexity**  
 - Peering: Increases with VPC count. You need to set up a VPC Peering between every VPC. Less complexity with a small number of VPC count.  
 - TGW: Increases with Transit Gateway count/region count. Less complexity with a higher number of VPC count compares to VPC Peering. You need to manage a very less number of connections/attachments.
**Bandwidth limit**
 - Peering: No limit.  
 - TGW: Up to 50 Gbps (burst)/attachment.
**Latency**
 -  Peering: Lowest
 - TGW: Slightly higher compared to VPC Peering because of additional Transit Gateway hop.
**Cost**
 - Peering: Data transfer. (operational cost is high)
 - TGW: Data transfer, Data processing, and Hourly per attachment. (operational cost is less)
**Visibility/Monitoring**
 - Peering: VPC Flow Logs. Limited visibility compared to TGW.
 - TGW: VPC Flow Logs, Transit Gateway Network Manager, CloudWatch Metrics.
**Security group (cross-referencing)**
 - Peering: Supported.
 - TGW: Not supported.
##### Choose **VPC Peering** if:
- Number of VPCs to be connected is lower(<10)
- You need multiple VPCs’ connectivity to On-premises.
- <span style="color:red;"> **You want to minimize data transfer costs when significant volumes of data transfer across regions, VPC Peering is cost-effective.** </span>
-  Need for low latency.
- You need high throughput. Network bandwidth requirement is more than 50 Gbps.
##### Choose **Transit Gateway** if:
- You need VPC connectivity at scale. Number of VPCs to be connected is higher (~>10) or scale in the future as the business grows.
- You need network-level segmentation. (possible with multiple TGW route tables)
-  You need multiple VPCs connectivity to On-premises.

![[VPC peering-1.png]]


![[Transit Gateway-1.png]]