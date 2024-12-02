## Relational database service (RDS)
It is a service that allows you to run relational databases in the cloud. 

Amazon RDS is a managed service that automates tasks such as hardware provisioning, database setup, patching, and backups. With these capabilities, you can spend less time completing administrative tasks and more time using data to innovate your applications. You can integrate Amazon RDS with other services to fulfill your business and operational needs, such as using AWS Lambda to query your database from a serverless application.

Amazon #RDS provides a number of different security options. Many Amazon RDS database engines offer encryption at rest (protecting data while it is stored) and encryption in transit (protecting data while it is being sent and received).

### **Amazon RDS database engines**
Amazon RDS is available on six database engines, which optimize for memory, performance, or input/output (I/O). Supported database engines include:

- Amazon #Aurora
- #PostgreSQL
- #MySQL
- #MariaDB
- Oracle Database
- Microsoft SQL Server

#### **Amazon Aurora**
[**Amazon Aurora**(opens in a new tab)](https://aws.amazon.com/rds/aurora/) is an enterprise-class relational database. It is compatible with MySQL and PostgreSQL relational databases. It is up to five times faster than standard MySQL databases and up to three times faster than standard PostgreSQL databases.

Amazon Aurora helps to reduce your database costs by reducing unnecessary input/output (I/O) operations, while ensuring that your database resources remain reliable and available. 

Consider Amazon Aurora if your workloads require high availability. It replicates six copies of your data across three Availability Zones and continuously backs up your data to Amazon S3.
### Scaling Horizontally with Read Replicas
In addition to scaling up by choosing a more powerful instance type or selecting high-IOPS storage, you can improve the performance of a database-backed application by adding additional RDS instances that perform only reads from the database. These instances are called read replicas. In a relational database, only the master database instance can write to the database. A read replica helps with performance by removing the burden of read-only queries from the master instance, freeing it up to focus on writes. Hence, read replicas provide the biggest benefit for applications that need to perform a high number of reads. Read replicas are also useful for running computationally intensive queries, such as monthly or quarterly reports that require reading and processing large amounts of data from the database.
### High Availability with Multi-AZ 
Even if you use read replicas, only the master database instance can perform writes against your database. If that instance goes down, your database-backed application won’t be able to write data until it comes back online. To ensure that you always have a master database instance up and running, you can configure high availability by enabling the multi-AZ feature on your RDS instance.
With multi-AZ enabled, RDS creates an additional instance called a standby database instance that runs in a different Availability Zone than your primary database instance. The primary instance instantly or synchronously replicates data to the secondary instance, ensuring that every time your application writes to the database, that data exists in multiple Availability Zones. If the primary fails, RDS will automatically fail over to the secondary. The failover can result in an outage of up to two minutes, so your application will experience some interruption, but you won’t lose any data. With multi-AZ enabled, you can expect your database to achieve a monthly availability of 99.95 percent. It’s important to understand that an instance outage may occur for reasons other than an Availability Zone outage. Routine maintenance tasks such as patching or upgrading the instance can result in a short outage and trigger a failover. If you use the Amazon Aurora database engine—Amazon’s proprietary database engine designed for and available exclusively with RDS—you can take advantage of additional benefits when using multi-AZ. When you use Aurora, your RDS instances are part of an Aurora cluster. All instances in the cluster use a shared storage volume that’s synchronously replicated across three different Availability Zones. Also, if your storage needs increase, the cluster volume will automatically expand up to 64 TB.
### Backup and Recovery
Whether or not you use multi-AZ, RDS can take manual or automatic EBS snapshots of your instances. Snapshots are stored across multiple Availability Zones. If you ever need to restore from a snapshot, RDS will restore it to a new instance. This makes snapshots useful not only for backups but also for creating copies of a database for testing or development purposes. You can take a manual snapshot at any time. You can configure automatic snapshots to occur daily during a 30-minute backup window. RDS will retain automatic snapshots between 1 day and 35 days, with a default of 7 days. Manual snapshots are retained until you delete them. Enabling automatic snapshots also enables point-in-time recovery, a feature that saves your database change logs every 5 minutes. Combined with automated snapshots, this gives you the ability to restore a failed instance to within 5 minutes before the failure—losing no more than 5 minutes of data.
### Amazon RedShift
it is a data warehouse service which allows you to analyse a high and vast amount of data. It offers the ability to collect data from many sources and helps you to understand relationships and trends across your data.
Amazon Redshift is a specialized type of managed relational database called a data warehouse. A data warehouse stores large amounts of structured data from other relational databases and allows you to perform complex queries and analysis against that data. For example, Redshift can combine data from financial, sales, and inventory databases into a single data warehouse and then analyze or generate reports on that data. Because data warehouses can grow quite large, they require a lot of storage. To use Redshift, you create a cluster consisting of at least one compute node and up to 128 nodes. Using dense compute nodes, you can store up to 326 TB of data on magnetic disks, and with dense storage nodes you can store up to 2 PB of data on SSDs.
Redshift’s usefulness isn’t limited to pulling in data from relational databases. Redshift Spectrum is a feature of Redshift that lets you analyze data stored in S3. The data must be structured, and you must define the structure so that Redshift can understand it.
## No-SQL Databases 
### Dynamo DB
The basic unit of organization in DynamoDB is an item, which is analogous to a row or record in a relational database. DynamoDB stores items in tables. Each DynamoDB table is stored across one or more partitions. Each partition is backed by solid-state drives, and partitions are replicated across multiple Availability Zones in a region, giving you a monthly availability of 99.99 percent. Each item must have a unique value for the primary key. An item can also consist of other key-value pairs called attributes. Each item can store up to 400 KB of data

[**Amazon DynamoDB**(opens in a new tab)](https://aws.amazon.com/dynamodb/) is a key-value database service. It delivers single-digit millisecond performance at any scale.
- **Tables**: In DynamoDB, data is stored in tables. Unlike relational databases, DynamoDB is a NoSQL database, so it doesn’t use tables with fixed schemas.
- **Items**: Each table is made up of items. An item is a single record in a table and can have a unique set of attributes.
- **Attributes**: These are the data elements in an item. Attributes can be of different data types, such as strings, numbers, booleans, lists, and maps.
	 - Scalar A scalar data type has only one value and can be a string, a number, binary data, or a Boolean value.
	  - Set A set data type can have multiple scalar values, but each value must be unique within the set.
	  - Document The document data type is subdivided into two subtypes: list and map. Document data types can store values of any type. List documents are ordered, whereas map documents are not. Document data types are useful for storing structured data, such as an IAM policy document stored in JavaScript Object Notation (JSON) format. DynamoDB can recognize and extract specific values nested within a document, allowing you to retrieve only the data you’re interested in without having to retrieve the entire document
- **Primary Keys**:
    - **Partition Key**: A simple primary key consisting of one attribute. DynamoDB uses the partition key to distribute data across partitions.
    - **Composite Primary Key**: A combination of a partition key and a sort key. This allows for sorting data within a partition.
- **Secondary Indexes**: DynamoDB provides the ability to query data using secondary indexes:
    - **Global Secondary Index (GSI)**: An index with a different partition and sort key from the original table.
    - **Local Secondary Index (LSI)**: An index with the same partition key as the table but a different sort key.

#### **Partition Key**
A **Partition Key** is the simplest form of a primary key in DynamoDB. It consists of a single attribute that uniquely identifies each item in a table. This key is used to determine where the item is stored in DynamoDB's underlying storage system.

- **Data Distribution**: DynamoDB uses the partition key value to create a hash that is used to distribute data across multiple storage nodes. This ensures that data is evenly distributed and can be accessed efficiently, even at scale. However, if you choose a partition key that does not distribute data evenly (for example, using timestamps as keys that could cluster data in a narrow range), you might experience performance bottlenecks.
- **Example**: Suppose you are building a user management system, and you choose the `userId` attribute as your partition key. Each user in your table would be uniquely identified by their `userId`. If the `userId` attribute has a wide range of unique values, your data will be evenly distributed across DynamoDB partitions.

##### Considerations for Using a Partition Key:

- **Uniform Distribution**: It’s essential to choose a partition key that provides a uniform distribution of data to avoid "hot partitions." Hot partitions occur when a small number of partition keys receive a disproportionate amount of traffic, leading to performance degradation.
- **Single Access Pattern**: Using only a partition key limits your querying capabilities to fetching items by that specific key, which may restrict your application's flexibility in accessing data.
#### **Composite Primary Key**
A **Composite Primary Key** consists of two attributes: a **Partition Key** and a **Sort Key**. This combination allows you to create a more complex and flexible key structure for accessing and organizing your data.

- **Partition Key**: The first attribute, which functions similarly to the simple partition key. It is used to distribute data across DynamoDB's partitions.
- **Sort Key**: The second attribute, which is used to sort the data within each partition. The sort key allows you to store multiple related items under the same partition key and query them in a sorted manner.
- **Data Organization**: By using a composite key, you can efficiently store and retrieve related items that are logically grouped together. This is especially useful for use cases where you need to query a range of items that share the same partition key but differ in the sort key.
##### Example of Composite Primary Key Usage:
Imagine you are developing a blogging platform where each user can create multiple posts. You could structure your primary key as follows:

- **Partition Key**: `userId` (to group all posts by the same user under one partition)
- **Sort Key**: `timestamp` (to sort the user's posts by the time they were created)
#### Scaling Horizontally
DynamoDB uses the primary key to distribute items across multiple partitions. Distributing the data horizontally in this fashion makes it possible for DynamoDB to consistently achieve low-latency reads and writes regardless of how many items are in a table. The number of partitions DynamoDB allocates to your table depends on the number of write capacity units (WCU) and read capacity units (RCU) you allocate to your table. The higher the transaction volume and the more data you’re reading or writing, the higher your RCU or WCU values should be. Higher values cause DynamoDB to distribute your data across more partitions, increasing performance and decreasing latency. As demand on your DynamoDB tables changes, you can change the number of RCU and WCU accordingly. Alternatively, you can configure DynamoDB Auto Scaling to dynamically adjust the number of WCU and RCU based on demand. This automatic horizontal scaling ensures consistent performance, even during times of peak load.
#### Queries and Scans
Recall that nonrelational databases let you quickly retrieve items from a table based on the value of the primary key. For example, if the primary key of a table is Username, you can perform a query for the user named pdrake. If an item exists with that primary key value, DynamoDB will return the item instantly. Searching for a value in an attribute other than the primary key is possible, but slower. To locate all items with a Username that starts with the letter p, you’d have to perform a scan operation to list all items in the table. This is a read-intensive task that requires scanning every item in every partition your table is stored in. Even if you know all the attributes of an item except for the primary key, you’d still have to perform a scan operation to retrieve the item.
### Amazon DynamoDB Accelerator
[**Amazon DynamoDB Accelerator (DAX)**(opens in a new tab)](https://aws.amazon.com/dynamodb/dax/) is an in-memory cache for DynamoDB. 
It helps improve response times from single-digit milliseconds to microseconds.
## RDS vs No-SQL
In any time when you dont need a complex data analytics, the simple dynamoDb will make the job perfectly for you
## **Additional database services**

### Amazon DocumentDB
[**Amazon DocumentDB**(opens in a new tab)](https://aws.amazon.com/documentdb) is a document database service that supports MongoDB workloads. (MongoDB is a document database program.)
### Amazon Neptune
[**Amazon Neptune**(opens in a new tab)](https://aws.amazon.com/neptune) is a graph database service. 
You can use Amazon Neptune to build and run applications that work with highly connected datasets, such as recommendation engines, fraud detection, and knowledge graphs.
### Amazon Quantum Ledger Database (Amazon QLDB)
[**Amazon Quantum Ledger Database (Amazon QLDB)**(opens in a new tab)](https://aws.amazon.com/qldb) is a ledger database service. 
You can use Amazon QLDB to review a complete history of all the changes that have been made to your application data.
### Amazon Managed Blockchain
[**Amazon Managed Blockchain**(opens in a new tab)](https://aws.amazon.com/managed-blockchain) is a service that you can use to create and manage blockchain networks with open-source frameworks. 
Blockchain is a distributed ledger system that lets multiple parties run transactions and share data without a central authority.
### Amazon ElastiCache
[**Amazon ElastiCache**(opens in a new tab)](https://aws.amazon.com/elasticache) is a service that adds caching layers on top of your databases to help improve the read times of common requests. 
It supports two types of data stores: Redis and Memcached.

