<html lang="eng">
<head>
<title>AWS Cloud Developer Associate - MCQs</title>
</head>

<style>
    details span {
        background-color: green;
        color: black;
    }
</style>

<body>

### Time-To-Live (TTL) can be used to have DynamoDB delete expired items from a table without being charged for WCU consumption. When you set an attribute for use by TTL, what is the value you should set for that attribute to result in expiry?

- The number of seconds since last update for the item to remain in the table.
- The epoch timestamp (with unit seconds) after which the item can be removed. 
- The number of days since last update for the item to remain in the table.
- A string pattern which needs to match the TTL expression for expiry.
- A Boolean specifying true or false for expiration.

<details>
    <summary>Reveal Answer</summary>
    <span><strong>The epoch timestamp (with unit seconds) after which the item can be removed</strong></span>
</details>


### Optimistic concurrency control in DynamoDB provides a form of locking. Which is the correct description of the mechanism?

- Read, transform, conditionally write, retry as required.
- Strongly consistent write with lock option set true.
- Enable streams, check the stream to confirm no other updates are in progress, DeleteItem, PutItem.
- PutItem/UpdateItem, then strongly consistent GetItem to confirm that your change has not been overwritten.
- Conditional Write, retry, transform, read, retry.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>Read, transform, conditionally write, retry as required</strong></span>
</details>

### Which of the following are scenarios where you might select Amazon Kinesis Data Firehose for data processing? (Select THREE.)

- You want to ingest a very high volume of data and store it to Amazon Redshift.
- You want to ingest a very high volume of data in a single stream that must be processed by three consumer applications.
- You want to ingest a very high volume of data, transform its format, and store it to an Amazon Aurora database.
- You must respond to individual messages as they are received.
- You want to ingest a very high volume of data, transform its format, and store it to Amazon S3.
- You want to simplify retry handling on streaming data, and the order of records in the stream is not critical.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>1, 4, and 5</strong></span>
</details>

</body>
</html>

### A developer is deploying a new application to Amazon Elastic Container Service (Amazon ECS). The developer needs to securely store and retrieve different types of variables. These variables include authentication information for a remote API, the URL for the API, and credentials. The authentication information and API URL must be available to all current and future deployed versions of the application across development, testing, and production environments. How should the developer retrieve the variables with the FEWEST application changes?

- A. Update the application to retrieve the variables from AWS Systems Manager Parameter Store. Use unique paths in Parameter Store for each variable in each environment. Store the credentials in AWS Secrets Manager in each environment.
- B. Update the application to retrieve the variables from AWS Key Management Service (AWS KMS). Store the API URL and credentials as unique keys for each environment.
- C. Update the application to retrieve the variables from an encrypted file that is stored with the application. Store the API URL and credentials in unique files for each environment.
- D. Update the application to retrieve the variables from each of the deployed environments. Define the authentication information and API URL in the ECS task definition as unique names during the deployment process.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>
</details>

<div>
<h3>A financial company must store original customer records for 10 years for legal reasons. A complete record contains personally identifiable information (PII). According to local regulations, PII is available to only certain people in the company and must not be shared with third parties. The company needs to make the records available to third-party organizations for statistical analysis without sharing the PII.
<br/> A developer wants to store the original immutable record in Amazon S3. Depending on who accesses the S3 document, the document should be returned as is or with all the PII removed. The developer has written an AWS Lambda function to remove the PII from the document. The function is named removePii.
<br/> What should the developer do so that the company can meet the PII requirements while maintaining only one copy of the document?</h3>

- A. Set up an S3 event notification that invokes the removePii function when an S3 GET request is made. Call Amazon S3 by using a GET request to access the object without PII.
- B. Set up an S3 event notification that invokes the removePii function when an S3 PUT request is made. Call Amazon S3 by using a PUT request to access the object without PII.
- C. Create an S3 Object Lambda access point from the S3 console. Select the removePii function. Use S3 Access Points to access the object without PII. Most Voted
- D. Create an S3 access point from the S3 console. Use the access point name to call the GetObjectLegalHold S3 API function. Pass in the removePii function name to access the object without PII.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>

</div>


### A developer has written an AWS Lambda function. The function is CPU-bound. The developer wants to ensure that the function returns responses quickly. How can the developer improve the function's performance?

- A. Increase the function's CPU core count.
- B. Increase the function's memory.
- C. Increase the function's reserved concurrency.
- D. Increase the function's timeout.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>
 <div>CPU power is allocated proportionally to the amount of memory in the function</div>
</details>


<div>
<h3>
<div>
A company has a multi-node Windows legacy application that runs on premises. The application uses a network shared folder as a centralized configuration repository to store configuration files in .xml format. The company is migrating the application to Amazon EC2 instances. As part of the migration to AWS, a developer must identify a solution that provides high availability for the repository.
<br/><br/>
Which solution will meet this requirement MOST cost-effectively?
</div>
</h3>

- A. Mount an Amazon Elastic Block Store (Amazon EBS) volume onto one of the EC2 instances. Deploy a file system on the EBS volume. Use the host operating system to share a folder. Update the application code to read and write configuration files from the shared folder.
- B. Deploy a micro EC2 instance with an instance store volume. Use the host operating system to share a folder. Update the application code to read and write configuration files from the shared folder.
- C. Create an Amazon S3 bucket to host the repository. Migrate the existing .xml files to the S3 bucket. Update the application code to use the AWS SDK to read and write configuration files from Amazon S3.
- D. Create an Amazon S3 bucket to host the repository. Migrate the existing .xml files to the S3 bucket. Mount the S3 bucket to the EC2 instances as a local volume. Update the application code to read and write configuration files from the disk.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>
</div>

<div>
<h3>
A developer is creating an application that will be deployed on IoT devices. The application will send data to a RESTful API that is deployed as an AWS Lambda function. The application will assign each API request a unique identifier. The volume of API requests from the application can randomly increase at any given time of day.
During periods of request throttling, the application might need to retry requests. The API must be able to handle duplicate requests without inconsistencies or data loss.
<br/><br/>
Which solution will meet these requirements?
</h3>

- A. Create an Amazon RDS for MySQL DB instance. Store the unique identifier for each request in a database table. Modify the Lambda function to check the table for the identifier before processing the request.
- B. Create an Amazon DynamoDB table. Store the unique identifier for each request in the table. Modify the Lambda function to check the table for the identifier before processing the request.
- C. Create an Amazon DynamoDB table. Store the unique identifier for each request in the table. Modify the Lambda function to return a client error response when the function receives a duplicate request.
- D. Create an Amazon ElastiCache for Memcached instance. Store the unique identifier for each request in the cache. Modify the Lambda function to check the cache for the identifier before processing the request.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>
</details>

</div>

<div>
<h3>
A developer wants to expand an application to run in multiple AWS Regions. The developer wants to copy Amazon Machine Images (AMIs) with the latest changes and create a new application stack in the destination Region. According to company requirements, all AMIs must be encrypted in all Regions. However, not all the AMIs that the company uses are encrypted.
<br/><br/>
How can the developer expand the application to run in the destination Region while meeting the encryption requirement?
</h3>

- A. Create new AMIs, and specify encryption parameters. Copy the encrypted AMIs to the destination Region. Delete the unencrypted AMIs. Most Voted
- B. Use AWS Key Management Service (AWS KMS) to enable encryption on the unencrypted AMIs. Copy the encrypted AMIs to the destination Region.
- C. Use AWS Certificate Manager (ACM) to enable encryption on the unencrypted AMIs. Copy the encrypted AMIs to the destination Region.
- D. Copy the unencrypted AMIs to the destination Region. Enable encryption by default in the destination Region.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>
</details>
</div>

<div>
<h3>
A company hosts a client-side web application for one of its subsidiaries on Amazon S3. The web application can be accessed through Amazon CloudFront from https://www.example.com. After a successful rollout, the company wants to host three more client-side web applications for its remaining subsidiaries on three separate S3 buckets.
<br/><br/>
To achieve this goal, a developer moves all the common JavaScript files and web fonts to a central S3 bucket that serves the web applications. However, during testing, the developer notices that the browser blocks the JavaScript files and web fonts.
<br/><br/>
What should the developer do to prevent the browser from blocking the JavaScript files and web fonts?
</h3>

- A. Create four access points that allow access to the central S3 bucket. Assign an access point to each web application bucket.
- B. Create a bucket policy that allows access to the central S3 bucket. Attach the bucket policy to the central S3 bucket
- C. Create a cross-origin resource sharing (CORS) configuration that allows access to the central S3 bucket. Add the CORS configuration to the central S3 bucket.
- D. Create a Content-MD5 header that provides a message integrity check for the central S3 bucket. Insert the Content-MD5 header for each web application request.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>
</div>

### A developer has an application that stores data in an Amazon S3 bucket. The application uses an HTTP API to store and retrieve objects. When the PutObject API operation adds objects to the S3 bucket the developer must encrypt these objects at rest by using server-side encryption with Amazon S3 managed keys (SSE-S3). Which solution will meet this requirement?

- A. Create an AWS Key Management Service (AWS KMS) key. Assign the KMS key to the S3 bucket.
- B. Set the x-amz-server-side-encryption header when invoking the PutObject API operation.
- C. Provide the encryption key in the HTTP header of every request.
- D. Apply TLS to encrypt the traffic to the S3 bucket.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>

```bash
PUT /myfile.xml HTTP/1.1
Host: mybucket.s3.amazonaws.com
x-amz-server-side-encryption: AES256
```
</details>
