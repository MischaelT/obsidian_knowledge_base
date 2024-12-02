**API-Centric:** AWS services are accessed via #API s , making it essential to understand how to work with them programmatically.
## Application Architectures:
### 1. Monolithic Architecture

- In this architecture, all components are tightly coupled. If one part fails, the entire application may become unavailable. This approach can be limiting for large, high-load applications and can complicate deployment and scaling.
- **When to Use:** Suitable for small projects or #MVP s where simplicity and speed of development are priorities.
### 2. Microservices Architecture
- This architecture separates logical parts into distinct services, allowing them to function independently. If one service fails, others can continue to operate, leading to greater resilience.
- Services communicate through API calls or messaging systems (e.g., #RESTAPI, message queues).
- **AWS Services Supporting Microservices:**
    - **AWS Lambda**: Enables serverless computing for running code in response to events. #lambda
    - **Amazon API Gateway**: Allows you to create, publish, and manage APIs for your microservices.
    - **Amazon #ECS / #EKS**: Helps in orchestrating containerized applications.
### 3. Serverless computing
Serverless computing is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers. In this model, developers can focus on writing and deploying code without worrying about the underlying infrastructure. The cloud provider handles all background tasks, such as server management, scaling, and maintenance, allowing users to run applications in response to events and on demand.
#### Ke Characteristics:
1. **On-Demand Computing:**
    - Resources are allocated as needed, allowing users to scale applications seamlessly based on demand.
2. **Event-Driven Architecture:**
    - Serverless applications often operate on an event-driven basis, where functions are triggered by events (e.g., #HTTP requests, file uploads, database changes).
3. **Micro-Billing:**
    - Users are charged only for the compute time consumed during execution, which can lead to cost savings compared to traditional server models.
4. **Simplified Management:**
    - Developers do not need to manage server infrastructure, updates, or maintenance, leading to faster development cycles.
5. **Scalability:**
    - Applications can automatically scale up or down in response to workload changes, making it easier to handle variable traffic.
## AWS Well Achitected Framework
The [**AWS Well-Architected Framework**(opens in a new tab)](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) helps you understand how to design and operate reliable, secure, efficient, and cost-effective systems in the AWS Cloud. It provides a way for you to consistently measure your architecture against best practices and design principles and identify areas for improvement.
The Well-Architected Framework is based on six pillars: 
- Operational excellence
	 - **Focus**: Running and monitoring systems to deliver business value and continuously improving processes and procedures.
	- **Key Practices**:
	    - Automate operations (e.g., using AWS #CloudFormation).
	    - Monitor health (e.g., with Amazon #CloudWatch).
	    - Perform regular reviews and iterative improvement.
- Security
	- **Focus**: Protecting data, systems, and assets while maintaining compliance.
	- **Key Practices**:
	    - Implement strong identity controls (e.g., #IAM and #MFA).
	    - Enable data protection (e.g., encryption with AWS #KMS).
	    - Track and monitor security events (e.g., #CloudTrail, #GuardDuty).
- Reliability
	- **Focus**: Ensuring a workload performs its intended function correctly and consistently.
	- **Key Practices**:
	    - Design systems to withstand failures (e.g., Multi-AZ deployments).
	    - Automate recovery from failure (e.g., Auto Scaling).
	    - Monitor and test resiliency regularly
- Performance efficiency
	- **Focus**: Using IT and computing resources efficiently to meet system requirements.
	- **Key Practices**:
	    - Select the appropriate resource types and sizes.
	    - Optimize over time (e.g., by using Trusted Advisor).
	    - Use serverless architectures where possible (e.g., Lambda).
- Cost optimization
	- **Focus**: Managing costs effectively and avoiding unnecessary expenses.
	- **Key Practices**:
	    - Right-size resources.
	    - Use Reserved Instances or Savings Plans for predictable workloads.
	    - Leverage Spot Instances for non-critical workloads.
	    - Turn off unused resources (e.g., AWS budgets or CloudWatch alarms).
- Sustainability
	- **Focus**: Minimizing environmental impact and improving energy efficiency.
	- **Key Practices**:
	    - Use efficient resources and serverless technologies.
	    - Adopt multi-tenant solutions (shared resources).
	    - Monitor and reduce waste (e.g., using the AWS Customer Carbon Footprint Tool).