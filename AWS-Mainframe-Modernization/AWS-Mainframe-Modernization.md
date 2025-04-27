# AWS Mainframe Modernization

## 1. Approach to Mainframe Migration and Modernization
Mainframe workloads often lack the agility needed to deploy new business functions, and their 
technical complexity slows down development.

#### Common Modernization Drivers
`Increase Agility`
- Agility is the ability of a business to quickly and inexpensively respond to change.

`Reduce Costs`
- Migrating Mainframe workloads to the cloud optimizes cost around 60% up to 90%.

`Mitigate Risks`
- Mainframe specialists retiring which limits the capability of maintaining.
- Risks such as running an unsupported technology.

#### The AWS Approach
1. Define goals and portfolio analysis
2. Select workload and deep dive discovery
3. Select pattern and tool vendor
4. Migrate and modernize to AWS
5. Optimize and innovate
6. Perform lessons learned for process improvement

#### Evolution to Agile Services
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

#### Migration for one Mainframe Workload
- Using proven tools for automated patterns that provide re-platforming and automated refactoring 
  capabilities to minimize the risks and accelerate the speed of migration.
- During the migration, the application code is ported or converted, then recompiled for 
  deployment on AWS.
- Data is also converted and migrated, usually to a relational database.
- There should be no manual code rewrite if possible to avoid human errors and risks.
- In many cases, the toolset provides compatibility runtimes. Sometimes they are packaged in 
  libraries. (E.g. VSAM index files are modernized to a relational databases)

#### Roles in AWS Mainframe Modernization
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


### The Migration Acceleration Program (MAP)
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

#### 1. Assess Phase
- Understand the current mainframe environment and what the gaps are that need to be addressed 
  for a successful migration. This is where a case for change is created.
- During this phase, the migration readiness is considered. A directional business case is 
  defined and the application portfolio is reviewed.
- **Primary Outcome:** Statement of Work (SOW) and high-level estimate of the infrastructure and 
  migration costs.
- **Duration:** 2 to 4 weeks.

##### Key Activities
1. Approach presentation
2. Rapid portfolio review
3. Pattern and tool guidance
4. POC scoping (source code analysis, candidate identification, and success criteria)
5. Initial cost estimates (infrastructure cost and migration cost)
6. SOW proposal for the Mobilize phase.

#### Workload selection criteria
- Define the business and technical characteristics that are considered when selecting a 
  workload for migration.

#### Portfolio Analysis
- After defining the criteria, the characteristics of each workload is collected and compared. 
  This helps focus on building the portfolio with the dimensions that are important.
- Time-bound to avoid having it extended for a long periods of time.
- 

`2. Mobilize`
- Start laying the groundwork for the larger-scale migration, preparing the teams, and 
  validating hypothesis. A POC is delivered, a Cloud Center of Excellence is formed, and a 
  migration plan is prepared.

`3. Modernize`
- Start migrations to the cloud in multiple **_waves_**.
- Operate the migrated applications on the cloud.
- Modernize the application to make the most of what the cloud has to offer, and improve the 
  migration for the next set of applications.