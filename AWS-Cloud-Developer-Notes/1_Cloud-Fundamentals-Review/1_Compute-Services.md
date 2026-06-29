# Servers in the Cloud and Compute Services [^](../../README.md#3-aws-certified-developer-associate)

1. [Amazon EC2 Instance Family](#amazon-ec2-instance-family-)
2. [Anatomy of an Instance](#anatomy-of-an-instance-)
3. [EC2 Dashboard](#ec2-dashboard-)
4. [AWS Command Line Interface](#aws-command-line-interface-aws-cli-)
5. [Elastic Block Stores](#elastic-block-store-ebs-)
6. [Virtual Private Cloud (VPC)](#virtual-private-cloud-vpc-)
7. [Lambda](#lambda-)
8. [Elastic Beanstalk](#elastic-beanstalk)

## Amazon EC2 Instance Family [^](#servers-in-the-cloud-and-compute-services-)

Amazon EC2 instance types follow this naming pattern:

```text
<family><generation><options>.<size>
```

Example:

```text
m7i.large
│││ └──── Size
││└────── Options
│└─────── Generation
└──────── Family
```

### Instance Family
The **family** indicates the primary purpose of the instance.

| Family | Name                   | Best For                                        |
|--------|------------------------|-------------------------------------------------|
| **t**  | Burstable              | Development, testing, small web applications    |
| **m**  | General Purpose        | Balanced CPU and memory workloads               |
| **c**  | Compute Optimized      | CPU-intensive applications                      |
| **r**  | Memory Optimized       | Databases, caches, large Java heaps             |
| **x**  | Extra Memory           | Very large in-memory databases (e.g., SAP HANA) |
| **i**  | Storage Optimized      | Fast local NVMe SSD storage                     |
| **g**  | GPU                    | Graphics rendering, AI inference                |
| **p**  | GPU (High Performance) | AI/ML training, HPC                             |
| **h**  | High Disk Throughput   | Big data processing                             |
| **d**  | Dense Storage          | Large local storage workloads                   |

### Generation
The number indicates the hardware generation.

Generally:
- Higher number = Newer hardware
- Better performance
- Better networking
- Better price/performance

### Options
Letters after the generation describe the processor or additional capabilities.

| Option   | Meaning                  | Notes                                                             |
|----------|--------------------------|-------------------------------------------------------------------|
| **a**    | AMD processor            | Uses AMD EPYC CPUs                                                |
| **i**    | Intel processor          | Uses Intel Xeon CPUs                                              |
| **g**    | AWS Graviton processor   | ARM-based CPU designed by AWS                                     |
| **n**    | High networking          | Higher network bandwidth                                          |
| **d**    | Local NVMe SSD           | Includes instance-attached SSD storage                            |
| **e**    | Extra storage or memory  | Meaning varies depending on the instance family                   |
| **z**    | High-frequency Intel CPU | Optimized for high clock speed workloads                          |
| **flex** | Flexible vCPU allocation | Lower-cost option with flexible CPU allocation (e.g., `m7i-flex`) |

> **Note:** Not every family supports every option.

### Size
The size determines the amount of CPU and memory allocated.

| Size    | Relative Capacity |
|---------|-------------------|
| nano    | Smallest          |
| micro   | Very Small        |
| small   | Small             |
| medium  | Medium            |
| large   | Large             |
| xlarge  | Larger            |
| 2xlarge | ~2× xlarge        |
| 4xlarge | ~4× xlarge        |
| 8xlarge | ~8× xlarge        |
| ...     | Continues upward  |

> **Note:** The exact vCPU and RAM depend on the instance family.

## Anatomy of an Instance [^](#servers-in-the-cloud-and-compute-services-)
Ana EC2 instance is made up of:

1. **Host's physical hardware components**
2. **Hypervisor (software that hides hardware resources from the application OS**
   - Original hypervisor
   - Nitro Hypervisor
3. Network Interface

### Traditional Hypervisor
A traditional hypervisor's job is to protect physical hardware and BIOS, virtualize the CPU, storage, and networking; and provide rich set of management capabilities.

### AWS Nitro System
- Combination of dedicated hardware and a lightweight hypervisor for a faster innovation and enhanced security.
- Separates the traditional hypervisor's functions. These functions are offloaded to dedicated hardware and software.
- Offloads all hardware, management, and security operations to a dedicated card. Hence, the hypervisor no longer has to carve out a portion of compute resources to handle this I/O.

### Network Interface
- Each instance comes with an elastic network interface.
- Logical component that represents a virtual network card.
- Allows the instance to communicate with other instances, servers, features, and anything on the internet.


### Bare-metal Instances
Instances ideal for the following applications:
- Workload that requires access to hardware feature set
- Applications that need to run in non-virtualized environments for licensing or support requirements
- Customer that wants to use their own hypervisor

## Connecting to EC2 

### Connect using SSH
- Secure Shell (SSH) is a network protocol that facilitates a secure, encrypted connection between two systems (SSH Client and SSH Server).
- When connected to the server, the client can remotely perform all operations as if they were standing in front of the server.
- SSH authentication to an EC2 instance is done through the use of **key pair** associated with the instance when launched.
  - The key pairs, a public and a private key, are a form of asymmetric cryptography used to authenticate the client and server to each other.
  - The key pair makes it possible to secure, connect, and manage the instance, which is why **it is very important not to lose the key pair**.
- There are variety of SSH tools such as **PuTTY**, **WinSCP**, **xShell**

### Controlling Access to Instance
- By default, all traffic is allowed out of the instance. An inbound rule must be created if wanted any traffic to be allowed in.
- If using SSH, ensure that port 22 is configured as an inbound security group rule. Connection error will be received if not configured.

### Connect using EC2 Instance Connect
- Provides a secure way to connect to **Linux instances** (default to Linux and Ubuntu) using SSH.
- Removes the need to share and manage SSH key pairs.
- All connection requests using EC2 instance connect are logged to AWS CloudTrail to audit connection requests.
- connect using the Amazon EC2 console (browser-based), Amazon EC2 Instance Connect CLI, or the SSH client of choice.

### Accessing using AWS Systems Manager Session Manager
- Use **Session Manager** to directly start a session with an instance while working in the EC2 dashboard or AWS account.
- After the session has started, run bash commands.
- Session Manager removes the need to open inbound ports, manage SSH keys, or use bastion hosts.
- Use Session Manager with **AWS PrivateLink** to prevent traffic from going through the public internet.

> a **managed node** is any compute resource that is registered with AWS Systems Manager (SSM) 


### AWS Systems Manager
1. If needed, install the AWS Systems Manager on the resource.
2. Create an IAM role containing the `AmazonSSMManagedInstanceCore` permission.
3. Attach the IAM role to the resource (e.g. EC2 instance)
4. Connect to the resource using Sessions Manager

>  AWS Systems Manager (SSM) can be installed on an Amazon EC2 instance, On-premises server, or virtual machines. This allows SSM to manage the installed resource.

#### Benefits of Session Manager
- **Centralized access control to managed nodes using IAM policies**
  - grand and revoke access to managed nodes.
  - control which individual users or groups in the organization can use Session Manager and which managed nodes can be accessed, through IAM.
- **No open inbound ports and no need to manage bastion hosts or SSH keys**
- **One-click access to managed nodes from the console and AWS CLI**
  - Using AWS Systems Manager console or Amazon EC2 console, or AWS CLI
  - Permissions to managed nodes are provided through IAM policies instead of SSH keys or other mechanism. This makes connection time greatly reduced.
- **Port forwarding**
  - Redirect any port inside the managed node to a local port on a client. This allows to connect to the local port and access the server application that is running inside the node.
- **Cross-platform support for windows, Linux, and macOS**
- **Logging and auditing session activity**
  - Record the connections made to managed nodes and the commands that were run. 
  - Receive notifications when a user in the organization starts or ends session activity.

## Amazon Machine Images (AMI)

### Boot Modes
- When a computer boots, the first software that it runs is responsible for initializing the platform and providing an interface for the OS to perform platform-specific operations. 
- The AMI boot mode parameter signals to EC2 which boot mode to use when launching an instance.

#### UEFI Boot Mode
- Unified Extensible Firmware Interface (UEFI) is run by Graviton instance types by default.
- When an instance is launched, a key-value store for variables is created. The store can be used by UEFI and the instance OS for storing UEFI variables.
- UEFI variables are used by the bootloader and OS to configure early system startup. Because of this, OS can manage certain settings of the boot process, like the boot order, or the keys for UEFI Secure Boot.
- Never store sensitive data in UEFI variable store.
- Provides additional defense-in-depth that helps customer secure software from threats that persist across reboots.

### Launch Permissions
- **Public**: The owner of the AMI grants launch permissions to all AWS accounts.
- **explicit**: Grant launch permission to specific AWS accounts, organizations, or organizational units.
- **implicit**: The owner of the AMI has launch permissiosn for the AMI they own.


#### Legacy BIOS Boot Mode
- Run by Intel and AMD instance types on default.
- The original way of booting a system using the BIOS firmware.

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

## Elastic Block Store (EBS) [^](#servers-in-the-cloud-and-compute-services-)
AWS allows to create a volume from either of the following three commands:
1. Create and attach EBS volumes while creating an EC2 instance using the **Launch Instance** wizard.
2. Create an empty EBS volume, and later attach to a running instance.
3. Create an EBS volume from a previously created snapshot and later attach to a running instance.

## Virtual Private Cloud (VPC) [^](#servers-in-the-cloud-and-compute-services-)
- A VPC spans all the AZ in the region.
- Control virtual networking environment, which includes:
  - **IP address ranges**
  - **subnets**
  - **route tables**
  - **network gateways**
- VPC is found under **Networking & Content Delivery** section of the AWS Management Console.
- The default limit is **5 VPCs** per region. Increase of these limits can be requested.
- AWS resources are automatically provisioned in a default VPC.
- There are no additional charges in creating and using a VPC.
- Store data in S3 and restrict access to that it's only accessible from instances in the VPC.

### Network ACLs
- A given Network ACL can be associated with multiple subnets
- For default ACLs, **it allows all inbound/outbound IPv4 traffic and, if applicable, IPv6 traffic**.
- For custom ACLs, **denies all inbound/outbound IPv4 traffic**. This can be modified.
- Inbound/Outbound rules are numbered and ordered. **The lowest numbered rule is evaluated first**.
- The incoming/outgoing traffic to/from a given subnet follows the rules mentioned in the associated network ACL.
- If an inbound rule is allowed, a separate outbound rule must be created. Network ACLs see traffic between client and server as two different streams. Hence, there must be one rule for each stream.

### Security Groups
- Attached to the **elastic network interface** of the AWS resources within the subnet.
- Stateful, have inbound and outbound rules. If traffic is allowed in, that traffic is automatically allowed back out.
- Allow rule to be added for other security groups, or add a rule for the security group itself.
- Have hidden explicit deny. This means that anything that is not explicitly allowed, is denied.

### Five Reserved IPs
There are five reserved addresses **inside each subnet** that are reserved for the use of AWS resources.

1. The network address `x.x.x.0` (e.g. the last .0 in 10.0.0.0)
2. The first IP address after the network address: `x.x.x.1` (e.g. 10.0.0.1) - AWS uses this address **for the Amazon VPC router**.
3. The second IP address after the network address (e.g. 10.0.0.2) - AWS uses this address **for DNS**
4. The third IP address (e.g. 10.0.0.3) - This address is reserved in case it is needed in the future.
5. The last IP in the subnet (e.g. 10.0.0.255) - This is the broadcast address but **AWS does not support broadcast in a VPC**.

> For a subnet range of /28, there are 16 address. hence, the usable addresses are 16 - 5 = 11 address.

## Lambda [^](#servers-in-the-cloud-and-compute-services-)
- Lambdas have a time limit of 15 minutes.
- The code run on AWS Lambda is called a "Lambda function"
- Can be triggered by other AWS services.
- Supports **Java**, **Go**, **PowerShell**, **Node.js**, **C#/.NET**, **Python**, and **Ruby**.
- There is a runtime API that allows to use other programming language to author functions.
- Lambda code can be authored via the console.

### Creating a Lambda
AWS provides three (3) options to get the template code for the function:
- **Author from scratch**: Start in a simple Hello World example.
- **Use a blueprint**: Build a Lambda application from a sample code and configuration presets for common use cases.
- **Browse Serverless app repository**: Deploy a sample Lambda application from the AWS Serverless Application Repository.

### Deleting a Lambda
Deleting a function permanently removes the function code. However, the related IAM roles are retained in the account.

## Elastic Beanstalk
- Orchestration service to deploy a web application easily. Spins up all the services needed for the application.
- Found under the compute section of the AWS management console.
- **Pricing:** There is no additional charge. The resources that are created are the ones being billed.

---------------------------
`NEXT TOPIC:` [II. Storage and Content Delivery](2_Storage-and-CD.md)
---------------------------
