# Pricing and Support [↑](AWS-Practitioner-Essentials-Notes.md)

- [AWS Pricing Concepts](#aws-pricing-concepts-)
- [AWS Pricing and Billing Services](#aws-pricing-and-billing-services-)
  - [AWS Organizations](#aws-organizations)
  - [AWS Billing and Cost Management Dashboard](#aws-billing-and-cost-management-dashboard)
  - [AWS Budgets](#aws-budgets)
  - [AWS Cost Explorer](#aws-cost-explorer)
  - [AWS Pricing Calculator](#aws-pricing-calculator)

## `AWS Pricing Concepts` [↑](#pricing-and-support-)

### Main Concepts of AWS Pricing
1. **Pay as you go:** Adapt to changing business needs and reduce the risk of over-provisioning or missing capacity.
2. **Save when you commit:** Savings Plans offer savings over on-demand prices when committing to a 1 or 3-year plan.
3. **Pay less by using more** 

### Driving Factors of Cost
1. **Compute**
   - Pay from the time you launch a resource until the time you stop the instance.
2. **Storage**
   - Pricing depends on how much storage have been provisioned or how much are being used.
   - For Amazon S3, consider the following six cost components:
     1. Storage Pricing
     2. Request and data retrieval pricing
     3. Data transfer and transfer acceleration pricing
     4. Data management and analytics pricing
     5. Replication pricing
     6. Price to process data with Amazon S3 Object Lambda
3. **Data Transfer**
   - In most cases, there is no charge for inbound data transfer or for data transfer between AWS services within the same Region. There are some exceptions, so be sure to verify data transfer rates before beginning
   - **Outbound Data Transfer**
     - is aggregated across services and then charged at the outbound data transfer rate.
     - The more data transferred, the less being paid per gigabyte.
     - For data storage and transfer, it is typically paid per gigabyte.


## AWS Pricing and Billing Services [↑](#pricing-and-support-)

### AWS Organizations
- Provides centralized management and governance of AWS environment.
- Create , group, and manage accounts.
- Apply security policies at the account level and consolidate billing with multiple accounts using a single payment method.
- **Use Cases:**
  - Consolidate multiple AWS accounts into one central organizations.
  - Implement organization-wide policies.
- **More Information:** [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)

### AWS Billing and Cost Management Dashboard
- Centralizes cost management, showing current charges, usage, forecasts, and detailed breakdowns.
- Also provides tools to manage payments, view invoices, set budgets, and consolidate billings.
- **Use Cases:**
  - Visualizations and billing reports of monthly AWS spend.
  - Setup and manage payment methods.
- **More Information:** [AWS Billing User Guide](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/view-billing-dashboard.html)

### AWS Budgets
- Helps set custom budgets and sends alerts when cost, usage, or Savings Plans and Reserved Instances (RIs) 
utilization or coverage exceed defined thresholds.
- **Use Cases:**
  - Set up alerts for when projected costs exceed predefined thresholds. 
  - Forecast future expenses based on current usage trends.
- **More Information:** [Managing Costs with AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)

### AWS Cost Explorer

### AWS Pricing Calculator





