# Task 1.2 - Identify and remediate issues by using monitoring availability metrics [↑](Domain-1.md)

- **AWS Services Review**
  - [AWS Monitoring and Remediation Services Overview](#aws-monitoring-and-remediation-services-overview-)
- **AWS Skills Review**

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

















