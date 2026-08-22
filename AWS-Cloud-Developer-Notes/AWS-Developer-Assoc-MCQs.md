##### Time-To-Live (TTL) can be used to have DynamoDB delete expired items from a table without being charged for WCU consumption. When you set an attribute for use by TTL, what is the value you should set for that attribute to result in expiry?

- The number of seconds since last update for the item to remain in the table.
- The epoch timestamp (with unit seconds) after which the item can be removed. 
- The number of days since last update for the item to remain in the table.
- A string pattern which needs to match the TTL expression for expiry.
- A Boolean specifying true or false for expiration.

<details>
    <summary>Reveal Answer</summary>
    <span><strong>The epoch timestamp (with unit seconds) after which the item can be removed</strong></span>
</details>

----

#### Optimistic concurrency control in DynamoDB provides a form of locking. Which is the correct description of the mechanism?

- Read, transform, conditionally write, retry as required.
- Strongly consistent write with lock option set true.
- Enable streams, check the stream to confirm no other updates are in progress, DeleteItem, PutItem.
- PutItem/UpdateItem, then strongly consistent GetItem to confirm that your change has not been overwritten.
- Conditional Write, retry, transform, read, retry.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>Read, transform, conditionally write, retry as required</strong></span>
</details>

----

#### Which of the following are scenarios where you might select Amazon Kinesis Data Firehose for data processing? (Select THREE.)

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

----


#### A developer is deploying a new application to Amazon Elastic Container Service (Amazon ECS). The developer needs to securely store and retrieve different types of variables. These variables include authentication information for a remote API, the URL for the API, and credentials. The authentication information and API URL must be available to all current and future deployed versions of the application across development, testing, and production environments. How should the developer retrieve the variables with the FEWEST application changes?

- A. Update the application to retrieve the variables from AWS Systems Manager Parameter Store. Use unique paths in Parameter Store for each variable in each environment. Store the credentials in AWS Secrets Manager in each environment.
- B. Update the application to retrieve the variables from AWS Key Management Service (AWS KMS). Store the API URL and credentials as unique keys for each environment.
- C. Update the application to retrieve the variables from an encrypted file that is stored with the application. Store the API URL and credentials in unique files for each environment.
- D. Update the application to retrieve the variables from each of the deployed environments. Define the authentication information and API URL in the ECS task definition as unique names during the deployment process.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>
</details>

----

<div>
<h4>A financial company must store original customer records for 10 years for legal reasons. A complete record contains personally identifiable information (PII). According to local regulations, PII is available to only certain people in the company and must not be shared with third parties. The company needs to make the records available to third-party organizations for statistical analysis without sharing the PII.
<br/> A developer wants to store the original immutable record in Amazon S3. Depending on who accesses the S3 document, the document should be returned as is or with all the PII removed. The developer has written an AWS Lambda function to remove the PII from the document. The function is named removePii.
<br/> What should the developer do so that the company can meet the PII requirements while maintaining only one copy of the document?</h4>

- A. Set up an S3 event notification that invokes the removePii function when an S3 GET request is made. Call Amazon S3 by using a GET request to access the object without PII.
- B. Set up an S3 event notification that invokes the removePii function when an S3 PUT request is made. Call Amazon S3 by using a PUT request to access the object without PII.
- C. Create an S3 Object Lambda access point from the S3 console. Select the removePii function. Use S3 Access Points to access the object without PII.
- D. Create an S3 access point from the S3 console. Use the access point name to call the GetObjectLegalHold S3 API function. Pass in the removePii function name to access the object without PII.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>

</div>

----


#### A developer has written an AWS Lambda function. The function is CPU-bound. The developer wants to ensure that the function returns responses quickly. How can the developer improve the function's performance?

- A. Increase the function's CPU core count.
- B. Increase the function's memory.
- C. Increase the function's reserved concurrency.
- D. Increase the function's timeout.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>
 <div>CPU power is allocated proportionally to the amount of memory in the function</div>
</details>

----


<div>
<h4>
<div>
A company has a multi-node Windows legacy application that runs on premises. The application uses a network shared folder as a centralized configuration repository to store configuration files in .xml format. The company is migrating the application to Amazon EC2 instances. As part of the migration to AWS, a developer must identify a solution that provides high availability for the repository.
<br/><br/>
Which solution will meet this requirement MOST cost-effectively?
</div>
</h4>

- A. Mount an Amazon Elastic Block Store (Amazon EBS) volume onto one of the EC2 instances. Deploy a file system on the EBS volume. Use the host operating system to share a folder. Update the application code to read and write configuration files from the shared folder.
- B. Deploy a micro EC2 instance with an instance store volume. Use the host operating system to share a folder. Update the application code to read and write configuration files from the shared folder.
- C. Create an Amazon S3 bucket to host the repository. Migrate the existing .xml files to the S3 bucket. Update the application code to use the AWS SDK to read and write configuration files from Amazon S3.
- D. Create an Amazon S3 bucket to host the repository. Migrate the existing .xml files to the S3 bucket. Mount the S3 bucket to the EC2 instances as a local volume. Update the application code to read and write configuration files from the disk.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>
</div>

----

<div>
<h4>
A developer is creating an application that will be deployed on IoT devices. The application will send data to a RESTful API that is deployed as an AWS Lambda function. The application will assign each API request a unique identifier. The volume of API requests from the application can randomly increase at any given time of day.
During periods of request throttling, the application might need to retry requests. The API must be able to handle duplicate requests without inconsistencies or data loss.
<br/><br/>
Which solution will meet these requirements?
</h4>

- A. Create an Amazon RDS for MySQL DB instance. Store the unique identifier for each request in a database table. Modify the Lambda function to check the table for the identifier before processing the request.
- B. Create an Amazon DynamoDB table. Store the unique identifier for each request in the table. Modify the Lambda function to check the table for the identifier before processing the request.
- C. Create an Amazon DynamoDB table. Store the unique identifier for each request in the table. Modify the Lambda function to return a client error response when the function receives a duplicate request.
- D. Create an Amazon ElastiCache for Memcached instance. Store the unique identifier for each request in the cache. Modify the Lambda function to check the cache for the identifier before processing the request.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>
</details>

</div>

----

<div>
<h4>
A developer wants to expand an application to run in multiple AWS Regions. The developer wants to copy Amazon Machine Images (AMIs) with the latest changes and create a new application stack in the destination Region. According to company requirements, all AMIs must be encrypted in all Regions. However, not all the AMIs that the company uses are encrypted.
<br/><br/>
How can the developer expand the application to run in the destination Region while meeting the encryption requirement?
</h4>

- A. Create new AMIs, and specify encryption parameters. Copy the encrypted AMIs to the destination Region. Delete the unencrypted AMIs.
- B. Use AWS Key Management Service (AWS KMS) to enable encryption on the unencrypted AMIs. Copy the encrypted AMIs to the destination Region.
- C. Use AWS Certificate Manager (ACM) to enable encryption on the unencrypted AMIs. Copy the encrypted AMIs to the destination Region.
- D. Copy the unencrypted AMIs to the destination Region. Enable encryption by default in the destination Region.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>
</details>
</div>

----

<div>
<h4>
A company hosts a client-side web application for one of its subsidiaries on Amazon S3. The web application can be accessed through Amazon CloudFront from https://www.example.com. After a successful rollout, the company wants to host three more client-side web applications for its remaining subsidiaries on three separate S3 buckets.
<br/><br/>
To achieve this goal, a developer moves all the common JavaScript files and web fonts to a central S3 bucket that serves the web applications. However, during testing, the developer notices that the browser blocks the JavaScript files and web fonts.
<br/><br/>
What should the developer do to prevent the browser from blocking the JavaScript files and web fonts?
</h4>

- A. Create four access points that allow access to the central S3 bucket. Assign an access point to each web application bucket.
- B. Create a bucket policy that allows access to the central S3 bucket. Attach the bucket policy to the central S3 bucket
- C. Create a cross-origin resource sharing (CORS) configuration that allows access to the central S3 bucket. Add the CORS configuration to the central S3 bucket.
- D. Create a Content-MD5 header that provides a message integrity check for the central S3 bucket. Insert the Content-MD5 header for each web application request.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>
</div>

----

#### A developer has an application that stores data in an Amazon S3 bucket. The application uses an HTTP API to store and retrieve objects. When the PutObject API operation adds objects to the S3 bucket the developer must encrypt these objects at rest by using server-side encryption with Amazon S3 managed keys (SSE-S3). Which solution will meet this requirement?

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

----

#### A developer is creating an application that includes an Amazon API Gateway REST API in the us-east-2 Region. 
#### The developer wants to use Amazon CloudFront and a custom domain name for the API. The developer has acquired an SSL/TLS certificate for the domain from a third-party provider.
#### How should the developer configure the custom domain for the application?

- A. Import the SSL/TLS certificate into AWS Certificate Manager (ACM) in the same Region as the API. Create a DNS A record for the custom domain.
- B. Import the SSL/TLS certificate into CloudFront. Create a DNS CNAME record for the custom domain.
- C. Import the SSL/TLS certificate into AWS Certificate Manager (ACM) in the same Region as the API. Create a DNS CNAME record for the custom domain.
- D. Import the SSL/TLS certificate into AWS Certificate Manager (ACM) in the us-east-1 Region. Create a DNS CNAME record for the custom domain.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>D</strong></span>

CloudFront is a global service, and CloudFront requires its ACM certificate to be provisioned/imported in `us-east-1 (N.Virginia)`

</details>

-----

#### A development team maintains a web application by using a single AWS CloudFormation template. The template defines web servers and an Amazon RDS database. 
#### The team uses the Cloud Formation template to deploy the Cloud Formation stack to different environments.
#### During a recent application deployment, a developer caused the primary development database to be dropped and recreated. The result of this incident was a loss of data. The team needs to avoid accidental database deletion in the future.
#### Which solutions will meet these requirements? (Choose two.)

- A. Add a CloudFormation Deletion Policy attribute with the Retain value to the database resource.
- B. Update the CloudFormation stack policy to prevent updates to the database.
- C. Modify the database to use a Multi-AZ deployment.
- D. Create a CloudFormation stack set for the web application and database deployments.
- E. Add a Cloud Formation DeletionPolicy attribute with the Retain value to the stack.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>A and B</strong></span>

</details>

-----
#### An application that is hosted on an Amazon EC2 instance needs access to files that are stored in an Amazon S3 bucket. The application lists the objects that are stored in the S3 bucket and displays a table to the user. During testing, a developer discovers that the application does not show any objects in the list.
#### What is the MOST secure way to resolve this issue?

- A. Update the IAM instance profile that is attached to the EC2 instance to include the S3:* permission for the S3 bucket.
- B. Update the IAM instance profile that is attached to the EC2 instance to include the S3:ListBucket permission for the S3 bucket.
- C. Update the developer's user permissions to include the S3:ListBucket permission for the S3 bucket.
- D. Update the S3 bucket policy by including the S3:ListBucket permission and by setting the Principal element to specify the account number of the EC2 instance.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>

</details>

-------

#### An application under development is required to store hundreds of video files. The data must be encrypted within the application prior to storage, with a unique key for each video file.
#### How should the developer code the application?

- A. Use the KMS Encrypt API to encrypt the data. Store the encrypted data key and data.
- B. Use a cryptography library to generate an encryption key for the application. Use the encryption key to encrypt the data. Store the encrypted data.
- C. Use the KMS GenerateDataKey API to get a data key. Encrypt the data with the data key. Store the encrypted data key and data.
- D. Upload the data to an S3 bucket using server side-encryption with an AWS KMS key.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>

Use the KMS `GenerateDataKey` API to get a data key. Encrypt the data with the data key. Store the encrypted data key and data.

</details>

--------
#### A company is planning to deploy an application on AWS behind an Elastic Load Balancer. The application uses an HTTP/HTTPS listener and must access the client IP addresses.
#### Which load-balancing solution meets these requirements?

- A. Use an Application Load Balancer and the X-Forwarded-For headers.
- B. Use a Network Load Balancer (NLB). Enable proxy protocol support on the NLB and the target application.
- C. Use an Application Load Balancer. Register the targets by the instance ID.
- D. Use a Network Load Balancer and the X-Forwarded-For headers.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

An Application Load Balancer (ALB) operates at **Layer 7 (HTTP/HTTPS)** and automatically adds the [X-Forwarded-For HTTP](../Quick-Links/X-Forwarded-For-Header.md) header.
</details>

-----
#### A developer wants to debug an application by searching and filtering log data. The application logs are stored in Amazon CloudWatch Logs. The developer creates a new metric filter to count exceptions in the application logs. However, no results are returned from the logs.
#### What is the reason that no filtered results are being returned?

- A. A setup of the Amazon CloudWatch interface VPC endpoint is required for filtering the CloudWatch Logs in the VPC.
- B. CloudWatch Logs only publishes metric data for events that happen after the filter is created.
- C. The log group for CloudWatch Logs should be first streamed to Amazon OpenSearch Service before metric filtering returns the results.
- D. Metric data points for logs groups can be filtered only after they are exported to an Amazon S3 bucket.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>B</strong></span>

</details>

------
#### A company hosts a batch processing application on AWS Elastic Beanstalk with instances that run the most recent version of Amazon Linux. The application sorts and processes large datasets.
#### In recent weeks, the application's performance has decreased significantly during a peak period for traffic. A developer suspects that the application issues are related to the memory usage. The developer checks the Elastic Beanstalk console and notices that memory usage is not being tracked.
#### How should the developer gather more information about the application performance issues?

- A. Configure the Amazon CloudWatch agent to push logs to Amazon CloudWatch Logs by using port 443.
- B. Configure the Elastic Beanstalk .ebextensions directory to track the memory usage of the instances.
- C. Configure the Amazon CloudWatch agent to track the memory usage of the instances.
- D. Configure an Amazon CloudWatch dashboard to track the memory usage of the instances.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>

The **Amazon CloudWatch agent** can collect additional system-level metrics from the EC2 instances running your Elastic Beanstalk application, such as:

- Memory utilization
- Disk utilization
- Swap utilization
- Processes
- Other OS-level metrics

</details>

------

#### A developer is implementing an AWS Cloud Development Kit (AWS CDK) serverless application. The developer will provision several AWS Lambda functions and Amazon API Gateway APIs during AWS CloudFormation stack creation. The developer's workstation has the AWS Serverless Application Model (AWS SAM) and the AWS CDK installed locally.
#### How can the developer test a specific Lambda function locally?

- A. Run the sam package and sam deploy commands. Create a Lambda test event from the AWS Management Console. Test the Lambda function.
- B. Run the cdk synth and cdk deploy commands. Create a Lambda test event from the AWS Management Console. Test the Lambda function.
- C. Run the cdk synth and sam local invoke commands with the function construct identifier and the path to the synthesized CloudFormation template.
- D. Run the cdk synth and sam local start-lambda commands with the function construct identifier and the path to the synthesized CloudFormation template.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>

</details>

-----

#### An e-commerce web application that shares session state on-premises is being migrated to AWS. The application must be fault tolerant, natively highly scalable, and any service interruption should not affect the user experience.
#### What is the best option to store the session state?

- A. Store the session state in Amazon ElastiCache.
- B. Store the session state in Amazon CloudFront.
- C. Store the session state in Amazon S3.
- D. Enable session stickiness using elastic load balancers.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

</details>

------

#### A developer has designed an application to store incoming data as JSON files in Amazon S3 objects. Custom business logic in an AWS Lambda function then transforms the objects, and the Lambda function loads the data into an Amazon DynamoDB table. Recently, the workload has experienced sudden and significant changes in traffic. The flow of data to the DynamoDB table is becoming throttled.
#### The developer needs to implement a solution to eliminate the throttling and load the data into the DynamoDB table more consistently.
#### Which solution will meet these requirements?

- A. Refactor the Lambda function into two functions. Configure one function to transform the data and one function to load the data into the DynamoDB table. Create an Amazon Simple Queue Service (Amazon SQS) queue in between the functions to hold the items as messages and to invoke the second function.
- B. Turn on auto scaling for the DynamoDB table. Use Amazon CloudWatch to monitor the table's read and write capacity metrics and to track consumed capacity.
- C. Create an alias for the Lambda function. Configure provisioned concurrency for the application to use.
- D. Refactor the Lambda function into two functions. Configure one function to store the data in the DynamoDB table. Configure the second function to process the data and update the items after the data is stored in DynamoDB. Create a DynamoDB stream to invoke the second function after the data is stored.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

The problem is that Lambda can process many incoming events concurrently, potentially sending a large burst of writes to DynamoDB.

DynamoDB can't necessarily absorb that burst at the same rate.

</details>


----

#### A software company is launching a multimedia application. The application will allow guest users to access sample content before the users decide if they want to create an account to gain full access. The company wants to implement an authentication process that can identify users who have already created an account. The company also needs to keep track of the number of guest users who eventually create an account.
#### Which combination of steps will meet these requirements? (Choose two.)

- A. Create an Amazon Cognito user pool. Configure the user pool to allow unauthenticated users. Exchange user tokens for temporary credentials that allow authenticated users to assume a role.
- B. Create an Amazon Cognito identity pool. Configure the identity pool to allow unauthenticated users. Exchange unique identity for temporary credentials that allow all users to assume a role.
- C. Create an Amazon CloudFront distribution. Configure the distribution to allow unauthenticated users. Exchange user tokens for temporary credentials that allow all users to assume a role.
- D. Create a role for authenticated users that allows access to all content. Create a role for unauthenticated users that allows access to only the sample content.
- E. Allow all users to access the sample content by default. Create a role for authenticated users that allows access to the other content.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>B and D</strong></span>

B - Cognito Identity Pools assign users a unique identity ID.
That allows the application to distinguish users, including guests.

D - More emphasis on Authenticated/Non-Authenticated roles

</details>

-----
#### A company is providing read access to objects in an Amazon S3 bucket for different customers. The company uses IAM permissions to restrict access to the S3 bucket. The customers can access only their own files.
#### Due to a regulation requirement, the company needs to enforce encryption in transit for interactions with Amazon S3.
#### Which solution will meet these requirements?

- A. Add a bucket policy to the S3 bucket to deny S3 actions when the aws:SecureTransport condition is equal to false.
- B. Add a bucket policy to the S3 bucket to deny S3 actions when the s3:x-amz-acl condition is equal to public-read.
- C. Add an IAM policy to the IAM users to enforce the usage of the AWS SDK.
- D. Add an IAM policy to the IAM users that allows S3 actions when the s3:x-amz-acl condition is equal to bucket-owner-read.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

</details>

----
#### A team is developing an application that is deployed on Amazon EC2 instances. During testing, the team receives an error. The EC2 instances are unable to access an Amazon S3 bucket.
#### Which steps should the team take to troubleshoot this issue? (Choose two.)

- A. Check whether the policy that is assigned to the IAM role that is attached to the EC2 instances grants access to Amazon S3.
- B. Check the S3 bucket policy to validate the access permissions for the S3 bucket.
- C. Check whether the policy that is assigned to the IAM user that is attached to the EC2 instances grants access to Amazon S3.
- D. Check the S3 Lifecycle policy to validate the permissions that are assigned to the S3 bucket.
- E. Check the security groups that are assigned to the EC2 instances. Make sure that a rule is not blocking the access to Amazon S3.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A and B</strong></span>

</details>

-----
#### A company is creating an application that processes .csv files from Amazon S3. A developer has created an S3 bucket. The developer has also created an AWS Lambda function to process the .csv files from the S3 bucket.
#### Which combination of steps will invoke the Lambda function when a .csv file is uploaded to Amazon S3? (Choose two.)

- A. Create an Amazon EventBridge rule. Configure the rule with a pattern to match the S3 object created event.
- B. Schedule an Amazon EventBridge rule to run a new Lambda function to scan the S3 bucket.
- C. Add a trigger to the existing Lambda function. Set the trigger type to EventBridge. Select the Amazon EventBridge rule.
- D. Create a new Lambda function to scan the S3 bucket for recently added S3 objects.
- E. Add S3 Lifecycle rules to invoke the existing Lambda function.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A and C</strong></span>

S3 Lifecycle rules are for things like transitioning objects to different storage classes or deleting objects. They do not invoke Lambda functions.

</details>

-----
#### A developer is writing an application for a company. The application will be deployed on Amazon EC2 and will use an Amazon RDS for Microsoft SQL Server database. The company's security team requires that database credentials are rotated at least weekly.
#### How should the developer configure the database credentials for this application?

- A. Create a database user. Store the user name and password in an AWS Systems Manager Parameter Store secure string parameter. Enable rotation of the AWS Key Management Service (AWS KMS) key that is used to encrypt the parameter.
- B. Enable IAM authentication for the database. Create a database user for use with IAM authentication. Enable password rotation.
- C. Create a database user. Store the user name and password in an AWS Secrets Manager secret that has daily rotation enabled.
- D. Use the EC2 user data to create a database user. Provide the user name and password in environment variables to the application.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>C</strong></span>
</details>

----
#### A developer is developing an application that uses signed requests (Signature Version 4) to call other AWS services. The developer has created a canonical request, has created the string to sign, and has calculated signing information.
#### Which methods could the developer use to complete a signed request? (Choose two.)

- A. Add the signature to an HTTP header that is named Authorization.
- B. Add the signature to a session cookie.
- C. Add the signature to an HTTP header that is named Authentication.
- D. Add the signature to a query string parameter that is named X-Amz-Signature.
- E. Add the signature to an HTTP header that is named WWW-Authenticate.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A and D</strong></span>

</details>

-----

#### A developer is integrating Amazon ElastiCache in an application. The cache will store data from a database. The cached data must populate real-time dashboards.
#### Which caching strategy will meet these requirements?

- A. A read-through cache
- B. A write-behind cache
- C. A lazy-loading cache
- D. A write-through cache


<details>
    <summary>Reveal Answer</summary>
 <span><strong>D</strong></span>

| Strategy              | How it works                                                    | Why not?                                                                   |
|-----------------------| --------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **A. Read-through**   | Application requests data → cache fetches from DB if missing    | Primarily optimized for **reads/cache population on demand**               |
| **B. Write-behind**   | Application writes to cache → cache asynchronously writes to DB | Database update is **delayed**, which isn't ideal when consistency matters |
| **C. Lazy-loading**   | Data is loaded into cache only when requested                   | Data may be **stale or absent** until someone requests it                  |
| **D. Write-through**  | Data is written to cache **and database synchronously**         | Keeps cache populated with the latest data                                 |

</details>

------
#### A company has a front-end application that runs on four Amazon EC2 instances behind an Elastic Load Balancer (ELB) in a production environment that is provisioned by AWS Elastic Beanstalk. A developer needs to deploy and test new application code while updating the Elastic Beanstalk platform from the current version to a newer version of Node.js. The solution must result in zero downtime for the application.
#### Which solution meets these requirements?

- A. Clone the production environment to a different platform version. Deploy the new application code, and test it. Swap the environment URLs upon verification.
- B. Deploy the new application code in an all-at-once deployment to the existing EC2 instances. Test the code. Redeploy the previous code if verification fails.
- C. Perform an immutable update to deploy the new application code to new EC2 instances. Serve traffic to the new instances after they pass health checks.
- D. Use a rolling deployment for the new application code. Apply the code to a subset of EC2 instances until the tests pass. Redeploy the previous code if the tests fail.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

</details>

------
#### A developer is creating an AWS Lambda function. The Lambda function will consume messages from an Amazon Simple Queue Service (Amazon SQS) queue. The developer wants to integrate unit testing as part of the function's continuous integration and continuous delivery (CI/CD) process.
#### How can the developer unit test the function?

- A. Create an AWS CloudFormation template that creates an SQS queue and deploys the Lambda function. Create a stack from the template during the CI/CD process. Invoke the deployed function. Verify the output.
- B. Create an SQS event for tests. Use a test that consumes messages from the SQS queue during the function's Cl/CD process.
- C. Create an SQS queue for tests. Use this SQS queue in the application's unit test. Run the unit tests during the CI/CD process.
- D. Use the aws lambda invoke command with a test event during the CIICD process.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

Unit testing should test the Lambda function's logic without requiring real AWS resources such as an SQS queue.

</details>

----
#### A developer is working on a web application that uses Amazon DynamoDB as its data store. The application has two DynamoDB tables: one table that is named artists and one table that is named songs. The artists table has artistName as the partition key. The songs table has songName as the partition key and artistName as the sort key.
#### The table usage patterns include the retrieval of multiple songs and artists in a single database operation from the webpage. The developer needs a way to retrieve this information with minimal network traffic and optimal application performance.
#### Which solution will meet these requirements?

- A. Perform a BatchGetltem operation that returns items from the two tables. Use the list of songName/artistName keys for the songs table and the list of artistName key for the artists table.
- B. Create a local secondary index (LSI) on the songs table that uses artistName as the partition key. Perform a query operation for each artistName on the songs table that filters by the list of songName. Perform a query operation for each artistName on the artists table.
- C. Perform a BatchGetitem operation on the songs table that uses the songName/artistName keys. Perform a BatchGetltem operation on the artists table that uses artistName as the key.
- D. Perform a Scan operation on each table that filters by the list of songName/artistName for the songs table and the list of artistName in the artists table.


<details>
    <summary>Reveal Answer</summary>
 <span><strong>A</strong></span>

DynamoDB's `BatchGetItem` is designed exactly for this.

A single `BatchGetItem` request can retrieve items from multiple DynamoDB tables.

```text
Application → GetItem → artists
Application → GetItem → artists
Application → GetItem → songs
Application → GetItem → songs
Application → GetItem → songs
```

One BatchGetItem request containing keys from both tables.

</details>