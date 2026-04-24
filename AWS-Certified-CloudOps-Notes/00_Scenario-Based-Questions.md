# Scenario Based Questions

## Scenario - Centralized Logs
You are managing and monitoring a web application hosted on an EC2 instance. 
To meet compliance requirements for logging and storing all API calls to your AWS resources, 
you need to implement centralized logging for API calls using AWS services.

What is your solution?

### 1. Enable CloudTrail
When CloudTrail is enabled, all API calls made to AWS services are recorded from the AWS Management Console and the AWS SDKs.

### 2. Enable CloudWatch Logs integration
Enable CloudWatch Logs integration with CloudTrail

- **Create a log group in CloudWatch Logs:** The `create-log-group` command creates a log group in CloudWatch Logs to store logs.
- **Create a trail in CloudTrail:** The `create-trail` command creates a trail in CloudTrail, specifying an S3 bucket for storing logs.
- **Integrate CloudTrail with CloudWatch Logs:** Specify the log group ARN and a role with the necessary permissions for CloudTrail to publish logs to CloudWatch Logs.
- **Start logging:** The `start-logging` command begins logging API events.

Ensure that the IAM role associated with CloudTrail has the correct permissions to publish logs to CloudWatch Logs.

The IAM role must have the following permissions:
- `logs:PutLogEvents`
- `logs:CreateLogStream`
- `logs:DescribeLogStreams`

### 3. Enable DynamoDB Streams
To track changes happening in Amazon DynamoDB tables, enable **DynamoDB Streams** which captures detailed logs of each
item that is inserted, updated, or deleted from a DynamoDB table.

Configure a stream to capture data and send it to a Lambda function, or store the stream data in Amazon Kinesis or CloudWatch Logs for further analysis.

### 4. Enable Amazon S3 access logging
For compliance, enable access logging on S3 buckets by configuring an S3 bucket where logs will be stored.

### 5. Setup IAM roles and policies for logging
Ensure that EC2 instance and other resources such as DynamoDB have the necessary IAM roles and permissions to interact with CloudTrail, CloudWatch, and Amazon D3 for logging

### 6. Ensure Compliance with AWS Config
Track changes to resources and enable AWS Config to continuously record configuration changes to track compliance over time.

## Scenario - Monitoring and Logging for Auto-Scaled ELB EC2 Instance
If you have an application running on EC2 instances with an Auto Scaling group behind a load balancer, 
how can you configure monitoring and logging for this design?

### 1. Enable Amazon CloudWatch for metrics and alerts
Enable detailed monitoring and track CloudWatch metrics:
- `CPUUtilization`
- `NetworkIn` and `NetworkOut`
- `DiskReadOps` and `DiskWriteOps`
- `StatusCheckFailed`

Then, configure CloudWatch alarms to trigger alerts using Amazon SNS when thresholds are exceeded
Subscribe the CloudOps team to CloudWatch alarms using SNS topics for instant notifications

### 2. Enable logging for troubleshooting and compliance
Configure CloudWatch Logs agent to collect EC2 instance logs, including application and system logs.
- /var/log/messages
- /var/log/httpd/access.log
- /var/log/httpd/error.log

### 3. Auto Scaling Group Monitoring
Enable Scaling group metrics and track auto-scaling such as:
- `GroupDesiredCapacity`
- `GroupInServiceInstances`
- `GroupPendingInstances`
- `GroupTerminatingInstances`

Configure alarms for scale up and scale down actions based on the CPU, memory, or requests per instance.

You can also monitor Auto Scaling group lifecycle events in CloudTrail to track instance launches, terminations, and scaling activities. 
This adds additional logs to troubleshoot unexpected scale down events.

### 4. Elastic Load Balancer Monitoring
Enable ELB CloudWatch metrics such as:
- RequestCount
- HTTPCode_ELB_4XX_Count
- HTTPCode_ELB_5XX_Count
- TargetResponseTime
- UnHealthyHostCount

Then you can configure CloudWatch alarms with notifications if the following conditions occur:
- Response time is too high (latency spikes)
- There are too many 4XX/5XX errors (indicating application issues)
- Instances become unhealthy

### 5. VPC Logs for security analysis
Add detection for suspicious traffic patterns or denied connections by enabling network traffic logging to and from instances.

### 6. Automate log and metric analysis
Use CloudWatch Logs Insights to query logs, analyze error patterns, and identify application issues.

Configure Lambda for automated actions such as 
- auto-restart unhealthy instances detected by CloudWatch
- moving old logs to Amazon S3 Glacier for cost savings

## Scenario - Incorrect Alarm Threshold
As a CloudOps engineer, you must troubleshoot a false-positive alert from a CloudWatch alarm monitoring Amazon EC2 CPU utilization.

The alarm threshold is manually set at 80 percent, but because of the workload fluctuations, it frequently triggers even when the system is healthy.

### Implement CloudWatch Anomaly detection
- Use CloudWatch anomaly detection and create dynamic thresholds based on machine learning models that analyze past data.
  1. Navigate to **CloudWatch metrics**.
  2. Select **EC2 CPU Utilization**
  3. Select **Anomaly detection** to enable for the metric to adjust the sensitivity
  4. Update the alarm to trigger when utilization is outside the anomaly band

Once CloudWatch anomaly detection is enabled, the alarm triggers only if CPU usage is abnormal compared to historical trends.

## Scenario - Troubleshooting Performance
A CloudOps engineer begins a troubleshooting process to investigate a performance issue where an application running on
EC2 instances within an Auto Scaling group is experiencing intermittent slow response times.

### Hypothesize root causes
- **EC2 CPU Utilization (%)** - High CPU usage might indicate overloaded instances
- **Application LB Target Response Time** - A high response time suggests latency at the backend
- **Auto Scaling Group Desired Capacity compared to Actual Capacity** - If instances are not scaling, it might be an issue with the auto-scaling policies

### Validate Data collection from services
- **EC2 Instances:** Ensure the CloudWatch agent is running
- **Auto Scaling Groups:** Confirm group metrics collection is enabled
- **ELB Access Logs:** Ensure ELB is publishing metrics to CloudWatch
- **VPC Flow Logs:** Verify logs are being collected in the CloudWatch log group
