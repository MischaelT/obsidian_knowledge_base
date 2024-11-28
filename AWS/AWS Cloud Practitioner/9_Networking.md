The #VPS (Virtual Private Server) is a collection of the IP addresses which you can use to separate a certain part of your applications.

## VPC CIDR Blocks 
Each VPC requires a Classless Inter-Domain Routing (CIDR) block to define the range of IP version 4 (IPv4) addresses that resources within the VPC can use. Default VPCs have a CIDR of 172.31.0.0/16, which includes all addresses from 172.31.0.0 to 172.31.255.255. The /16 refers to the size of the CIDR. You must choose a CIDR size between /16 and /28, Virtual Private Cloud 177 but otherwise, any CIDR you could assign to a traditional network can also be assigned to a VPC. The smaller the CIDR size, the greater the number of IP addresses available to the VPC. The following are a few examples of CIDR blocks that you could assign to a VPC: ✓■ 10.0.0.0/16 (10.0.0.0–10.0.255.255) ✓■ 192.168.0.0/24 (192.168.0.0–192.168.0.255) ✓■ 172.16.0.0/28 (172.16.0.0–172.16.0.15) At your request, AWS can also assign an IPv6 CIDR block to y


There are two options what your VPC can be:
- public: everyone in the internet can access it. To make this work you have to attach Internet Gateway #IGW  ![[Pasted image 20241028091418.png]]
 - private: only authorized people can get access to it. To make this work you have to attach a  virtual private gateway that allows you to establish the VPN connection to your resources. 
   A virtual private gateway allows traffic into the VPC only if it is coming from an approved network.
   ![[Pasted image 20241028091514.png]]
   - However the VPN still uses the normal internet to transfer data which can be unacceptable in the certain scenarios. That's why there's one more way to establish a fully private and separated from the others physical connection between your resources and AWS. It called Direct Connect.
     ![[Pasted image 20241028091638.png]]

Subnets is a way to control access to the gateway.
A subnet is really nothing more than a single block of Internet Protocol (IP) addresses. Any compute device that requires network connectivity must be identified by an IP address that’s unique to the network. The servers or other networked devices that are assigned an IP address within one subnet are generally able to communicate with each other by default but might have traffic coming into and/or out of the subnet restricted by firewall rules.
AWS, as a matter of fact, permits up to 200 subnets per AZ.

However not the least important function of the subnets is that they can help you to control traffic permissions. Any packet from the internet got checked upon a assess control list of the networks (ACL). And by default all inbound and outbound traffic is allowed. Which is essentially the list of permissions for this particular packet can leave or enter the subnet bases on where it was sent from and how it's trying to communicate. This serves a purpose of a network level segmentation and on both ways: in and out
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
### AWS Route 53

it is Amazon's #DNS system it allows to put in correspondence the physical address of the server and the website address.  it can connect people for the infrastructure within aws and outside.

- You can buy and manage domains here (add dns records, transfer the domain name from other registars, etc.)

![[Pasted image 20241104090644.png]]

That's how route53 and cloudfront works in synergy:
![[Pasted image 20241104091055.png]]

1. Customer sends a request to the DNS resolver to get the ip name of the company's servers. 
2. Upon receival the response from aws #Route53, the customer sends a request to the closest edge location where aws cloudfront sent the request further to the application load balancer.
3. Load balancer forwards teh request further to the #EC2 instance
