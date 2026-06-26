# Networking and Elasticity [^](../../README.md#3-aws-certified-developer-associate)
The network is the foundation of your infrastructure.

## Amazon Route 53
- Highly available and highly scalable cloud DNS service that has servers distributed around the globe used to translate human-readable names into IP addresses.

### Features
- Scales automatically to manage spikes in DNS queries
- Register a domain name (or manage an existing one)
- Routes internet traffic to the resources of the domain
- Checks the health of the resources.
- Allows to route users based on their geographic location.

## EC2 Auto Scaling
- Monitors EC2 instances and automatically adjusts by adding or removing EC2 instances based on conditions defined.

### Features
- Automatically **scale-in** and **scale-out** based on needs.
- Included automatically with Amazon EC2
- Automate how Amazon EC2 instances are managed.
- Adds instances only when needed, optimizing cost savings.
- **Predictive scaling** removes the need for manual adjustment of auto-scaling parameters over time.
- Works very well with AWS Messaging Services such as SNS to help alert when EC2 condition occurs.

### Setup needs for creating an Auto-Scaling Group

#### Count of instances
- The desired amount of EC2 instances to have available.
- If any instance goes down/fails, a new instance automatically spins up.

#### Launch templates
- Specify the configuration details such as the following in the **Launch Template**:
  - **AMI ID**
  - **instance type**
  - **a key pair**
  - **security groups**
  - other parameters used to launch EC2 instances.

### Target Tracking Scaling Policy option
- An option during the configuration of the Auto-Scaling Group (Automatic Scaling)
- When this is selected, a CloudWatch metric and target value must be chosen.
- This lets the scaling policy adjust the desired capacity in proportion to the metric's value.
- If `No Scaling Policy` is selected, the scaling group will remain

### Instance Maintenance Policy
- Control Auto-Scaling Group's availability during instance replacement events.

#### Replacement Behaviors
1. **No Policy**
   - For rebalancing events, new instances will launch before terminating others.
   - For all other events, instances terminate and launch at the same time.
2. **Launch before terminating**
   - Launch new instances and wait for them to be ready before terminating others.
   - Allows to go above the desired capacity by a given percentage 
   - may temporarily increase cost.
3. **Terminate and Launch**
   - Terminate and launch instance at the same time.
   - Allows to go below the desired capacity by a given percentage.
   - May temporarily reduce availability.
4. **Flexible**
   - Set custom values for the minimum and maximum amount of available capacity.
   - Gives greater flexibility in setting how far below and over the desired capacity EC2 auto-scaling goes when replacing instances.


