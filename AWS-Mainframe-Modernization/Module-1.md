# Module 1: Approach to Mainframe Migration and Modernization (Conceptual Introduction) [↑](../README.md)
- [1. Introduction](#introduction-)
- [2. The Migration Accelerated Program (MAP)](#the-migration-acceleration-program-map-)
  - [2.1. The Assess Phase](#1-assess-phase-)
  - [2.2. The Mobilize Phase](#2-mobilize-phase-)
  - [2.3. The Migrate and Modernize Phase](#3-migrate-and-modernize-)
- [3. Large Mainframe Workload By Workload Migration](#large-mainframe-workload-by-workload-migration-)


## Introduction [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
Mainframe workloads often lack the agility needed to deploy new business functions, and their 
technical complexity slows down development.

### Common Modernization Drivers
`Increase Agility`
- Agility is the ability of a business to quickly and inexpensively respond to change.

`Reduce Costs`
- Migrating Mainframe workloads to the cloud optimizes cost around 60% up to 90%.

`Mitigate Risks`
- Mainframe specialists retiring which limits the capability of maintaining.
- Risks such as running an unsupported technology.

### The AWS Approach
1. Define goals and portfolio analysis
2. Select workload and deep dive discovery
3. Select pattern and tool vendor
4. Migrate and modernize to AWS
5. Optimize and innovate
6. Perform lessons learned for process improvement

### Evolution to Agile Services
`1. Monolith`
- Mainframe Monolith has tightly coupled programs calling one another.
- The first-phase is short term migration where the monolith workload is transformed into 
  macroservices-coarsegrained business services.
- The mainframe workload legacy data store is migrated to a shared relational database for 
  better reliability.

`2. Macroservices`
- API enablement shared database.

`3. Microservices`
- Independent deployable service owning its own data for information hiding and for avoiding 
  coupling. Hence, there is one database per microservice.
- The second-phase talks about the optimization of the macroservices into microservices. 
  Microservices are extracted only when and where it makes sense.

### Migration for one Mainframe Workload
- Using proven tools for automated patterns that provide re-platforming and automated refactoring 
  capabilities to minimize the risks and accelerate the speed of migration.
- During the migration, the application code is ported or converted, then recompiled for 
  deployment on AWS.
- Data is also converted and migrated, usually to a relational database.
- There should be no manual code rewrite if possible to avoid human errors and risks.
- In many cases, the toolset provides compatibility runtimes. Sometimes they are packaged in 
  libraries. (E.g. VSAM index files are modernized to a relational databases)

### Roles in AWS Mainframe Modernization
<div style="padding:10px">
<details>
  <summary><strong>1. Business Developers</strong></summary>
  Identify opportunities, help customers set a mainframe modernization strategy, and get started.
</details>
</div>

<div style="padding:10px">
<details>
  <summary><strong>2. Delivery architects and consultants</strong></summary>
  Works together with client throughout the migration, from scoping a POC to building and 
delivering the migration plan.
</details>
</div>

<div style="padding:10px">
<details>
  <summary><strong>3. Executives and Managers</strong></summary>
  Sets the migration goals, track them, and make sure the decisions being made are aligned with 
their business goals. They are usually present in all phases of the migration.
</details>
</div>

<div style="padding:10px">
<details>
  <summary><strong>4. Software Development Engineers and Product Owners</strong></summary>
  Maintains the modernized application moving forward and are present in all phases. They are 
the ones who understand the application including interdependencies, execution flow, operating 
modele, and modernization goals.
</details>
</div>

<div style="padding:10px">
<details>
  <summary><strong>5. Solutions Architect</strong></summary>
Helps in prioritize which workloads to start with, selecting migration patterns and tools, and 
providing a sizing of the estimated target infrastructure. Commonly engaged during the assess phase.
</details>
</div>


## The Migration Acceleration Program (MAP) [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
The MAP is a comprehensive and proven cloud migration program that takes a holistic approach to 
migrations. The purpose of MAP is to reduce the risks and increase velocity for mainframe 
modernization projects.

#### The 6 pillars of MAP
1. Migration Methodology
2. AWS and partner tools
3. AWS Partners
4. AWS Professional Services
5. AWS training
6. AWS investment

---

### `1. Assess Phase` [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
- Understand the current mainframe environment and what the gaps are that need to be addressed 
  for a successful migration. This is where a case for change is created.
- During this phase, the migration readiness is considered. A directional business case is 
  defined and the application portfolio is reviewed.
- **Primary Outcome:** Statement of Work (SOW) and high-level estimate of the infrastructure and 
  migration costs.
- **Duration:** 2 to 4 weeks.
- **Cost:** Pre-sale and No cost to customer

#### Key Activities
1. Approach presentation
2. Rapid portfolio review
3. Pattern and tool guidance
4. POC scoping (source code analysis, candidate identification, and success criteria)
5. Initial cost estimates (infrastructure cost and migration cost)
6. SOW proposal for the Mobilize phase.

#### Sweet Spots
During the mainframe modernization opportunity qualification process, these components are the 
most favorable qualities for a successful mainframe migration.

**Business**

- Migration deadline within 1-3 years.
- Mainframe contract renewal within 2-4 years.
- Mainframe annual cost of >$1M
- Mainframe managed by customer
- Data center exit strategy in place
- Existing AWS customer and usage
- Mainframe skills shortage or personnel retiring
- Customer learned from past failed attempts at modernization

**Technical**

- IBM mainframe z/OS
- CICS, COBOL, PL/I, DB2, VSAM, JCL
- COBOL on any platform

#### Defining Goals
For each goal, ensure to define the:
- **Metrics** that will be used to track the goal.
- **Target date** for the goal to be achieved.
- **Milestones** to track the progress during the migration.

During alignment, all stakeholders and executives should understand the following:
- A phased modernization approach required integration tools.
- Procurement timelines need to be taken in to consideration.
- Technical then business-level modernization must be serialized.
- Each migration patterns has its trade-offs.

#### Workload selection criteria
- Define the business and technical characteristics that are considered when selecting a
  workload for migration.
- Generally speaking, the first workloads should include the following criteria:

| Business Criteria      | Technical Criteria       |
|------------------------|--------------------------|
| - Business value       | - Tool support           |
| - Time constraints     | - Mainframe stack        |
| - Regulatory demands   | - IT target stack        |
| - Agility requirements | - Complexity             |
| - Competitive pressure | - Developer availability |
| - Business strategy    | - Technology roadmap     |


#### Portfolio Analysis
- After defining the criteria, the characteristics of each workload is collected and compared.
  This helps focus on building the portfolio with the dimensions that are important.
- Building the portfolio requires the involvement of business and technical resources and is 
  time-bound to avoid having it extended for a long period of time.
- Once complete, a straightforward analysis is conducted. Workloads are ranked to see which ones 
  are aligned with the selection criteria.

<table>
<tr style="text-align:left; background-color:grey"><th><strong>NOTE:</strong></th></tr>
<tr><td>To make a portfolio, make a workload inventory on the mainframe, 
list business functions being supported, and collect technical aspects.</td></tr>
</table>

#### Migration Pattern Definition
The following are considered when defining a migration pattern.
1. **Technology stack constraints:** Niche or outdated technologies
2. **Size of the workload:** Number of Lines of codes
3. **Third-Party dependencies:** 
4. **Nonfunctional requirements:** Transactions per second, latency, high availability, security,
   and scalability
5. **Mainframe documentations:** Test cases and technical explanations
6. **Workload type:** Stabilized, slow-moving, maintenance mode.
7. **Pattern and tool support:** Source tech stack consideration.
8. **Organizational constraints:** Mainframe Business function SMEs
9. **Time constraints:** Migration deadlines and contract renewal.
10. **Business objectives and prioritization:** BusOps stuffs.
11. **IT strategy:** Cloud, managed services in AWS, elasticity, portability, and serverless.
12. **Target IT stack preferences:** Languages, frameworks, data store types, CI/CD.


#### POC Scoping
After the customer choose the best tool, the POC is scope using the selected tool. A good POC 
includes the following:
- Between 10K to 20K LOC.
- Independently testable functionalities
- Representation of general workload (online, batch, or service calls)
- Representation of data structures.
- Increased technical difficulty over the average program difficulty.
- Meaningful insights to the business.
- Entry points defined to discover dependencies.

#### Initial Cost Estimates
To build a directional business case, a target environment sizing on AWS is needed to be created 
with the aggregated Total Cost of Ownership (TCO) and migration costs.

Here a Rough Order of Magnitude (ROM) of the costs associated with a given workload or the 
entire mainframe when migrated into AWS is generated.

Migration and modernization costs can include both a tool license cost and professional services 
cost for delivering the project.

#### SOW proposal for Mobilize Phase
After an application subset has been identified as the scope for a POC and an initial cost 
estimate is determined, create a SOW that meets the technical requirements that includes the 
following:
- Detailed project scope
- Deliverables
- Expected cost of service

---

### `2. Mobilize Phase` [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
- Start laying the groundwork for the larger-scale migration, preparing the teams, and 
  validating hypothesis. 
- A POC is delivered, a Cloud Center of Excellence is formed, and a migration plan is prepared.

#### Keypoints of the Mobilize Phase
- **Primary Outcome:** Deliver the POC, Create the migration plan, Migrate and Modernize SOW
- **Duration:** 6 to 12 weeks
- **Cost:** SOW billable to customer, MAP funding.

#### Key Activities
- POC delivery
- Full scope discovery and inventory
- Full scope source code analysis
- Proposed target architecture
- Proposed operating model
- Migration acceptance criteria
- Migration Plan
- Business Case
- Migrate and Modernize SOW proposal

#### POC delivery
- This is the viability test for the customer scenario.
- It shows the tool's abilities, the deliverables quality, the speed of the tool, and also 
  validates that this is a viable path to achieve the customer's goals.
 
#### Deep-dive Workload Discovery
- A broader and deeper assessment is conducted.
- Target architectures are proposed and an operating model is created.
- Acceptance criteria is accepted and a plan is created to migrate mainframe workloads including 
  application, data, dependencies, and test strategies.

##### `Security`
- Security requirements of the application is identified. Whether it is using mainframe security 
  products.
- Examples: _Resource Access Control Facility (RACF)_, _Access Control Facility 2 (ACF2)_, Top 
  Secret, or a home-built authentication and authorization system.

##### `Interfaces`
- Interfaces of the workload are identified including the basic mapping support (BMS Maps), the 
  _Simple Object Access Protocol API (SOAP API)_, and Message Format Service Screens (MFS).

##### `Scheduling`
- Scheduling requirement on a workload scheduler is identified.
- Examples: _Tivoli Workload Scheduler_, _Control-M_, or _CA-7_.

##### `Printing`
- Printing requirements are identified

##### `Data Sources`
- Identify the data sources being used by the workload such as DB2 tables and Visual Storage Access Method (VSAM).

##### `Dependencies`
- Identify the dependencies between the selected application and other corporate applications.

##### `Code`
- Identify the source codes, copy books, and utilities being used by the application.

---

### `3. Migrate and Modernize` [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
- Start migrations to the cloud in multiple **_waves_**. At the end of each wave, the teams capture lessons learned 
  and what could be done to improve the migration for the next set of application.
- Operate the migrated applications on the cloud and modernize them as needed for additional benefits.
- Modernize the application to make the most of what the cloud has to offer, and improve the 
  migration for the next set of applications.

#### Key points
- **Primary Outcome:** Successful migration and modernization.
- **Duration:** 6 to 24 months
- **Cost:** SOW billable to the customer, MAP funding.

#### Key Activities
1. Environment Build
2. Mass migration
3. Integrations
4. System integration tests
5. Performance tests
6. User acceptance tests
7. Training
8. Go live
9. Support

#### Migration and Modernize to AWS
The activities and duration of the migration project will depend on the pattern and toolset chosen. But the overall 
activities will include the following.

###### 1. **Capture and automate tests**

Start by capturing the existing tests and automating them for functional equivalence testing and for regression 
tests after they are in AWS.

###### 2. **Migrate data and application code**

Start migrating application code and data. The activities under this depend on the pattern chosen and can include 
the following:
- Converting legacy programming languages into modern ones.
- Porting and recompiling existing codes.
- Rewriting applications from scratch or replacing them with commercial off-the-shelf products.

Data is migrated together with the code because the schema should be known by the application code.

##### 3. **Test Functional Equivalence**
Utilizing the captured and automated tests for functional equivalence after each subnet is modernized to ensure that 
the application retains the same functionality.

###### 4. Migrate scheduling, printing, security, and other integrated dependencies
The scheduling, printing, security, and managed file transfer integrated dependencies will also be migrated as a 
part of the deep-dive discovery.

For example, you can deploy the same job scheduling solution to submit jobs in AWS or migrate from your current job scheduler entirely. 
Do this by migrating RACF, ACF2, or Top-Secret definitions into AWS Directory Service, LDAP, or Microsoft Active Directory.

##### Implement Integration Patterns
- In a phased approach, modernized and legacy workloads remain integrated by interfacing with programs that were 
previously modernized, remain on the mainframe, or by sharing common data.
- Common patterns are using message queueing, pub/sub, or APIs to interface between the cloud and the mainframe and 
  change data capture (CDC) for data synchronization.

##### Integration and User Acceptance tests
Integration testing followed by User Acceptance tests takes place after having the code, data, and integrated 
dependencies migrated into development and test environment on the cloud.

#### Production cut-over
After all testing has been done, the production cut-over begins. It can be a switch to the modernized version of the 
application, or it can follow a blue/green deployment.

#### Scalable Mechanisms

##### Modernization Pipeline
- Use a modernization pipeline where legacy artifacts such as code and data are fed into the modernization process. 
  This will output a modernized version of the code and data.

<div align="center">
  <img src="../img/modernization-pipeline.png" height="60%" width="60%"/>
</div>


#### Integration with Legacy
Integration with legacy should also use a solution that can be reused throughout the organization for other 
migrated workloads. For example, CDC synchronization mechanism allows to scale more than including the 
synchronization capability within the application code itself.

<div align="center">
  <img src="../img/integration-with-legacy.png" height="60%" width="60%"/>
</div>


#### Optimize and Innovate
The customer should take advantage of the agility benefits, reduced cost, and mitigation of risks. They can optimize 
even further and innovate using the available services on AWS.

##### 1. Refactor Remnants from Mainframe
A short-term migration brings remnants from the mainframe. This can be addressed through the CI/CD pipeline enabling 
a seamless transition and faster deployment.

#### 2. Break down macro-services into micro-services.
The tight-coupling from mainframe monolith can be converted into microservices through API or Queueing.

#### 3. Take advantage of fully managed services
Presence of fully managed services are easier to use.

#### 4. Innovate with AI and ML, IoT, and other services


## Large Mainframe Workload-by-Workload Migration [↑](#module-1-approach-to-mainframe-migration-and-modernization-conceptual-introduction-)
A large mainframe is typically composed of many workloads which contain a set of applications, middleware, 
subsystems, data stores, operating system, and hardware resources performing a cohesive set of business functions.

- A workload often has one data store (DB2 or VSAM) and is supported by one transaction monitor (CICS).
- Large mainframe run multiple workloads in parallel. Each mainframe workload is migrated separately. This means 
  that each workload has dedicated resources for computing and data storage on the AWS side.
- Some workload use AWS EC2 instances, containers, or AWS Lambda. Some workloads can run on AWS Mainframe 
  Modernization fully managed runtime. 

### Risk Minimization for Large Mainframe Migration
#### 1. Start Small
- Break down mainframe into workloads.
- Migrate workloads in separate projects, not in a big bang.
- Achieve business benefits for each project.
- Use agile and lean delivery team for each project.
- Learn and develop best practices for quick scaling.

#### 2. Migrate Quickly
- Use proven migration accelerators for short-term value.
- Automate to minimize technical risks with no manual rewrite.
- Automate to avoid increasing duration, cost, and human risk.

#### 3. Optimize
- Incremental transitions with **_Cloud Native Maturity Model_**:
  - From COBOL to Java or polyglot
  - From IaaS to cloud-centered
  - From monolith to microservices
  - From large database to fit-for-purpose data stores

-----------

## NEXT MODULE: [Getting Started with AWS Mainframe Modernization Service](Module-2.md)