# IAM - Access Control Deep Dive

<div>
<details>
<summary>1. General Ideas</summary>

## Important
- User access points are called API endpoints.
- Every action taken in the AWS account is via APIs.
- All the API endpoints support HTTP and TLS encryption during the transmission to protect request/response from being viewed in transit.
- No matter the means used to access AWS, each API request is authenticated and authorized via IAM and recorded by AWS CloudTrail as it crosses the AWS API interface.

## Specifying Principals in a Policy

### 1. AWS Accounts
- When used as the principal in a policy, authority is delegated to the account within that account.
- The permission in the policy statement can be granted to all identities, including IAM users and roles in that account.
- Specified using ARN or a shortened form that consists of the aws prefix followed by the account number

```json
{"Principal": {"AWS": "arn:aws:iam:123456789012:root" } }
```
```json
{ "Principal": { "AWS": "123456789012" } }
``` 

### 2. IAM Users
- When one principal is mentioned in the element, permission is granted to each principal.
- This is a logical OR and not a logical AND because authentication is done one principal at a time.
- The username is case-sensitive. Wildcard (*) is cannot be used.

```json
{"Principal": {"AWS": "arn:aws:iam:123456789012:user/myUserName"} }
```

```json
{
  "Principal": {
    "AWS": [
      "arn:aws:iam:123456789012/username1",
      "arn:aws:iam:123456789012/username2"
    ]
  }
}
```

### 3. Federated Users
- Manage identities outside of AWS using Identity Provider (IdP) and give permissions to use AWS resources in the account.
- IAM supports SAML-based IdPs and web identity providers such as Login with Amazon, Amazon Cognito, Facebook, or Google.

```json
{
  "Principal": { "Federated": "www.amazon.com" }
}
```

```json
{
  "Principal": { "Federated": "arn:aws:iam::123456789012:saml-provider/provider-name" }
}
``` 

### 4. IAM Roles
Delegate access to users, applications, or service that does not usually have access to AWS resources

```json
{"Principal":  { "AWS":  "arn:aws:iam:123456789012:role/<role-name>"} }
```

### 5. AWS Services
- IAM roles that can be assumed by an AWS Service is called **Service roles**.
- Service roles must include a **trust policy**, which are resource-based policies that are attached to a role that define which principals can assume the role.
- A **Service Principal** is an identifier that is used to grant permissions to a service.
- The common format of an identifier is `long_service_name.amazonaws.com`.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": [
          "elasticmapreduce.amazonaws.com",
          "glue.amazonaws.com"
        ]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```




</details>
</div>