# Capstone Project

<h1>Building a Reliable and Safe AWS Simulated Hybrid Cloud Architecture with VPN</h1>

<h2>Description</h2>
<p>This project represents my capstone experience, completed in collaboration with the Fields Institute at the University of Toronto. As a team of three, we carefully analyzed project requirements and developed a compelling business scenario based on our findings.
<br/>
<br/>
Consider an imaginary business scenario where a software solution provider aims to migrate to cloud environment, specifically Amazon Web Services (AWS). They need both a production environment, including a website for license sales and a database for storing sensitive customer data, and a non-production environment for testing and development purposes, using diverse operating systems. Additionally, the company seeks secure connectivity between their on-premises systems and the cloud environment, requiring a VPN connection.
 <br/>
 <br/>
Developing a robust cybersecurity plan for businesses begins with meticulous identification and protection of critical assets. These assets comprise sensitive data like customer information and financial records, along with vital systems such as servers and networks. Additionally, safeguarding the repository of codes and systems within the development cloud environment is crucial for protecting intellectual property (IP) and ensuring smooth business operations.
With digital transformation and remote work becoming prevalent, the conventional approach of trusting all within the internal network lacks adequate security. Considering our current compliance to the traditional security model, we recognize the need to incorporate elements of Zero Trust Architecture (ZTA). We acknowledge that the immediate adoption of ZTA is not feasible. We understand that transitioning towards zero trust is a gradual process that may take several years to fully implement. Therefore, our strategy involves introducing elements of zero trust into our infrastructure with a long-term objective in mind. <br/>
 <br/>
We have constructed our infrastructure using AWS to create a simulated hybrid-cloud environment, giving utmost importance to adopting Infrastructure as Code (IaC) principles with the help of Terraform. Additionally, we have established vulnerability management by combining Tenable scanners and agents.</p>

<h2>Utilities Used</h2>

- <b>Terraform</b> 
- <b>Tenable.io</b>
- <b>MySQL</b>
- <b>HMTL</b>
- <b>Public Key Infrastructure</b>
- <b>SSH</b>
- <b>AWS KMS</b>

<h2>Cloud Environment </h2>

- <b>Amazon Web Services (AWS)</b>

<h2>Team Members</h2>

- <b>Sangeeth Das Kallullathil</b> 
- <b>Mojdeh Akhavan</b>
- <b>Samprit Ghosh</b>

<h2>Organization</h2>
<p align="left">
<b>Cyber Connexion Cohort 7 program - Fields Institute - University of Toronto </b>

<h2>Project walk-through:</h2>
<p align="left">
<b>Business Scenario: </b>
<br/>
<p>A software solution provider is planning to transition to the cloud, specifically Amazon Web Services (AWS). The company needs to establish both a production environment and a non-production (development) environment. For the production environment, they require a website to sell licenses/subscriptions and a database to store sensitive customer information like personally identifiable data (PII) such as name, address, phone number, birthday, and gender. Customers will access the website using login credentials. The non-production environment is meant for testing and development, requiring various operating systems. Additionally, the company has requested a secure VPN connection to link their on-premises systems with the cloud environment.</p>
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/7bc9ce23581153fb3879f91db6ec9b48d6c4334f/Team1_Slides_Final.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>Full Infrastructure Diagram: </b>
<br />
<br/>
The provided infrastructure diagram illustrates the architecture designed for this specific scenario, featuring three distinct Virtual Private Clouds (VPCs).
<br/>
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/8c507978bdc56371f020aef566837cc2f238d251/capstone_team1.drawio.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
The Production (Prod) VPC is organized in a three-tier architecture spread across two availability zones. It comprises the presentation (or Web) tier, the logic (or App) tier, and the data tier. The presentation tier contains key components responsible for direct user interactions, including the business's e-Commerce website. The logic tier houses essential code that translates user actions into functional application behavior. Meanwhile, the data tier acts as a secure storage medium for the relevant application data. High availability is ensured by deploying all compute and storage resources across two availability zones. Additionally, autoscaling groups are employed for the Web and App tiers, allowing dynamic instance additions or removals based on health checks or scaling policies. This approach ensures continuous availability while optimizing cost management.
<br/>
<br/>
The Development (Non-Prod) VPC serves as a dedicated environment for comprehensive software testing, experimentation with various operating systems, and crucial debugging and troubleshooting activities.

Lastly, a "simulated" on-premises VPC has been implemented to virtually represent the business's physical office space. This VPC hosts a VPN gateway enabling site-to-site VPN connections between the on-premises infrastructure and the cloud environment. This ensures seamless and secure communication between the two environments. <br/>
<br />
<b>Infrastructure As a Code: </b>
<br />
<br/>
In our AWS cloud infrastructure, we have extensively utilized <b>Terraform</b> for deployment purposes. Terraform empowers us with infrastructure as code (IaC) capabilities, allowing the management and provisioning of AWS resources through declarative code. This approach streamlines the deployment process, eliminating manual errors and ensuring consistency. Moreover, Terraform offers an extensive range of AWS provider resources, facilitating the creation and management of diverse AWS services and configurations. Its modular and reusable code structure further enhances scalability and simplifies maintenance tasks.
<br/>
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/9c2cd70727f210d8ad68e6751aac3906599b4c8d/Screenshot%202023-07-22%20at%2011.06.48%20AM.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>Production Environment - 3 Tier Architecture</h3>
<b>Resource Map: </b>
<br />
<br />
Public Subnets are connected to the internet via an <b>Internet ateway</b>.
 <br/>
 <br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/ea42ae98c212759930f2c00990da3d944ebe0b99/Screenshot%202023-07-06%20at%2010.29.21%20AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Private Subnets are connected to the internet via an <b>Network Address Translation (NAT) gateway</b>.
 <br/>
 <br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/ea42ae98c212759930f2c00990da3d944ebe0b99/Screenshot%202023-07-22%20at%2012.28.32%20PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>Web layer: </b>
<br />
<br />
The Web layer consists of two Amazon Linux 2023 instances deployed across two subnets. These instances serve a dual purpose, functioning as both a Bastion host and a web host. An Internet-facing Application Load Balancer ensures the seamless functioning of the Web tier.
Additionally, the Web layer employs encrypted Amazon <b>Elastic Block Store (EBS)</b> volumes to ensure the security and protection of data.

The primary purpose of the Web layer is to host a website tailored for license and subscription sales. Customers gain access to this website by providing their login credentials. To illustrate the website's capabilities, we have developed a sample version for demonstration purposes.
<br/>
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/dd16f04a74ecb419858326120217ef67a4de1fa5/website.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>

<br />
<br />
<b>App layer: </b>
<br />
<br />
The App tier is securely placed in the private subnet, ensuring restricted access. To interact with the App tier, access is granted only through the bastion host residing in the Web layer, utilizing <b>SSH</b> access via a 4096-bit <b>RSA public key</b>. An <b>internal application load balancer</b> is employed within the App tier to manage and distribute traffic effectively.
<br />
<br />
Inside the App tier, the EC2 instance is equipped with MySQL client software, enabling the execution of MySQL queries and facilitating seamless interactions with the database hosted in the data tier. This architecture ensures a robust and controlled environment for managing database operations and enhances the overall security of the system.
<br/>
<br/>


<b>Data layer: </b>
<br />
<br />
In the production VPC, the data tier is thoughtfully positioned in a private subnet to ensure enhanced security. To efficiently manage database operations, we have provisioned an RDS instance with a MySQL engine. Moreover, to ensure high availability, data durability, and fault tolerance, we have created a read-only replica of the database in a separate availability zone.

To maintain strict security measures, the data tier is linked to a NAT gateway, while security groups and Network Access Control Lists (NACLs) have been meticulously configured to disallow internet access. This configuration safeguards against unauthorized access from external networks.

Access to the data tier is exclusively permitted for the app tier. The app tier accesses the data tier using specific credentials. Furthermore, the data tier's RDS instance has only the 3306-port open, exclusively receiving MySQL queries from the app tier. These measures collectively create a robust and secure architecture for managing sensitive data, mitigating potential risks and ensuring smooth database operations.
<br/>
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/148a32534f4df2dd476f408f0014df92a37393af/database.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />


<b>Database Management and MySQL Queries: </b>
<br />
<br />
In the app tier, the EC2 instance is equipped with MySQL client software, enabling the execution of MySQL queries and seamless interaction with the database located in the data tier. This setup allows for efficient communication between the application and the underlying database, ensuring smooth data retrieval and management.
<br/>
<br/>
Presented below is the table created in the data tier.
 <br/>
 <br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/bd0c89d5180e37e52a16d72c78f6317843fab18f/table.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
An example showcases a sample MySQL query execution.
 <br/>
 <br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/28eb95fcc27bf089ace1420cb3fc40a335686d1d/mysqlquery.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/09c9e456828a73435f3787569e87142603d3b398/queryresult.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<b>Network Segmentation </b>
<br />
<br />
To improve security, we employ sophisticated network segmentation techniques to establish isolated security zones. This involves implementing stringent access controls and network policies to regulate traffic flow and minimize lateral movement. We use <b>Network Access Control Lists (NACLs)</b> to govern both incoming and outgoing traffic at the subnet level. Furthermore, <b>Security Groups</b> are utilized to control access at the instance level and <b>Application Load Balancers</b>, which manage traffic between different subnets within the production VPC. These measures create a robust security framework, safeguarding our infrastructure and data from unauthorized access and potential threats.
<br />
Below, we present the network architecture's diverse security groups (SG) intended to regulate traffic flow between different tiers of the system.
<br />
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/bf1f5885fdc1b8dd609280bba6d3831f130ad529/sgs.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<b>Identity and Access Management (IAM) </b>
<br />
<br />
To effectively implement this, we leverage robust identity and access management (IAM) tools on AWS. These tools enable us to manage access controls for users, groups, and roles, ensuring authorized access to specific resources following <b>the principle of least privilege</b>. To safeguard the root AWS account, we activate multi-factor authentication (MFA) for an extra layer of security. Administrator users handle daily admin tasks, and non-root users are protected with MFA.

For programmatic access to AWS from Terraform, we generate unique, short-term access keys for authorized users, eliminating the need to share passwords or keys. We enhance security and monitor user activities using AWS CloudTrail, ensuring compliance, tracking resource changes, and facilitating troubleshooting.

A few of the IAM roles are listed in the following table.
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/a511621ee640c1618aea0eab8d8b5dedec527ade/IAM.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<b>Virtual Private Network (VPN) </b>
<br />
<br />
In the business scenario, a secure Virtual Private Network (VPN) connection was essential to link the cloud and on-premises environments. The VPN ensures encryption in transit, establishing a secure connection for employees accessing cloud resources. To accomplish this, we utilized an AWS CloudFormation template, simplifying the deployment process of a site-to-site VPN connection using strongSwan. This approach guarantees a robust and secure communication channel between the two environments, enhancing data protection and enabling seamless resource access.
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/002fe998f80c7dcfc977949908266fca3183b53d/VPN.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<h3>Vulnerability Management - Tenable.io</h3>
<br />
Securing our infrastructure relies on the crucial practice of vulnerability management. A reliable vulnerability management tool is essential as it detects security vulnerabilities and assesses associated risks. Based on these evaluations, organizations can make informed decisions regarding remediation or acceptance of risks.

Vulnerability management is an ongoing process, conveniently depicted through a vulnerability management life cycle. It commences with meticulous preparation and obtaining a comprehensive asset account. Subsequently, necessary scans are conducted to identify vulnerabilities. The following step involves thorough analysis and prioritization of which vulnerabilities should receive immediate attention. This systematic approach empowers organizations to proactively fortify their security measures and effectively mitigate potential risks.

Given the scope of our project, performing comprehensive scans of the entire architecture is not feasible. However, to bolster our security measures, we have conducted fundamental scans using advanced vulnerability management tools, specifically tenable.io. For this purpose, we employed both <b>Nessus Agent</b> and <b>Nessus Scanner</b> to enhance our vulnerability detection and management capabilities.

<b>Nessus Agents</b> offer the advantage of not requiring credentials management since they operate directly on the target device. This allows them to collect local vulnerability data at a high frequency. However, their limitation lies in providing an "inside-out" view of the device's vulnerabilities, focusing solely on internal perspectives.

<b>Nessus Scanners</b> offer broader coverage as they can scan the entire network, identifying any potential vulnerabilities. With the ability to use provided credentials, they can also access the "inside-out" view of the device's vulnerabilities. However, managing credentials, permissions, and dealing with failed login issues become necessary trade-offs. Additionally, the network's impact restricts the scanning frequency, reducing the ability to scan as frequently as with Nessus Agents.

In our setup, we have deployed Nessus Agents on the EC2 instances within the Web and App tiers of the Prod VPC. We conducted a Basic Agent Scan on these instances to assess vulnerabilities. Additionally, a Nessus Scanner was installed on an EC2 instance within the On-prem VPC.

Using the Nessus Scanner, we executed a Basic Network Scan and a Host Discovery Scan, specifically targeting the EC2 instances within the Non-Prod VPC. These scans enable us to gain valuable insights into the security status of our infrastructure, allowing us to address any potential vulnerabilities and enhance overall security.
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/68d929a1fa5f6b89ce75fe0bce96cb4fe2914fae/Screenshot%202023-07-26%20at%204.00.36%20PM.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
Below is a sample agent scan result from our recent scan on an instance within the production environment. The scan revealed several critical and high-severity vulnerabilities, primarily attributed to outdated software versions. We promptly addressed these vulnerabilities by diligently updating the software, ensuring enhanced security and safeguarding our infrastructure from potential threats.
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/4b84d94611cf6e60a8be9d18e70aa0ecca740148/agent.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the non-production environment, we utilized on-premises scanners to conduct both a Host Discovery scan and a Basic Network Scan. The Host Discovery scan yielded information at an info-level severity, detecting remote hosts that responded to pings and revealing details about the scan, such as scanner type and duration.

The Basic Network Scan revealed two medium-level severity vulnerabilities:

The remote web server supports Trace and/or Track methods, commonly used for web server debugging. This can be resolved by disabling these HTTP methods.
The server's SSL certificate is untrusted, which can be addressed by obtaining a valid SSL certificate.
Taking appropriate measures to mitigate these vulnerabilities ensures a more secure and reliable non-production environment.
<br />
<br />
<h3>Improvements</h3>
<br />



To further enhance the hybrid cloud environment's security and efficiency, several future improvements can be considered:

1. Implement SSL certificates for HTTPS to encrypt web traffic and protect data in transit, safeguarding sensitive information from interception.

2. Replace the bastion host with AWS Session Manager for more secure and streamlined instance management, eliminating the need for direct SSH access and providing better control and auditing.

3. Create web servers in private subnets and utilize a proxy server in public subnets to reduce the attack surface and gain granular control over incoming traffic, enhancing security.

4. Consider SASE/SSE zero-trust solutions as an alternative to traditional VPNs for comprehensive and efficient network access and data protection.

5. Utilize a web application firewall (WAF) to detect and mitigate web-based attacks, such as SQL injection and cross-site scripting, adding an extra layer of protection to the production environment.

6. Implement Tenable Credentialed Scans for improved vulnerability management, conducting authenticated scans to gain deeper insights into the infrastructure's security posture and remediate potential vulnerabilities.

7. Establish a robust incident response plan and implement security event notifications to promptly detect, respond to, and recover from security incidents, minimizing the impact of potential breaches and ensuring timely remediation.

By adopting these measures, the hybrid cloud environment can stay resilient against security threats, ensuring data protection and smooth operations.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
