## **Amazon CloudWatch**

[**Amazon CloudWatch**(opens in a new tab)](https://aws.amazon.com/cloudwatch/) is a web service that enables you to monitor and manage various metrics and configure alarm actions based on data from those metrics.
All AWS resources automatically send their metrics to CloudWatch. These metrics include things such as EC2 instance CPU utilization, S3 bucket sizes, and DynamoDB consumed read and write capacity units. CloudWatch stores metrics for up to 15 months

### Alarms
With CloudWatch, you can create [**alarms**(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) that automatically perform actions if the value of a particular metric has gone above or below a predefined threshold.
- Just send a notification to an SNS topic
- Auto Scaling action By specifying an EC2 Auto Scaling action, the EC2 Auto Scaling service can add or remove EC2 instances in response to changing demand. For example, if a metric indicates that instances are overburdened, you can have EC2 Auto Scaling respond by adding more instances.
- EC2 action If you’re monitoring a specific instance that’s having a problem, you can use an EC2 action to stop, terminate, or recover the instance. Recovering an instance migrates the instance to a new EC2 host, something you may need to do if there’s a physical hardware problem on the hardware hosting the instance.

### Dashboard
The CloudWatch [**dashboard**(opens in a new tab)](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html) feature enables you to access all the metrics for your resources from a single location.

### CloudWatch Logs
CloudWatch Logs collects and stores log files from AWS and non-AWS sources and makes it easy to view, search, and extract custom metrics from them. Log Events, Streams, and Groups You configure your applications and AWS services to send log events to CloudWatch Logs. A log event is analogous to a line in a log file and always contains a timestamp and an event message. Many AWS services produce their own logs called vended logs that you can stream to CloudWatch Logs. Such logs include Route 53 DNS query logs, #VPC flow logs, and CloudTrail logs. #CloudWatch Logs can also receive custom logs from your applications, such as web server access logs. CloudWatch Logs organizes log events by log streams by storing log events from the same source in a single log stream. For example, web server access logs from a specific EC2 instance would be stored in one log stream, while #Route53 #DNS query logs would be stored in a separate log stream. CloudWatch further organizes log streams into log groups. To organize related log streams, you can place them into the same log group. For instance, if you have several log streams that are collecting web server log events from multiple web servers, you can group all of those log streams into a single log group. CloudWatch Logs stores log events indefinitely by default, but you can configure a log group’s retention settings to delete events automatically. Retention settings range from 1 day to 10 years. You can also archive your logs by exporting them to an S3 bucket

### Events

The CloudWatch Events feature lets you continuously monitor for specifi c events that represent a change in your AWS resources—particularly write-only API operations—and take an action when they occur. For example, an EC2 instance going from the running state to the stopped state would be an event. An #IAM user logging into the AWS Management Console would also be an event. CloudWatch Events can then automatically and immediately take actions in response to those events. You start by creating a rule to defi ne the events to monitor, as well as the actions you want to take in response to those events. You defi ne the action to take by selecting a target, which is an AWS resource. Some targets you can choose from include the following:
✓■ Lambda functions 
✓■ EC2 instances 
✓■ #SQS queues 
✓■ #SNS topics 
✓■ #ECS tasks

CloudWatch responds to events as they occur, in real time. Unlike CloudWatch alarms, which take action when a metric crosses and remains crossing a numeric threshold, CloudWatch events trigger immediately. For example, you can create a CloudWatch event to send an SNS notifi cation whenever an EC2 instance terminates. Or you could trigger a Lambda function to process an image fi le as soon as it hits an S3 bucket.
## **AWS CloudTrail**

[**AWS CloudTrail**(opens in a new tab)](https://aws.amazon.com/cloudtrail/) records API calls for your account. The recorded information includes the identity of the API caller, the time of the API call, the source IP address of the API caller, and more. You can think of CloudTrail as a “trail” of breadcrumbs (or a log of actions) that someone has left behind them.

Recall that you can use API calls to provision, manage, and configure your AWS resources. With CloudTrail, you can view a complete history of user activity and API calls for your applications and resources. 

Events are typically updated in CloudTrail within 15 minutes after an API call. You can filter events by specifying the time and date that an API call occurred, the user who requested the action, the type of resource that was involved in the API call, and more.

Within CloudTrail, you can also enable [**CloudTrail Insights**(opens in a new tab)](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-insights-events-with-cloudtrail.html). This optional feature allows CloudTrail to automatically detect unusual API activities in your AWS account. 

For example, #CloudTrail Insights might detect that a higher number of Amazon #EC2 instances than usual have recently launched in your account. You can then review the full event details to determine which actions you need to take next.

## **AWS Trusted Advisor**

[**AWS Trusted Advisor**(opens in a new tab)](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) is a web service that inspects your AWS environment and provides real-time recommendations in accordance with AWS best practices.

Trusted Advisor compares its findings to AWS best practices in five categories: cost optimization, performance, security, fault tolerance, and service limits. For the checks in each category, Trusted Advisor offers a list of recommended actions and additional resources to learn more about AWS best practices. 

The guidance provided by AWS Trusted Advisor can benefit your company at all stages of deployment. For example, you can use AWS Trusted Advisor to assist you while you are creating new workflows and developing new applications. You can also use it while you are making ongoing improvements to existing applications and resources.

When you access the Trusted Advisor dashboard on the AWS Management Console, you can review completed checks for cost optimization, performance, security, fault tolerance, and service limits.

For each category:

- The green check indicates the number of items for which it detected **no problems**.
- The orange triangle represents the number of recommended **investigations**.
- The red circle represents the number of recommended **actions**

