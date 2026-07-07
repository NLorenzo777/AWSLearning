<html lang="eng">

[//]: # (<link rel="stylesheet href="styles.css">)

# Scaling Serverless Architectures [^](../../README.md#3-aws-certified-developer-associate)
Build today with tomorrow in mind

## Scaling Best Practices
- Separate application and database
- Take advantage of the AWS Global Cloud Infrastructure
- Identify and avoid heavy lifting
- Monitor for percentile
- Refactor as you go

## Concurrency
- **Concurrency** is the number of Lambda invocations that can be run at the same time.
- If the number of requests for invocations exceeds the account or Lambda function concurrency limit, requests are throttled.

> Concurrency = (request rate) * (average duration of a function)

> If the available concurrency is exceeded, requests will be throttled.

- With **asynchronous event source**, there will be two retries for a failed or throttled request.
- For a **synchronous event source**, there are no retries built in.

### Streaming Event Sources
- In Streaming event sources (like Amazon Kinesis Data Streams) concurrency is measured by the number of shards.
- There is a limit of one concurrent Lambda invocations per shard.
- Lambda will continue to retry a record until the record is successfully processed for most streaming services or the retention period of the record expires.
  - This means that if one record in a batch fails, the whole batch of records and by extension the shard serving that batch is help up until retention period expires.

### Polling Event Sources
Polling event sources like Amazon SQS adjust concurrency depending on the depth of messages in the queue, up to the function or account limit

## Scaling Considerations

</html>