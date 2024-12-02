## **The AWS shared responsibility model**
AWS is responsible for some parts of your environment and you (the customer) are responsible for other parts. This concept is known as the [**shared responsibility model**(opens in a new tab)](https://aws.amazon.com/compliance/shared-responsibility-model/).

The shared responsibility model divides into customer responsibilities (commonly referred to as “security in the cloud”) and AWS responsibilities (commonly referred to as “security of the cloud”).
![[Pasted image 20241108154807.png]]

You can think of this model as being similar to the division of responsibilities between a homeowner and a homebuilder. The builder (AWS) is responsible for constructing your house and ensuring that it is solidly built. As the homeowner (the customer), it is your responsibility to secure everything in the house by ensuring that the doors are closed and locked. 
![[Pasted image 20241125094249.png]]

## Customers: Security in the cloud
Customers are responsible for the security of everything that they create and put _in_ the AWS Cloud.
When using AWS services, you, the customer, maintain complete control over your content. You are responsible for managing security requirements for your content, including which content you choose to store on AWS, which AWS services you use, and who has access to that content. You also control how access rights are granted, managed, and revoked.

The security steps that you take will depend on factors such as the services that you use, the complexity of your systems, and your company’s specific operational and security needs. Steps include selecting, configuring, and patching the operating systems that will run on Amazon EC2 instances, configuring security groups, and managing user accounts. 

Use this simple rule of thumb: if you can edit it, you own it. The key—especially during a project’s planning stages—is to be aware of your responsibilities and to always make security a critical priority
## AWS: Security of the cloud
AWS is responsible for security _of_ the cloud.
- Physical security of data centers
- Hardware and software infrastructure
- Network infrastructure
- Virtualization infrastructure

AWS operates, manages, and controls the components at all layers of infrastructure. This includes areas such as the host operating system, the virtualization layer, and even the physical security of the data centers from which services operate. 

AWS is responsible for protecting the global infrastructure that runs all of the services offered in the AWS Cloud. This infrastructure includes AWS Regions, Availability Zones, and edge locations.

Although you cannot visit AWS data centers to see this protection firsthand, AWS provides several reports from third-party auditors. These auditors have verified its compliance with a variety of computer security standards and regulations.
## IAM - Identity and Access management
- users - a specific entity which represents user with a particular set of permissions
- groups - a specific set of permissions, which we can assign to the specific user
- roles - a permissions used by application and services rather than people

When creating a role, you begin by defining a trusted entity—the entity (or beneficiary) that will be trusted to use the role. That entity could be an AWS service (like EC2), an identity provided by a third-party federated identify provider (like Google or Amazon Cognito—which allow a digital identity to be linked across multiple identity management systems), or a different AWS account. You might, for instance, need to give users logged in to your mobile application through their Google accounts access to specific resources on AWS services (such as data kept on S3). You’ll have to specify exactly what permissions you want to give the role or, in other words, what you want the beneficiary processes to be able to do. You’ll then choose the policy that best fits your anticipated needs and associate it with the role
## AWS KMS
When you select to encrypt an AWS resource, KMS will apply encryption using a customer master key (CMK) that’s been generated especially for your account. You can manage your keys—including creating new keys or scheduling the deletion of old ones— through either the KMS Dashboard or the Encryption Keys page within IAM.
What can be encrypted? Just about any data managed by an AWS service, including Relational Database Service (RDS) and DynamoDB databases. Elastic Block Store (EBS) volumes that you attach to EC2 instances can also be encrypted when you create them. When they’re encrypted, those resources will, for all practical purposes, be unreadable without the decryption key. AWS will invisibly decrypt your data only when the access request is accompanied by successful authentication. Encryption for S3 works in much the same way, but there’s a twist. You can have S3 encrypt the objects of a bucket at any time—during or after bucket creation. You can select either S3-managed server-side encryption keys (SSE-S3) or KMS-managed keys (SSE-KMS). Either way, the process will often all take place “under the hood” without requiring any further input from you.
## **Encryption Options in AWS**
### Encryption at Rest
Encryption at rest protects your data when it's stored on disk. AWS offers various services to ensure that data stored in these services is encrypted:
- **Amazon #S3**:
    - **Server-Side Encryption (SSE)** can be used to automatically encrypt data when it is written to S3.
        - **SSE-S3**: Uses Amazon S3-managed keys to encrypt data.
        - **SSE-KMS**: Uses AWS Key Management Service #KMS to manage the encryption keys.
        - **SSE-C**: Allows customers to manage their own encryption keys.
    - You can also **upload pre-encrypted data** (client-side encryption).
- **Amazon #EBS (Elastic Block Store)**:
    - EBS volumes can be encrypted with **AWS KMS**. When creating an EBS volume, encryption is optionally enabled, and it uses AES-256 encryption by default.
    - Encryption ensures that both the data and its backups are encrypted, providing enhanced security for persistent storage.
- **Amazon #RDS (Relational Database Service)**:
    - Supports encryption at rest for databases like MySQL, PostgreSQL, and Oracle. Encryption is provided using **AWS KMS**.
    - This applies to data, backups, and automated snapshots, making it easier to maintain security for your databases.
### Encryption in Transit
Encryption in transit ensures that data is securely transmitted over networks, protecting it from interception during transmission
- **HTTPS** (Hypertext Transfer Protocol Secure) is used by services like **API Gateway**, **S3**, and Elastic Load Balancer #ELB to automatically encrypt data while in transit.
- For **custom applications**, you can implement **TLS (Transport Layer Security)**, which ensures that the data transmitted between clients and servers is encrypted.
- **AWS Certificate Manager (ACM)** helps manage SSL/TLS certificates that are used for encrypting data in transit. It simplifies the process of provisioning, managing, and deploying certificates for your applications.
## **AWS Security Tools**
### **Amazon Inspector**
- Amazon Inspector is a security assessment service that automatically assesses applications for vulnerabilities and deviations from security best practices.
- It focuses on EC2 instances and container-based applications, identifying potential security issues such as outdated software or improper configurations.
- It can be used to ensure that applications comply with internal security standards and external regulatory requirements.
### **AWS Security Hub**
- AWS Security Hub is a service that centralizes and consolidates security findings from multiple AWS services (e.g., Amazon GuardDuty, AWS Inspector, AWS Firewall Manager).
- It gives a comprehensive view of the security posture across your AWS accounts, allowing you to monitor security alerts, automate security responses, and track compliance with security standards.
- You can integrate third-party security tools and services as well.
### AWS Shield
- **AWS Shield** provides DDoS (Distributed Denial of Service) protection for AWS services and applications.
- **Shield Standard**: Free and automatically protects against most common DDoS attacks, protecting services like CloudFront and Elastic Load Balancers (ELBs).
- **Shield Advanced**: A paid service that offers more comprehensive protection, including for large-scale or sophisticated DDoS attacks, with enhanced detection, real-time attack visibility, and protection for applications.
### Amazon GuardDuty
- Amazon GuardDuty is a continuous security monitoring service that uses machine learning and threat intelligence to identify suspicious activity.
- It can detect issues like unauthorized access attempts, compromised EC2 instances, or unusual network activity.
- GuardDuty can integrate with other AWS services (e.g., AWS CloudWatch, AWS Lambda) to automate responses to security incidents.