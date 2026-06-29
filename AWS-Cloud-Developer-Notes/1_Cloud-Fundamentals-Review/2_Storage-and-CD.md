`PREVIOUS CONTENT:` [I. Compute Services](1_Compute-Services.md)
-----------------------------
# Storage and Content Delivery [^](../../README.md#3-aws-certified-developer-associate)

- [Amazon S3](#amazon-s3-bucket-)
- [DynamoDB](#dynamodb--)
- [Amazon RDS](#amazon-rds-)
- [Amazon Redshift](#amazon-redshift-)


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

## Database Services

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
- Can handle more than 10 trillion requests per day.
- Supports key-value and document data models.
- Synchronously replicates data across three (3) AZs in an AWS Region

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