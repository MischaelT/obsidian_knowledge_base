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
## AWS Artifact 
The service which provides different juridic documents