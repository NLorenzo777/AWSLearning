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

