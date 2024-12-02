## 6 strategies for migration

When migrating applications to the cloud, six of the most common [migration strategies(opens in a new tab)](https://aws.amazon.com/blogs/enterprise-strategy/6-strategies-for-migrating-applications-to-the-cloud/)
### Rehosting
**Rehosting** also known as “lift-and-shift” involves moving applications without changes. 
In the scenario of a large legacy migration, in which the company is looking to implement its migration and scale quickly to meet a business case, the majority of applications are rehosted.   
### Replatforming
**Replatforming**, also known as “lift, tinker, and shift,” involves making a few cloud optimizations to realize a tangible benefit. Optimization is achieved without changing the core architecture of the application.
### Refactoring/re-architecting
**Refactoring** (also known as **re-architecting**) involves reimagining how an application is architected and developed by using cloud-native features. Refactoring is driven by a strong business need to add features, scale, or performance that would otherwise be difficult to achieve in the application’s existing environment.
### Repurchasing
**Repurchasing** involves moving from a traditional license to a software-as-a-service model. 
For example, a business might choose to implement the repurchasing strategy by migrating from a customer relationship management (CRM) system to Salesforce.com.
#### **When Repurchase May Not Be Ideal**
While repurchase can be transformative, it might not suit every situation:
- **Data Sensitivity:** Some industries, like finance or healthcare, may have strict regulatory requirements that complicate the use of certain SaaS solutions.
- **Dependency on Custom Features:** Legacy applications may have specific customizations that SaaS solutions cannot replicate.
- **Integration Challenges:** Migrating to a new platform might require significant changes to existing workflows or integrations.
### Retaining
**Retaining** consists of keeping applications that are critical for the business in the source environment. This might include applications that require major refactoring before they can be migrated, or, work that can be postponed until a later time.
### Retiring
**Retiring** is the process of removing applications that are no longer needed.
## AWS Snow Family members
The [**AWS Snow Family**(opens in a new tab)](https://aws.amazon.com/snow) is a collection of physical devices that help to physically transport up to exabytes of data into and out of AWS. 

![[Pasted image 20241110125733.png]]
### AWS Snowcone 
[**AWS Snowcone**(opens in a new tab)](https://aws.amazon.com/snowcone) is a small, rugged, and secure edge computing and data transfer device. 
It features 2 CPUs, 4 GB of memory, and up to 14 TB of usable storage.
### AWS Snowball
[**AWS Snowball**(opens in a new tab)](https://aws.amazon.com/snowball/) offers two types of devices:
- **Snowball Edge Storage Optimized** devices are well suited for large-scale data migrations and recurring transfer workflows, in addition to local computing with higher capacity needs. 
    - Storage: 80 TB of hard disk drive (HDD) capacity for block volumes and Amazon S3 compatible object storage, and 1 TB of SATA solid state drive (SSD) for block volumes. 
    - Compute: 40 vCPUs, and 80 GiB of memory to support Amazon EC2 sbe1 instances (equivalent to C5).
- **Snowball Edge Compute Optimized** provides powerful computing resources for use cases such as machine learning, full motion video analysis, analytics, and local computing stacks. 
    - Storage: 80-TB usable HDD capacity for Amazon S3 compatible object storage or Amazon EBS compatible block volumes and 28 TB of usable NVMe SSD capacity for Amazon EBS compatible block volumes. 
    - Compute: 104 vCPUs, 416 GiB of memory, and an optional NVIDIA Tesla V100 GPU. Devices run Amazon EC2 sbe-c and sbe-g instances, which are equivalent to C5, M5a, G3, and P3 instances.
### AWS Snowmobile
[**AWS Snowmobile**(opens in a new tab)](https://aws.amazon.com/snowmobile) is an exabyte-scale data transfer service used to move large amounts of data to AWS. 
You can transfer up to 100 petabytes of data per Snowmobile, a 45-foot long ruggedized shipping container, pulled by a semi trailer truck.

## Database migration

### **AWS Database Migration Service (AWS DMS)**
**AWS DMS** is a fully managed service designed to help migrate databases to AWS quickly and securely. It supports both **homogeneous migrations** (e.g., Oracle to Oracle) and **heterogeneous migrations** (e.g., Oracle to Amazon Aurora or PostgreSQL). It is typically used when you want to move a database from an on-premises environment, or even between AWS services, with minimal downtime.
#### Key Features:
- **Continuous Data Replication**: AWS DMS supports continuous data replication, which means it can migrate your database without taking it offline. This is particularly useful for applications that need to remain online during migration.
- **Supports Multiple Database Engines**: It supports a wide range of source and target database engines, such as:
    - **Source**: Oracle, SQL Server, MySQL, PostgreSQL, MariaDB, MongoDB, and others.
    - **Target**: Amazon RDS, Amazon Aurora, Amazon Redshift, DynamoDB, and other AWS services.
- **Automated Monitoring**: AWS DMS provides automated monitoring, so you can easily track your migration process and make adjustments if needed.
- **Data Validation**: It includes tools to check the consistency of data between the source and target databases during and after migration.
- **Minimal Downtime**: It allows for migrations with minimal downtime, which is key for production systems. You can use it for live migrations (where replication happens in real-time) or for a one-time migration.
#### How AWS DMS Works:
1. **Source Database**: AWS DMS connects to the source database and starts extracting data.
2. **Replication Instance**: The service uses a replication instance in AWS to process and transform data as it moves from the source database to the target.
3. **Target Database**: Once the data is processed, it’s moved to the target database, such as Amazon RDS or Amazon Aurora.
**Use Cases for AWS DMS**:
- Migrating databases to Amazon RDS or Aurora.
- Replicating on-premises databases to the cloud for disaster recovery.
- Real-time analytics by moving data to Amazon Redshift.
### **AWS Schema Conversion Tool (AWS SCT)**
**AWS SCT** helps you convert your database schema (the structure of your database) from one database engine to another. It is particularly useful when performing **heterogeneous migrations**, where the source and target databases are of different types (e.g., Oracle to Amazon Aurora or MySQL to PostgreSQL).
#### Key Features:
- **Schema Conversion**: AWS SCT converts database objects like tables, views, stored procedures, and functions from one database engine to another. It helps automate the process of converting the schema, which is often a tedious and error-prone task when done manually.
- **Assessment Reports**: SCT generates an assessment report, which provides an analysis of the compatibility between the source and target database engines. This report identifies any potential issues that may arise during migration, such as unsupported features or differences in data types.
- **Code Conversion**: It helps in converting stored procedures, triggers, and functions. Some manual adjustments may still be necessary depending on the complexity of the code.
- **Comprehensive Support for Different Engines**: AWS SCT supports many popular database engines, including:
    - **Source**: Oracle, SQL Server, MySQL, PostgreSQL, and others.
    - **Target**: Amazon Aurora, Amazon RDS, Amazon Redshift, and other AWS databases.
#### How AWS SCT Works:
1. **Connect to the Source Database**: SCT connects to your source database and retrieves the schema.
2. **Generate Conversion Report**: It evaluates how compatible the schema is with the target engine and generates a detailed report.
3. **Convert the Schema**: AWS SCT converts the schema (tables, indexes, etc.) to a format compatible with the target database engine.
4. **Deploy Converted Schema**: The converted schema can be deployed directly to the target database, but you may need to manually modify certain parts (e.g., stored procedures) that aren’t fully compatible.
**Use Cases for AWS SCT**:
- Converting an on-premises Oracle database schema to Amazon Aurora.
- Migrating from SQL Server to PostgreSQL.
- Preparing a database schema for migration to AWS RDS or Amazon Aurora.
### Integration of AWS DMS and AWS SCT
When migrating databases, **AWS DMS** and **AWS SCT** are often used together:
- **AWS SCT** helps convert the database schema to match the target database engine.
- **AWS DMS** then migrates the data from the source database to the target database, ensuring that the migration is done with minimal downtime.