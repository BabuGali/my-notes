- Connect Amazon VPCs, AWS accounts, and on-premises networks to a single gateway
- AWS Transit Gateway connects your Amazon Virtual Private Clouds (VPCs) and on-premises networks through a central hub. This connection simplifies your network and puts an end to complex peering relationships. Transit Gateway acts as a highly scalable cloud router—each new connection is made only once.
![[AWS/AWS SAA-C03/images/transit gateway.png]]
##### VPC Peering and Transit Gateway
- VPC Peering and Transit Gateway are used to connect multiple VPCs
-  VPC Peering provides Full-mesh architecture while Transit Gateway provides hub-and-spoke architecture
 **Connectivity Options**  
 - Peering: VPC to VPC. Hybrid connectivity is not supported.  
  - TGW: VPC to VPC. Supports hybrid connectivity using VPN or Direct Connect Gateway attachments. Reuse same VPN/DX connection for multiple VPCs.
  **Architecture**
   - Peering: Full Mesh (One to one mapping).  
   - TGW: Hub and Spoke.
   **Transitive Routing**
    - Peering: Not supported.
    - TGW: Supported.
   **Bandwidth limit**
   - Peering: No limit.
   - TGW: Up to 50 Gbps (burst)/attachment.
   **Latency**
    - Peering: Lowest.
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
- VPC peering
	- Low cost since you need to pay only for data transfer.
	- No bandwidth limit
	- Disadvantage
		- Each new VPC increases the complexity of the network
- Transit Gateway
	- 