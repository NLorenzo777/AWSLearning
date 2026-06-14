# Servers in the Cloud and Compute Services [^](../../README.md#3-aws-certified-developer-associate)

1. [EC2 Dashboard](#ec2-dashboard-)
2. [AWS Command Line Interface](#aws-command-line-interface-aws-cli-)

## EC2 Dashboard [^](#servers-in-the-cloud-and-compute-services-)

### Instances
* **Launch Templates:**
  - These are the scripts that contain configuration information written either in JSON or YAML format 
  - Automate instance launches, simplify permission policies, and enforce best practices across organization.

### Network and Security
- **Security Groups**
    - Acts as a firewall rules that control the traffic for EC2 instances or VPC.
    - It's possible to define multiple Security Groups.
    - Security group rules can be modified anytime; the new rules are automatically applied to all instances that are associated with the security group.
- **Elastic IP Addresses**
  - An Elastic IP Address us a static IPv4 address.
  - Assume you have a server running on an EC2 instance, that has specific IP address. In case the instance fails, the back-up instance will spin up.
  The back-up instance will have a different IP address, which requires to update the IP address used by the client application.
  - The problem can be solved by using the elastic IP address.
  - An Elastic IP address can mark the failure of an instance by remapping the current IP address to another instance in the account.
- **Placement Group**
  - EC2 instances are spread out across underlying hardware. But sometimes there is a requirement to place the group of interdependent instances to meet the needs of workload.
  - AWS allows placing the instances based on either of the following placement strategies:
    - cluster (tightly packed)
    - partition (logically grouped)
    - spread across underlying hardware
- **Key-Pairs**
  - A key-pair is a pair of encrypted public and unencrypted PEM encoded private keys.
  - The public key is placed automatically on the instance, and the private key is made available to the user, just once.
  - You can only log in to your running instance with the help of your private key.
- **Network Interfaces**
  - A network interface represents a virtual network card in a VPC, and it has a both private and public IP addresses.
  - When an instance is created, a default network interface is attached.
  - Create and attach additional network interfaces to any instance. An EC2 instance can have multiple network interfaces.

### Load Balancing
A load balancer distributes traffic across multiple targets.
- [Application Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)
- [Network Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html)

## AWS Command Line Interface (AWS CLI) [^](#servers-in-the-cloud-and-compute-services-)
Below are the steps to configure the AWS CLI on a machine.

#### 1. Create an IAM for the CLI to use
Once created, the `AWS Access Key ID` and `AWS Secret Access Key` is needed.

#### 2. Run the command on terminal
```bash
aws configure
```

This CLI will prompt and ask for the AMI credentials in step 1.

#### 3. Configure the session token to null
```bash
aws configure set aws_session_token ""
```
The `aws_session_token` is not needed when using the Access Key of an Admin IAM user.

### Important Information about AWS CLI
- **Mac/Linux users** needs to let the system know that sensitive information is residing in the .aws folder.
```bash
export AWS_CONFIG_FILE=~/.aws/config
export AWS_SHARED_CREDENTIALS_FILE=~/.aws/credentials
```

- **Windows users with GitBash only** have to set environment variables.
```bash
setx AWS_ACCESS_KEY_ID <AMI Access key>
setx AWS_SECRET_ACCESS_KEY <AMI Secret Access Key>
setx AWS_DEFAULT_REGION us-east-1 
```

### Setting the default region in the CLI
```bash
aws configure set default.region us-east-1
```

## Elastic Block Store (EBS)
AWS allows to create a volume from either of the following three commands:
1. Create and attach EBS volumes while creating an EC2 instance using the **Launch Instance** wizard.
2. Create an empty EBS volume, and later attach to a running instance.
3. Create an EBS volume from a previously created snapshot and later attach to a running instance.







