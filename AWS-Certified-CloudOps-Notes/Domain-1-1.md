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
- `Compute Metrics:` Include CPU utilization, CPUCreditBalance, DiskReadOps, DiskWriteOps, instance status checks, auto scaling metrics, invocations, duration, and more.
- `Storage Metrics:` EBS VolumdIdleTime, EBS BurstBalance, BucketSizeBytes, NumberOfObjects, PercentIOLimit, read/write operations, EBS volume performance, and more.
- `Database Metrics:` Amazon RDS connections, CPU utilization, memory utilization, query latency, ReadLatency, WriteLatency, DatabaseConnections, CustomerReadCapacityUnits, ConsumedWriteCapacityUnits, CacheHitRate, and more.
- `Networking:` NetworkIn, NetworkOut, PacketsDropCount, RequestCount, ActiveFlowCount, 4XXErrorRate, 5XXErrorRate, TotalAcceleratedBytes, VPC flow logs, ELB request count, latency, error rates, and more.

## Logging , monitoring, and observability [↑](#aws-services-review)
- `Logging:` records data and events that occur within a system.
- `Monitoring:` collects and analyzes metrics, logs, and traces.
- `Observability:` adds the ability to monitor systems as a whole, providing complete visibility.

## Log Management [↑](#aws-services-review)
`CloudWatch Logs management` helps to meet compliance and regulatory requirements, optimize storage costs, and provide a comprehensive view of system's performance.
