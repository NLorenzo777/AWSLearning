# AWS Global Infrastructure and Reliability [↑](../README.md#1-aws-cloud-practitioner-notes)

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

## `AWS Regions` [↑](#aws-global-infrastructure-and-reliability-)
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

## `Availability Zones (AZs)` [↑](#aws-global-infrastructure-and-reliability-)
- One or more data centers group together with redundant power, network, and connectivity in a region.
- located tens of miles apart from each other.

---
**Recommended:** A best practice is to run across at least two AZs in a region.

---

## `Edge Locations` [↑](#aws-global-infrastructure-and-reliability-)
A site that Amazon CloudFront uses to store cached copies of content closer to customers for faster delivery.

Cache a copy locally that is closed to customers/clients.

### Amazon CloudFront
- Is a Content Delivery Network (CDN) of AWS
- Uses Edge locations all around the world to help accelerate communications with users.
- When a customer requests from a certain location, CloudFront retrieves the file from the cache.
  in the edge location and delivers the file to the customer.

### Amazon Route 53
- A Domain Name System (DNS) owned by Amazon.
- Helps direct customers to the correct web locations with low-latency delivery.

### Amazon Outposts
- Install a mini operational region directly in privately owned data center.
- Owned and operated by AWS but isolated within the building.

## `Provisioning AWS Resources` [↑](#aws-global-infrastructure-and-reliability-)
- Every action in AWS is an API call.

### 1. AWS Management Console
- Browser based.
- Manage AWS resources visually.
- Useful for test environments, view AWS bills, view monitoring, work with non-technical resources.
- Great for learning and providing visualization for the user.

### 2. AWS Command Line Interface (CLI)
- For a more systematic/programmatic approach
- Make API calls using the terminal on the machine.
- Makes action scriptable and repeatable.
- Can be run automatically, scheduled, or triggered.
- Can be used to launch an Amazon EC2 instance, connect EC2 instance to specific Auto Scaling group.

### 3. AWS Software Development Kits (SDKs)
- Interact with AWS resources through various programming languages.
- Makes easy for developers to create programs that use AWS without using the low level APIs.
- Includes C++, Java, .NET, and more.

### 4. Various Other Tools
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
