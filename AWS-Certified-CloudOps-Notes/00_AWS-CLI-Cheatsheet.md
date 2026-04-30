# AWS CLI Cheatsheet

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