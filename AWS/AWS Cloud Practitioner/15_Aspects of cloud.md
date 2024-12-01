
## **Advantages of cloud computing**
Operating in the AWS Cloud offers many benefits over computing in on-premises or hybrid environments. 
In this section, you will learn about six advantages of cloud computing:
- Trade upfront expense for variable expense.
	Upfront expenses include data centers, physical servers, and other resources that you would need to invest in before using computing resources. 
	Instead of investing heavily in data centers and servers before you know how you’re going to use them, you can pay only when you consume computing resources.
- Benefit from massive economies of scale.
	Upfront expenses include data centers, physical servers, and other resources that you would need to invest in before using computing resources. 
	Instead of investing heavily in data centers and servers before you know how you’re going to use them, you can pay only when you consume computing resources.
- Stop guessing capacity
	With cloud computing, you don’t have to predict how much infrastructure capacity you will need before deploying an application. 
	For example, you can launch Amazon Elastic Compute Cloud (Amazon EC2) instances when needed and pay only for the compute time you use. Instead of paying for resources that are unused or dealing with limited capacity, you can access only the capacity that you need, and scale in or out in response to demand.
- Increase speed and agility.
	The flexibility of cloud computing makes it easier for you to develop and deploy applications.
	This flexibility also provides your development teams with more time to experiment and innovate.
- Stop spending money running and maintaining data centers.
	Cloud computing in data centers often requires you to spend more money and time managing infrastructure and servers. 
	A benefit of cloud computing is the ability to focus less on these tasks and more on your applications and customers.
- Go global in minutes.
	Cloud computing in data centers often requires you to spend more money and time managing infrastructure and servers. 

## **Licensing in AWS Cloud**

AWS provides flexible licensing strategies to help organizations optimize costs while meeting their operational and compliance requirements. This is particularly relevant for software like databases, operating systems, and enterprise applications (e.g., Microsoft or Oracle products).

### **1. Bring Your Own License (BYOL)**

- **Description**: Customers migrate their existing software licenses to AWS rather than purchasing new ones.
- **Common Use Cases**:
    - Organizations that have invested heavily in on-premises licenses and want to leverage those in the cloud.
    - Software with high customization or specific configurations, such as Oracle databases or Windows Server.
- **Benefits**:
    - **Cost Savings**: Avoid purchasing new licenses or paying for licenses included in AWS service costs.
    - **Compliance**: Ensures compliance with vendor-specific license agreements.
    - **Flexibility**: Allows businesses to migrate workloads without needing to adjust application dependencies or configurations.
- **Examples**:
    - Running an Oracle database with a BYOL option on Amazon RDS or EC2 instances.
    - Using Microsoft SQL Server on EC2 with BYOL licensing.

---

### **2. Included Licensing (License-Included Model)**

- **Description**: AWS provides the required software licenses as part of the service offering. Customers pay for the licenses as part of their usage charges.
- **Common Use Cases**:
    - Businesses that do not already own licenses for the software they plan to use.
    - Organizations looking for simplified licensing and management, especially for cloud-native workloads.
- **Benefits**:
    - **Simplified Pricing**: No separate licensing fees; costs are bundled into the AWS service charges.
    - **Ease of Use**: AWS manages updates, compliance, and licensing details, reducing operational overhead.
    - **Scalability**: Licensing costs scale with usage, aligning with the cloud’s pay-as-you-go model.
- **Examples**:
    - Amazon RDS for MySQL, PostgreSQL, and SQL Server (license included).
    - EC2 instances with pre-installed Windows Server.

---

### **Key Differences Between BYOL and License-Included**

|**Aspect**|**BYOL**|**License-Included**|
|---|---|---|
|**Cost**|Lower for customers with existing licenses.|Bundled into the AWS service fee.|
|**Flexibility**|Retain control over licensing terms and configurations.|Simplified pricing and management.|
|**Use Cases**|Existing investments in licenses; specific compliance needs.|New workloads or simplified license management.|
|**Example**|Running Oracle databases on EC2 with BYOL.|Running MySQL on Amazon RDS with licensing included.|


## Six core perspectives of the Cloud Adoption Framework
At the highest level, the [**AWS Cloud Adoption Framework (AWS CAF)**(opens in a new tab)](https://d1.awsstatic.com/whitepapers/aws_cloud_adoption_framework.pdf) organizes guidance into six areas of focus, called **P****erspectives**. Each Perspective addresses distinct responsibilities. The planning process helps the right people across the organization prepare for the changes ahead.
### Business Perspective
The **Business Perspective** ensures that IT aligns with business needs and that IT investments link to key business results.
Use the Business Perspective to create a strong business case for cloud adoption and prioritize cloud adoption initiatives. Ensure that your business strategies and goals align with your IT strategies and goals.
Common roles in the Business Perspective include: 
- Business managers
- Finance managers
- Budget owners
- Strategy stakeholders
### People Perspective
The **People Perspective** supports development of an organization-wide change management strategy for successful cloud adoption.
Use the People Perspective to evaluate organizational structures and roles, new skill and process requirements, and identify gaps. This helps prioritize training, staffing, and organizational changes.
Common roles in the People Perspective include: 
- Human resources
- Staffing
- People managers
### Governance Perspective
The **Governance Perspective** focuses on the skills and processes to align IT strategy with business strategy. This ensures that you maximize the business value and minimize risks.
Use the Governance Perspective to understand how to update the staff skills and processes necessary to ensure business governance in the cloud. Manage and measure cloud investments to evaluate business outcomes.
Common roles in the Governance Perspective include: 
- Chief Information Officer (CIO)
- Program managers
- Enterprise architects
- Business analysts
- Portfolio managers
### Platform Perspective
The **Platform Perspective** includes principles and patterns for implementing new solutions on the cloud, and migrating on-premises workloads to the cloud.
Use a variety of architectural models to understand and communicate the structure of IT systems and their relationships. Describe the architecture of the target state environment in detail.
Common roles in the Platform Perspective include: 
- Chief Technology Officer (CTO)
- IT managers
- Solutions architects

### Security Perspective
The **Security Perspective** ensures that the organization meets security objectives for visibility, auditability, control, and agility. 
Use the AWS CAF to structure the selection and implementation of security controls that meet the organization’s needs.
Common roles in the Security Perspective include: 
- Chief Information Security Officer (CISO)
- IT security managers
- IT security analysts
### Operations Perspective
The **Operations Perspective** helps you to enable, run, use, operate, and recover IT workloads to the level agreed upon with your business stakeholders.
Define how day-to-day, quarter-to-quarter, and year-to-year business is conducted. Align with and support the operations of the business. The AWS CAF helps these stakeholders define current operating procedures and identify the process changes and training needed to implement successful cloud adoption.
Common roles in the Operations Perspective include: 
- IT operations managers
- IT support managers