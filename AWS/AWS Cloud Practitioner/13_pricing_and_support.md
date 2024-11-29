AWS offers a range of cloud computing services with pay-as-you-go pricing. 
## Core principles
### Pay for what you use.
For each service, you pay for exactly the amount of resources that you actually use, without requiring long-term contracts or complex licensing. 
### Pay less when you reserve.
Some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing.
For example, suppose that your company is using Amazon EC2 instances for a workload that needs to run continuously. You might choose to run this workload on Amazon EC2 Instance Savings Plans, because the plan allows you to save up to 72% over the equivalent On-Demand Instance capacity.
### Pay less with volume-based discounts when you use more.
Some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage.
For example, the more Amazon S3 storage space you use, the less you pay for it per GB.
## AWS Pricing Calculator
The [**AWS Pricing Calculator**(opens in a new tab)](https://calculator.aws/#/) lets you explore AWS services and create an estimate for the cost of your use cases on AWS. You can organize your AWS estimates by groups that you define. A group can reflect how your company is organized, such as providing estimates by cost center.

When you have created an estimate, you can save it and generate a link to share it with others.
## AWS Pricing Calculator
The [**AWS Pricing Calculator**(opens in a new tab)](https://calculator.aws/#/) lets you explore AWS services and create an estimate for the cost of your use cases on AWS. You can organize your AWS estimates by groups that you define. A group can reflect how your company is organized, such as providing estimates by cost center.
When you have created an estimate, you can save it and generate a link to share it with others.
##  AWS Billing & Cost Management 
Use the [**AWS Billing & Cost Management dashboard**(opens in a new tab)](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html) to pay your AWS bill, monitor your usage, and analyze and control your costs.
- Compare your current month-to-date balance with the previous month, and get a forecast of the next month based on current usage.
- View month-to-date spend by service.
- View Free Tier usage by service.
- Access Cost Explorer and create budgets.
- Purchase and manage Savings Plans.
- Publish [AWS Cost and Usage Reports(opens in a new tab)](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html).
## **Consolidated billing**
In an earlier module, you learned about AWS Organizations, a service that enables you to manage multiple AWS accounts from a central location. AWS Organizations also provides the option for [**consolidated billing**(opens in a new tab)](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html). 

The consolidated billing feature of AWS Organizations enables you to receive a single bill for all AWS accounts in your organization. By consolidating, you can easily track the combined costs of all the linked accounts in your organization. The default maximum number of accounts allowed for an organization is 4, but you can contact AWS Support to increase your quota, if needed.

On your monthly bill, you can review itemized charges incurred by each account. This enables you to have greater transparency into your organization’s accounts while still maintaining the convenience of receiving a single monthly bill.

Another benefit of consolidated billing is the ability to share bulk discount pricing, Savings Plans, and Reserved Instances across the accounts in your organization. For instance, one account might not have enough monthly usage to qualify for discount pricing. However, when multiple accounts are combined, their aggregated usage may result in a benefit that applies across all accounts in the organization.
## **AWS Budgets**
In [**AWS Budgets**(opens in a new tab)](https://aws.amazon.com/aws-cost-management/aws-budgets), you can create budgets to plan your service usage, service costs, and instance reservations.

The information in AWS Budgets updates three times a day. This helps you to accurately determine how close your usage is to your budgeted amounts or to the AWS Free Tier limits.
In AWS Budgets, you can also set custom alerts when your usage exceeds (or is forecasted to exceed) the budgeted amount.
### **AWS Cost Explorer**
[**AWS Cost Explorer**(opens in a new tab)](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/) is a tool that lets you visualize, understand, and manage your AWS costs and usage over time.

AWS Cost Explorer includes a default report of the costs and usage for your top five cost-accruing AWS services. You can apply custom filters and groups to analyze your data. For example, you can view resource usage at the hourly level.

![[Pasted image 20241110130559.png]]
This example of the AWS Cost Explorer dashboard displays monthly costs for Amazon EC2 instances over a 6-month period. The bar for each month separates the costs for different Amazon EC2 instance types, such as t2.micro or m3.large. 

By analyzing your AWS costs over time, you can make informed decisions about future costs and how to plan your budgets.
