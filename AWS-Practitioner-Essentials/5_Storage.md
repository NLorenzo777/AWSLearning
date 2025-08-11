#### `PREVIOUS MODULE:` [Networking](4_Networking.md)

-----------
# Storages in AWS [↑](../README.md#1-aws-cloud-practitioner-notes)

- [Instance Stores](#instance-stores-)
- [Elastic Block Stores (EBS)](#amazon-elastic-block-store-amazon-ebs-)
  - [EBS Snapshots](#ebs-snapshots)
  - [Amazon Data Lifecycle Manager](#amazon-data-lifecycle-manager)
- [Amazon Simple Storage Service (S3)](#amazon-simple-storage-service-amazon-s3-)
  - [Amazon S3 Buckets](#s3-buckets)
  - [S3 Storage Classes](#amazon-s3-storage-classes)
  - [S3 Storage Lifecycle](#amazon-s3-storage-lifecycle)
- [Amazon Elastic File System (EFS)](#amazon-elastic-file-system-amazon-efs-)
  - [Amazon EFS Storage Classes](#amazon-efs-storage-classes)
- [Amazon FSx](#amazon-fsx-)
- [Additional Storage Services](#additional-storage-services-)
  - [AWS Storage Gateway](#1-aws-storage-gateway)
    - [Gateway Types](#gateway-types)
  - [AWS Elastic Disaster Recovery](#2-aws-elastic-disaster-recovery)

## `Instance Stores` [↑](#storages-in-aws-)
- Block level storage volumes that behaves like a physical hard drive.
- Unmanaged non-persistent, high-performance block storage.
- Provides **temporary block-level storage** for an EC2 instance.
- A disk storage that is physically attached to the host computer for an EC2 instance, therefore
  has the same life span as the instance.
- When the instance is stopped/terminated the data is lost as well.

## `Amazon Elastic Block Store (Amazon EBS)` [↑](#storages-in-aws-)
- Service that provides **block-level storage** volumes that can be used with EC2 instances.
- Provides persistence of data even if EC2 is stopped/terminated.
- Created by defining the configuration (such as volume size and type) and provisioning it.
- **Does not automatically resize**. It is a hard drive.
- Stores data in a single AZ. When attaching an EC2 instance, both the instance and the EBS
  volume must reside within the same AZ.

### EBS Snapshots
- A feature of EBS that takes incremental backup for the volume.
- Enable rapid creation of new volumes from existing data to quickly deploy for identical test environments that mirror production.
- The first backup taken of a volume copies all the data. Only the blocks of data that have
  been changed since the most recent snapshot are saved _(Incremental backup)_.
- _Full backup_ includes that data that has not been changed.

### Amazon Data Lifecycle Manager
- Automate the creation, retention, and deletion of EBS snapshots.
- Schedule snapshots during off-peak hours to minimize performance impact and automatically delete outdated backups to control storage costs.
- Particularly valuable for large-scale deployments where manual snapshot management would be time-consuming and error-prone.
- Reduce manual effort and establish consistent backup policies to maintain compliance requirement.
- **Create an EBS Snapshot Policy:** Using Amazon EC2 Console, API calls, AWS CLI, SDKs, or CloudFormation.
- **Exclude Volumes:** Narrow down the data to be included in the snapshot by choosing options to exclude either the root or data volume.
- **Set Custome Schedule:** Schedule when EBS Snapshots will happen.

------
`Object Storage:`
- Data storage architecture that managed data as objects in a flat address space.
- Offers unlimited scalability so it can store vast amounts of unstructured data without worrying about capacity constraints.
- Each object consists of **data**, **metadata**, and **key**.
- The data might be an image, video, text document, or file of any type.
- Metadata contains information about the data is, how it is used, size, and so on.
- The key is the unique identifier of the object.
------

## `Amazon Simple Storage Service (Amazon S3)` [↑](#storages-in-aws-)
- Service that provides **object-level storage**.
- Store and retrieve a virtually unlimited amount of data.
- An object in Amazon S3 is the fundamental unit of data storage. When a file is uploaded, it becomes an object and is **stored durably across multiple facilities within the region**.
- Each object typically includes the data itself, metadatam and a unique identifier (key).
- Store data as version controlled _objects_ (object maximum size of **5TB**).
- Everything that is stored in S3 is _private_ by default.

### S3 Buckets
- Container for storing objects in Amazon S3.
- Basic unit for access control and can hold virtually unlimited number of objects.
- Crucial role in data management by making it possible to group related objects and apply policies at the bucket level.

### Amazon S3 Storage Classes

| Storage Class / Tier                                    | Description                                                                                                                                                                                                                                                                                                                |
|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **S3 Standard**                                         | - Designed for frequently accessed data<br/> - Stores data in minimum of 3 AZs.<br/> - Provides high availability for objects.<br/> - Applicable for websites, content distribution, and data analytics.<br/> - Has a higher cost than other storage classes intended for infrequently accessed data and archival storage. |
| **S3 Standard-Infrequent Access<br/> (S3 Standard-IA)** | - Similar to S3 Standard but lower storage price but higher retrieval prices.<br/> - Ideal for infrequently accessed data.<br/> - Stores data in minimum of 3 AZs.<br/>                                                                                                                                                    |
| **S3 One Zone-Infrequent Access<br/> (S3 One Zone-IA)** | - Stores data in a single AZ<br/> - Lower storage price than standard-IA<br/>                                                                                                                                                                                                                                              |
| **S3 Intelligent Tiering**                              | - Ideal for data with unknown or changing access patterns<br/> - Requires small monthly monitoring and automation fee per object.<br/> - If an object is no accessed for 30 consecutive days, Amazon S3 automatically moves it to S3 Standard-IA tier. Once accessed, automaticall moved to S3 Standard tier.              |
| **S3 Glacier Instant Retrieval**                        | - For archived data that requires immediate access. Retrieve objects within a few ms.                                                                                                                                                                                                                                      |
| **S3 Glacier Flexible Retrieval**                       | - Low-cost storage for data archiving.<br/> - Able to retrieve objects within a few minutes to hours (1 minute to 12 hours).                                                                                                                                                                                               |
| **S3 Glacier Deep Archive**                             | - Lowest-cost object storage class for archiving.<br/> - Retrieve objects within 12 hours.<br/> - Supports long-term retention and digital preservation for data that might be accessed **once or twice a year**.<br/> - All objects are replicated and stored across at least 3 geographically dispersed AZs.             |
| **S3 Outposts**                                         | - Creates S3 buckets on Amazon S3 Outposts.<br/> - Makes it easier to retrieve, store, and access data on AWS outposts.<br/> - Works well for workloads with local data residency requirements.                                                                                                                            |

### EBS and S3 comparison

| Elastic Block Storage                             | Amazon S3                                  |
|---------------------------------------------------|--------------------------------------------|
| Up to 16 TiB in size                              | Unlimited storage (Maximum 5TB per object) |
| Persisting                                        | Write once / Read Many                     |
| Solid state by default (HDD)                      | Durable (99.999999999%)                    |
| File is divided into blocks making easy to update | Have to be updated as a whole              |
| Attached to EC2 instances and AZ level resource   | Web enabled and serverless                 |

### Amazon S3 Storage Lifecycle
Automation process to avoid manually managing storage of objects.

When a lifecycle configuration for an object or group of object is defined, there are two (2) types of actions:
1. **Transition Action:** define when objects should transition to another storage class.
2. **Expiration Action:** define when objects expire and should be permanently deleted.

**Use Cases**
- Periodic logs uploaded that might want to be deleted after a certain span of time.
- Data that changes in access frequency

------
`File Storage:`
- Provide shared file systems accessible over networks so multiple users and application can access the same data simultaneously.
- Offer scalability and flexibility to expand storage capacity as needs grow without managing physical infrastructure.
------

## `Amazon Elastic File System (Amazon EFS)` [↑](#storages-in-aws-)
- Fully-managed, scalable file storage for use with AWS cloud and on-premise resources.
- Operates using Linux Network File System (NFS) protocol.
- **Multiple Redundancy:** Regional resource, stores data in and across multiple AZs.
- **Elastic Storage:** Automatically scales to petabytes as files are added or removed without disrupting applications.
- **Shared Access:** Designed to support a wide variety of workloads and multiple instances can access the data simultaneously.

### Amazon EFS Storage Classes
Configure file systems quickly without any minimum fee or setup cost. Pay only for the storage used and choose from a range of storage classes designed to fit use case:

1. **EFS Standard and EFS Standard-Infrequent Access (Standard-IA)**
    - Multi-AZ resilience and highest level of durability and availability
    - Higher cost associated due to higher availability and durability.
2. **EFS One Zone and EFS One Zone-Infrequent Access**
    - Additional savings by saving data in single AZ.
3. **EFS Archive Storage**
    - Offers a storage price up to 50% lower compared to EFS IA, providing a more cost-optimized experience for cold, rarely-accessed data.

## `Amazon FSx` [↑](#storages-in-aws-)
- Fully-managed file storage services for popular file systems like Windows, Lustre, and NetApp ONTAP.
- **File System Integration:** Supports industry-standard file system protocols, allowing convenient integration with existing applications, workflows, and development tools.
- **Managed Infrastructure:** Reduces the complexity of managing infrastructure while delivering the features and capabilities of traditional file systems.
- **Scalable Storage:** Adjusts resources dynamically, eliminating the need for complex capacity planning and manual infrastructure management.
- **Cost Effective**


## `Additional Storage Services` [↑](#storages-in-aws-)

### 1. AWS Storage Gateway
- A fully-managed, hybrid-cloud storage service that provides on-premises access to virtually unlimited cloud storage.
- Used to extend local storage to the cloud while maintaining low-latency access to frequently used data.
- **Benefits:**
    - **Seamless Integration:** Enables smooth connectivity between on-premises applications and AWS Cloud storage, preserving existing workflows and minimizing disruptions.
    - **Improved Data Management:** Provides centralized management of hybrid storage environments, enhancing accessibility, security, and compliance.
    - **Local Caching:** Locally keeps frequently accessed data for quick access while managing less-used data in the cloud.
    - **Cost Optimization:** Reduce on-premise storage costs by using cloud storage for data archiving, backup, and disaster recovery purpose.

#### Gateway Types

1. **Amazon S3 File Gateway**
   - Bridges local environment with Amazon S3.
   - Provides on-premise applications with access to virtually unlimited cloud storage through **familiar file protocols**.
   - Makes it possible to store and retrieve cloud objects using **familiar file operations**.
   - When you deploy an S3 File Gateway, it appears to your local systems as a standard file server. 
   Files written to this server are automatically uploaded to Amazon S3 while maintaining local access to recently used data **through intelligent caching**.
   
2. **Volume Gateway**
    - Create virtual storage volumes while maintaining local access to data.
    - Functions as a bridge between on-premise infrastructure and AWS Cloud storage by presenting cloud data as **iSCSI volumes** that can be mounted by existing applications.
    - Operates **2 main configurations:**
      - **_Cached volume mode:_** Stores primary data in the cloud while frequently accessed data is cached locally for low-latency access.
      - **_Stored volume mode:_** Locally keeps complete dataset while asynchronously backing up to the cloud as EBS Snapshots.

3. **Tape Gateway**
   - Enables replacing of physical tape infrastructure with virtual tape capabilities while benefitting from the durability and scalability of AWS Cloud Storage.
   - Provides an interface that works with existing tape backup software, making the transition from physical tapes to cloud storage seamless.
   - When you deploy a Tape Gateway, it presents itself to your backup applications as standard tape hardware. Your backup software writes data to these virtual tapes just as it would to physical tapes and stored in Amazon S3.

### 2. AWS Elastic Disaster Recovery
A fully-managed service that streamlines recovery of physical, virtual, and cloud-based servers into AWS.

-----------

#### `NEXT MODULE:` [Databases](6_Databases.md)

-----------