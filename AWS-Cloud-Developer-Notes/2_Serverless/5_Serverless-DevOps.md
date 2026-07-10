#### `PREVIOUS TOPIC:` [Scaling Serverless Architectures](4_Serverless-Scaling-Architectures.md)

-----
# DevOps in AWS [^](../../README.md#3-aws-certified-developer-associate)

<div style="padding-bottom:5px; border:3px;">
<details style="background-color:rgb(231 231 231 / 0.4);">

<summary>1. Introduction</summary>

## DevOps
- is the combination of cultural philosophies, practices, and tools that increases and organization's ability to deliver applications and services at high velocity.
- is a combination of cultural philosophies for removing barriers and sharing end-to-end responsibility.

## Benefits of DevOps

1. **Speed** - Teams move at a higher velocity and adapt to changing markets more effectively.
2. **Rapid Delivery** - Increase the frequency and pace of releases to address bugs and add features more quickly.
3. **Reliability** - Manage the quality of application and infrastructure changes to deliver at a more rapid pace while maintaining
4. **Scale** - Use automation and consistency to help reduce risk as infrastructure and development processes are scaled
5. **Improved Collaboration** - Build more effective teams under a DevOps cultural model
6. **Security** - Move quickly while retaining control and preserving compliance.


</details>
</div>

<div style="padding-bottom:5px; border:3px;">
<details style="background-color:rgb(231 231 231 / 0.4);">

<summary>2. DevOps Methodology</summary>

## 7 Core Principles of a DevOps Culture

1. Create a highly collaborative environment
2. Automate when possible
3. Focus on customer needs
4. Develop small and release often
5. Include security at every phase
6. Continuously experiment and learn
7. Continuously improve


## DevOps Practices
1. Communication and Collaboration
2. Monitoring and Observability
3. Continuous Integration (CI)
4. Continuous Delivery or Continuous Deployment (CD)
5. Microservice Architectures
6. Infrastructure as a Code

## DevOps Pipeline

1. **Code**
2. **Build** - Compile code, check code style and standards, analyze code complexity and maintainability, validate dependencies, create container images, run unit tests
3. **Test** - Functional testing, Integration testing, Regression testing, Acceptance testing, Load testing, Security testing
4. **Release** - Prepare and package the code with a specific version number
5. **Deploy** - Deploy the release to targeted environments such as test, staging, alpha, beta, or productions
6. **Monitor** - Monitor the application in production to quickly detect unusual activity or errors.

</details>
</div>

<div style="padding-bottom:5px; border:3px;">
<details style="background-color:rgb(231 231 231 / 0.4);">

<summary>3. AWS DevOps Tools</summary>

### Code Stage
- AWS tools, SDKs, and the AWS CDK

### Build Stage
- Using `AWS CodeBuild` to automatically compile source code, run tests, and produce software packages that are ready to deploy

### Deploy Stage
- Using `AWS CodeDeploy` to automate software deployments to a variety of compute services such as EC2, AWS Fargate, AWS Lambda, and on-premise servers

### Monitoring Stage
- Use `AWS X-Ray` to collect data about requests that the application serves.
- Provide tools that can be use to view, filter, and gain insights into the data to identify issues and opportunities for optimization.
- Using `Amazon CloudWatch` to monitor AWS resources and the applications being run on AWS in real time.

</details>
</div>