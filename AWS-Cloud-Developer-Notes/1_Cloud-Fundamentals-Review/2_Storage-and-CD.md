# Storage and Content Delivery [^](../../README.md#3-aws-certified-developer-associate)

- [Amazon S3](#amazon-s3-bucket)


## Amazon S3 Bucket
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

## DynamoDB
- Serverless NoSQL document database
- Can handle more than 10 trillion requests per day.
- Supports key-value and document data models.
- Synchronously replicates data across three (3) AZs in an AWS Region
- 


