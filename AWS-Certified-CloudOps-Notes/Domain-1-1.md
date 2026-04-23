# Task 1.1 - Implement metrics, alarms, and filters by using AWS monitoring and logging services [↑](Domain-1.md)

- **AWS Services Review**
  - [1. AWS Container Services](#aws-container-services-)
  - [2. Amazon SNS](#amazon-sns-)
  - [3. Amazon SNS Security and Access Control](#amazon-sns-security-and-access-control-)
  - [4. Amazon SNS Use Cases](#amazon-sns-use-cases-)
  - [5. Amazon SNS Cost Management](#amazon-sns-cost-management-)
  - [6. Amazon SNS Best Practices](#amazon-sns-best-practices-)
  - [7. Cost Optimization Services](#cost-optimization-services-)
  - [8. Summary](#summary-)
- **AWS Skills Review**
  - [1. Metric Identification](#metric-identification-)
  - [2. Logging, Monitoring, and Observability](#logging--monitoring-and-observability-)
  - [3. Log Management](#log-management-)

# AWS Services Review

## AWS Container Services [↑](#aws-services-review)
As a CloudOps engineer, your role is crucial in providing full observability into containerized workloads.

### `Amazon Managed Service for Prometheus`
- Amazon Managed Service for Prometheus offers a powerful solution for container monitoring.
- It eliminates the need to manage Prometheus infrastructure while providing comprehensive observability.
- Seamlessly scales with workload, helping to ensure reliable metric collection and querying across entire container environment.
- Use Cases:
    - Collect and store time-series data from container workloads
    - Monitor critical metrics including pod health, node performance, and cluster state.
    - Create and manage custom alerting rules to proactively respond to issues.

### `Amazon Managed Grafana`
- Transforms monitoring data into actionable insights through visualization capabilities.
- This service provides centralized platform for monitoring and analyzing container infrastructure, helping to identify trends, troubleshoot issues, and make data-driven decisions.
- Use Cases:
    - Visualize container performance metrics, including CPU, memory, disk, and network data in real time.
    - Build and customize dashboards tailored to different team needs and stakeholders.
    - Integrate data from multiple sources like Prometheus and CloudWatch for comprehensive operational views.

### `CloudWatch Container Insights`
- Automatically collect and aggregate metrics and logs from Amazon ECS, Amazon EKS, and AWS Fargate for real-time performance monitoring and troubleshooting.
- Automatically identifies critical operational concerns such as high resource usage, throttling events, and failed deployments, while providing detailed Amazon EKS control plane metrics.
- CloudOps engineers effectively maintain optimal health and performance of containerized workloads.
- Use Cases:
    - Monitoring container clusters with automated metric collection and log aggregation.
    - Track essential performance metrics including CPU, memory, disk, and network usage.
    - Set up proactive alerts for resource constraints and performance issues.

### Best Practices
To ensure optimal performance, security, and manageability of containerized environments, adopt the following:
* Implement automated monitoring and alert
* Use tags and labels for efficient resource tracking
* Regularly review and optimize container resource allocations
* Conduct periodic security audits of containerized applications
* Implement logging strategies for improved troubleshooting

## Amazon SNS [↑](#aws-services-review)
CloudOps engineers understand how to use of Amazon SNS to implement notification systems and help ensure reliable, secure, and scalable message delivery within your AWS environment.

### SNS topic and subscriptions
A notification structure is created through organized **topics** that cater to communication needs across systems.

Whether you are managing system alerts, user notifications, or deployment updates, each topic serves as a distinct communication channel.

These topics connect to multiple subscriber endpoints, offering flexible message delivery through various channels.

### Types of Subscribers
1. Email/Email-JSON
2. Mobile text messaging (SMS)
3. Mobile push notification
4. HTTP/HTTPS
5. AWS Lambda
6. Amazon SQS
7. Kinesis Data Firehouse

### Message Publishing
- Publishers interact with Amazon SNS by sending messages to _topics_, which serve as communication channels.
- The messages can range from simple text to complex structured data formats like JSON or XML.
- When a publisher sends a message to an SNS topic, the service immediately processes it for delivery to all subscribed endpoints.
- Amazon SNS excels at handling both text-based and structured messages
    - **Text messages** are perfect for simple notifications.
    - **Structured messages** allow for more complex data transmission, including platform-specific formats for mobile push notifications and HTML-formatted emails.
- **Message filtering** gives subscribers precise control over which messages they receive.
- Subscribers can create filter policies using JSON syntax to define acceptance rules based on message attributes. This filtering occurs at Amazon SNS level, reducing unnecessary message delivery and processing overhead.

### Message Delivery
- Amazon SNS has built-in retry logic for delivering messages.
- For failed messages, you can configure an SQS queue as a **dead-letter queue (DLQ)** to capture, analyze, and troubleshoot failed and undelivered messages.
- Use **CloudWatch metrics** to monitor the delivery status of messages. Setup **CloudWatch alarms** for error thresholds.
- When there is a need for a **low operational overhead and fully event-driven solution** to alert and send an email when a defined percentage of WorkSpaces quota have been reached. Do the following:
    1. Monitor the Healthy metric in CloudWatch, which shows the count of WorkSpaces used.
    2. Set a CloudWatch alarm to send a notification to SNS when the threshold is exceeded.
    3. Invoke a Lambda function, which calls the TerminateWorkSpaces API.

### Monitoring and Auditing
**Amazon SNS automatically integrates with CloudWatch** to provide metrics on the number of messages published, delivered, and failed. There are metrics that can be monitored such as:
- `NumberOfMessagesPublished`
- `NumberOfNotificationsPublished`
- `NumberOfNotificationsFailed`

Use `CloudTrail` to log and audit all Amazon SNS API calls. This provides an audit trail for governance and compliance purposes.

## Amazon SNS Security and Access Control [↑](#aws-services-review)
Amazon SNS integrates with AWS IAM to control who can publish messages, subscribe to topics, and configure Amazon SNS settings.

- **At rest:** Amazon SNS supports server-side encryption using AWS Key Management (AWS KMS) to encrypt the stored messages.
- **In Transit:** Messages are transmitted securely using HTTPS, helping ensure they are encrypted during transit.
- **Private Connectivity:** Use VPC endpoints for private connectivity between Amazon SNS and resources within VPC, providing an additional layer of security by keeping the traffic within the AWS network.

## Amazon SNS Use Cases [↑](#aws-services-review)
Use Amazon SNS notifications in many ways. For example, when an `AWS CodePipeline` deployment is complete, Amazon SNS sends a message to a Slack webhook to notify developers.

Other Use Cases:
- **Cross-Region messaging** to publish messages to topics in one Region and have them delivered to subscribers in another region.
- **Fan-out Architectures** where a single message sent to a topic is distributed to a multiple subscribers
- Sending SMS notifications or push notifications to mobile devices.
- Pushing notifications to mobile devices, integrating with push notification and third-party services.
- Built-in customizable retries.

## Amazon SNS Cost Management [↑](#aws-services-review)
- Pay-as-you-go pricing model where costs are determined by the number of published messages and notifications delivered to subscribers, with different rates applying **based on the delivery protocol** such as HTTP(S), email, or SMS.
- Strategies to optimize costs:
    - Implement message filtering to reduce unnecessary deliveries.
    - Batch messages when possible
    - Regularly audit SNS topics and subscriptions to remove unused endpoints.

Monitor Amazon SNS usage with `AWS Cost Explorer` and `CloudWatch metrics` to identify cost patterns and opportunities for optimization.

Setting up `AWS Budgets` can help track and alert on Amazon SNS spending thresholds.

## Amazon SNS Best Practices [↑](#aws-services-review)
To implement notification systems and help ensure reliable, secure, and scalable message delivery within your AWS environment, adopt the following best practices:

### Topic Design
Plan SNS topics wisely to make sure they are organized based on use cases. For example, have a separate topics for system alerts, user notifications, or application logs.

### Limit topic subscribers
Avoid overloading a topic with too many subscribers that don't need the notifications. Use message filtering to only send relevant messages to appropriate subscribers.

### Use DLQs
Set up DLQs for critical systems that need reliable message delivery. Use proper logging and monitoring to detect failures.

### Optimize SMS usage
If sending SMS messages, consider optimizing the content to avoid excessive costs, especially if application sends frequent or long messages.

## Cost Optimization Services [↑](#aws-services-review)
As a CloudOps engineer, cost optimization in AWS helps to ensure efficient resource use while minimizing unnecessary spending.

### CloudWatch Logs: Compliance Cost and Optimization
- Configure CloudWatch Logs to meet compliance requirements such as:
    - Health Insurance Portability and Accountability Act (HIPAA)
    - General Data Protection Regulation (GDPR)
    - Payment Card Industry Data Security Standard (PCI DSS)
    - SOC 2
- Add encryption, restricted access, and controlled deletion
- Optimize CloudWatch Logs storage over time.
- Configure log expiration policies and delete older logs automatically to reduce storage costs.

### Cloud Financial Management
The following are AWS cost management tools:
- `AWS Budget`
- `AWS Cost and Usage Report`
- `AWS Cost Explorer`
- `Savings Plans`
- `AWS Billing Conductor`
- `AWS Compute Optimizer`

## Summary [↑](#aws-services-review)

### Core Monitoring Services
- Amazon CloudWatch
- AWS CloudTrail
- AWS Config

### Operational tools and event management
- Amazon SNS
- Amazon EventBridge
- AWS Systems Manager

### Observability
- AWS X-Ray

### Visualization and Metrics
- Amazon Managed Grafana
- Amazon Managed Service for Prometheus


# AWS Skills Review

## Metric Identification [↑](#aws-services-review)
CloudOps engineers use metric filters, composite alarms, and automated responses to optimize system performance, enhance security, and reduce manual intervention.
This granular alerting improves observability.

### Common Metrics
- `Compute Metrics:` Include CPU utilization, CPUCreditBalance, DiskReadOps, DiskWriteOps, instance status checks, auto-scaling metrics, invocations, duration, and more.
- `Storage Metrics:` EBS VolumdIdleTime, EBS BurstBalance, BucketSizeBytes, NumberOfObjects, PercentIOLimit, read/write operations, EBS volume performance, and more.
- `Database Metrics:` Amazon RDS connections, CPU utilization, memory utilization, query latency, ReadLatency, WriteLatency, DatabaseConnections, CustomerReadCapacityUnits, ConsumedWriteCapacityUnits, CacheHitRate, and more.
- `Networking:` NetworkIn, NetworkOut, PacketsDropCount, RequestCount, ActiveFlowCount, 4XXErrorRate, 5XXErrorRate, TotalAcceleratedBytes, VPC flow logs, ELB request count, latency, error rates, and more.

## Logging , monitoring, and observability [↑](#aws-services-review)
- `Logging:` records data and events that occur within a system.
- `Monitoring:` collects and analyzes metrics, logs, and traces.
- `Observability:` adds the ability to monitor systems as a whole, providing complete visibility.

## Log Management [↑](#aws-services-review)
`CloudWatch Logs management` helps to meet compliance and regulatory requirements, optimize storage costs, and provide 
a comprehensive view of system's performance.

The following categories provide more information about log management

### CloudWatch Metrics
- `Default Metrics:` Auto enabled for most AWS services such as Amazon EC2, Amazon RDS, and AWS Lambda.
- `Custom Metrics:` Use CloudWatch agent or the PutMetricData API.

Install the CloudWatch agent on Amazon EC2/Linux:
```bash
sudo yum install amazon-cloudwatch-agent

sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

### CloudWatch Logs
- Configure collection with the following services:
  - **Amazon EC2:** Use the CloudWatch agent
  - **AWS Lambda:** It automatically sends logs to CloudWatch
  - Services that enable logging: **Amazon VPC**, **Amazon Rout 53**, **Amazon RDS**
- Organize logs in **log groups**
- Set retention policies
- Enable log streaming to Amazon S3, Amazon OpenSearch Service, and more.

### Metric Filters and Alarms
- Create filters to extract values from logs such as 500 errors:
``{$.status = 500}``
- Trigger alarms based on metric thresholds such as `CPUUtilization` greater than 80 percent.
- Use Amazon SNS to notify using email or SMS or invoke Lambda or Systems Manager for remediation.

### CloudWatch Dashboards
- Visualize key metrics and logs across services.
  - CPU plus memory from Amazon EC2
  - Databases connections from Amazon RDS
  - 4xx/5xx errors from Elastic Load Balancing

### AWS CloudTrail
- Enable AWS CloudTrail
  - CloudTrail logs all API activity on your AWS account.
  - It is automatically enabled for management events, such as creating, deleting, or modifying resources.
- Configuration:
  - Create a trail (organization-wide or per account)
  - Send logs to Amazon S3, optionally to CloudWatch Logs for near real-time analysis.
  - Enable data events for Amazon S3. Use Lambda if needed for deep auditing
- Use Cases:
  - Detecting unauthorized access
  - Tracking who changed security groups or deleted a resource
  - Integrating with CloudWatch alarms to alert on specific events such as the `DeleteTrail API` call

### Amazon Managed Services for Prometheus
- Configuration:
  - Create a workspace in Amazon Managed Service for Prometheus
  - Install Prometheus on your cluster (Amazon EKS or self-managed K8s)
  - Configure remote_write in Prometheus
    - `remote_write: -url: https://aps-workspaces.us-west-2.amazonaws.com/workspaces/ws-1234/api/v1/remote_write`
  - IAM Role for Service Account (IRSA) for secure push
  - Query metrics using Amazon Managed Grafana or APIs

### Integration and Automation
- **Automate:** Use `EventBridge` rules plus Lambda or Systems Manager to automatically remediate such as restart a failed EC2 instance.
- **Alert:** Amazon SNS and CloudWatch Alarms
- **Log Processing:** Use `CloudWatch Logs Insights` for querying logs.
- **Dashboards:** Use Amazon Managed Grafana and Amazon Managed Services for Prometheus and CloudWatch dashboards.

### IAM permissions for monitoring
Ensure proper IAM policies for services or agents:

```json
{
  "Action": [
    "logs:PutLogEvents",
    "logs:CreateLogStream",
    "cloudwatch:PutMetricData"
  ],
  "Resource": "*",
  "Effect": "Allow"
}
```

Also grant:
- ``cloudtrail:LookupEvents``
- ``aps:RemoteWrite for Prometheus``

### Best Practices
The following are best practices for log management
- Collect and store logs with CloudWatch and CloudTrail
- Monitor metrics and trends with CloudWatch and Amazon Managed Service for Prometheus
- Alert on thresholds with CloudWatch alarms and Amazon SNS
- Visualize health with CloudWatch dashboards and Amazon Managed Grafana
- Automate responses with EventBridge, Lambda, and Systems Manager
- Maintain compliance and audits with CloudTrail and Amazon S3.


## CloudWatch Agents [↑](#aws-services-review)
- Collects logs and system-level metrics from EC2 instances and on-premises servers. Centralizing this data in CloudWatch for monitoring and analysis.
- The agent can be configured to gather custom metrics, giving deeper insights into your applications and infrastructure.
- By using CloudWatch agent, it is possible to streamline log management process, set up automated alerts based on log patterns, and gain operational visibility across servers whether they are in cloud or on-premise.

### Installing and Configuring

#### Step 1: Amazon EC2 Instances
- Install the CloudWatch agent
  - Amazon Linux, RHEL, or CentOS: ``sudo yum install -y amazon-cloudwatch-agent``
  - For Ubuntu or Debian: ``sudo apt-get install -y amazon-cloudwatch-agent``
- Create the IAM role and attach it to the EC2 instance
- Create the agent configuration
- start the agent.

#### Step 2: Amazon ECS Clusters
- Option A: Using EC2 launch type
  - Install CloudWatch agent on Amazon ECS container instances (Same as EC2)
  - Make sure the Amazon ECS instance IAM role which includes CloudWatch permissions
- Option B: Using Fargate
  - Use **FireLens** (FluentBit) with sidecar configuration to push logs to CloudWatch logs.

#### Step 3: Amazon EKS Clusters
- Use CloudWatch agent as a **DaemonSet**
  - Use AWS provided DaemonSet manifest to collect the following:
    - CPU, memory disk, network usage
    - Container-level logs and metrics
- Use IAM Role for Service Account (IRSA)
  - Grant CloudWatch permissions using IAM and bind to Kubernetes service account
- Customize ConfigMap
  - Modify `cwagentconfig` ConfigMap to tweak collected metrics such as CPU, memory, disk, and logs.

## CloudWatch Alarms [↑](#aws-services-review)
- CloudOps engineers configure, identify, and troubleshoot CloudWatch alarms to automate responses to operational issues.
- CloudWatch alarms can invoke AWS services directly or indirectly through EventBridge for complex or custom actions.

#### Detect
To detect application failures, security threats, and system anomalies in real time, you can configure CloudWatch alarms
**based on filters in CloudWatch Log groups** to trigger alerts when specific log patterns or error messages appear.

#### Query
To query and analyze your data in real time, you can use `CloudWatch Log Insights` to analyze logs, detect issues, identify application
defects, security threats, anomalies, and more.

### CloudWatch Alarm Configurations
Alarms can be created on the following
- **CloudWatch metrics** such as CPUUtilization or DiskReadOps
- **Custom metrics** from CloudWatch agents
- **Logs** using Metric Filters

#### Composite Alarms
- Combine multiple alarms into one parent alarm.
- Add AND/OR logic between alarms
- Reduces alert noise by only triggering when multiple conditions are met.
  - Example: Only alert if ``CPU > 80% AND Memory > 75%``

```text
aws cloudwatch put-composite-alarm \
--alarm-name "AppHealthAlarm" \
--alarm-rule 'ALARM("High-CPU") AND ALARM("High-Memory")' \
--alarm-actions arn:aws:sns:us-east-1:123456789012:NotifyMe
```

#### Invoke Actions from CloudWatch Alarms
CloudWatch alarms can invoke the following:
- **SNS topics** such as email and SMS alerts, Lambda, Amazon SQS, and more
- **Amazon EC2 actions** such as Stop, Terminate, Reboot, and Recover
- **Auto-scaling policies**

#### EventBridge for Advanced Actions
- Use CloudWatch alarm to **send EventBridge rule**
- EventBridge matches te alarm state change and invokes the following:
  - Lambda
  - Step Functions
  - Systems Manager Automation
  - Any AWS service that supports EventBridge targets
- Then configure the rule to invoke a Lambda function, for example, that restarts an application or sends enriched alerts.

#### Alarm States
- `OK:` means everything is fine
- `ALARM:` Threshold breached
- `INSUFFICIENT_DATA:` No data or missing metrics

#### Troubleshooting Steps
1. **Check alarm history:** `aws cloudwatch describe-alarm-history --alarm-name "High-CPU"`
2. **Verify metrics are present**
   - Check if the underlying metric is publishing
   - Use get-metric-data or the CloudWatch metrics console.
3. **Check evaluation periods** if the threshold is not crossed for the full evaluation-periods, alarm won't trigger.
4. **Inspect Amazon SNS delivery**
   - Check CloudWatch Logs if a Lambda target failed
   - Look at **SNS Delivery logs** if messages aren't received.
5. **Use metric math** to troubleshoot complex thresholds such as average of EC2s
6. **Update threshold or actions** `aws cloudwatch put-metric-alarm --alarm-name "High-CPU" --threshold 85`


## CloudWatch Dashboards [↑](#aws-services-review)
CloudOps engineers use CloudWatch dashboards for observability, monitoring, centralized tracking, resource and cost management,
and proactive incident response.

### Create a Dashboard
1. Navigate to **CloudWatch > Dashboards**
2. Choose **Create Dashboard**
3. Enter a **name**, and then **add widgets**, such as line, number, text, stacked area, or bar charts.
4. Choose metrics from Amazon EC2, Amazon RDS, Application Load Balancer, Lambda and so on.
5. Add alarms to show their current state.

### Display Cross-account Cross-region Metrics
To enable CloudWatch cross-account and cross-region visibility in AWS Organizations, do the following:
1. Use AWS Organizations or Resource Access Manager (RAM) to share dashboards
2. Create IAM roles that allow viewing metrics from another account
3. Use CloudWatch cross-account data sharing.
  - Set up source accounts to share metrics
  - In the monitoring account, include linked accounts in the dashboard widget

#### Sample policy for shared role:
```json
{
  "Effect": "Allow",
  "Action": [
    "cloudwatch:GetMetricData",
    "cloudwatch:ListMetrics",
    "cloudwatch:GetDashboard"
  ],
  "Resource": "*"
}
```

### Use cross-region metrics
CloudWatch dashboards are global, but metrics are regional.

When adding a widget, specify the region. `"region": "us-west-2"`

You can combine metrics from multiple regions in the same dashboard by specifying them in each widget.

### Share dashboards
To share dashboards
- Share with IAM roles and users
- Use service control policies (SCPs) and CloudWatch console access
- Restrict or allow access using IAM policies

Use embedded dashboards in tools such as:
- Amazon Managed Grafana
- Internal tools using signed API links with IAM authentication
- CloudWatch dashboard URLs if users have IAM access

### Manage and Automate dashboards
Automate options:
- Infrastructure as a Code (IaC) such as `AWS CloudFormation`, `TerraForm`, or `AWS Cloud Development Kit (AWS CDK)` to define dashboards
- AWS CLI or SDKs to update dashboards dynamically
- Version dashboard configs in Git (track changes)

Monitor widget limits such as:
- Max 500 dashboards per account (default quota)
- Each dashboard: up to 100 widgets

Review pricing: Dashboards are charged per month per dashboard

### Best Practices
- Integrate and visualize CloudWatch metrics such as alarms, logs, and traces with color-coded alarms for quick issue identification
- Query logs and implement custom metrics for deeper insights
- Configure logging strategies with alerts to trigger notifications for critical events
- Use AWS tracing tools to analyze service dependencies and performance
- Add annotations and variables such as account, Region, and time-series data for dynamic and scalable monitoring

## Integration
CloudOps engineers must enable and configure comprehensive logging across critical AWS services to maintain operational visibility and security compliance.

By implementing logging for ELB, ECS, CloudFront, and WAF, engineers can track network traffic patterns, monitor container deployments,
analyze content delivery performance, and detect potential security threats in real time.

This helps ensure robust system health monitoring and rapid incident response capabilities

### Elastic Load Balancing Logging
Collect access logs through Elastic Load Balancer to identify key insights such as:
- Client IP
- Request timestamps
- Response codes
- Latencies
- Backend health

Use `Amazon Athena` or `CloudWatch Logs Insights` to analyze logs

### Amazon ECS Logging
Collect logs from Amazon ECS tasks and service to monitor and troubleshoot application logs, container status, and errors.

Use CloudWatch logs to centralize logs and optimize troubleshooting of issues

### CloudFront Logging
Collect logs for CloudFront distributions to identify key insights such as the following:
- Request URLS
- HTTP methods
- Response codes
- Caching details

These key insights help analyze CloudFront distribution performance, security, threats, bot traffic, and more

### AWS WAF Logging
Collect detailed logs of web requests filtered by AWS WAF rules to identify key insights such as the following:
- IP Addresses
- Request URIs
- Attack Patterns
- Blocked requestions

These key insights help identify DDoS attacks, SQL injections, and bot traffic.

### Best Practices
The goal is to collect the needed logs to monitor the following:
- Performance, requests, latency, errors, and bottlenecks
- Security and compliance to detect unauthorized access, attacks, and anomalies
- Cost and service usage based on log insights

## Scenario Questions

### Scenario - Centralized Logs
You are managing and monitoring a web application hosted on an EC2 instance. 
To meet compliance requirements for logging and storing all API calls to your AWS resources, you need to implement 
centralized logging for API calls using AWS services.

What is your solution?
[Solution](00_Scenario-Based-Questions.md#scenario---centralized-logs)

### Scenario - Monitoring and Logging
- [Solution](00_Scenario-Based-Questions.md#scenario---monitoring-and-logging-for-auto-scaled-elb-ec2-instance)


