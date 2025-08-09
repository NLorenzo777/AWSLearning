#### `PREVIOUS MODULE:` [Migrating-to-the-AWS-Cloud](11_Migrating-to-the-AWS-Cloud.md)

----

# Well-Architected Solutions [↑](../README.md#1-aws-cloud-practitioner-notes)

- [AWS Specialized Services](#aws-specialized-services)
  - [Development Services](#development-services-)
  - [Business Application Services](#business-application-services-)
  - [End-User Computing Services](#end-user-computing-services-)
  - [IoT Services](#iot-services-)
- [AWS Well-Architected Framework](#aws-well-architected-framework-)
  - [6 Pillars of Well Architected Framework](#6-pillars-of-well-architected-framework-)
  - [AWS Well-Architected Tool](#aws-well-architected-tool-aws-wa-tool-)

## `AWS Specialized Services`
AWS services are purpose-built for specific use cases. There are four (4) specialized AWS Service types:

### Development Services [↑](#well-architected-solutions-)

#### 1. AWS CodeBuild
- Fully managed continuous integration service that compiles source codes, runs tests, and produces software packages for deployment.
- Automatically scales to meet demand, and pay for the build time used.

#### 2. AWS CodePipeline
- Fully managed CI/CD service that automates the **build**, **test**, and **deploy** phases of release process.
- Helps developers streamline software release workflows and reliably deliver new features and fixes without needing to provision servers.
  - **CI/CI Pipelines** automate the integration, testing, and deployment of code changes to help provide quick and reliable software delivery.

#### 3. AWS X-Ray
- Tracing, debugging, and performance analysis tool that helps developers visualize application behaviour.
- Developers can quickly identify performance bottlenecks, troubleshoot issues, and optimize applications for better efficiency and reliability.

#### 4. AWS AppSync
- Fully managed GraphQL service.
- Developers can create a single GraphQL API that can securely access, manipulate, and combine data from multiple data sources.
- Helps developers connect frontend applications with backend data.
  - **GraphQL is a query language for APIs, clients request only the specific data they need.**

#### 5. AWS Amplify
- Streamline the process of developing, deploying, and managing secure and scalable full-stack applications on AWS.
- Developers can quickly add features, like authentication, APIs, storage, and hosting, with minimal infrastructure management.
  - **Full-stack applications** are software systems that involve both frontend (user interface) and backend (server-side) deployment.

### Business Application Services [↑](#well-architected-solutions-)
Services that are ideal for managing business application needs such as customer service operations and email promotions.

#### 1. Amazon Connect
- AI-powered contact center service to efficiently set up and operate a scalable customer service call center.
- Amazon Connect provides capabilities for call routing, recording, and analytics while integrating seamlessly with other AWS services.

#### 2. Amazon Simple Email Services (Amazon SES)
- Scalable and cost-effective email service provider that can be integrated into any application for reliable, high-volume email automation.
- Helps businesses optimize the delivery of transactional and marketing emails, resulting in enhanced customer engagement.

### End-User Computing Services [↑](#well-architected-solutions-)
IT departments often need to provide remote access to resources like virtual desktops and applications.

#### 1. Amazon AppStream 2.0
- Fully managed service that streams application from the cloud directly to any compatible device.
- Includes SaaS applications and applications converted from desktop to SaaS without code revisions.
- Provides instant access to powerful software without the need for high-end local hardware.

#### 2. Amazon WorkSpaces
- Fully managed cloud-based desktop computing service.
- Employees can securely access their work environment from any device with an internet connection.
- Employees can perform the same tasks as if they were on a physical office computer, while companies can benefit from cost-efficiency and easy administration.

### 3. Amazon WorkSpaces Secure Browser (formerly Amazon WorksSpaces Web)
- Fully managed remote enterprise browser.
- Provides protected environment for employees to access private websites, SaaS application, and the public internet.
- IT departments don't need to manage specialized client software, infrastructure, or VPN connections.

### IoT Services [↑](#well-architected-solutions-)
IoT is a network of connected physical devices embedded with sensors and software that collect and exchange data over the internet.

#### 1. AWS IoT Core
- Managed cloud service used to securely connect physical devices with cloud applications.
- Create efficient IoT solutions by streamlining the complex process of ingesting, processing, and acting on device data.
- Device connections and data are secured with mutual authentication and ent-to-end encryption.
- Choose from several communication protocols.


## `AWS Well-Architected Framework` [↑](#well-architected-solutions-)

### 6 Pillars of Well-Architected Framework [↑](#well-architected-solutions-)

#### 1. Operational Excellence
- Focuses on operations, monitoring, automation, and continuous improvement.

#### 2. Security
- Protection of systems and data through best practices.
- Least Privilege and data integrity.
- IAM utilization

#### 3. Reliability
- Emphasizes recovery planning and system adaptability to meet changing demands
- Amazon ELB and Auto-Scaling Groups

#### 4. Performance Efficiency
- Encourages using the right resources for the job and adjusting as needs evolve.

#### 5. Cost Optimization
- Helps control and reduce costs  through smart provisioning and resource management.

#### 6. Sustainability
- Promotes energy-efficient design and environmentally conscious resource usage.

### AWS Well-Architected Tool (AWS WA Tool) [↑](#well-architected-solutions-)
- A free service that helps assess and improve cloud workloads based on the six key pillars.
- Offers workload reviews, milestone tracking, and custom lenses for tailored evaluations and improvement plans.
- Integrated with AWS services like AWS IAM and APIs.
- Supports team collaboration and continuous progress tracking.
- Ideal for architects, engineers, and compliance teams.
- It promotes consistent, actionable, and well-documented architecture reviews.