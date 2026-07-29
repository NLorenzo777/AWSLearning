# DynamoDB [^](../../README.md#3-aws-certified-developer-associate)

<div>
<details>
<summary>1. DynamoDB Overview</summary>

## Important Basic information
- Serverless NoSQL document database
- Can handle more than 10 trillion requests per day. Support peaks of more than 20 million requests per second
- Supports key-value and document data models.
- Synchronously replicates data across three (3) AZs in an AWS Region
- Automatically scales up and down to adjust for the capacity and maintain system performance.
- Two Capacity modes: **provisioned** and **on-demand**
    - **on-demand**: Billed for every read and write that application performs.
    - **provisioned**: Specify the number of reads and writes per second.

## Technical Overview
- Uses **partition key** to find each item in the database
- Uses **sort key** to store related attributes in a sorted order. This allows multiple items to be queried as a collection.
- The **primary key** is a combination of the partition and sort key (called composite primary key). If there is no sort key, the primary key and partition key are the same.

## Tables and Partitions
- item (row), attribute (column)
- Data are stored in partitions and divides a table's item into multiple partitions based on the **partition key**
- A **Partition** is an allocation of storage for a table, backed by SSDs and automatically replicated across multiple AZs within a region.
- The partition key is also known as its **hash attribute**.

## Data Types
- **Number**
- **String**
- **Binary (Base 64 encoded)**
- Boolean
- Null
- Map `(e.g. {"key1": "value1"})`
- List `(e.g. ["item1", "item2"])`

`Number, String, and Binary are the only data types that can be a primary key`

## Basic Item Requests

### Write
- `PutItem` - Write item to specified primary key
- `UpdateItem` - Change attributes for item with specified primary key
- `BatchWriteItem` - Write a bunch of items to specified primary keys
- `DeleteItem` - Remove item associated with specified primary key

### Read
- `GetItem` - Retrieve item associated with specified primary key
- `BatchGetItem` - Retrieve items with a bunch of specified primary keys
- `Query` - For specified partition key, retrieve items matching sort key expression
- `Scan` - Get every item in the table
</details>
</div>

<div>
<details>
<summary>2. Consistency</summary>

## Consistency
- **Strongly consistent** - consistent across all involved AZs.
- **Eventually consistent** - possibility of a stale data

### Facts about Consistency
- DAX passes strongly consistent reads through but does not cache them
- Strongly consistent reads can be made via a VPC endpoint
- LSI and GSI both support eventually consistent reads
- Make two eventually consistent reads (each uip to 4KB) for one RCU.
- All successful writes are redundantly stored and durable - there is no eventual or strong consistency choice to be made for writes
- 
</details>
</div>

<div>
<details>
<summary>3. Read/Write Capacity Units</summary>


## Read/Write Capacity Units
- User must specify read and write throughput values when creating a table.
- DynamoDB reserves the necessary resources to handle throughput requirements and divides the throughput evenly among partitions.

### Read Capacity Units (RCU)
- The number of strongly consistent reads per second of items up to 4KB in size
- 1 RCU = 1 item (4kb or less) read per second

> Note: Eventually consistent reads consume half as many RCUs as Strongly consistent reads.

### Write Capacity Units (WCU)
- The number of 1KB writes per second
- 1 RCU = 1KB or less write per second

</details>
</div>

<div>
<details>
<summary>4. Secondary Indexes</summary>

## Secondary indexes
- These indexes improve the application's ability to access data quickly and efficiently
- Use to perform queries on attributes that are not part of the table's primary key.

### Local Secondary Index (LSI)
- Index that is local to a partition key
- Allows to query item with the same partition key - specified with the query.
- The total size of an item collection **cannot exceed 10GB**
- uses the table's partition key with a unique sort key. (allowed five per table)
- Can only be created when a table is created and cannot be deleted.
- Consume storage and the table's provisioned throughput.

### Global Secondary Index (GSI)
- Index is across all partition keys
- Allows to query over the entire table, across all partitions.
- It is possible to have a partition key and optional sort key that are different from the partition key and sort key of original table.
- Can be created when a table is created or can be added to an existing table and it can be deleted.
- Supports eventual consistency only.

</details>
</div>

<div>
<details>
<summary>5. DynamoDB Security</summary>

## DynamoDB Security
- Uses IAM to create and manage credentials. DynamoDB requires both authentication and permission to access tables and data.
- Access are controlled at the table and item level.
- Tables have encryption at rest by default.

</details>
</div>

<div>
<details>
<summary>6. Design Considerations</summary>

## Design Considerations

### Uniform Workloads
When you make a large number of consecutive reads or consecutive writes to a narrow range of partition keys, the same partitions are accessed repeatedly (**hot partitions**)

To achieve maximum read/write throughput, implement read and write operations as follows:
- Choose the partition key carefully to avoid hotspots
- Consider concatenating a random number or a calculated value to the partition key when writing data to ensure distribution of partition keys.
- Distribute reads and writes across multiple partitions

### Hot and Cold Data
Consider access patterns for your data. For example, you might have an Orders table with a partition key of customer id and sort key of timestamp. Your application probably accesses the latest order data most of the time. It might rarely access data about very old orders.

In such cases, consider breaking the time series data into separate tables. Store the frequently accessed “hot” data in a separate table with higher throughput. Store rarely accessed “cold” data in tables with lower throughput.

You can even move the old data to other storage options such as an Amazon S3 bucket and delete the table that contains the old data.

### Auto-Scaling in DynamoDB
The three parameters are set when Auto Scaling in DynamoDB
- Minimum Capacity
- Maximum Capacity
- Target Utilization

</details>
</div>