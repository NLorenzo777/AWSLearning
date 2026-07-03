<html lang="eng">
<head>
<title>AWS Cloud Developer Associate - MCQs</title>
</head>

<style>
    details span {
        background-color: green;
        color: black;
    }
</style>

<body>

### Time-To-Live (TTL) can be used to have DynamoDB delete expired items from a table without being charged for WCU consumption. When you set an attribute for use by TTL, what is the value you should set for that attribute to result in expiry?

- The number of seconds since last update for the item to remain in the table.
- The epoch timestamp (with unit seconds) after which the item can be removed. 
- The number of days since last update for the item to remain in the table.
- A string pattern which needs to match the TTL expression for expiry.
- A Boolean specifying true or false for expiration.

<details>
    <summary>Reveal Answer</summary>
    <span><strong>The epoch timestamp (with unit seconds) after which the item can be removed</strong></span>
</details>


### Optimistic concurrency control in DynamoDB provides a form of locking. Which is the correct description of the mechanism?

- Read, transform, conditionally write, retry as required.
- Strongly consistent write with lock option set true.
- Enable streams, check the stream to confirm no other updates are in progress, DeleteItem, PutItem.
- PutItem/UpdateItem, then strongly consistent GetItem to confirm that your change has not been overwritten.
- Conditional Write, retry, transform, read, retry.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>Read, transform, conditionally write, retry as required</strong></span>
</details>

### Which of the following are scenarios where you might select Amazon Kinesis Data Firehose for data processing? (Select THREE.)

- You want to ingest a very high volume of data and store it to Amazon Redshift.
- You want to ingest a very high volume of data in a single stream that must be processed by three consumer applications.
- You want to ingest a very high volume of data, transform its format, and store it to an Amazon Aurora database.
- You must respond to individual messages as they are received.
- You want to ingest a very high volume of data, transform its format, and store it to Amazon S3.
- You want to simplify retry handling on streaming data, and the order of records in the stream is not critical.

<details>
    <summary>Reveal Answer</summary>
 <span><strong>1, 4, and 5</strong></span>
</details>

</body>
</html>