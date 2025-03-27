# AWS Practitioner Essentials

- [I. Introduction](#introduction-to-amazon-web-services-)
  - [Deployment Models for Cloud Computing](#deployment-models-for-cloud-computing-)
  - [Benefits of Cloud Computing](#benefits-of-cloud-computing-)
- [II. Compute](#compute-in-the-cloud-)
  - [Amazon EC2](#amazon-elastic-compute-cloud-ec2-)
  - [EC2 Instance Types](#amazon-ec2-instance-types-)
  - [EC2 Pricing Options](#amazon-ec2-pricing-)
  - [Amazon EC2 Auto Scaling](#scalability-and-elasticity-)
  - [Elastic Load Balancing](#elastic-load-balancer-elb-)
    - [`Amazon SNS`](#amazon-simple-notification-service-amazon-sns)
    - [`Amazon SQS`](#amazon-simple-queue-services-amazon-sqs)
  - [Serverless Computing](#additional-compute-services-serverless-computing)
    - [Lambda](#1-aws-lambda)
    - [Container](#2-aws-container-service)
    - [AWS Fargate](#3-aws-fargate)
- [III. AWS Global Infrastructure and Reliability](#aws-global-infrastructure-and-reliability-)
  - [AWS Regions](#aws-regions-)
  - [Availability Zones (AZs)](#availability-zones-azs-)
  - [Edge Locations](#edge-locations-)
    - [`Amazon CloudFront`](#amazon-cloudfront)
    - [`Amazon Route 53`](#amazon-route-53)
    - [`Amazon Outposts`](#amazon-outposts)
  - [Provisioning Resources](#provisioning-aws-resources-)
    - [AWS Management Console](#1-aws-management-console)
    - [AWS CLI](#2-aws-command-line-interface-cli)
    - [AWS SDKs](#3-aws-software-development-kits-sdks)
    - [Other Tools](#4-various-other-tools)
      - `Amazon Elastic Beanstalk`
      - `Amazon CloudFormation`
- [IV. Networking](#networking-)
  - [Amazon Virtual Private Cloud (VPC)](#amazon-virtual-private-cloud-amazon-vpc)
  - [VPC Components](#components-in-a-vpc-)
    - [`AWS Direct Connect`](#3-aws-direct-connect-)
  - [Network Security Layers](#network-security-layers-)
  - [Network ACLs](#network-access-control-list-network-acls-)
  - [Security Groups](#security-groups-)
  - [Global Networking](#global-networking-)
    - [Domain Name System](#domain-name-system-dns-)
    - [Amazon Route 53](#amazon-route-53-)
- [V. Storage and Databases](#storage-and-databases-)

## Terminologies:
`Cloud Computing`: On-demand delivery of IT resources and applications through the internet with pay-as-you-go pricing.

`Memory`: A temporary storage are for processing.

`Hardware Accelerators`: A component that can expedite data processing.

`Input/Output Operations Per Second (OIPS)`: A metric that indicates how many I/O operations a
device can perform per second.

## Introduction to Amazon Web Services [↑](#aws-practitioner-essentials)

### `Deployment Models for Cloud Computing` [↑](#aws-practitioner-essentials)
When selecting a cloud strategy, a company must consider factors such as required cloud application components, 
preferred resource management tools, and any legacy IT infrastructure requirements.

#### 1. Cloud-Based Deployment
- Run all parts of the application in the cloud.
- Migrate existing applications to the cloud.
- Design and build new applications in the cloud.

#### 2. On-Premises Deployment (private cloud deployment)
- Deploy resources by using virtualization and resource management tools.
- Increase resource utilization by using application management and virtualization technologies.
- Resources are deployed on premises by using virtualization and resource management tools.

#### 3. Hybrid Deployment
- Connect cloud-based resources to on-premises infrastructure.
- Integrate cloud-based resources with legacy IT applications.
- For instance where legacy applications that are better maintained on premises, or government regulations
that require business to keep certain records on premises.





### `Benefits of Cloud Computing` [↑](#aws-practitioner-essentials)

#### Trade upfront expense for variable expense
`Upfront expense` refers to data centers, physical servers, and other resources that you would need to invest
before using them. `Variable expense` means you only pay for computing resources you consume instead of investing
heavily in data centers and servers before you know how you're going to use them.

#### Stop spending money to run and maintain data centers
Cloud computing provides the ability to focus less on data centers that requires more expenses and time managing
infrastructure and servers. Which gives more focus on applications and customers.

#### Stop guessing capacity
Pay only for the compute time that is used. You can also scale in or scale out in response to demand.

#### Benefit from massive economies of scale
Achieve a lower variable cost than getting your own by using cloud computing.
Because usage from hundreds of thousands of customers can aggregate in the cloud, providers, 
such as AWS, can achieve higher economies of scale. The economy of scale translates into 
lower pay-as-you-go prices. 

#### Increase speed and agility
Cloud computing flexibility makes it easier to develop and deploy applications.
When computing in data centers, it may take weeks to obtain new resources that is needed. By comparison,
cloud computing enables to access new resources within minutes.

#### Go Global in minutes
Enables to deploy applications to customers around the world quickly, while providing low latency.


## Compute in the Cloud [↑](#aws-practitioner-essentials)
### `Amazon Elastic Compute Cloud (EC2)` [↑](#aws-practitioner-essentials)
- Provides resizable compute capacity in the cloud as Amazon EC2 instances.
- An Amazon EC2 instance enables the use of a virtual server to run applications in the AWS cloud.
- Provision and launch EC2 instance within minutes.
- Pay only for the compute time used when an instance is running, not when it is stopped or terminated.
- Save cost by paying only for server capacity needed or wanted.

### `How Amazon EC2 works` [↑](#aws-practitioner-essentials)
#### 1. Launch
- Launch an instance by selecting a template with basic configurations for your instance.
- These configurations include the operating system (OS), application server, or applications.
- The instance type (specific hardware configurations of the instance) can also be selected.
- Specify the security settings to control the network traffic that can flow into and out of the instance.
#### 2. Connect
- The instance can be connected in several ways.
- Programs and applications have multiple different methods to connect directly to the instance and exchange data.
- Users can also connect to the instance by logging in and accessing the computer desktop.
#### 3. Use
- After connecting, the instance can now be used.
- Run commands to install software, add storage, copy and organize file, and more.

### `Amazon EC2 Instance Types` [↑](#aws-practitioner-essentials)
#### 1. General Purpose
- Balanced resources (compute, memory, and networking resources)
- Diverse workloads such as application servers, gaming servers, backend for enterprise apps, small - medium DBs.
- Web servers and code repositories

#### 2. Compute Optimized
- For compute intensive tasks like gaming servers, High Performance Computing (HPC), Scientific modeling.
- The difference is, compute optimized applications are ideal for high-performance web servers, compute-intensive
application servers, and dedicated gaming servers.

#### 3. Memory Optimized
- Utilizes hardware accelerators.
- Designed to deliver fast performance for workloads that process large datasets in memory.
- `Memory`
  - In computing memory is a temporary storage area.
  - It holds all the data and instructions that a CPU needs to be able to complete actions.
  - Before a computer program or application is able to run, it is loaded from storage into memory.
  - This preloading process gives the CPU direct access to the computer programs.

#### 4. Accelerated Computing Instances
- Use hardware accelerators, or coprocessors, to perform some functions more efficiently than is 
possible in software running on CPUs. Tasks like Floating point number calculations, Graphics processing, 
Data Pattern matching.
- `Hardware Accelerator`: Is a component that can expedite data processing.
- Ideal for workloads such as graphics applications, game streaming, and application streaming.

#### 5. Storage Optimized
- Good for high performance for locally stored data.
- Designed for workloads that require high, sequential read and write access to large datasets on **local storage**.
- Examples are Distributed file systems, Data warehousing applications, 
and high-frequency online transaction processing (OLTP) systems.
- `Input/Output Operations Per Second (OIPS)`
  - Is a metric that measures the performance of a storage device.
  - It indicates how many different input or output operations a device can perform in a second.

### `Amazon EC2 Pricing` [↑](#aws-practitioner-essentials)
#### 1. On-Demand
- ideal for short-term, irregular workloads that cannot be interrupted.
- No upfront costs or minimum contracts apply.
- The instance can run continuously until it is stop, and pay for only the compute time used.
- Example: developing and testing applications and running applications that have unpredictable usage patterns.

#### 2. Reserved Instances
- billing discount applied to the use of On-Demand Instances in an AWS account.
- At the end of the term, the Amazon EC2 instance can still be used without interruption. 
However, On-Demand rates will be charged until one of the following is done.
  1. Terminate the Instance
  2. Purchase a new reserved instance that matches the instance attributes. 
  

`Standard Reserved Instances:`
- Good fit if the EC2 instance type and size is known for steady-state applications.
- The following is required to be indicated upon availing:
  - **Instance type and size**: for example, `m5.xlarge`
  - **Platform description (OS):** for example, MS Windows Server or Red Hat Ent. Linux
  - **Tenancy:** Default tenancy or dedicated tenancy

`Convertible Reserved Instances:`
- If the EC2 Instances are needed to run in different AZs or different instance types.
- `Note:` You trade in a deeper discount when you require flexibility to run your EC2 Instances.

#### 3. Savings Plans
- Reduce cost for 1-year or 3-year term.
- Savings up to 72% compared to On-Demand rates.
- There is no need to specify up front what EC2 instance type and size, OS, and tenancy to get a discount.
- There is no need to commit to a certain number of EC2 instances as it does not include EC2 capacity reservation options.


#### 4. Spot Instances
- ideal for workloads with flexible start and end times, or that can withstand interruptions.
- These are unused Amazon EC2 computing capacity and offer a cost savings of 90% off.
- Use cases examples are background processing job that can start and stop as needed (such as data processing for a customer survey).
- If there is a Spot Instance request and there is no EC2 capacity available, the request is not successful until capacity becomes available.
- There is a chance that the instance may be interrupted once capacity is no longer available (Unexpected interruptions).

#### 5. Dedicated Hosts
- Physical servers with Amazon EC2 instance capacity that is fully dedicated for use.
- There are existing per-socket, per-core, or per-VM software licenses available to help maintain license compliance.
- The most expensive pricing.

### `Scalability and Elasticity` [↑](#aws-practitioner-essentials)
- Involves beginning with only the resources needed and designing the architecture to automatically respond
to changing demand by scaling out or in. Pay for only the resource used.
- There is no need to worry about lack of computing capacity.

#### Amazon EC2 Auto Scaling
- Enables to automatically add or remove Amazon EC2 instances in response to changing application demand.
- Maintain a greater sense of application availability by automatically scaling instances in and out as needed.
- There are two approaches in Amazon EC2 Auto Scaling:
  1. _Dynamic scaling_ responds to changing demand.
  2. _Predictive scaling_ automatically schedules the right number of EC2 instances based on predicted demand.

<div align="center">
  <img src="../img/AutoScaling_1.png" height="250" width="250"/>
</div>

#### Auto Scaling Notes:
- When an _Auto Scaling Group_ is created, Set the minimum number of Amazon EC2 instances at one.
- **minimum capacity:** is the number of EC2 instances that launch immediately after the group is created.
- **desired capacity:** instance even though the application needs a minimum. If this is not set, the
desired capacity will be the minimum capacity by default.
- **maximum capacity:** Maximum instance the group will scale out in response to increased in demand.

With Amazon EC2 scaling, you pay for only the instances you use, when you use them. This is a cost-effective
architecture that provides the best customer experience while reducing expenses.

### `Elastic Load Balancer (ELB)` [↑](#aws-practitioner-essentials)
- an application that takes in request and routes to the instances to be processed.
- ELB is automatically scalable with no change in the hourly cost.
- Single URL that each front-end uses. Single point of contact for all incoming web traffic to Auto Scaling group.
- Promotes de-coupled architecture.

`Elastic Load Balancing:` is a major AWS service that automatically distributes incoming application traffic 
across multiple resources, such as Amazon EC2 instances.


### Messaging and Queueing [↑](#aws-practitioner-essentials)
#### Tightly Coupled Architecture
- Applications communicating directly without **buffer**.
- When there is change in a certain component, it affects other components as well or even the whole system.

#### Loosely Couple Architecture
- Single failure won't cause cascading failures.

To help maintain application availability when a single component fails, an application can be designed
through a **microservices** approach.

<div align="center">
  <img src="../img/microservices1.png" height="300px" width="300px"/>
</div>

#### Amazon Simple Notification Service (Amazon SNS)
- a publish/subscribe (pub/sub) service.
- Using _Amazon SNS topics_, a publisher publishes messages to subscribers.
- Subscribers can be web servers, email addresses, AWS Lambda functions, or several other options.

#### Amazon Simple Queue Services (Amazon SQS)
- A message queueing service.
- Allows to send, store, receive messages between software components at any volume without losing messages 
or requiring other services to be available.
- In Amazon SQS, an application sends messages into a queue. A user or service retrieves the message from the queue, 
processes it, and then deletes it from the queue.
- `SQS Queues`: Where messages are placed until they are processed.
- `Payload`: The data contained within a message. Encrypted until delivery.

### Additional Compute Services (Serverless Computing)
You cannot see or access the underlying infrastructure that hosts your application. All the management such as
provisioning, scaling, high availability is handled by the cloud provider (AWS).

Another benefit of serverless computing is the flexibility to scale serverless applications automatically.
Severless computing can adjust the applications' capacity by modifying the units of consumption, such as throughput and memory.

#### 1. AWS Lambda
- Upload a code into a Lambda Function that is invoked through a configured **Trigger**.
- This function is run in an environment that is not to be taken care of by the user.
- Lambda automatically scales the function to meet demand.
- Not for longer running processes since it is designed to run for less than **15 minutes**
- Pay only for the compute time.
- For example, a Lambda function might involve automatically resizing uploaded images to the AWS Cloud. Whereas the trigger
is when a new image is uploaded.

<div align="center">
  <img src="../img/lambda1.png" height="50%" width="50%"/>
</div>

#### 2. AWS Container Service
- There is access in underlying environment but there is still efficiency and portability.
- The container is a `Docker` container. (Widely known platforms that uses OS level virtualization to deliver software)
- `Container`: is a package or object for a code and dependencies. Runs on top of an EC2 instances and are isolated from one another.

<div align="center">
  <img src="../img/container1.png" height="50%" width="50%"/>
</div>

Suppose that a company’s application developer has an environment on their computer that is different 
from the environment on the computers used by the IT operations staff. The developer wants to ensure 
that the application’s environment remains consistent regardless of deployment, so they use a 
containerized approach. This helps to reduce time spent debugging applications and diagnosing 
differences in computing environments.

- Container Orchestration Tools:
  - **Amazon Elastic Container Service (ECS)**
    - is a highly scalable, high-performance container management system that enables you 
    to run and scale containerized applications on AWS.
  - **Amazon Elastic Kubernetes Service (EKS)**
    - is a fully managed service that you can use to run Kubernetes on AWS.

#### 3. AWS Fargate
- There is no need for EC2 instances.
- Serverless compute platform for ECS and EKS.
- focus more on innovating and developing your applications, and you pay only for the resources that are required 
- to run your containers.

#### Summary
<div>
<details>
<summary>Running Docker container-based workloads on AWS, select Orchestration tools</summary>
<strong>Amazon EC2 or AWS Fargate</strong>
</details>
</div>

<div>
<details>
<summary>Host short running functions, Service oriented applications, event driven applications and 
no provisioning or managing servers</summary>
<strong>AWS Lambda</strong>
</details>
</div>

<div>
<details>
<summary>Host traditional applications, Full access to the OS</summary>
<strong>Amazon EC2</strong>
</details>
</div>

### `Useful Links:` 
<div>
  <ul>
    <li><a href="https://aws.amazon.com/products/compute/#AWS_compute_services">More AWS Compute Services</a></li>
    <li><a href="https://aws.amazon.com/getting-started/hands-on/?awsf.getting-started-category=category%23compute&awsf.getting-started-content-type=content-type%23hands-on&getting-started-all.sort-by=item.additionalFields.content-latest-publish-date&getting-started-all.sort-order=desc&awsm.page-getting-started-all=2">Hands-On Tutorials</a></li>
  </ul>
</div>


## AWS Global Infrastructure and Reliability [↑](#aws-practitioner-essentials)
### `AWS Regions` [↑](#aws-practitioner-essentials)
- Areas where a group of data centers is located.
- Are Geographically isolated areas.
- Contains multiple isolated and physically separate AZs within a geographic region.

1. `Compliance`
   - There might be a need to run data within a specific area only. 
   - A company might be under a requirement where all of its data is to reside within boundary of a country.
2. `Proximity` - Due to latency factor.
3. `Feature Availability`
4. `Pricing` - Each country has its own tax structure.

-----
`Amazon Bracket`: Amazon's Quantum Computing platform.

-----

### `Availability Zones (AZs)` [↑](#aws-practitioner-essentials)
- One or more data centers group together with redundant power, network, and connectivity in a region.
- located tens of miles apart from each other.

---
**Recommended:** A best practice is to run across at least two AZs in a region.

---

### `Edge Locations` [↑](#aws-practitioner-essentials)
A site that Amazon CloudFront uses to store cached copies of content closer to customers for faster delivery.

Cache a copy locally that is closed to customers/clients.

#### Amazon CloudFront
- Is a Content Delivery Network (CDN) of AWS
- Uses Edge locations all around the world to help accelerate communications with users.
- When a customer requests from a certain location, CloudFront retrieves the file from the cache 
  in the edge location and delivers the file to the customer.

#### Amazon Route 53
- A Domain Name System (DNS) owned by Amazon.
- Helps direct customers to the correct web locations with low-latency delivery.

#### Amazon Outposts
- Install a mini operational region directly in privately owned data center.
- Owned and operated by AWS but isolated within the building.

### `Provisioning AWS Resources` [↑](#aws-practitioner-essentials)
- Every action in AWS is an API call.

#### 1. AWS Management Console
- Browser based.
- Manage AWS resources visually.
- Useful for test environments, view AWS bills, view monitoring, work with non-technical resources.
- Great for learning and providing visualization for the user.

#### 2. AWS Command Line Interface (CLI)
- For a more systematic/programmatic approach
- Make API calls using the terminal on the machine.
- Makes action scriptable and repeatable.
- Can be run automatically, scheduled, or triggered.
- Can be used to launch an Amazon EC2 instance, connect EC2 instance to specific Auto Scaling group.

#### 3. AWS Software Development Kits (SDKs)
- Interact with AWS resources through various programming languages.
- Makes easy for developers to create programs that use AWS without using the low level APIs.
- Includes C++, Java, .NET, and more.

#### 4. Various Other Tools
`4.1. AWS Elastic Beanstalk`
- Service that helps provision Amazon EC2 based environments.
- Takes in information (application code and desired configs) and provides the environment for 
  the user.
- Provide the code and config settings, and it will deploy the resources necessary to perform the 
  following tasks:
  - Adjust capacity
  - Load balancing
  - Automatic Scaling
  - Application health monitoring
- Helps focus on business application and not the infrastructure

`4.2. AWS CloudFormation`
- Infrastructure as code tool used to define a wide variety of AWS resources in a declarative 
  way using text based documents (JSON or Yaml) called _CloudFormation Templates_.
- Supports the provisioning AWS resources: EC2 instance, Storage, Database, Analytics, ML.
- Manages all the API calls related for you.
- The AWS CloudFormation consumes the template and produces a structured working environment for 
  the user in parallel.
- Provisions resources in a safe, repeatable manner, enabling to frequently build infrastructure 
  and applications without having to perform manual actions.

## Networking [↑](#aws-practitioner-essentials)
### `Amazon Virtual Private Cloud (Amazon VPC)`
- Provision a logically isolated section of the AWS cloud.
- The resources can be public or private facing. Public resources are in a public subnet while 
  private resources are under a private subnet.
- A networking service that can be used to establish boundaries around AWS resources.

---
`Subnet:` Group of IP addresses. A section of a VPC that can contain resources such as EC2 
instances or Amazon RDBs.

`Public Subnet:` Contains resources that need to be accessible by the public.
`Private Subnet:` Contains resources that should be accessibly only through private network.

---

### `Components in a VPC` [↑](#aws-practitioner-essentials)
#### 1. Internet Gateway (IGW)
- Allows public traffic from the internet to access resources in the VPC.
- It is a doorway for the public to use. Without IG, no once can access resources in the VPC.

#### 2. Virtual Private Gateway (VPG)
- To access private resources in a VPC.
- Allows protected internet traffic to enter into the VPC.
- Still prone to traffic since it uses the same path used by the public.
- VPG establish a virtual private network (VPN) connection between the VPC and a private network.
- Allows traffic into the VPC only if it is coming from an approved network.

<div align="center">
  <img src="../img/networking1.png" height="50%" width="80%"/>
</div>

#### 3. AWS Direct Connect [↑](#aws-practitioner-essentials)
- AWS service that lets users establish a dedicated private connection between data center 
  and a VPC.
- Helps reduce network costs and increase the amount of bandwidth that can travel through the 
  network.
- Network traffic remains in the AWS network and never touches the public path which promotes 
  more security and prevents bottleneck and sudden increase in latency.


### `Network Security Layers` [↑](#aws-practitioner-essentials)
- Network Hardening
- Application Security
- User Identity
- Authentication and Authorization
- Distributed Denial of Service (DDoS) Prevention
- Data Integrity
- Encryption

#### Network Access Control List (Network ACLs) [↑](#aws-practitioner-essentials)
- A virtual firewall that controls inbound and outbound traffic **at the subnet level**.
- Checks the packets (message from the internet) permissions if it is allowed to enter or leave the 
  network. These permissions indicate who sent the packet and how the packet is trying to 
  communicate with the resources in a subnet.
- Only evaluates a packet if it crosses a **certain subnet**.
- Stateless (focuses on the list, it does not check if it originates from its own subnet or not.)
- By default, ACL allows all inbound and outbound traffic and can be customized by adding 
  personalized rules.
- for custom network ACLs, all inbound and outbound traffics are denied by default until rules 
  to specify is added.

---
`Stateless packet filtering`
- ACLs remember nothing and check packets that cross the subnet border inbound and outbound.
- After a packet has entered a subnet, it must have its permissions evaluated for resources 
  within the subnet, such as EC2 instances.

---

#### Security Groups [↑](#aws-practitioner-essentials)
- A virtual firewall that controls inbound and outbound traffic for an EC2 instance.
- By default, denies all inbound and outbound traffic. Then custom rules are configured to 
  allow certain traffics.
- Does not allow any IP address by default.
- **Instance level type of security**.
- Every newly launch instance is already assigned to a default security group.
- Can be modified to indicate what type of traffics can be accepted (HTTPS, OS, Admin).
- Stateful

---
`Stateful packet filtering`
- Security groups remember previous decisions made for incoming packets.
- When a packet response for a request returns to the instance, the security group remembers the 
  previous request. The security group allows the response to proceed, regardless of inbound 
  security group roles.

---

### `Network Traffics in VPC`
- When a data is requested from an application hosted in the AWS cloud, the request is sent as a 
  packet. A **packet** is a unit of data sent over the internet or a network.

### `Global Networking` [↑](#aws-practitioner-essentials)

#### Domain Name System (DNS) [↑](#aws-practitioner-essentials)
- Translates website names into IP addresses.
- Acts as a _phonebook_ of the internet.
- `DNS resolution:` process of translating a domain name to an IP address 

<div align="center">
  <img src="../img/dns1.png" width="80%"/>
</div >

#### Amazon Route 53 [↑](#aws-practitioner-essentials)
- A DNS web service that gives developers and businesses a reliable way to route end users to 
  internet applications hosted in AWS.
- Manages the DNS records for domain names.
- This is where new domain names are registered.
- Existing domain names and records managed by other domain registrars can also be transferred.

<div align="center">
  <img src="../img/dns2.png" width="80%"/>
</div >

1. A customer requests data from the application by going to AnyCompany's website.
2. Amazon Route 53 uses DNS resolution to retrieve the IP Address of AnyCompany's website. This 
   information is sent back to the customer.
3. The customer's request is sent to the nearest edge location through Amazon CloudFront.
4. Amazon CloudFront connects to the Application Load Balancer, which sends the incoming packet 
   to an Amazon EC2 instance.

## Storage and Databases [↑](#aws-practitioner-essentials)
### `Instance Stores`
- Block level storage volumes that behaves like a physical hard drive.
- Provides **temporary block-level storage** for an EC2 instance.
- A disk storage that is physically attached to the host computer for an EC2 instance, therefore 
  has the same life span as the instance.
- When the instance is stopped/terminated the data is lost as well.

### `Amazon Elastic Block Store (Amazon EBS)` [↑](#aws-practitioner-essentials)
- Service that provides **block-level storage** volumes that can be used with EC2 instances.
- Provides persistence of data even if EC2 is stopped/terminated.
- Created by defining the configuration (such as volume size and type) and provisioning it.
- Does not automatically resize. It is a hard drive.
- Stores data in a single AZ. When attaching an EC2 instance, both the instance and the EBS 
  volume must reside within the same AZ.
- #### EBS Snapshots
  - A feature of EBS that takes incremental backup for the volume.
  - The first backup taken of a volume copies all the data. Only the blocks of data that have 
    been changed since the most recent snapshot are saved _(Incremental backup)_.
  - _Full backup_ includes that data that has not been changed.

### `Amazon Simple Storage Service (Amazon S3)` [↑](#aws-practitioner-essentials)
- Service that provides **object-level storage**.
- Store and retrieve a virtually unlimited amount of data.
- Store data as version controlled _objects_ (object maximum size of **5TB**).
- Objects are stored in **buckets**.
------
`Object Storage:`
- Each object consists of **data**, **metadata**, and **key**.
- The data might be an image, video, text document, or file of any type.
- Metadata contains information about the data is, how it is used, size, and so on.
- The key is the unique identifier of the object.
------

#### Amazon S3 Storage Classes

| Storage Class / Tier                                    | Description                                                                                                                                                                                                                                                                                                           |
|---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **S3 Standard**                                         | - Designed for frequently accessed data<br/> - Stores data in minimum of 3 AZs.<br/> - Provides high availability for objects. - Applicable for websites, content distribution, and data analytics.<br/> - Has a higher cost than other storage classes intended for infrequently accessed data and archival storage. |
| **S3 Standard-Infrequent Access<br/> (S3 Standard-IA)** | - Similar to S3 Standard but lower storage price but higher retrieval prices.<br/> - Ideal for infrequently accessed data.<br/> - Stores data in minimum of 3 AZs.<br/>                                                                                                                                               |
| **S3 One Zone-Infrequent Access<br/> (S3 One Zone-IA)** | - Stores data in a single AZ<br/> - Lower storage price than standard-IA<br/>                                                                                                                                                                                                                                         |
| **S3 Intelligent Tiering**                              | - Ideal for data with unknown or <br/>changing access patterns<br/> - Requires small monthly monitoring and automation fee per object.<br/> - If an object is no accessed for 30 consecutive days, Amazon S3 automatically moves it to S3 Standard-IA tier. Once accessed, automaticall moved to S3 Standard tier.    |
| **S3 Glacier Instant Retrieval**                        | - For archived data that requires immediate access. Retrieve objects within a few ms.                                                                                                                                                                                                                                 |
| **S3 Glacier Flexible Retrieval**                       | - Low-cost storage for data archiving.<br/> - Able to retrieve objects within a few minutes to hours (1 minute to 12 hours).                                                                                                                                                                                          |
| **S3 Glacier Deep Archive**                             | - Lowest-cost object storage class for archiving.<br/> - Retrieve objects within 12 hours.<br/> - Supports long-term retention and digital preservation for data that might be accessed **once or twice a year**.<br/> - All objects are replicated and stored across at least 3 geographically dispersed AZs.        |
| **S3 Outposts**                                         | - Creates S3 buckets on Amazon S3 Outposts.<br/> - Makes it easier to retrieve, store, and access data on AWS outposts.<br/> - Works well for workloads with local data residency requirements.                                                                                                                       |

#### EBS and S3 comparison

| Elastic Block Storage                             | Amazon S3                                  |
|---------------------------------------------------|--------------------------------------------|
| Up to 16 TiB in size                              | Unlimited storage (Maximum 5TB per object) |
| Persisting                                        | Write once / Read Many                     |
| Solid state by default (HDD)                      | Durable (99.999999999%)                    |
| File is divided into blocks making easy to update | Have to be updated as a whole              |
| Attached to EC2 instances and AZ level resource   | Web enabled and serverless                 |

### `Amazon Elastic File System (Amazon EFS)`
- Managed file system. Multiple instances can access the data at the same time.
- Linux file system.
- Regional resource, stores data in and across multiple AZs.
- Automatic scalable file system used with AWS cloud services and on-premise resources.
- Can scale on demand to petabytes without disrupting applications.

### `Amazon Relational Database Service (Amazon RDS)`
- Automates tasks such as hardware provisioning, database setup, patching, and backups.
- Less time spent in completing administrative tasks and more time using data to innovate 
  applications.
- Can be integrated with other services such as using AWS Lambda to query the database from a 
  serverless application.
- Offers encryption at rest and encryption in transit.

`Lift-and-Shift` - Migration of on-premise database to the cloud.

#### Amazon RDS Database Engines
- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle Database
- Microsoft SQL Server

### `Amazon Aurora`
- An enterprise-class relational database.
- Compatible with MySQL and PostgreSQL.
- Up to 5x faster than standard MySQL databases and up to 3x faster than standard 
  PostgreSQL databases.
- Price is 1/10th the cost of commercial databases. Cost is reduced by reducing unnecessary I/O 
  operations, while ensuring that database resources remain reliable and available.
- Recommended for workloads that require high availability. It replicates **6 copies** of data 
  across **3 AZs** and continuously backups data to Amazon S3.

### `Amazon DynamoDB`
- Stores data redundantly across AZs. Mirrors data across multiple drives.
- Key-value database service that is reliable and high performance (millisecond response time).
- For Non-Relational Database (NoSQL). Simple flexible schemas
- Adding and removing of attributes can be done at any time.
- Automatically Scales while maintaining consistent performance. Mekase it a suitable choice for 
  use cases that require high performance while scaling.

#### Non Relational Database (NoSQL Databases)
- Uses structures (JSON, key-value pairs) other than rows and columns to organize data.

### `Amazon Redshift`
- Data warehouse as a service
- Handles the heavy lifting in provisioning the data warehouse so that users can focus on the 
  data alone.
- Applicable for Big BI data solutions (Big Data Analytics) which is a concept of looking at 
  historical data.
- Offers ability to collect data from many sources and helps understand relationships and trends 
  across data.

### `AWS Database Migration Service (Amazon DMS)`
- Enables the migration of RDBs, NRDBs, and other types of data stores.
- **Homogenous Databases:** Databases that are of the same type.
- **Heterogeneous Databases:** Databases that are of different source/type. Additional step 
  where an AWS Schema Conversion tool is used.

### `Additional Database Services`

| Purpose-Build Databases                         | Description                                                                                                                                                                         |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amazon DocumentDB**                           | - Document database service that supports **MongoDB** workloads <br/> - Fully managed native **JSON** document.                                                                     |
| **Amazon Neptune**                              | - A Graph database service.<br/> - For applications that are build and run with highly connected datasets<br/> - Ex: Recommendation engines, fraud detection, and knowledge graphs. |
| **Amazon Quantum Ledger Datbase (Amazon QLDB)** | - Review a complete history of all the changes that have been made to application data.                                                                                             |
| **Amazon Managed Blockchain**                   | - Service to create and manage blockchain networks with open-source frameworks.<br/>                                                                                                |
| **Amazon ElastiCache**                          | - Service that adds caching layers on top of <br/>databases to help improve the read times of common requests. Supports _Redis_ and _Memcached_ data store types.                   |
| **Amazon DynamoDB Accelerator**                 | - In-Memory cache for DynamoDB. <br/> - Helps improve response times from single-digit milliseconds to microseconds.                                                                |

#### Useful Links
- [Deep Dive - Databases](https://docs.aws.amazon.com/decision-guides/latest/databases-on-aws-how-to-choose/databases-on-aws-how-to-choose.html)
