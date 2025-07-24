# Databases in AWS [↑](AWS-Practitioner-Essentials-Notes.md)
- [RDBS Introduction](#relational-database-services-)
- [Amazon Relational Database Service (Amazon RDS)](#amazon-relational-database-service-amazon-rds-)
  - [Supported Database Engines](#amazon-rds-supported-database-engines)
- [Amazon Aurora](#amazon-aurora-)
- [Amazon DynamoDB](#amazon-dynamodb-)
- [Amazon Redshift](#amazon-redshift-)
- [Amazon Database Migration Service (DMS)](#amazon-database-migration-service-amazon-dms-)
- [Other Amazon Database Services](#additional-database-services-)

## Relational Database Services [↑](#databases-in-aws-)
- RDBs store data in a way that relates it to other pieces of data, and they use structures query language (SQL) to manage and query data.
- Stores data in an easily understandable, consistent, and scalable way that **works great for applications requiring structured data management**.

## `Amazon Relational Database Service (Amazon RDS)` [↑](#databases-in-aws-)
- Managed relational database service that handles routine database tasks such as backups, patching, and hardware provisioning.
- Supports multiple database instance class types that optimize for memory, performance, or I/O.
- Offers Multi-AZ deployment and automated backups to improve data resilience. There is also an option to manually create backups using **RDS Snapshots**.
- Offers security features including network isolation, _encryption in transit_, and _encryption at rest_.
- Readily scale database resources vertically or horizontally.
- Remove the burden of database administration while maintaining high availability and security in AWS.

### Amazon RDS Supported Database Engines
- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle Database
- Microsoft SQL Server

## `Amazon Aurora` [↑](#databases-in-aws-)
- An enterprise-class relational database.
- Compatible with MySQL and PostgreSQL.
- Up to 5x faster than standard MySQL databases and up to 3x faster than standard
  PostgreSQL databases.
- Price is 1/10th the cost of commercial databases. Cost is reduced by reducing unnecessary I/O
  operations, while ensuring that database resources remain reliable and available.
- Recommended for workloads that require high availability. It replicates **6 copies** of data
  across **3 AZs** and continuously backups data to Amazon S3.

## `Amazon DynamoDB` [↑](#databases-in-aws-)
- Stores data redundantly across AZs. Mirrors data across multiple drives.
- Key-value database service that is reliable and high performance (millisecond response time).
- For Non-Relational Database (NoSQL). Simple flexible schemas
- Adding and removing of attributes can be done at any time.
- Automatically Scales while maintaining consistent performance. Mekase it a suitable choice for
  use cases that require high performance while scaling.

### Non Relational Database (NoSQL Databases)
- Uses structures (JSON, key-value pairs) other than rows and columns to organize data.

## `Amazon Redshift` [↑](#databases-in-aws-)
- Data warehouse as a service
- Handles the heavy lifting in provisioning the data warehouse so that users can focus on the
  data alone.
- Applicable for Big BI data solutions (Big Data Analytics) which is a concept of looking at
  historical data.
- Offers ability to collect data from many sources and helps understand relationships and trends
  across data.

## `Amazon Database Migration Service (Amazon DMS)` [↑](#databases-in-aws-)
- Enables the migration of RDBs, NRDBs, and other types of data stores.
- **Homogenous Databases:** Databases that are of the same type.
- **Heterogeneous Databases:** Databases that are of different source/type. Additional step
  where an AWS Schema Conversion tool is used.

## `Additional Database Services` [↑](#databases-in-aws-)

| Purpose-Build Databases                          | Description                                                                                                                                                                         |
|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amazon DocumentDB**                            | - Document database service that supports **MongoDB** workloads <br/> - Fully managed native **JSON** document.                                                                     |
| **Amazon Neptune**                               | - A Graph database service.<br/> - For applications that are build and run with highly connected datasets<br/> - Ex: Recommendation engines, fraud detection, and knowledge graphs. |
| **Amazon Quantum Ledger Database (Amazon QLDB)** | - Review a complete history of all the changes that have been made to application data.                                                                                             |
| **Amazon Managed Blockchain**                    | - Service to create and manage blockchain networks with open-source frameworks.<br/>                                                                                                |
| **Amazon ElastiCache**                           | - Service that adds caching layers on top of <br/>databases to help improve the read times of common requests. Supports _Redis_ and _Memcached_ data store types.                   |
| **Amazon DynamoDB Accelerator**                  | - In-Memory cache for DynamoDB. <br/> - Helps improve response times from single-digit milliseconds to microseconds.                                                                |

### Useful Links
- [Deep Dive - Databases](https://docs.aws.amazon.com/decision-guides/latest/databases-on-aws-how-to-choose/databases-on-aws-how-to-choose.html)