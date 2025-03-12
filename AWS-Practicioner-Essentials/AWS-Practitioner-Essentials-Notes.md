# AWS Practitioner Essentials

## Terminologies:
`Cloud Computing`: On-demand delivery of IT resources and applications through the internet with pay-as-you-go pricing.

`Memory`: A temporary storage are for processing.

`Hardware Accelerators`: A component that can expedite data processing.

`Input/Output Operations Per Second (OIPS)`: A metric that indicates how many I/O operations a
device can perform per second.

## Introduction to Amazon Web Services

### `Deployment Models for Cloud Computing`
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





### `Benefits of Cloud Computing`

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


## Compute in the Cloud
### `Amazon Elastic Compute Cloud (EC2)`
- Provides resizable compute capacity in the cloud as Amazon EC2 instances.
- An Amazon EC2 instance enables the use of a virtual server to run applications in the AWS cloud.
- Provision and launch EC2 instance within minutes.
- Pay only for the compute time used when an instance is running, not when it is stopped or terminated.
- Save cost by paying only for server capacity needed or wanted.

### `How Amazon EC2 works`
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

### `Amazon EC2 Instance Types`
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

### `Amazon EC2 Pricing`
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

### `Scalability and Elasticity`
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

### `Elastic Load Balancer (ELB)`
- an application that takes in request and routes to the instances to be processed.
- ELB is automatically scalable with no change in the hourly cost.
- Single URL that each front-end uses. Single point of contact for all incoming web traffic to Auto Scaling group.
- Promotes de-coupled architecture.

`Elastic Load Balancing:` is a major AWS service that automatically distributes incoming application traffic 
across multiple resources, such as Amazon EC2 instances.


### Messaging and Queueing
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
  <img src="../img/lambda1.png" height="100%" width="80%"/>
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


## AWS Global Infrastructure




