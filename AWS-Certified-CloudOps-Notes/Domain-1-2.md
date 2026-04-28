# Task 1.2 - Identify and remediate issues by using monitoring availability metrics [↑](Domain-1.md)

- **AWS Services Review**
  - [AWS Monitoring and Remediation Services Overview](#aws-monitoring-and-remediation-services-overview-)
  - [EventBridge](#eventbridge-)
  - [Systems Manager](#systems-manager-)
- **AWS Skills Review**
  - [Analyzing](#analyzing-)
  - [Amazon X-Ray](#amazon-x-ray)
  - [Remediation](#remediation-)
  - [Event-Driven Workflows](#event-driven-workflows-)
  - [Notifications](#notifications)

# Review AWS Services

## AWS Monitoring and Remediation Services Overview [↑](#Review-aws-services)
AWS offers services such as **Lambda**, **User Notifications**, **CloudTrail**, **EventBridge**, **Amazon Route 53**,
**AWS X-Ray**, and **Systems Manager** to identify and remediate issues using monitoring and availability metrics to
maintain system performance, reliability and security.

### Monitoring performance metrics and system events
- **CloudWatch** can collect CPU, memory, network, and application logs and track CPU utilization, request latency, and error rates.
- **X-Ray** traces application requests, detects latency issues, and helps to identify slow database queries that impact user experience.

### Detect and respond to issues automatically
To add automation and remediation.
- **EventBridge** can be configured to monitor CloudWatch alarms that trigger Lambda for automated remediation such as instance restart, clear cache, or adjust configurations.
- **Systems Manager** can run remediation scripts when security issues occur.
- **Route 53 health checks** monitor the availability. Automatic DNS failover redirects traffic to a healthy backup instance if a failure is detected.

### Identify unauthorized access and security threats
- **CloudTrail** captures and logs all AWS API calls and detects unauthorized actions.
- **System Manager** revokes credential
- **User Notifications** and **Amazon SNS** send real-time notifications and alerts to teams
- **AWS WAF** and **Amazon Route 53** block IPs and redirect traffic.

## EventBridge [↑](#Review-aws-services)
Monitor and troubleshoot event-driven automation, and to route, enrich, and deliver events across AWS services to automate responses, monitor system health, and troubleshoot issues efficiently

### EventBridge Key Concepts

#### Event Bus
- Core component of EventBridge that receives and routes events from **AWS services**, **custom applications**, and **SaaS providers**.
- Example, an EC2 instance can be configured to send a status change event to an EventBridge event bus.

#### Event Bus Policies
- EventBridge bus policies ensure that make sure that events from different AWS accounts or organizations to be shared across event buses.
- Bus policies are useful from multi-account AWS Organizations

#### Event Rules
- Define how events are filtered and routed to specific targets such as Lambda, Amazon SNS, Amazon SQS, and AWS Step Functions.
- An event must match the rule's pattern to be processed (e.g. Create a rule to collect EC2 instance state changes).

#### Event Targets
- Event targets such as Lambda, Amazon SNS, Amazon SQS, Systems Manager, and Step Functions, are destinations for events after a rule matches.

#### EventBridge Pipes
- Connect event sources directly to targets with filtering and optional enrichment.
- Pipes can reduce the need for custom Lambda functions to process and route events.
- Pipes can also support event sources such as:
  - `Amazon SQS`
  - `Amazon DynamoDB streams`
  - `Amazon Kinesis`
  - `Amazon Managed Streaming for Apache Kafka (Amazon MSK)`

#### Schema Registry and Schema Discovery
- **Schema Registry:** stores schemas for event structures to help applications consume events
- **Schema Discovery:** automatically detects and catalogs event schemas

#### Monitoring and Troubleshooting EventBridge
- Use CloudWatch Logs and metrics to monitor event failures
- Use X-Ray for tracing event-driven workflows
- Use DLQs to capture failed event for analysis
- Use EventBridge API Calls logged in CloudTrail for auditing
- Use EventBridge to archive and replay events to resend them to the event bus that originally received them. This is commonly used in debugging and testing event-driven applications.

## Systems Manager [↑](#Review-aws-services)
System Manager service manage AWS infrastructure at scale for automation, monitoring, security, and troubleshooting.

### Key Concepts

#### SSM Agent and instance management
The SSM Agent must be installed and running on managed instances. It is supported on the following:
- Amazon EC2 instances
- On-premises servers
- Hybrid environment using **AWS Systems Manager Hybrid Activations**.
- Ensure you understand how to troubleshoot SSM Agent connectivity issues around AWS Identity and Access Management (IAM) roles, agent logs, VPC endpoints, and more.

#### Session Manager
- Provides secure shell access to EC2 instances without opening ports 22 or 3389.
- It logs all activity to CloudWatch and Amazon S3 for auditing.

#### Run Command
- Run shell commands across multiple instances and automate software updates, security fixes, and system diagnostics.
- Commands are logged in CloudTrail for auditing

#### Patch Manager
- Automates operating system patching for Amazon EC2 and on-premises Windows and Linux instances.
- You can configure **Patch baselines** to define which patches to install, and it supports patch compliance reporting in Systems Manager.

#### Parameter Store
- Stores secure string parameters secrets such as Passwords and API Keys.
- Supports AWS KMS encryption for enhanced security.

#### Inventory and Compliance
Collects software, operating systems, and configuration details across instances and helps asset management, compliance checks, and security audits.

#### Automation Documents
- Automation runs operational tasks such as stopping instances, patching, and backups.
- Uses documents that are JSON or YAML scripts that define automation actions such as AMI creation, Instance recovery, compliance enforcement.
- You can create **Runbooks** from **Systems Manager Automation Documents** to help automate operational tasks across AWS resources

#### OpsCenter
- For centralized incident management.
- Provides dashboard for operational issues (OpsItems) across AWS resources.
- Integrates with AWS Config, CloudTrail, and AWS Security Hub.

# Review AWS Skills

## Analyzing [↑](#Review-aws-services)
Analyze log data and respond to operational issues

The following categories provide more information about log monitoring, troubleshooting, and management

### `Amazon CloudWatch` Logs
Key AWS services that generate logs as follows:
- **Route 53 logs:** Provide details on DNS query requests, including query names, IP addresses, response times, and DNS errors.
- **Lambda logs:** Logs generated by AWS Lambda functions (invocation, execution duration, logs generated by the function, error messages)
- **CloudTrail logs:** Logs that capture API calls made in the AWS account (management console actions, AWS SDK calls)
- **Custom logs:** Logs generated by own application or infrastructure (web server logs, database logs, application logs)

### Using `CloudWatch Logs Insights`
- `CloudWatch Logs Insights` is an interactive query tool to explore and analyze log data and to help identify patterns, troubleshoot operational issues, and gain insights from the logs.
- CloudWatch Logs Insights syntax: **fields**, **filter**, **stats**, **sort**, **limit**, **regular expressions**.

#### 1. Filtering Log data
- Use queries to search through logs for specific keywords or patterns.
- For example: `fields @timestamp, @message | filter @message like /error/`

#### 2. Time-based queries
- Narrow down query to a specific time range.
- For example: `fields @timestamp, @message | filter @timestamp >= '2025-04-01' and @timestamp < '2025-04-02`

#### 3. Aggregation
- Aggregate the data, such as counting the occurrences or calculating average values.
- For example: `stats count() by @message`

#### 4. Sorting results
- Sort logs to focus on the most relevant data
- For example: `fields @timestamp, @message | sort @timestamp desc`

#### 5. Pattern matching
- Us regular expressions to search for complex patterns in log messages such as matching error codes.

#### 6. Join logs
- Join data from multiple log groups to correlate events and gain more insights

#### 7. Creating visualizations
- After running a query, use CloudWatch Logs Insights to **create graphs**, such as time series plots, to visualize trends and anomalies.

### Identify patterns and anomalous behavior

#### Error detection
Identify operational issues by looking for common error patterns in the logs, such as the following:
- **Lambda errors:** specific error patterns in Lambda function logs
- **CloudTrail API errors:** Look for failed API calls that could indicate permission issues or unexpected behavior in CloudTail logs
- **Route 53 DNS query failures:** Search for error codes like `SERVFAIL` or `NXDOMAIN` that indicate DNS issues.

#### Latencies and performance issues
- In **Lambda Logs**, measure the **execution time** to identify if functions are running longer than expected.
  - Use the CloudWatch **Duration** metric that is automatically tracked instead of trying to engineer this from the logs.
- **Route 53 logs** might show patterns of high DNS query response times or timeouts.
- **CloudTrail logs** might indicate spikes in API usage or sudden changes in the volume of requests.

#### Anomaly detection
- **Traffic Spikes:** unusual spike in requests in Lambda logs or CloudTrail logs might indicate a potential **DDoS attack** or **system overload**.
- **Increased Error rates:** A sudden rise in errors, such as a spike in HTTP 500 errors in custom logs or Lambda errors could suggest a service failures or misconfiguration.

#### Responding to Operational issues
Based on the findings on the logs, initiate appropriate remediation actions such as scaling, fixing misconfigurations, or optimizing the applications

- **Lambda timeout errors:**
  - Increasing the Lambda timeout limit
  - Optimizing the code to reduce execution time
  - Refactoring Lambda functions or optimizing the event-driven architecture to handle more requests.
- **Route 53 DNS failures**
  - This might be misconfiguration in DNS records issue
  - DNS servers are being unreachable because of network issues
- **CloudTrail API call errors**
  - Determine whether the issue is caused by permission problems (IAM roles, IAM policies, or incorrect API usage).
  - Review the error messages for clues on fixing permissions or correcting API requests.
- **Scaling issues**
  - Caused by increase in resource utilization such as CPU usage or out-of-memory errors.
  - Optimize resource-intensive operations.
- **Custom logs**
  - Review the specific areas of the code or infrastructure that could be causing the issues
  - Scale instances, optimize database queries, or adjust application logic to reduce bottlenecks.

#### Log Management best practices
- Centralized logging
- Log retention policies
- CloudWatch Log groups
- Automating alerts

## Amazon X-Ray
To learn more about identifying performance issues. See the concepts of Amazon X-Ray

How do you identify latency in a microservices-based web application if users are reporting slow response times.

#### 1. Trace the request
- Start by tracing a sample request that users have complained about.
- The **X-Ray Service Map** lets you see the entire flow, from the frontend service to the backend database.
- Ensure to do the following:
  - Install X-Ray SDK.
  - Enable X-Ray on AWS services
  - Use the service map to provide an overview of how different services interact and the performance of those interactions
  - Follow individual traces to see the full lifecycle of a request to understand which service or resource in introducing latency
  - Check the heatmap to visualize the latency of requests and highlight slow-performing requests, to identify problem areas.

#### 2. Analyze
- Slow API calls
- Inefficient database queries
- Lambda cold starts
- Service interdependencies

#### 3. Drill Down into segments
By analyzing the trace data segments with high latency or errors, you can drill down to identify the services or components that are causing issues:
- Long-running database queries
- Inefficient API calls
- Slow Lambda functions

#### 4.Remediate and Optimize
Use **X-Ray trace data** to guide code optimizations, resource scaling, or infrastructure changes to address performance issues.

#### 5. Monitor the performance
Integrate X-Ray with CloudWatch to correlate trace data with other metrics. Configure CloudWatch alarms based on X-Ray metrics.
This adds proactive alerts for when performance issues occur, helping to take remedial action before the problem escalates.

## Remediation [↑](#Review-aws-services)
How do you analyze and respond to a CloudWatch Logs Insights query that identifies Lambda functions are failing because of timeout errors?

#### 1. Query and pattern
Run a query to identify that the Lambda function is frequently timing out after a specific duration

```text
fields @timestamp, @message | filter @ message like /timeout/
```

#### 2. Root Cause
After examining the execution duration, you can find that the function is performing heavy computation without adequate resource allocation

#### 3. Remediation
Increase the Lambda function timeout setting and optimize the function to reduce execution time.
The memory allocation can also be increased to speed up processing.

#### 4. Test and Verify

## Event-Driven Workflows [↑](#Review-aws-services)
Use `EventBridge` to route, filter, transform, and deliver events between AWS services, SaaS applications, and own applications.

### Steps to route events
1. Create an EventBridge rule.
2. Choose the event bus (default bus or custom bus)
3. Define an event pattern, such as filter events from Amazon S3.
4. Choose a target, such as an SNS topic, Lambda function, Step function

### Enrich Events
- EventBridge can modify, enhance, and transform event data before sending it to a target.
- For example, use input transformers and transform an EC2 instance state change event into a custom message before forwarding the event to the target.

### Delivering Events
After an event is routed and enriched, EventBridge can deliver it to various AWS services, including the following:
- **Lambda** (trigger serverless functions)
- **Amazon SNS** and **Amazon SQS** (send notifications or queue messages)
- **Step Functions** (orchestrate workflows)
- **Systems Manager Automation** (perform system maintenance tasks)

If an EC2 instance stops unexpectedly (event), then the Lambda function (target) invokes the **StartInstances** API.

### Troubleshooting EventBridge issues
- Check the event rules and verify the rule's event pattern is correctly filtering events.
- Use the **Test Rule feature** in the EventBridge console.
- Confirm the target service has proper **IAM permissions to receive events**.
- Check event logs:
  - Use `CloudTrail` to track EventBridge actions
  - Use `CloudWatch Logs` to check for errors.
- Check failed events
  - Enable a DLQ for unprocessed events
  - Review event retry policies

### Cross-Region Event Routing
1. Set up and EventBridge rule in the source region
2. Navigate to the EventBridge console in the source region.
3. Create a rule
4. Create a name
5. Select the source event bus
6. Define a pattern
7. Select the target as an event bus in another region
8. Configure permissions in the target region
9. Verify cross-region event delivery.

## Notifications

### Scenario - Event-driven workflows and notifications
How can you send AWS event data to an external monitoring tool such as Datadog, Slack, or PagerDuty?

#### 1. Set up a Slack webhook

#### 2. Configure the EventBridge pipe
- Create the pipe
- Choose a source, CloudWatch events (EC2 instance changes).
- Set filter to send only stopped events
- Add enrichment
- Set the target as Slack Webhook (API destination)
- Configure authentication and use a bearer token or API key.

#### 3. Send a custom JSON payload to Slack
Use input transformers to format messages such as

```json
{
  "text": "EC2 Instance <instance-id> has changed to <state>"
}
```

#### 4. Deploy and Verify
Stop an EC2 instance to test then check and verify that Slack received the alert.


















