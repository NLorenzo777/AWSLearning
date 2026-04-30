# Task 1.3 - Implement performance optimization strategies for compute, storage, and database resource [↑](Domain-1.md)

# Review AWS Services
AWS Service features for optimization strategies
- `CloudWatch`
- `AWS Compute Optimizer`
- `Amazon EBS`
- `DataSync`
- `S3 Transfer Acceleration`
- `Lifecycle policies`
- `Amazon EFS`
- `Amazon FSx`
- `Amazon RDS`
- `placement groups`

Performance optimization reduces incidents, adds proactive monitoring, and directly impacts costs, performance, and user experience.

## Compute Optimization [↑](#Review-aws-services)

### AWS Compute Optimizer
- Get recommendations for the following
  - Rightsizing instances
  - Auto-scaling to scale resources dynamically based on demand
- Use for cost-aware storage recommendations
- Common Patterns:
  - **Underutilization**: Less than 20% CPU
  - **Overutilization**: More than 80% CPU
  - Memory pressure
  - Network bottlenecks

### AWS Systems Manager
- Run automation runbooks to remediate compute issues
- Perform Amazon EC2 patching, restarts, or log collection

### AWS Trusted Advisor
Use `Trusted Advisor` to receive performance and cost optimizations, such as identifying underutilized EC2 instances.

### AWS X-Ray
Use `X-Ray` to trace application performance bottlenecks and visualize latency across microservices or AWS Lambda functions

### Amazon EC2 instances
- **Burstable** for cost-effective intermittent load.
- **Graviton-based** for lower cost and better performance of compute-intensive workloads
- **Spot instance** for non-critical workloads.

### Basic and Detailed Monitoring
| Feature                 | Basic Monitoring      | Detailed Monitoring            |
|-------------------------|-----------------------|--------------------------------|
| Granularity             | 5-minutes intervals   | 1-minute intervals             |
| Cost                    | Free                  | Additional charges             |
| CloudWatch alarms       | Limited sensitivity   | More responsive alarms         |
| Dashboards and insights | Less precise data     | Better for trends and spikes   |
| Use cases               | General health checks | Real-time alerting and scaling |

## Container Optimization [↑](#Review-aws-services) 
- `Amazon Fargate` automate resource allocation and scaling for Amazon ECS.
- **Cluster Autoscaler**, **Karpenter**, or **Fargate for Kubernetes** workloads optimize Amazon EKS.

## Compute Storage [↑](#Review-aws-services)
Optimize storage performance, cost efficiency, and system reliability for EC2 instances and associated resources.

### Amazon EBS
Different types of EBS volumes are suited for various kinds of workloads.

#### EBS volume type collection
- Different workloads have different storage requirements. One might require higher throughput, where another requires low latency.
- Selecting the right EBS helps ensure optimal performance and costs
- `Amazon Cloudwatch` can proactively adjust volume types based on actual usage patterns
- Performance characteristics include:
  - **gp3:** 3,000 baseline IOPS
  - **io2:** High-performance, mission-critical
  - **st1:** Throughput-intensive workloads
  - **sc1:** Cold storage, infrequent access

#### Key performance metrics
Help determine whether the chosen EBS volume meets the workload's needs or requires a different volume type
- **IOPS**
- **queue depth**
- **latency**
- **throughput**

#### Cost Optimization - Storage analysis
- Storage-related performance issues can severely impact application performance and availability
- Use `Compute Optimizer` for cost-aware storage recommendations
- Enable **elastic volumes** for dynamic storage scaling without downtime.
- **Systematic Troubleshooting**
  - Analyzing CloudWatch metrics
  - Checking burst balance for bustable volumes
  - Adjusting IOPS provisioning
  - Evaluating EC2 instance limitations

#### Workload-specific Configurations - Database workloads
For database workloads, use the following requirements to determine the volume type
- I/O intensity requirements
- Storage capacity needs
- Performance requirements
- Backup strategies
- Recovery objectives
- Cost constraints
- Growth planning 
- Availability needs

Example:
- Transactional databases benefit from **provisioned IOPS volumes**
- Data warehouses use **throughput-optimized volumes**
- Dev environments uses **general-purpose volumes**
- Archive databases use cold storage volumes

#### Regular Maintenance
Maintain EBS volumes for performance optimization, compliance, data protection, security, cost optimization, lifecycle management, disaster recovery, alerts, and health monitoring

```jupyter
def storage_maintenance():
 tasks = {
     'snapshot_volumes': create_snapshots(),
     'analyze_performance': check_performance_metrics(),
     'optimize_costs': review_volume_types(),
     'check_utilization': monitor_usage()
 }
 return generate_report(tasks)
```

#### Volume Type Modification
Use Multi-attach for EBS volumes for multi-instance access to improve redundancy and workload distribution

Modify volume types and IOPS
```bash
aws ec2 modify-volume \
--volume-id vol-1234567890abcdef0 \
--volume-type io2 \
--iops 10000
```

Enable Multi-Attach for supported volumes
```bash
aws ec2 modify-volume \
--volume-id vol-1234567890abcdef0 \
--multi-attach-enabled
```

#### Cost Optimization

```python
def analyze_volume_costs():
 ec2 = boto3.client('ec2')
 volumes = ec2.describe_volumes()
 for volume in volumes['Volumes']:
     # Calculate monthly cost
     cost = calculate_volume_cost(
         volume['Size'],
         volume['VolumeType'],
         volume.get('Iops', 0)
     )

     # Generate optimization recommendations
     recommendations = get_cost_recommendations(
         volume,
         cost
     )
```

#### Performance Testing
```python
def test_volume_performance():
 # Run flexible io benchmark
 benchmark_command = [
   'fio',
   '--name=benchmark',
   '--filename=/dev/xvdf',
   '--rw=randrw',
   '--bs=4k',
   '--iodepth=64',
   '--runtime=300'
 ]
 return subprocess.run(opens in a new tab)(benchmark_command)
```

#### Best Practices
Keep the following key considerations in mind

| Performance         | Cost                  | Reliability             | Scalability         |
|---------------------|-----------------------|-------------------------|---------------------|
| IOPS requirements   | Volume type selection | Backup strategies       | Volume modification |
| Throughput needs    | Size optimization     | Multi-AZ configurations | Instance types      |
| Latency sensitivity | Snapshot management   | Snapshot policies       | Growth planning     |
| Queue depth         | Usage patterns        | Recovery procedures     | Performance scaling |

## Enhanced Networking
CloudOps engineers configure enhanced networking that uses single root I/O virtualization (SR-IOV) to provide
high-performance networking capabilities that improve latency and packet per seconds (PPS) performance and reduce CPU overhead.

### Instance store implementation
Optimize performance for specific workloads that require fast, temporary storage, reducing the bottleneck on overall application infrastructure using instance store volumes,
especially non-volatile memory express (NVMe) SSD instance store volumes. 

**NVMe** instance store volumes are used in Nitro-based EC2 instances, offering low latency, high speed storage.




