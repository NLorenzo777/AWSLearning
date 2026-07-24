# AWS CLI Cheatsheet

- [Configuration Commands](#configuration-commands-)
- [CloudWatch Commands](#cloudwatch-commands-)
- [EC2 Commands](#ec2-commands-)
- [S3 Commands](#s3-commands-)
- [IAM Commands](#iam-commands-)
- [VPC Commands](#vpc-commands-)
- [Lambda Commands](#lambda-commands-)
- [Database Commands](#database-commands-)
- [ElastiCache Commands](#elasticache-commands-)

## Configuration Commands [^](#aws-cli-cheatsheet)
- `aws config get region`: returns the region currently in.
- `aws configure`: will set up the current user credential.

----------------------------------------------------------------------
## CloudWatch Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Check alarm history</summary>

```bash
aws cloudwatch describe-alarm-history --alarm-name "High-CPU"
```
</details>

<details>
<summary>Update threshold or actions</summary>

```bash
aws cloudwatch put-metric-alarm --alarm-name "High-CPU" --threshold "85"
```
</details>

<details>
<summary>Delete a CloudWatch alarm</summary>

```bash
aws cloudwatch delete-alarms --alarm-names "High-CPU"
```
</details>

<details>
<summary>Create a SNS topic</summary>

```bash
aws sns create-topic --name OpsAlerts
```
```text
// response be like
arn:aws:sns:us-east-1:123456789012:OpsAlerts
```
</details>

<details>
<summary>Subscribe to an endpoint</summary>

```bash
aws sns subscribe \
 --topic-arn arn:aws:sns:us-east-1:123456789012:MyOpsAlerts \
 --protocol email \
 --notification-endpoint elkins@example.com
```
</details>

<details>
<summary>Enable CloudWatch Agent</summary>

```bash
sudo systemctl enable amazon-cloudwatch-agent
```
</details>

----------------------------------------------------------

## EC2 Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Modify volume type and IOPS</summary>

```bash
aws ec2 modify-volume \
-- volume-id vol-1234567890abcdef0 \
-- volumetype io2 \
-- iops 10000
```
</details>

<details>
<summary>Enable Multi-attach for supported volumes</summary>

```bash
aws ec2 modify-volume \
--volume-id vol-1234567890abcdef0 \
--multi-attach-enabled
```
</details>

<details>
<summary>Create AMI with instance store</summary>

```bash
aws ec2 register-image \
--name "app-with-instance-store" \
--block-device-mappings '[
  {
    "DeviceName": "/dev/xvdb"
    "VirtualName": "ephemeral0"
  }
]'
```
</details>

<details>
<summary>Running an EC2 Instance</summary>

```bash
aws ec2 run-instances \
--image-id ami-xxxxxxxx \
--count 1 \
--instance-type t2.micro
```
</details>

<details>
<summary>Getting the Available Volumes in a region</summary>

```bash
aws ec2 describe-volumes --region us-east-1 --query 'Volumes[*].[VolumeId,State,AvailabilityZone]' --output table 
```
- `--output` can be table, json, or xml
</details>

<details>
<summary>Deleting a Volume in a region</summary>

```bash
aws ec2 delete-volume --volume-id 'vol-xxxxxxxxxxxxxxxxx' --region us-east-1
```
- **Deletion is irreversible, ensure that data are backed-up using snapshots**
</details>

<details>
<summary>Create a Load Balancer</summary>

```bash
aws elbv2 create-load-balancer \
--name MyLoadBalancer \
--subnets subnet-12345 subnet-67890 \
--security-groups sg-12345 \
--scheme internet-facing \
--type application #default type 

--
```
</details>


----------------------------------------------------------------------
## IAM Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Get List of IAM users in a region</summary>

```bash
aws iam list-users --profile <optional>
```

#### Response
```json
{
"Users": [
    {
        "Path": "/",
        "UserName": "Admin",
        "UserId": "XXXXXXXXXXXXXXXXXXXXX",
        "Arn": "arn:aws:iam::388752792305:user/Admin",
        "CreateDate": "2021-01-28T13:44:15+00:00"
    }
]
}
```

</details>

<details>
<summary>Create a Policy</summary>

```bash
aws iam create-policy \
--policy-name <name goes here> \
--policy-document file://<file name goes here>
```
</details>

<details>
<summary>Attaching a Policy to a User</summary>

```bash
aws iam attach-user-policy \
--policy-arn arn:aws:iam::aws:policy/AdministratorAccess \
--user-name MyUserName
```

</details>

----------------------------------------------------------------------

## S3 Commands [^](#aws-cli-cheatsheet)
<details>
<summary>Creating a S3 Bucket</summary>

```bash
aws s3api create-bucket \
-- bucket <name of the bucket> \
-- region <name of the region>
```

</details>

<details>

<summary>Creating an S3 bucket - example</summary>

```bash
aws s3api create-bucket \
--bucket my-unique-bucket-name \
-- region us-east-1 #or other region
```

If successful, this will return a JSON response.
```text
{
    "Location": "/my-unq-bckt-789",
    "BucketArn": "arn:aws:s3:::my-unq-bckt-789"
}

```
</details>

<details>

<summary>Upload a file in S3 Bucket</summary>

```bash
aws s3 cp <source> <target>
```
</details>

## VPC Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Creating a VPC</summary>

```bash
aws ec2 create-vpc \
--cidr-block 10.0.0.0/16 \
--tag-specifications "ResourceType=vpc,Tags=[{Key=Name,Value=MyVpc}]"
```
</details>


<details>
<summary>Retrieve VPC Ids</summary>

```bash
aws ec2 describe-vpcs --filters "Name=tag:Name,Values=MyVpc" \
--query "Vpcs[0].VpcId"
--output text
```
</details>

<details>
<summary>Delete VPC</summary>

```bash
aws ec2 delete-vpc --vpc-id <vpc id>
```
</details>

--------------------------------------------------------
## Lambda Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Create a Lambda Function</summary>

```bash
aws lambda create-function \
--function-name MyFunction \
--runtime nodejs18.x \
--zip-file fileb://my-function.zip \
--handler my-function.handler \
--role arn:aws:iam::xxxxxxxxxxxx:role/service-role/MyFunction-role-tges6bf4
```

</details>

--------------------------------------------------------

## Database Commands [^](#aws-cli-cheatsheet)

<details>
<summary>Create a DynamoDB Table</summary>

```bash
aws dynamodb create-table \
--table-name MyTableName \
--attribute-definition AttributeName=MyPrimaryKey,AttributeType=S \
--key-schema AttributeName=MyPrimaryKey,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

</details>

<details>
    <summary>Put an Item in a DynamoDB table</summary>

```bash
aws dynamodb put-item \
--table-name my_table_name \
--item '{
"country_code": {"S": "US"},
"country_name": {"S": "United States"} }' \
--region us-east-2 \
--return-consumed-capacity TOTAL
```
</details>

<details>
<summary>Updating an Item in a DynamoDB table</summary>

```bash
aws dynamodb update-item \
--table-name my_table_name \
--key '{
"country_code": {"S": "US"},
"country_name": {"S": "United States"}}' \
--update-expression "SET primary_language = :newval" \
--expression-attribute-values '{":newval":{"S":"english"}}' \
--region us-east-2 \
--return-values ALL_NEW
```
</details>

<details>
    <summary>Query a DynamoDB table</summary>

```bash
aws dynamodb query \
--table-name my_table_name \
--key-condition-expression "country_code" = ":code" \
--expression-attribute-values '{":code": {"S": "US"}}' \
--region us-east-2 --output text
```
</details>


<details>

<summary>Create a Database (RDS)</summary>

```bash
aws rds create-db-instance \
--db-instance-identifier <name of db instance> \
--db-instance-class db.t3.micro \
--engine postgresql \
--master-username postgres \
--master-user-password postgres \
--allocated-storage <number>
```

</details>

------
## ElastiCache Commands [^](#aws-cli-cheatsheet)

<details>
    <summary>Create a Cache Subnet Group</summary>

```bash
aws elasticache create-cache-subnet-group \
  --cache-subnet-group-name "subnet-group-redis-cluster-mode-enabled" \
  --cache-subnet-group-description "Subnet group for Amazon ElastiCache for Redis with Cluster Mode Enabled" \
  --subnet-ids <subnet01> <subnet02> <subnet03>
```

#### Running this command generates a JSON response

```json
{
  "CacheSubnetGroup": {
    "CacheSubnetGroupName": "subnet-group-redis-cluster-mode-enabled",
    "CacheSubnetGroupDescription": "Subnet group for Amazon ElastiCache for Redis with Cluster Mode Enabled",
    "VpcId": "vpc-abcd1234",
    "Subnets": [
      {
        "SubnetIdentifier": "subnet-012345678abcdefghi",
        "SubnetAvailabilityZone": {
          "Name": "us-east-1a"
        }
      },
      {
        "SubnetIdentifier": "subnet-123456789abcdefghi",
        "SubnetAvailabilityZone": {
          "Name": "us-east-1b"
        }
      },
      {
        "SubnetIdentifier": "subnet-234567890abcdefghi",
        "SubnetAvailabilityZone": {
          "Name": "us-east-1c"
        }
      }
    ],
    "ARN": "arn:aws:elasticache:us-east-1:111111111111:subnetgroup:subnet-group-redis-cluster-mode-enabled"
  }
}
```
</details>





