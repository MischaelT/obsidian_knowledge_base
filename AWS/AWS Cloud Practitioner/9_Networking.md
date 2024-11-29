The #VPC  (Virtual Private Cloud) is a collection of the IP addresses which you can use to separate a certain part of your applications.
## VPC CIDR Blocks 
Each VPC requires a Classless Inter-Domain Routing (CIDR) block to define the range of IP version 4 (IPv4) addresses that resources within the VPC can use. Default VPCs have a CIDR of 172.31.0.0/16, which includes all addresses from 172.31.0.0 to 172.31.255.255. The /16 refers to the size of the CIDR. You must choose a CIDR size between /16 and /28, Virtual Private Cloud 177 but otherwise, any CIDR you could assign to a traditional network can also be assigned to a VPC. The smaller the CIDR size, the greater the number of IP addresses available to the VPC. The following are a few examples of CIDR blocks that you could assign to a VPC: 
- 10.0.0.0/16 (10.0.0.0–10.0.255.255) 
-  192.168.0.0/24 (192.168.0.0–192.168.0.255)
-  172.16.0.0/28 (172.16.0.0–172.16.0.15) 
(we use precisely these ranges, because it is the ranges which are defined as a private IPs)
At your request, AWS can also assign an IPv6 CIDR blocks. 
## Types of VPC
There are two options what your VPC can be:
- public: everyone in the internet can access it. To make this work you have to attach Internet Gateway #IGW  
- An internet gateway is a VPC resource that allows EC2 instances to obtain a public IP address and access the internet. For instances in a subnet to have internet access, that subnet must contain a default route to the internet gateway that’s attached to the VPC. A subnet with a default route to an internet gateway is called a public subnet. Each instance must also have a public IP address. When you launch an instance, you can choose to have AWS automatically assign it one. You can’t reassign an automatically assigned public IP address, and when the instance stops or terminates, you lose it. Alternatively, you can allocate an elastic IP address and then assign it to an instance. Elastic IP addresses can be reassigned to different instances and don’t change until you deallocate them.
- ![[Pasted image 20241028091418.png]]
 - private: only authorized people can get access to it. To make this work you have to attach a  virtual private gateway that allows you to establish the #VPN connection to your resources. 
   A virtual private gateway allows traffic into the VPS only if it is coming from an approved network.
   ![[Pasted image 20241028091514.png]]
   - However the VPN still uses the normal internet to transfer data which can be unacceptable in the certain scenarios. That's why there's one more way to establish a fully private and separated from the others physical connection between your resources and AWS. It called #DirectConnect. Direct Connect provides private network connectivity to your VPC and public services such as Amazon S3 and Glacier. There’s no need to have a separate internet circuit just to access these services. This means you can bypass the internet altogether when accessing your AWS resources. Keep in mind that Direct Connect doesn’t provide internet access, so if you need it, you’ll still need a separate internet connection. Direct Connect links are offered through AWS Partner Network (APN) partners. Direct Connect operates using a dedicated link that operates at 1 or 10 Gbps. Because of this, it’s not subject to the high and unpredictable latency of a broadband internet connection. If you need fast, consistent connectivity to AWS, Direct Connect is a good option versus connecting via the internet. It is, however, more expensive. If you need less than 1 Gbps of bandwidth, you can obtain a hosted Direct Connect connection from an APN partner. A hosted connection comes in speeds of 50 Mbps, 100 Mbps, 200 Mbps, 300 Mbps, 400 Mbps, and 500 Mbps.
     ![[Pasted image 20241028091638.png]]

Subnets is a way to control access to the gateway.
A subnet is really nothing more than a single block of Internet Protocol (IP) addresses. Any compute device that requires network connectivity must be identified by an IP address that’s unique to the network. The servers or other networked devices that are assigned an IP address within one subnet are generally able to communicate with each other by default but might have traffic coming into and/or out of the subnet restricted by firewall rules.
AWS, as a matter of fact, permits up to 200 subnets per AZ.

As with a VPC, you must define a CIDR for each subnet. The subnet CIDR must be a subset of the VPC CIDR, with a size between /16 and /28. For example, if the default VPC CIDR is 172.31.0.0/16, then a subnet CIDR could be 172.31.16.0/20. Each subnet exists only within a single Availability Zone. Refer to Figure 10.1 for a sample VPC topology with two subnets.
![[Pasted image 20241128095600.png]]

However not the least important function of the subnets is that they can help you to control traffic permissions. Any packet from the internet got checked upon a assess control list of the networks (ACL). And by default all inbound and outbound traffic is allowed. Which is essentially the list of permissions for this particular packet can leave or enter the subnet bases on where it was sent from and how it's trying to communicate. This serves a purpose of a network level segmentation and on both ways: in and out
## VPC Peering
A VPC peering connection is a private, point-to-point connection between only two VPCs. VPC peering allows resources in different VPCs to communicate with each other over the private AWS network instead of the internet. A VPC peering connection allows instances in one VPC to access certain types of resources in another VPC, such as another instance or a network load balancer. VPC peering connections are fast, reliable, and secure. There’s also no need for VPC resources to have internet access in order to use VPC peering. Peered VPCs can be in the same region or in different regions.
## Virtual Private Networks
A virtual private network (VPN) allows you to connect a VPC to an external network, such as a data center or office, via a secure connection that traverses the public internet. To set up a VPN connection, you create a virtual private gateway and attach it to a VPC. You then configure your customer gateway—a physical or virtual router or firewall on your network—to connect to the virtual private gateway. AWS has tested a variety of customer gateways from different manufacturers including Cisco, Juniper, Palo Alto Networks, and Check Point. VPN connections are encrypted using AES 128- or 256-bit encryption. IP routing can be configured statically, or you can use the Border Gateway Protocol (BGP) to share routes between your VPC and external network. A single VPC can have up to 10 VPN connections.


The issue is that sometimes you can have several instances in the same subnet, and you should have a way to fine grain the access based on the particular instance. The way how it's can be reached is by introducing a security groups. Any instance by default reject any incoming traffic. 
 **Security groups are stateful and deny all inbound traffic by default**.

The key differences between the security groups and subnets:

| Aspect              | Security Groups                                     | Subnets                                   |
| ------------------- | --------------------------------------------------- | ----------------------------------------- |
| **Purpose**         | Control access to individual resources              | Segment the network within a VPC          |
| **Level**           | Resource level (instance, Lambda function, etc.)    | Network level within a VPC                |
| **Direction**       | Manages both **inbound** and **outbound** traffic   | Defines IP range and routing              |
| **Type**            | Stateful firewall rules                             | Stateless IP segmentation                 |
| **Scope**           | Applies directly to resources like EC2, RDS, etc.   | Defines network boundary (public/private) |
| **Internet Access** | Controls port/protocol access, not internet routing | Manages internet access via route tables  |

### Difference between stateless and stateful

Stateful system does track the state of itself. The security groups are stateful, meaning, that if they have an inbound traffic from a certain endpoint, that means that outbound traffic will also be allowed. On the other way stateless system doesnt keep track of the system.  The subnet is stateless, meaning that every package is being treated independently. 

|Feature|Stateful|Stateless|
|---|---|---|
|**Connection Tracking**|Remembers connection state|No memory of previous packets|
|**Rule Configuration**|Simplifies response traffic handling|Requires separate rules for return traffic|
|**Performance**|Typically slower due to state tracking|Faster for high-throughput environments|
|**AWS Examples**|Security Groups|Network ACLs|
|**Common Use**|Firewalls, dynamic access control|Routers, high-throughput filtering|

![[Pasted image 20241028095123.png]]
## AWS Route 53

it is Amazon's #DNS system it allows to put in correspondence the physical address of the server and the website address.  it can connect people for the infrastructure within aws and outside.

- You can buy and manage domains here (add dns records, transfer the domain name from other registars, etc.)

![[Pasted image 20241104090644.png]]

That's how route53 and cloudfront works in synergy:
![[Pasted image 20241104091055.png]]

1. Customer sends a request to the DNS resolver to get the ip name of the company's servers. 
2. Upon receival the response from aws #Route53, the customer sends a request to the closest edge location where aws cloudfront sent the request further to the application load balancer.
3. Load balancer forwards teh request further to the #EC2 instance
### Hosted Zones
To have Route 53 host the DNS for a public domain name, you create a public hosted zone and specify the domain name. You can then define the resource records for that domain. If you use Route 53 to register a domain name, it automatically takes care of creating a public hosted zone for the domain. Route 53 can also provide name resolution for private domain names. A private domain name is one used on a network other than the internet. Route 53 private hosted zones provide DNS resolution for a single domain name within multiple VPCs. This is useful for assigning user-friendly domain names to VPC resources such as EC2 instances or application load balancers. For example, instead of hardcoding a database server’s IP in an application, you can define a record in a private hosted zone with the name db.example.com that points to the database server’s IP address. Because private domain names aren’t accessible from the internet, there are no registrars, so you can pick any domain name you want. Name resolution for private hosted zones is not available outside of the VPC you select.

### Routing Policies
In some cases, you just need a domain name to resolve to a particular IP address. But there are other times when you want the value of a resource record to change dynamically to work around failures or ensure users get pointed to the least busy server. Route 53 lets you accomplish this with a variety of routing policies. Simple The Simple routing policy is the default for new resource records. It simply lets you map a domain name to a single static value, such as an IP address. It doesn’t check whether the resource the record points to is available. Weighted A Weighted policy distributes traffic across multiple resources according to a ratio. For example, when introducing a new web server, you may want to route only 10 percent of the traffic to the new server while evenly distributing the load across the rest. Latency A Latency policy sends users to resources in the AWS Region that’s closest to them. This is useful if, for instance, you want to send European users to the eu-west-1 region while sending users in the United States to the us-east-1 region. Failover A Failover policy lets you route traffic to a primary resource unless it’s unavailable. In that case, traffic will be redirected to a secondary resource.
Geolocation A Geolocation policy lets you route users based on their specific continent, country, or state. Multivalue Answer A Multivalue Answer policy allows you to evenly distribute traffic across multiple resources. Unlike Weighted policies that return a single record, a Multivalue Answer policy returns all records, sorted in a random order.

### Health Checks
All routing policies with the exception of Simple can use health checks to determine whether they should route users to a given resource. A health check can check one of three things: an endpoint, a CloudWatch alarm, or another health check. All health checks occur every 10 seconds or 30 seconds. Endpoint Endpoint health checks work by connecting to the endpoint you want to monitor via HTTP, HTTPS, or TCP. Route 53 has health checkers in several AWS Regions, and you can choose which health checkers a health check uses. This lets you ensure that an endpoint is reachable from various locations around the world. CloudWatch alarm A Route 53 health check can monitor the status of a CloudWatch alarm. This is useful if you want to consider a resource unhealthy if it’s experiencing high latency or is servicing a high number of connections. Calculated This type of health check monitors the status of other health checks. For example, if you want to consider the status of both an Endpoint health check and a CloudWatch alarm health check, you can create a Calculated health check to take both into account. Traffic Flow and

### Traffic Flow and Traffic Policies
If you require complex routing scenarios for a public hosted zone, creating multiple resource records with a variety of different routing policies can become an administrative nightmare. As an alternative to manually engineering routing policies, you can use the Route 53 Traffic Flow visual editor to create a diagram to represent the desired routing. The diagram you create represents a traffic policy that you can save and associate with a domain name by creating a policy record. Route 53 doesn’t create the individual resource records but instead hides the routing behind the single policy record. The cost is currently $50 USD per month per policy record. You can use the same routing policies that are available with normal resource records: Simple, Weighted, Latency, Failover, Geolocation, and Multivalue Answer. But in addition, Traffic Flow offers another routing policy that’s not otherwise available: Geoproximity. The Geoproximity routing policy lets you direct users to a resource based on how close they are to a geographic location. This differs from the Geolocation routing policy that routes based on the user’s specific continent, country, or state.