The [**AWS Well-Architected Framework**(opens in a new tab)](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) helps you understand how to design and operate reliable, secure, efficient, and cost-effective systems in the AWS Cloud. It provides a way for you to consistently measure your architecture against best practices and design principles and identify areas for improvement.
The Well-Architected Framework is based on six pillars: 
- Operational excellence
	 is the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures.  
	 Design principles for operational excellence in the cloud include performing operations as code, annotating documentation, anticipating failure, and frequently making small, reversible changes.
- Security
	The **Security** pillar is the ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies. 
	When considering the security of your architecture, apply these best practices:
		- Automate security best practices when possible.
		- Apply security at all layers.
		- Protect data in transit and at rest.
- Reliability
	**Reliability** is the ability of a system to do the following:
	- Recover from infrastructure or service disruptions
	- Dynamically acquire computing resources to meet demand
	- Mitigate disruptions such as misconfigurations or transient network issues
	Reliability includes testing recovery procedures, scaling horizontally to increase aggregate system availability, and automatically recovering from failure.
- Performance efficiency
	**Performance efficiency** is the ability to use computing resources efficiently to meet system requirements and to maintain that efficiency as demand changes and technologies evolve. 
	Evaluating the performance efficiency of your architecture includes experimenting more often, using serverless architectures, and designing systems to be able to go global in minutes.
- Cost optimization
	**Cost optimization** is the ability to run systems to deliver business value at the lowest price point. 
	Cost optimization includes adopting a consumption model, analyzing and attributing expenditure, and using managed services to reduce the cost of ownership.
- Sustainability
	Sustainability is the ability to continually improve sustainability impacts by reducing energy consumption and increasing efficiency across all components of a workload by maximizing the benefits from the provisioned resources and minimizing the total resources required.
	To facilitate good design for sustainability:
	- Understand your impact
	- Establish sustainability goals
	- Maximize utilization
	- Anticipate and adopt new, more efficient hardware and software offerings
	- Use managed services
	- Reduce the downstream impact of your cloud workloads
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
## **Si core perspectives of the Cloud Adoption Framework**
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