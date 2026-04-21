# Domain 1 - Monitoring, Logging, Analysis, Remediation, and Performance Optimization [↑](../README.md)

#### Overview
- As a CloudOps engineer, maintaining the health, security, and efficiency of applications and infrastructure is important.
- Monitoring, logging, analysis, remediation, and performance optimization form the foundation of effective cloud operations, ensuring reliability, scalability, and cost efficiency.

#### Services in-scope
1. `Amazon CloudWatch` [>](../AWS-Practitioner-Essentials/9_Monitoring-and-Analytics.md#amazon-cloudwatch-)
2. `AWS CloudTrail` [>](../AWS-Practitioner-Essentials/9_Monitoring-and-Analytics.md#aws-cloudtrail-)
3. `AWS Config` [>](../AWS-Practitioner-Essentials/9_Monitoring-and-Analytics.md#aws-config-)
4. `AWS X-Ray` [>](../AWS-Practitioner-Essentials/12_Well-Architected-Solutions.md#3-aws-x-ray)
5. `Amazon EventBridge` [>](../AWS-Practitioner-Essentials/2_Compute-in-Cloud.md#amazon-eventbridge)
6. `AWS Security Hub` [>](../AWS-Practitioner-Essentials/8_Security.md#additional-security-services-)
7. `AWS Systems Manager` [>](../AWS-Practitioner-Essentials/8_Security.md#3-aws-systems-manager)
8. `AWS Managed Grafana` [>](https://docs.aws.amazon.com/prescriptive-guidance/latest/implementing-logging-monitoring-cloudwatch/amg-dashboarding-visualization.html)
9. `Amazon Managed Services for Prometheus` [>](https://docs.aws.amazon.com/prometheus/latest/userguide/what-is-Amazon-Managed-Service-Prometheus.html)
10. `Amazon SNS` [>](../AWS-Practitioner-Essentials/2_Compute-in-Cloud.md#amazon-simple-notification-service-amazon-sns) 

## Task 1.1 - Implement metrics, alarms, and filters by using AWS monitoring and logging services

### AWS Container Services
As a CloudOps engineer, your role is crucial in providing full observability into containerized workloads.

#### `Amazon Managed Service for Prometheus`
- Amazon Managed Service for Prometheus offers a powerful solution for container monitoring.
- It eliminates the need to manage Prometheus infrastructure while providing comprehensive observability.
- Seamlessly scales with workload, helping to ensure reliable metric collection and querying across entire container environment.
- Use Cases:
  - Collect and store time-series data from container workloads
  - Monitor critical metrics including pod health, node performance, and cluster state.
  - Create and manage custom alerting rules to proactively respond to issues.

#### `Amazon Managed Grafana`
- Transforms monitoring data into actionable insights through visualization capabilities.
- This service provides centralized platform for monitoring and analyzing container infrastructure, helping to identify trends, troubleshoot issues, and make data-driven decisions.
- Use Cases:
  - Visualize container performance metrics, including CPU, memory, disk, and network data in real time.
  - Build and customize dashboards tailored to different team needs and stakeholders.
  - Integrate data from multiple sources like Prometheus and CloudWatch for comprehensive operational views.

#### `CloudWatch Container Insights`
- Automatically collect and aggregate metrics and logs from Amazon ECS, Amazon EKS, and AWS Fargate for real-time performance monitoring and troubleshooting.
- Automatically identifies critical operational concerns such as high resource usage, throttling events, and failed deployments, while providing detailed Amazon EKS control plane metrics.
- CloudOps engineers effectively maintain optimal health and performance of containerized workloads.
- Use Cases:
  - Monitoring container clusters with automated metric collection and log aggregation.
  - Track essential performance metrics including CPU, memory, disk, and network usage.
  - Set up proactive alerts for resource constraints and performance issues.

#### Best Practices
To ensure optimal performance, security, and manageability of containerized environments, adopt the following:
* Implement automated monitoring and alert
* Use tags and labels for efficient resource tracking
* Regularly review and optimize container resource allocations
* Conduct periodic security audits of containerized applications
* Implement logging strategies for improved troubleshooting

### Amazon SNS
CloudOps engineers understand how to use of Amazon SNS to implement notification systems and help ensure reliable, secure, and scalable message delivery within your AWS environment.

#### SNS topic and subscriptions
A notification structure is created through organized **topics** that cater to communication needs across systems.

Whether you are managing system alerts, user notifications, or deployment updates, each topic serves as a distinct communication channel.

These topics connect to multiple subscriber endpoints, offering flexible message delivery through various channels.

#### Types of Subscribers
1. Email/Email-JSON
2. Mobile text messaging (SMS)
3. Mobile push notification
4. HTTP/HTTPS
5. AWS Lambda
6. Amazon SQS
7. Kinesis Data Firehouse

#### Message Publishing
