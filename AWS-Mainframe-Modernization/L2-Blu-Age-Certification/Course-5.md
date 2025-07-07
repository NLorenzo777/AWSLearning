# Course 5: Reviewing te Customer's Codebase with AWS Blu Insights Advanced Features [↑](../../README.md)

## Codebase analysis & POC

### `What is a typical project`
**zOS Technologies and their AWS Blu Insights location:**

- **Database:**
  - DB2 (IBM Database 2) - SQL files
  - VSAM (Virtual Storage Access Method) - LISTCAT file
- **Code:**
  - COBOL (COmmon Business Oriented Language) - COB and CPY files
- **Transaction Management System:**
  - CICS (Customer Information Control System) - CSD file
- **Display:**
  - BMS (Basic Mapping Support) - BMS files
- **Scripts:**
  - JCL (Job Control Language) - JCL and PROC files
- **Control Cards:**
  - CTL or Unknown because this can be almost anything.

**Application features and related artefacts**

- Batch (JCL, PROC, COB, CPY, LISTCAT, CTL)
- Screens (CSD, COB, CPY, BMS)
- Transaction: application services that are called externally (e.e. an already modern front-end)
  - Through a broker (typically IBM MQ)
  - Through CICS Transaction gateway
  - Through custom mechanism
  - COB, CPY

### `Codebase Analysis`
- Identify the type of application based on the customer description.
- Verify that the received artefacts match the description. (e.g. batch application means JCLs)
- Identify in the codebase the parts that corresponds to the customer description.
- Use complexity analysis to identify the potential pain points and inquire about them.
- Focus on the things that stand out (e.g. another language, a huge proportion of something, etc.)
- Study the coding style by analyzing the code and the graphs:
  - Highly connected graph.
  - Huge programs: business services (good architecture but complex POC scoping)
  - Loosely coupled graph
- Start identifying and removal of dead coe by pruning the codebase.


### `Code Pruning`
- Entry points are the elements externally called
  - JCL Jobs (JCL) typically called by the scheduler.
  - CICS transaction called by CICS (trigger COBOL associated programs)
  - Externally called transaction (trigger COBOL associated programs)

- Process:
  - Ask the customer for the whole codebase and iterates until it is complete
  - List all the still active entry points (by the customer, using existing logging mechanisms)
  - Use dependencies to keep only those endpoints and all their dependencies.
  - The rest of the code is supposed "Dead" and can be removed from the project.
  - The ROM can now be computed or refreshed in order to be accurate and up-to-date.

### `POC Goals`
- Demonstrate the process on something real, that the customer can manipulate, test, etc.
- Validate and finalize the project plan, budget, schedule.
- Useful for both parties before the final engagement.
- Tackle customer worries by handling them quickly.
- Allows to start diving deeper and deeper in the customer legacy codebase.
- Processes begin to be put in place with no rush (exchange platform, meetings, deliveries)

### `POC Scoping`
- Representative of the whole project workload
  - at the data level (database, files)
  - at the code level (batch, screens, transactions)
  - at the complexity level (not too easy, not too hard)
  - at the volume level (1% - 5% LOC)
- Must be business meaningful without bringing too much code
- Done quickly (10-12 weeks duration)
- Must deal with some of the pain points, specificities, if present so that confidence is established even in those cases

### `POC Test Cases`
Same as project test cases

- In all cases:
  - Database extraction before the test case execution
  - Database extraction after the test case execution
  - Performance information
- Screen Test Case:
  - Capture of the screens while executing positive and negative test cases
- Batch Test Case:
  - Batch input files at the start of the job
  - Batch output files at the end of the job
  - Job log
- Transaction (Backend Service) test case
  - Capture of messages (in and out) when called by other system

### `Complexity Analysis`
Things to look for:
- A lot of complexity in few LOC.
- A low complexity in a lot of LOC.
- Anything outside the diagonal basically.

### `AWS Blu Insight Labels`
- Allow to store knowledge on files.
- Create as many as needed.
- Label all the complex files.
  - Go to Assets > Statistics
  - Write a query to filter the files that has a high complexity depending on the graph.
    - For example, `cyclomatic complexity > 120`
  - Select all the filtered files.
  - Edit properties and add label.
