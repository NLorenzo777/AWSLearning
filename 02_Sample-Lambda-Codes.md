# Lambda Codes

<div>
<details>
<summary>get_movie.py</summary>

### `get_movie.py`

```python3
import boto3
import json

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('movies')
    
def lambda_handler(event, context):
    title = event['title']
    response = table.get_item(
        Key={'title': title}
    )
    return {
        'statusCode': 200,
        'headers': {
            'Content-Type': 'application/json'
        },
        "body": response
    }
```

</details>
</div>

<div>
<details>
<summary>update_movie.py</summary>

### `update_movie.py`

```python3
import boto3
import decimal
from decimal import Decimal

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('movies')

def lambda_handler(event, context):
    year = event['year']
    title = event['title'] if event['title'] else ''
    rating = event['rating'] if event['rating'] else '0.0'
    plot = event['plot'] if event['plot'] else ''
    response = table.update_item(
        Key={
            'title': title
        },
        UpdateExpression="set info.rating=:r, info.plot=:p",
        ExpressionAttributeValues={
                ':r': Decimal(str(rating)),
                ':p': plot
        },
        ReturnValues="UPDATED_NEW"
    )
    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "application/json"
        },
        "body": response
    }
```

</details>
</div>

<div>
<details>
<summary>delete_movie.py</summary>

### `delete_movie.py`

```python3
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('movies')

def lambda_handler(event, context):
    year = event['year']
    title = event['title']
    response = table.delete_item(
        Key={
            'title': title
        },
        ConditionExpression = "attribute_exists(info.actors)",
        ReturnValues="ALL_OLD"
    )
    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "application/json"
        },
        "body": response
    }
```

</details>
</div>












