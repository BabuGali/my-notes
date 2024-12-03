- Network layer service
- to improve the availability and performance of you applications for local and global users
- It directs the traffic to optimal endpoints of your TCP and UPD
- Unicast IP vs Anycast IP
- Uses Anycast IP - acts as a fixed entry point
- Works with Elastic IP, Ec2 instances, ALB, NLB
- Health Checks
- If workloads that cater to a global clients then AWS recommends to use AWS Global Accelerator 
- it uses endpoint weights to distribute the portion of traffic to dedicated end point
- Launch AWS Global accelerator and create endpoints for all the regions.
- To mitigate endpoint failure, Global accelerator automatically re-routes traffic to your nearest healthy available endpoints
- protect from DDoS
![[global acceleratior.png]]

Global Accelerator vs Cloud Front
- CloudFront uses Edge locations to catch the content while global accelerator uses edge locations to find an optimal pathway to the nearest regional endpoint 