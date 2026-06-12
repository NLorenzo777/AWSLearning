# AWS CLI Cheatsheet

- [CloudWatch Commands](#cloudwatch-commands-)
- [EC2 Commands](#ec2-commands-)
- [S3 Commands](#s3-commands-)
- [IAM Commands](#iam-commands-)

## CloudWatch Commands [^](#aws-cli-cheatsheet)
#### Check alarm history
```bash
aws cloudwatch describe-alarm-history --alarm-name "High-CPU"
```

#### Update threshold or actions
```bash
aws cloudwatch put-metric-alarm --alarm-name "High-CPU" --threshold "85"
```

#### Delete a CloudWatch alarm
```bash
aws cloudwatch delete-alarms --alarm-names "High-CPU"
```

#### Create a SNS topic
```bash
aws sns create-topic --name OpsAlerts
```
```text
// response be like
arn:aws:sns:us-east-1:123456789012:OpsAlerts
```

#### Subscribe to an endpoint
```bash
aws sns subscribe \
 --topic-arn arn:aws:sns:us-east-1:123456789012:MyOpsAlerts \
 --protocol email \
 --notification-endpoint elkins@example.com
``` 

#### Enable CloudWatch Agent
```bash
sudo systemctl enable amazon-cloudwatch-agent
```
----------------------------------------------------------

## EC2 Commands [^](#aws-cli-cheatsheet)
#### Modify volume type and IOPS
```bash
aws ec2 modify-volume \
-- volume-id vol-1234567890abcdef0 \
-- volumetype io2 \
-- iops 10000
```

#### Enable Multi-attach for supported volumes
```bash
aws ec2 modify-volume \
--volume-id vol-1234567890abcdef0 \
--multi-attach-enabled
```

#### Create AMI with instance store
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

#### Running an EC2 Instance
```bash
aws ec2 run-instances \
--image-id ami-xxxxxxxx \
--count 1 \
--instance-type t2.micro
```

----------------------------------------------------------------------
## IAM Commands [^](#aws-cli-cheatsheet)

#### List of IAM Users
```bash
aws iam list-users --profile <optional>
```

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

----------------------------------------------------------------------

## S3 Commands [^](#aws-cli-cheatsheet)

#### Creating a S3 Bucket
```bash
aws s3api create-bucket \
-- bucket <name of the bucket> \
-- region <name of the region>
```
