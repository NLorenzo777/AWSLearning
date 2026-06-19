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

## DynamoDB [^](#storage-and-content-delivery-) 
- Serverless NoSQL document database
- Can handle more than 10 trillion requests per day.
- Supports key-value and document data models.
- Synchronously replicates data across three (3) AZs in an AWS Region

## Amazon RDS [^](#storage-and-content-delivery-)
- When creating a database, there are two (2) options:
  - **Standard create**: Set all the configuration options, including ones for availability, security, backups, and maintenance.
  - **Easy create:** Use industry best-practice configurations. All config options, except the encryption and VPC details, can be changed after the database is created.

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