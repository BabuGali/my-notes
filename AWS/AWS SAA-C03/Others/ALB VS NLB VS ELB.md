##### NLB
- protocols :TLS, TCP, UPD, TCP_UDP
- target types - Instance, IP, ALB
- You want to share/expose your services (e.g. SaaS services) to other consumers in different VPCs using PrivateLink VPC Endpoint.
- Traffic is routed to instance using the primary private IP address
##### ALB
- Protocols - HTTP and HTTPS
- Target types - Instance, IP and Lambda
- Applications need advanced routing (host-based, URL-based, query string based).
- Run multiple services (microservices) behind a single load balancer.
- if workloads hosted in a single Region and used by clients in the same region then you can use ALB. 
- If workloads that cater to a global clients then AWS recommends to use AWS Global Accelerator  
###### ELB
- ELB provides load balancing within one region
- AWS global accelerator provides traffic management across multiple regions 
- ELB cannot throttle requests 

