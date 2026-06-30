`PREVIOUS CONTENT:` [I. Compute Services](1_Compute-Services.md)
-----------------------------
# Storage and Content Delivery [^](../../README.md#3-aws-certified-developer-associate)

- [Amazon S3](#amazon-s3-bucket-)
- [Database Services](#database-services-)
- [DynamoDB](#dynamodb--)
- [Amazon RDS](#amazon-rds-)
- [Amazon Redshift](#amazon-redshift-)
- [Amazon Database Migration Service](#amazon-database-migration-service-amazon-dms-)


## Amazon S3 Bucket [^](#storage-and-content-delivery-)
- The bucket name must be unique worldwide, and must not contain spaces or uppercase letters.

#### Bucket versioning and encryption
- **Bucket versioning** - Recommended to be kept disabled
- **Encryption** - If enabled, will encrypt the files being stored in the bucket.
- **Object Lock** - If enabled, will prevent the files in the bucket from being deleted or modified

### Details of an Existing Bucket

#### Properties
- **Bucket Versioning**: Allows to keep multiple versions of an object in the same bucket.
- **Static web hosting**: Mark if the bucket is used to host a website.
- **Requester pays**: Makes the requester pay for requests and data transfer costs.
- **Server access logging**: Log requests for access to bucket.


#### Permissions
- Shows who has access to the S3 bucket and who has access to the data within the bucket.
- Enables to write an access policy (in JSON format) to provide access to the objects stored in the bucket.

#### Metrics
View the metrics for usage, request, and data transfer activity within the bucket such as 
**total bucket size, total number of objects, and storage class analysis**.

#### Management
- Allows to create life cycle rules to help manage objects.
- Includes rules such as transitioning objects to another storage class, archiving, or deleting after a specific period.

#### Access Points
- Create access endpoints for sharing the bucket at scale.
- Using an endpoint, you can perform all regular operations on the bucket.

## Database Services [^](../../README.md#3-aws-certified-developer-associate)

### Data Source Types

#### Structured Data
- organized to support transactional and analytical applications.
- can also be stored in non-relational databases.
- valuable because user can gain insight into overarching trends by efficiently running powerful data queries and analysis.

#### Semistructured Data
- Flexible and can be updated without the requirement to change the schema for every single record in the table.
- Allows a user to capture any data in any structure as data evolves and changes over time.
- often stored in Non-RDBS.
- Example of semistructured data include XML, email, JSON.

#### Unstructured Data
- not organized in any distinguishable and predefined manner.
- Commonly stored in non-relational key-value databases.
- Examples are word processing documents, videos, photos, other images.
- Not organized other than being placed into a file system, object store, or another repository such as data lakes.

### Relational Databases

#### Data Indexing
- Tables should be indexed to allow a query to quickly find the data needed to produce a result.
- Indexes can also help control the way data is physically stored on a disk.
- Indexing plays a huge part in the speed and efficiency of queries.


#### Online Transaction Processing (OLTP)
- Databases focus on recording Update, Insertion, and Deletion data transactions.
- OLTP queries are simple and short, which requires less time and space to process.
- e.g. ATM Banks

#### Online Analytical Processing (OLAP)
- Databases store historical data that has been input by OLTP.
- OLAP DBs allow users to view different summaries of multidimensional data.
- Using OLAP, extract information from a large database and analyze it for decision-making.
- e.g. BI tool

## DynamoDB [^](#storage-and-content-delivery-) 
- Serverless NoSQL document database
- Can handle more than 10 trillion requests per day. Support peaks of more than 20 million requests per second
- Supports key-value and document data models.
- Synchronously replicates data across three (3) AZs in an AWS Region
- Automatically scales up and down to adjust for the capacity and maintain system performance.
- Two Capacity modes: **provisioned** and **on-demand**
  - **on-demand**: Billed for every read and write that application performs.
  - **provisioned**: Specify the number of reads and writes per second.

### Technical Overview
- Uses **partition key** to find each item in the database
- Uses **sort key** to store related attributes in a sorted order. This allows multiple items to be queried as a collection.
- The **primary key** is a combination of the partition and sort key (called composite primary key). If there is no sort key, the primary key and partition key are the same.

#### Secondary indexes
These indexes improve the application's ability to access data quickly and efficiently

- **Local secondary index** - uses the table's partition key with a unique sort key. (allowed five per table)
- **Global secondary index** - uses a partition key and sort key that can be different from those on the table to model very complex data access patterns that differ from the original tble. (allowed 20 per table)

#### DynamoDB Security
- Uses IAM to create and manage credentials. DynamoDB requires both authentication and permission to access tables and data.
- Access are controlled at the table and item level.
- Tables have encryption at rest by default.

## Amazon RDS [^](#storage-and-content-delivery-)
- When creating a database, there are two (2) options:
  - **Standard create**: Set all the configuration options, including ones for availability, security, backups, and maintenance.
  - **Easy create:** Use industry best-practice configurations. All config options, except the encryption and VPC details, can be changed after the database is created.

### Technical Overview
- Security Groups are used to control access to databases
- Amazon RDS uses AES-256 bit encryption algorithm for data at rest.
- Securing communications to/from the database (data in-transit) is accomplished through HTTPS connections. These connections are encrypted using Secure Sockets Layer (SSL).

## Amazon Redshift [^](#storage-and-content-delivery-)
- Redshift delivers great performance by using machine learning.
- **Redshift Spectrum** is a feature that enables to run queries against data in Amazon S3.
- Redshift encrypts and keeps data secure in transit and at rest.
- Redshift clusters can be isolated using VPC.
- Redshift is NOT be used for processing day-to-day transactions.

## Amazon Database Migration Service (Amazon DMS) [^](#storage-and-content-delivery-)
- The service needs the source database endpoint and target database endpoint
- An EC2 instance must be created manually. AWS DMS will automatically configure the replication software and use this instance for replication.


## Amazon ElastiCache [^](#storage-and-content-delivery-)
- Provides high performance, resizable, and cost-effective in-memory cache.
- Supports two open-source in-memory caching engines: **Redis** and **Memcached**
- For real-time use cases that require ultrafast performance and high throughput.
- Primary data store for use cases that does not require durability (session stores, gaming leaderboards, streaming, API rate limiting).
- The default port for ElastiCache is 6379

### Pricing Options
1. **On-Demand Nodes** - Billed hourly (from the time a node launched until terminated) for memory capacity. Partial node hour is considered as a full hour
2. **Reserved Nodes** - 1-year or 3-year term. Pay one-time with lower hourly charged
3. **Backup Storage** - ElastiCache provides storage space for one snapshot free of charge for each active ElastiCache for Redis cluster
4. **Data Transfer** - No charge for data transfer between EC2 and ElastiCache inside the same AZ.

### ElastiCache for Redis (non-cluster mode) Characteristics
- Only one primary instance support is available for up to 5 read replicas per primary node
- Supported automatic failover. If primary node fails, one of the replicas is promoted to the primary role.
- All write activity takes place in the primary node. Read activity may happen from any nodes.
- Supported multi-AZ configuration
- AWS managed DNS services are automatically updated to point to the read/write primary node and read-only node.

### ElastiCache for Redis (cluster mode) Characteristics
- Supports up to 5 read replicas per primary node and supports multiple primary nodes (shards) up to total of 500 nodes (with no replica)
- Uses automatic node promotion
- Supports sharding as a means to distribute the load. Cluster mode is used when deploying a number of smaller nodes.

> ElastiCache for MemCached is much simpler and user-friendly

### ElastiCache for Redis Use Cases
1. **Caching** - Store copies of lookup tables and replies to costly queries from RDBMS
2. **Session stores** - Quickly create session stores
3. **Leaderboards**
4. **Geospatial**
5. **Message Queues**
6. **IoT Streaming**
7. **Machine Learning**

### ElastiCache for Memcached Use Cases
1. **Caching**
2. **Session Stores**
3. **Multithreaded Applications**
4. **API Counters**

## Amazon CloudFront [^](#storage-and-content-delivery-)
- Amazon continuously add Edge Locations.
- CloudFront ensures that end-user requests are served from the closes edge location.
- CloudFront works with non-AWS origin sources.
- Cache control headers determine how frequently CloudFront needs to check the origin for an updated version of user's file.
- The maximum size of a single file that can be delivered through Amazon CloudFront is 20GB.

### Important Notes - CloudFront
- As soon as CloudFront distribution is deployed, it attaches to its origin (e.g. S3) and starts caching its private content.
- Ones caching is complete, the CloudFront domain name URL will stop redirecting to the original URL.

-------------------------
`NEXT CONTENT:` [III. Security](3_Security.md)
------------------------