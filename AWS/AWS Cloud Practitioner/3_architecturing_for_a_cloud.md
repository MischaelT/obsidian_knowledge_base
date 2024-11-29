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