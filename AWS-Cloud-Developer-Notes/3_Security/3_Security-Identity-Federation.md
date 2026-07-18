#### [Access Delegation](2_Security-Access-Delegation.md)
----
# IAM - Access Federation Deep Dive [^](../../README.md#3-aws-certified-developer-associate)

<div>
<details>
<summary>1. Federating Users in AWS</summary>

## Federation Process

1. **Trust**
   - A trust relationship is configured between the Identity Provider (IdP) and the service provider.
   - The service provider trusts the IdP to authenticate users and relies on the information provided by the IdP about the users.
2. **IdP**
   - After authenticating a user, the IdP returns a message (called _assertion_) containing the user's sign-in name and other attributes that the service provider needs to establish a session with the user and to determine the scope of the resource access.
3. **Service Provider**
   - Receives the assertion from the user.
   - Validates the level of access requested
   - Sends the user the necessary credentials to access the desired resources.
4. **Access Granted**
   - With the right credentials from the service provider, the user now has direct access to the requested resources via an established session

AWS supports commonly used open identity standards, including Security Assertion Markup Language 2.0 (SAML), OIDC, and OAuth 2.0.

## AWS Services that support identity federations
- `AWS IAM Identity Center` - SSO to AWS accounts and centrally managed access to resources
- `AWS IAM` - Fine-grained access to AWS
- `Amazon Cognito` - Access to Web and mobile apps

</details>
</div>

<div>
<details>
<summary>2. SAML-Based Federation</summary>

#### `Quick Link:` [SAML 2.0-based Federation Overview](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html)

## The `AssumeRoleWithSAML` Request
- The SAML IdP must be configured to issue the claims that the AWS requires before the **AssumeRoleWithSAML** request can be called.
- Additionally, IAM must be used to create a SAML provider entity in the AWS account that represents the identity provider.
- an IAM role must be created that specified the SAML provider in the trust policy of the IAM policy that represents the IdP.

![img_17.png](img_17.png)

> `&RoleArn` - ARN of the role that the federated user is assuming

> `&PrincipalArn` - ARN of the SAML provider configured in the IAM that describes the IdP.

> `&SamlAssertion` - Base-64 encoded SAML authentication response that the IdP provides. The Service Provider uses this response to grant access to resources.

### Optional Parameters

- **Duration Seconds**
  - Role session lasts ranging from 900 seconds to the maximum session of 12 hours.
  - The default is 3600 seconds.
  - Session depends also on the time specified in the SAML authentication response's `SessionNotOnOrAfter` value (whichever is shorter).
- **Policy**
  - Includes the IAM policy that you want to use as an inline session policy.
  - The resulting session's permissions are the intersection of the role's identity-based policy and the session policies.
- **PolicyArns.member.N**
  - Includes the ARNs of the IAM managed policies that you want to use as managed session policies.
  - The policies must exist in the same account as the role.
  - Up to 10 managed policy ARNs.

</details>
</div>
