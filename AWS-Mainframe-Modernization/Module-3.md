# Module 3: Mainframe Modernization Patterns and Best Practices [↑](../README.md)
This module presents patterns as a toolbox for use in modernizing with AWS.

The two pattern families are geared toward moving workloads off the mainframe, or augmenting the mainframe workloads.

### `Roles and Responsibilities`
Below is how the roles and responsibilities interact with **short-term migration and modernization patterns and mainframe augmentation patterns**.

- **Business Developer**
  - Describes the strategy at high-level for customer executives.
  - Explain how the AWS approach is focused mostly on customer goals and uses the best pattern based  on those goals.
  - Engage mostly on the Assess phase of MAP.
- **Delivery Architect and Consultant**
  - Considers these options when designing the modernization plan and architecture for each of the customer's workloads (during the Mobilize phase).
  - Ensures the specific business goals and technical constraints are addressed.
- **Executive and Manager**
  - Ensures all the requirements are in place for the migration to start and complete successfully, including the right partner and AWS ProServe.
- **Software Development Engineers and Product Owner**
  - Understands how each reflects into the modernized application architecture, technology stack, KPIs, and maintenance in its target environment.
- **Solutions Architect**
  - Map these strategies for the customer needs, helping define the target architecture using the pattern with the best fit for their first workloads during the Assess phase.

## Mainframe Modernization Patterns [↑](#module-3-mainframe-modernization-patterns-and-best-practices-)
There are two families of patterns: [Migration and Modernization](#migration-and-modernization) and [Augmentation](#augmentation)

-----

#### `Migration and Modernization`
- Move the mainframe workloads in a 1-year to 2-year time frame.
- Shorter duration minimizes risks and provides faster ROI.

| Details                                | Description                                                                       |
|----------------------------------------|-----------------------------------------------------------------------------------|
| **Hardware emulator rehosting**        | The entire software stack is moved as-is.                                         |
| **Mainframe-compatible replatforming** | Code is ported and recompiled onto a mainframe-compatible runtime.                |
| **Automated refactoring**              | Code and data are automatically converted and refactored to a cloud-native stack. |
| **Modern middleware replatforming**    | Applications and data are migrated to similar modern middleware on AWS.           |


#### `Augmentation`
- Keep the mainframe and benefit from the AWS value proposition in parallel.
- Extend the mainframe workloads capabilities through integration with AWS.


| Details                          | Description                                                                                                                                                                                               |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Data Analytics**               | Customer use data replication techniques between the mainframe data stored and AWS, allowing to use AWS services and available partner tools to do analytics and get insights from mainframe data on AWS. |
| **New channels & New Functions** | Customer use AWS to augment their mainframe workloads with new channels, such as mobile or voice, and new features using AWS services.                                                                    |
| **Development and test**         | Customers offload and scale mainframe development and test environment on AWS for more agility and cost reduction.                                                                                        |
| **Backup and Archival storage**  | Customers replace their backup and archival storage (such as virtual tape hardware) with cost-optimized cloud storage backup solutions.                                                                   | 

-----

<table>
  <tr>
    <th style="text-align:left; background-color:grey; color:black; width:750px">Note:</th>
  </tr>
  <tr>
    <td>Within short-term migration and modernization patterns, this training focuses on patterns that move the mainframe workloads within a 1-year to 2-year time frame. 
Manual rewrite or manual reengineering do not appear in this course because typical mainframe workloads with millions of lines of code take a lot of time to migrate and are risky. 
    </td>
  </tr>
</table>

### Mainframe Strategies
Mainframe migration and modernization differ from the **Six Rs** migrations and modernization strategies used for distributed x86-based.

Two main reasons for the difference:
1. Different hardware architectures between mainframes and x86.
2. Different types of toolsets for migration and modernization.


Below are the Lift and Reuse Short-term Migration and Modernization Patterns.
These first three strategies reuse code and data with no manual code development, which reduces risks and accelerated the migration and modernization.

#### `Hardware Emulation`
Rehosting the mainframe software stack unchanged to the cloud, where the mainframe hardware instructions are emulated by software.

#### `Mainframe Compatible Replatforming`
Move and recompile application to execute mostly unchanged in a mainframe-compatible runtime.

#### `Automated Refactoring`
Converts mainframe-specific languages and data formats to modern languages and data formats, while maintaining functional equivalence.


### Repurchasing and Reengineering Strategies




