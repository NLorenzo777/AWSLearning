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


