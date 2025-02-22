## Elastic Block Storage (EBS)
There are several ways in AWS to store data. One way is to store it directly on the instance level. However this option may not be suitable for long-term storage, because it got erased every time you stop the instance.

Another way is to use Amazon Elastic Block Store #EBS. You can think of it as a virtual hard drive, which is not being erased on every startup. EBS allows you to choose the size and the amount of drives you wanna use.

Like everything else in the cloud, the storage volumes holding your instance’s OS and data are going to be virtual. In most cases, that’ll mean the 20 or 30 (or 2,000) GB drive holding your application is really just a 20 or 30 GB partition cleverly disguised to look like a stand-alone device. In fact, however, it was actually carved out of a much larger drive. What’s going on with the rest of the drive space? It’s probably being used for instances run by other AWS customers.

The physical drive where an EBS volume actually exists may live quite a distance from the physical server that’s giving your instance life. Rather than connecting directly to the motherboard via, say, a SATA cable the way a physical drive plugs into a physical computer, EBS volumes speak with your instance over a super low-latency network connection spanning the data center. As fast as the EBS-EC2 responses are, they’re still not quite as good as the experience you’ll get from #EC2 instance store volumes. So, what does EBS offer to compensate?
- Unlike the instance store that’s ephemeral, the data stored on EBS volumes will survive shutdowns and system crashes. That can be a factor for workloads where data persistence is necessary. 
- EBS volumes can be encrypted, which, when you’re working with sensitive data, can make a big difference.
- EBS volumes can be moved around, mounted on other instances, and, as you’ve seen, converted to AMIs.
Additionally it provides you with the functionality of creating a snapshots -  a backup of the data in EBS. It uses the incremental backup: it saves all the data only in the first request, after it just saves only the data which has been change since the last back up.
![[Pasted image 20241104094001.png]]


### **Pricing Tiers**:
- **General Purpose SSD (gp3)**: Good for most applications that need a balance of price and performance.
- **Provisioned IOPS SSD (io1/ io2)**: For I/O-intensive applications like databases.
- **Throughput Optimized HDD (st1)**: For large, sequential workloads.
- **Cold HDD (sc1)**: Lowest-cost storage, suited for infrequent access.
## Elastic File System (EFS)
In file storage, multiple clients can access the data which is stored in the in shared file folders. in this scenario the system uses block storage as well as the local file system to organize the files. 
The best use-case is when several applications have to share the same filesystem: has an access to the same files, modify or manage them.
### **Pricing Tiers**:
- **Standard**: For frequently accessed data.
- **Infrequent Access**: Lower-cost storage for infrequently accessed files.
## Difference between the EFS and EBS
- EBS store the data within a single availability zone and it should be in the same AZ as the resource that uses it. 
- #EFS is a regional service - it stores the data on the regional level and across several AZ within a region. Additionally you can connect your EFS using the AWS direct Connect
## Simple Storage Service (S3)
Object storage is a particular type of storages, where the data is being stored in a format of objects. It should have 3 characteristics: data, metadata and key. The data by itself, may be any data. The metadata is a description of the file, and finally the key is an unique identifier of every object.

When a file in object storage is being modified, the entire file is being replaced, not only particular parts which were changed.

The maximum size of the uploaded object is 5 terabytes.
### Access Permissions
S3 is storage for the internet, but that doesn’t mean everyone on the internet can read your data. By default, objects you put in S3 are inaccessible to anyone outside of your AWS account. S3 offers the following three methods of controlling who may read, write, or delete objects stored in your S3 buckets:
- Bucket policies
- User policies
- Bucket and object access control lists
#### Bucket Policies
A bucket policy is a resource-based policy that you apply to a bucket. You can use bucket policies to grant access to all objects within a bucket or just specific objects. You can also control which principals and accounts can read, write, or delete objects. You can also grant anonymous read access to make an object, such as a webpage or image, available to everyone on the internet.
#### User Policies
In Chapter 5, “Securing Your AWS Resources,” you learned about Identity and Access Management (IAM) user policies. You can use these policies to grant IAM principals access to S3 objects. Unlike bucket policies that you apply to a bucket, you can apply user policies only to an IAM principal. Keep in mind that you can’t use user policies to grant public (anonymous) access to an object.
### Encryption
S3 doesn’t change the contents of an object when you upload it. That means if you upload a document containing personal information, that document is stored unencrypted. Using appropriate access permissions can protect your data from unauthorized access, but to add an additional layer of security, you have the option of encrypting objects before storing them in S3. This is called encryption at rest . S3 gives you the following two options for encrypting objects at rest: 
- Server-side encryption—When you create an object, S3 encrypts the object and saves only the encrypted content. When you retrieve the object, S3 decrypts it and delivers the unencrypted object. Server-side encryption is the easiest to implement and doesn’t require you to keep track of encryption keys. Amazon manages the keys and therefore has access to your objects.
- Client-side encryption—You encrypt the data prior to uploading it to S3. You must decrypt the object when you retrieve it from S3. This option is more complicated, as you’re responsible for encryption and decryption. If you lose the key used to encrypt an object, you won’t be able to decrypt it. Organizations with strict security requirements may choose this option to ensure Amazon doesn’t have the ability to read their encrypted objects.
### Versioning
To further protect against accidentally deleting or overwriting the contents of your important fi les, you can use versioning. To understand how versioning works, consider this example. Without versioning, if you upload an object with the same name as an existing object in the same bucket, the contents of the original object will get overwritten. But if you enable versioning on the bucket and then upload an object with the same name as an existing object, S3 will simply create a new version of that object. The original version will remain intact and available. If you delete an object in a bucket on which versioning is disabled, the contents of the object aren’t deleted. Instead, S3 adds a delete marker to the object and hides it from the S3 service console view. Versioning is disabled by default when you create a bucket. You must explicitly enable versioning on a bucket to use it, and it applies to all objects in the bucket. There’s no limit to the number of versions of an object you can store. You can delete versions manually or automatically using object life cycle configurations
### Object Life Cycle Configurations
Because S3 can store practically unlimited amounts of data, it’s possible to run up quite a bill if you continually upload objects but never delete any. This could happen if you have an application that frequently uploads log fi les to a bucket. You may also spend more than necessary by keeping objects in a more expensive storage class when a cheaper one would meet your needs. Object life cycle confi gurations can help you control costs by automatically moving objects to different storage classes or deleting them after a time. Object life cycle confi guration rules are applied to a bucket and consist of one or both of the following types of actions: Transition actions Transition actions move objects to a different storage class once they’ve reached a certain age. For example, you can create a rule to move objects from the STANDARD storage class to the STANDARD_IA storage class 90 days after creation. Expiration actions These can automatically delete objects after they reach a certain age. For example, you can create a rule to delete an object older than 365 days. If you have versioning enabled on a bucket, you can create expiration actions to delete object versions of a certain age. This allows you to take advantage of versioning without having to store endless versions of an object. It’s common to use both types of act

Although bucket names must be globally unique, each bucket—and by extension any objects in that bucket—can exist in only one region. This helps with latency, security, cost, and compliance requirements, as your data is stored only in the region in which you create the bucket. You can use cross-region replication to copy the contents of an object from a bucket in one region to a bucket in another, but the objects are still uniquely separate objects. AWS never moves objects between regions.

#s3 allows you to choose the plan which is the best suitable for your business needs. There are such options:
### S3 Standard
- Designed for frequently accessed data
- Stores data in a minimum of three Availability Zones

Amazon S3 Standard provides high availability for objects. This makes it a good choice for a wide range of use cases, such as websites, content distribution, and data analytics. Amazon S3 Standard has a higher cost than other storage classes intended for infrequently accessed data and archival storage.
### S3 Standard-Infrequent Access (S3 Standard-IA)
- Ideal for infrequently accessed data
- Similar to Amazon S3 Standard but has a lower storage price and higher retrieval price
Amazon S3 Standard-IA is ideal for data infrequently accessed but requires high availability when needed. Both Amazon S3 Standard and Amazon S3 Standard-IA store data in a minimum of three Availability Zones. Amazon S3 Standard-IA provides the same level of availability as Amazon S3 Standard but with a lower storage price and a higher retrieval price.
### S3 One Zone-Infrequent Access (S3 One Zone-IA)
- Stores data in a single Availability Zone
- Has a lower storage price than Amazon S3 Standard-IA
Compared to S3 Standard and S3 Standard-IA, which store data in a minimum of three Availability Zones, S3 One Zone-IA stores data in a single Availability Zone. This makes it a good storage class to consider if the following conditions apply:
- You want to save costs on storage.
- You can easily reproduce your data in the event of an Availability Zone failure.
### S3 Intelligent-Tiering
- Ideal for data with unknown or changing access patterns
- Requires a small monthly monitoring and automation fee per object

In the S3 Intelligent-Tiering storage class, Amazon S3 monitors objects’ access patterns. If you haven’t accessed an object for 30 consecutive days, Amazon S3 automatically moves it to the infrequent access tier, S3 Standard-IA. If you access an object in the infrequent access tier, Amazon S3 automatically moves it to the frequent access tier, S3 Standard.
### S3 Glacier Instant Retrieval
- Works well for archived data that requires immediate access
- Can retrieve objects within a few milliseconds
When you decide between the options for archival storage, consider how quickly you must retrieve the archived objects. You can retrieve objects stored in the S3 Glacier Instant Retrieval storage class within milliseconds, with the same performance as S3 Standard.
### S3 Glacier Flexible Retrieval
- Low-cost storage designed for data archiving
- Able to retrieve objects within a few minutes to hours
S3 Glacier Flexible Retrieval is a low-cost storage class that is ideal for data archiving. For example, you might use this storage class to store archived customer records or older photos and video files. You can retrieve your data from S3 Glacier Flexible Retrieval from 1 minute to 12 hours.
### S3 Glacier Deep Archive
- Lowest-cost object storage class ideal for archiving
- Able to retrieve objects within 12 hours
- 3 AZ used
S3 Deep Archive supports long-term retention and digital preservation for data that might be accessed once or twice in a year. This storage class is the lowest-cost storage in the AWS Cloud, with data retrieval from 12 to 48 hours. All objects from this storage class are replicated and stored across at least three geographically dispersed Availability Zones.
### S3 Outposts
- Creates S3 buckets on Amazon S3 Outposts
- Makes it easier to retrieve, store, and access data on AWS Outposts
Amazon S3 Outposts delivers object storage to your on-premises AWS Outposts environment. Amazon S3 Outposts is designed to store data durably and redundantly across multiple devices and servers on your Outposts. It works well for workloads with local data residency requirements that must satisfy demanding performance needs by keeping data close to on-premises applications.
## AWS Storage Gateway
AWS Storage Gateway makes it easy to connect your existing on-premises servers to storage in the AWS cloud. Because it uses industry-standard storage protocols, there’s no need to install special software on your existing servers. Instead, you just provision an AWS Storage Gateway virtual machine on-premises and connect your servers to it. Storage Gateway handles the data transfer between your servers and the AWS storage infrastructure. The virtual machine can run on a VMware ESXi or Microsoft Hyper-V hypervisor. AWS Storage Gateway offers the following three virtual machine types for different use cases: 
- File gateways
- Volume gateways
- Tape gateways
#### File Gateways
A file gateway lets you use the Network File System (NFS) and Server Message Block (SMB) protocols to store data in Amazon S3. Although data is stored on S3, it’s cached locally, allowing for low-latency access. A file gateway can function as a normal on-premises file server. Because data is stored in S3, you can take advantage of all S3 features including versioning, bucket policies, life cycle management, encryption, and cross-region replication.
#### Volume Gateways
Volume gateways offer S3-backed storage volumes that your on-premises servers can use via the Internet Small Computer System Interface (iSCSI) protocol. Volume gateways support the following two configurations:
- Stored volumes With a stored volume, Storage Gateway stores all data locally and asynchronously backs it up to S3 as Elastic Block Store (EBS) snapshots. Stored volumes are a good option if you need uninterrupted access to your data. A stored volume can be from 1 GB to 16 TB in size.
- Cached volumes The volume gateway stores all your data on S3, and only a frequently used subset of that data is cached locally. A cached volume can range from 1 GB to 32 TB in size. This is a good option if you have a limited amount of local storage. A cached volume can range from 1 GB to 32 TB in size. Because only a subset of data is cached locally, it’s possible that any interruption in connectivity to AWS could make some data inaccessible. If this isn’t acceptable, you should use stored volumes instead.
Both configurations allow you to take manual or scheduled EBS snapshots of your volumes. EBS snapshots are always stored in S3. You can restore an EBS snapshot to an on-premises gateway storage volume or an EBS volume that you can attach to an EC2 instance.
#### Tape Gateways
A tape gateway mimics traditional tape backup infrastructure. It works with common backup applications such as Veritas Backup Exec and NetBackup, Commvault, and Microsoft System Center Data Protection Manager. You simply configure your backup application to connect to the tape gateway via iSCSI. On the tape gateway, you create virtual tapes that can store between 100 GB and 2.5 TB each. A tape gateway stores virtual tapes in a virtual tape library (VTL) backed by S3. Here’s how it works: when your backup software writes data to a virtual tape, the tape gateway asynchronously uploads that data to S3. Because backups can be quite large and take a long time to upload, the tape gateway keeps the data in cache storage until the upload is complete. If you need to recover data from a virtual tape, the tape gateway will download the data from the S3-backed VTL and store it in its cache. For cost-effective, long-term storage, you can archive virtual tapes by moving them out of a VTL and into a virtual tape shelf backed by Glacier. To restore an archived virtual tape, you must initiate a retrieve request, which can take 3 to 5 hours. Once the retrieval is complete, the virtual tape will be available in your S3-backed VTL and will be available to transfer to the tape gateway.

## **Amazon FSx**

Amazon FSx is a fully managed service that provides file storage for Windows and Lustre-based workloads. It offers highly scalable, high-performance file systems, with multiple options to support different types of applications.
#### Types of Amazon FSx:
- **Amazon FSx for Windows File Server**: This service provides a fully managed Windows file system that supports SMB (Server Message Block) protocol. It is ideal for applications that require a file system for Microsoft Windows environments.
    - **Use Cases**:
        - Windows-based applications needing file storage (e.g., enterprise applications).
        - Windows environments where SMB is used for shared file access.
- **Amazon FSx for Lustre**: This service is designed for high-performance workloads, especially for compute-intensive applications. Lustre is an open-source file system optimized for high-performance computing (HPC).
    - **Use Cases**:
        - Data analytics, machine learning, financial simulations, and rendering.
        - High-performance computing applications that need fast storage and data throughput.
## **AWS Backup**

AWS Backup is a fully managed service for automating and centrally managing backups across AWS services. It simplifies the process of creating and managing backups for AWS resources such as EC2, RDS, DynamoDB, EFS, and more.
#### Key Features:
- **Centralized Backup Management**: You can create and manage backup plans for AWS services in a single location.
- **Backup Policies**: Set automated backup policies for different AWS services, with options for frequency and retention.
- **Cross-region and Cross-account Backup**: You can back up data to other regions or accounts for added redundancy and disaster recovery.
- **Integration with AWS Services**: Works seamlessly with other AWS services like Amazon EC2, RDS, DynamoDB, EFS, and Amazon FSx.
#### Use Cases:
- **Disaster Recovery**: Ensure data is safely backed up in case of accidental deletion or system failure.
- **Compliance**: Meet regulatory requirements that necessitate the retention and protection of data over specific time periods.
- **Backup Automation**: Automate backups of critical workloads to reduce manual intervention and the risk of human error.
#### Benefits:
- Automated, centralized backup management.
- Reduced cost and complexity of backups across multiple services.
- Secure backup with encryption.
- Backup retention policies aligned with business needs.