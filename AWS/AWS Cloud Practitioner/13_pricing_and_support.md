## 

**How AWS pricing works**

AWS offers a range of cloud computing services with pay-as-you-go pricing. 

To learn more about how AWS pricing works, expand each of the following three categories.

## 

Pay for what you use.

For each service, you pay for exactly the amount of resources that you actually use, without requiring long-term contracts or complex licensing. 

  

## 

Pay less when you reserve.

Some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing.

  

For example, suppose that your company is using Amazon EC2 instances for a workload that needs to run continuously. You might choose to run this workload on Amazon EC2 Instance Savings Plans, because the plan allows you to save up to 72% over the equivalent On-Demand Instance capacity.

## 

Pay less with volume-based discounts when you use more.

Some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage.

  

For example, the more Amazon S3 storage space you use, the less you pay for it per GB.

## 

****AWS Pricing Calculator****

The [**AWS Pricing Calculator**(opens in a new tab)](https://calculator.aws/#/) lets you explore AWS services and create an estimate for the cost of your use cases on AWS. You can organize your AWS estimates by groups that you define. A group can reflect how your company is organized, such as providing estimates by cost center.

When you have created an estimate, you can save it and generate a link to share it with others.

## 

**How AWS pricing works**

AWS offers a range of cloud computing services with pay-as-you-go pricing. 

To learn more about how AWS pricing works, expand each of the following three categories.

## 

Pay for what you use.

For each service, you pay for exactly the amount of resources that you actually use, without requiring long-term contracts or complex licensing. 

  

## 

Pay less when you reserve.

Some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing.

  

For example, suppose that your company is using Amazon EC2 instances for a workload that needs to run continuously. You might choose to run this workload on Amazon EC2 Instance Savings Plans, because the plan allows you to save up to 72% over the equivalent On-Demand Instance capacity.

## 

Pay less with volume-based discounts when you use more.

Some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage.

  

For example, the more Amazon S3 storage space you use, the less you pay for it per GB.

## 

****AWS Pricing Calculator****

The [**AWS Pricing Calculator**(opens in a new tab)](https://calculator.aws/#/) lets you explore AWS services and create an estimate for the cost of your use cases on AWS. You can organize your AWS estimates by groups that you define. A group can reflect how your company is organized, such as providing estimates by cost center.

When you have created an estimate, you can save it and generate a link to share it with others.


Use the [**AWS Billing & Cost Management dashboard**(opens in a new tab)](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html) to pay your AWS bill, monitor your usage, and analyze and control your costs.

- Compare your current month-to-date balance with the previous month, and get a forecast of the next month based on current usage.
- View month-to-date spend by service.
- View Free Tier usage by service.
- Access Cost Explorer and create budgets.
- Purchase and manage Savings Plans.
- Publish [AWS Cost and Usage Reports(opens in a new tab)](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html).


## 

**Consolidated billing**

In an earlier module, you learned about AWS Organizations, a service that enables you to manage multiple AWS accounts from a central location. AWS Organizations also provides the option for [**consolidated billing**(opens in a new tab)](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html). 

The consolidated billing feature of AWS Organizations enables you to receive a single bill for all AWS accounts in your organization. By consolidating, you can easily track the combined costs of all the linked accounts in your organization. The default maximum number of accounts allowed for an organization is 4, but you can contact AWS Support to increase your quota, if needed.

On your monthly bill, you can review itemized charges incurred by each account. This enables you to have greater transparency into your organization’s accounts while still maintaining the convenience of receiving a single monthly bill.

Another benefit of consolidated billing is the ability to share bulk discount pricing, Savings Plans, and Reserved Instances across the accounts in your organization. For instance, one account might not have enough monthly usage to qualify for discount pricing. However, when multiple accounts are combined, their aggregated usage may result in a benefit that applies across all accounts in the organization.

To review and example of consolidated billing, choose the arrow buttons to display the four steps.



Step 1

![Three AWS accounts get added to a single account called "Primary Account".](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1731243600/Gd5H1eWPUGFVTBzF-QaYqg/tincan/fe470bc5add63f94f005d3da17a6db8131e78b9e/assets/Consolidated%20billing%201.png)

Suppose that you are the business leader who oversees your company’s AWS billing. 

Your company has three AWS accounts used for separate departments. In this example, Account 1 owes $19.64, Account 2 owes $19.96, and Account 3 owes $20.06. Instead of paying each location’s monthly bill separately, you decide to create an organization and add the three accounts. 

You manage the organization through the primary account.



![Charges from multiple accounts in a single consolidated bill. Charges incurred by primary account included.](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1731243600/Gd5H1eWPUGFVTBzF-QaYqg/tincan/fe470bc5add63f94f005d3da17a6db8131e78b9e/assets/Consolidated%20billing%202.png)

Continuing the example, each month AWS charges your primary payer account for all the linked accounts in a consolidated bill. Through the primary account, you can also get a detailed cost report for each linked account. 

The monthly consolidated bill also includes the account usage costs incurred by the primary account. In this case, the primary account incurred $14.14. This cost is not a premium charge for having a primary account. 

The consolidated bill shows the costs associated with any actions of the primary account (such as storing files in Amazon S3 or running Amazon EC2 instances). The total charged to the paying account, including the primary account and accounts one through three, is $73.80.


![Three non-consolidated AWS accounts. Each uses Amazon S3 and each is under 10 TB of usage.](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1731243600/Gd5H1eWPUGFVTBzF-QaYqg/tincan/fe470bc5add63f94f005d3da17a6db8131e78b9e/assets/Consolidated%20billing%203.png)

Consolidated billing also enables you to share volume pricing discounts across accounts. 

Some AWS services, such as Amazon S3, provide volume pricing discounts that give you lower prices the more that you use the service. In Amazon S3, after customers have transferred 10 TB of data in a month, they pay a lower per-GB transfer price for the next 40 TB of data transferred. 

In this example, there are three separate AWS accounts that have transferred different amounts of data in Amazon S3 during the current month: 

- Account 1 has transferred 2 TB of data.
- Account 2 has transferred 5 TB of data.
- Account 3 has transferred 7 TB of data.

Because no single account has passed the 10 TB threshold, none of them is eligible for the lower per-GB transfer price for the next 40 TB of data transferred.





## 

**AWS Budgets**

In [**AWS Budgets**(opens in a new tab)](https://aws.amazon.com/aws-cost-management/aws-budgets), you can create budgets to plan your service usage, service costs, and instance reservations.

The information in AWS Budgets updates three times a day. This helps you to accurately determine how close your usage is to your budgeted amounts or to the AWS Free Tier limits.

In AWS Budgets, you can also set custom alerts when your usage exceeds (or is forecasted to exceed) the budgeted amount.

## 

**Example: AWS Budgets**

Suppose that you have set a budget for Amazon EC2. You want to ensure that your company’s usage of Amazon EC2 does not exceed $200 for the month. 

In AWS Budgets, you could set a custom budget to notify you when your usage has reached half of this amount ($100). This setting would allow you to receive an alert and decide how you would like to proceed with your continued use of Amazon EC2.

To learn more about AWS Budgets, choose each of the numbered markers.



## 

**AWS Cost Explorer**

[**AWS Cost Explorer**(opens in a new tab)](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/) is a tool that lets you visualize, understand, and manage your AWS costs and usage over time.

AWS Cost Explorer includes a default report of the costs and usage for your top five cost-accruing AWS services. You can apply custom filters and groups to analyze your data. For example, you can view resource usage at the hourly level.

![[Pasted image 20241110130559.png]]
This example of the AWS Cost Explorer dashboard displays monthly costs for Amazon EC2 instances over a 6-month period. The bar for each month separates the costs for different Amazon EC2 instance types, such as t2.micro or m3.large. 

By analyzing your AWS costs over time, you can make informed decisions about future costs and how to plan your budgets.




## 

**AWS Support**

AWS offers four different [**Support plans**(opens in a new tab)](https://aws.amazon.com/premiumsupport/plans/) to help you troubleshoot issues, lower costs, and efficiently use AWS services. 

You can choose from the following Support plans to meet your company’s needs: 

- Basic
- Developer
- Business
- Enterprise On-Ramp
- Enterprise

## 

**Basic Support**

**Basic Support** is free for all AWS customers. It includes access to whitepapers, documentation, and support communities. With Basic Support, you can also contact AWS for billing questions and service limit increases.

With Basic Support, you have access to a limited selection of AWS Trusted Advisor checks. Additionally, you can use the **AWS Personal Health Dashboard**, a tool that provides alerts and remediation guidance when AWS is experiencing events that may affect you. 

If your company needs support beyond the Basic level, you could consider purchasing Developer, Business, Enterprise On-Ramp, and Enterprise Support.

## 

**Developer, Business, Enterprise On-Ramp, and Enterprise Support**

The Developer, Business, Enterprise On-Ramp, and Enterprise Support plans include all the benefits of Basic Support, in addition to the ability to open an unrestricted number of technical support cases. These Support plans have pay-by-the-month pricing and require no long-term contracts.  
  
The information in this course highlights only a selection of details for each Support plan. A complete overview of what is included in each Support plan, including pricing for each plan, is available on the [AWS Support(opens in a new tab)](https://aws.amazon.com/premiumsupport/plans/) site.  
  
In general, for pricing, the Developer plan has the lowest cost, the Business and Enterprise On-Ramp plans are in the middle, and the Enterprise plan has the highest cost.

To learn more about AWS support plans, expand each of the following four categories.

## 

Developer Support

Customers in the **Developer Support** plan have access to features such as:

- Best practice guidance
- Client-side diagnostic tools
- Building-block architecture support, which consists of guidance for how to use AWS offerings, features, and services together

For example, suppose that your company is exploring AWS services. You’ve heard about a few different AWS services. However, you’re unsure of how to potentially use them together to build applications that can address your company’s needs. In this scenario, the building-block architecture support that is included with the Developer Support plan could help you to identify opportunities for combining specific services and features.

## 

Business Support

Customers with a **Business Support** plan have access to additional features, including: 

- Use-case guidance to identify AWS offerings, features, and services that can best support your specific needs
- All AWS Trusted Advisor checks
- Limited support for third-party software, such as common operating systems and application stack components

Suppose that your company has the Business Support plan and wants to install a common third-party operating system onto your Amazon EC2 instances. You could contact AWS Support for assistance with installing, configuring, and troubleshooting the operating system. For advanced topics such as optimizing performance, using custom scripts, or resolving security issues, you may need to contact the third-party software provider directly.

## 

Enterprise On-Ramp Support

In November 2021, AWS opened enrollment into AWS Enterprise On-Ramp Support plan. In addition to all the features included in the Basic, Developer, and Business Support plans, customers with an Enterprise On-Ramp Support plan have access to:

- A pool of Technical Account Managers to provide proactive guidance and coordinate access to programs and AWS experts
    
- A Cost Optimization workshop (one per year)
    
- A Concierge support team for billing and account assistance
    
- Tools to monitor costs and performance through Trusted Advisor and Health API/Dashboard
    

Enterprise On-Ramp Support plan also provides access to a specific set of proactive support services, which are provided by a pool of Technical Account Managers.

- Consultative review and architecture guidance (one per year)
    
- Infrastructure Event Management support (one per year)
    
- Support automation workflows
    
- 30 minutes or less response time for business-critical issues
    

## 

Enterprise Support

In addition to all features included in the Basic, Developer, Business, and Enterprise On-Ramp support plans, customers with Enterprise Support have access to:

- A designated Technical Account Manager to provide proactive guidance and coordinate access to programs and AWS experts
    
- A Concierge support team for billing and account assistance
    
- Operations Reviews and tools to monitor health
    
- Training and Game Days to drive innovation
    
- Tools to monitor costs and performance through Trusted Advisor and Health API/Dashboard
    

The Enterprise plan also provides full access to proactive services, which are provided by a designated Technical Account Manager:

- Consultative review and architecture guidance
    
- Infrastructure Event Management support
    
- Cost Optimization Workshop and tools
    
- Support automation workflows
    
- 15 minutes or less response time for business-critical issues
    

## 

**Technical Account Manager (TAM)**

The Enterprise On-Ramp and Enterprise Support plans include access to a **Technical Account Manager (TAM)**.  
  
The TAM is your primary point of contact at AWS. If your company subscribes to Enterprise Support or Enterprise On-Ramp, your TAM educates, empowers, and evolves your cloud journey across the full range of AWS services. TAMs provide expert engineering guidance, help you design solutions that efficiently integrate AWS services, assist with cost-effective and resilient architectures, and provide direct access to AWS programs and a broad community of experts.  
  
For example, suppose that you are interested in developing an application that uses several AWS services together. Your TAM could provide insights into how to best use the services together. They achieve this, while aligning with the specific needs that your company is hoping to address through the new application.



## 

**AWS Marketplace**

[**AWS Marketplace**(opens in a new tab)](https://aws.amazon.com/marketplace) is a digital catalog that includes thousands of software listings from independent software vendors. You can use AWS Marketplace to find, test, and buy software that runs on AWS. 

For each listing in AWS Marketplace, you can access detailed information on pricing options, available support, and reviews from other AWS customers.

You can also explore software solutions by industry and use case. For example, suppose your company is in the healthcare industry. In AWS Marketplace, you can review use cases that software helps you to address, such as implementing solutions to protect patient records or using machine learning models to analyze a patient’s medical history and predict possible health risks.

### 

**AWS Marketplace categories**

![](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1731243600/Gd5H1eWPUGFVTBzF-QaYqg/tincan/fe470bc5add63f94f005d3da17a6db8131e78b9e/assets/CPE%20Digital%20-%20Module%208%20-%20AWS%20Marketplace.png)

AWS Marketplace offers products in several categories, such as Infrastructure Software, DevOps, Data Products, Professional Services, Business Applications, Machine Learning, Industries, and Internet of Things (IoT).

Within each category, you can narrow your search by browsing through product listings in subcategories. For example, subcategories in the DevOps category include areas such as Application Development, Monitoring, and Testing.