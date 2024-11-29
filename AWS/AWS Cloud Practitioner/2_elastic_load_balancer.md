The AWS Elastic Load Balancer (ELB) is a service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances.
- **Traffic Distribution**: All requests initially route through the #ELB, which intelligently directs them to the appropriate #EC2 instance based on various factors, such as instance health and current load.
- **Scalability**: The ELB effectively manages traffic, regardless of how many instances are operational at any given time, ensuring optimal resource utilization and improved fault tolerance.
### **Types of Elastic Load Balancers**
- **Classic Load Balancer (CLB)**: An older option that operates at both Layer 4 and Layer 7, suitable for basic load balancing of HTTP/HTTPS and TCP traffic.
- **Application Load Balancer (ALB)**: Ideal for HTTP/HTTPS traffic, it operates at the application layer (Layer 7) and supports advanced routing, SSL termination, and WebSocket support.
- **Network Load Balancer (NLB)**: Suitable for TCP/UDP traffic, it operates at the transport layer (Layer 4) and is optimized for high performance, handling millions of requests per second while maintaining ultra-low latency.
### **Key Features**
- **Health Checks**: ELB continuously monitors the health of registered EC2 instances, automatically routing traffic only to healthy instances. This enhances application reliability.
- **Auto Scaling Integration**: ELB works seamlessly with Auto Scaling groups, allowing for dynamic scaling of EC2 instances based on traffic demands.
- **Cross-Zone Load Balancing**: Distributes traffic evenly across all registered instances in multiple Availability Zones, improving resource utilization and fault tolerance.
### **Security Features**
- **SSL/TLS Termination**: ELB can handle SSL/TLS encryption and decryption, reducing the load on EC2 instances and improving performance.
- **Integration with AWS #WAF**: ELB can be integrated with AWS Web Application Firewall to provide an additional layer of security against common web exploits.