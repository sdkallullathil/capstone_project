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
With digital transformation and remote work becoming prevalent, the conventional approach of trusting all within the internal network lacks adequate security. Considering our current compliance to the traditional security model, we acknowledge that the immediate adoption of ZTA is not feasible. We understand that transitioning towards zero trust is a gradual process that may take several years to fully implement. Therefore, our strategy involves introducing elements of zero trust into our infrastructure with a long-term objective in mind. <br/>
 <br/>
We have constructed our infrastructure using AWS to create a simulated hybrid-cloud environment, giving utmost importance to adopting Infrastructure as Code (IaC) principles with the help of Terraform. Additionally, we have established vulnerability management by combining Tenable scanners and agents.</p>
<br />


<h2>Languages and Utilities Used</h2>

- <b>Terraform</b> 
- <b>MySQL</b>
- <b>Tenable.io</b>
- <b>HMTL</b>
- <b>SSH</b>

<h2>Cloud Environments Used </h2>

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
<br />
<b>Business Scenario: </b>
<br/>
<p>A software solution provider is planning to transition to the cloud, specifically Amazon Web Services (AWS). The company needs to establish both a production environment and a non-production (development) environment. For the production environment, they require a website to sell licenses/subscriptions and a database to store sensitive customer information like personally identifiable data (PII) such as name, address, phone number, birthday, and gender. Customers will access the website using login credentials. The non-production environment is meant for testing and development, requiring various operating systems. Additionally, the company has requested a secure VPN connection to link their on-premises systems with the cloud environment.</p>
<br/>
<img src="https://github.com/sdkallullathil/capstone_project/blob/7bc9ce23581153fb3879f91db6ec9b48d6c4334f/Team1_Slides_Final.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
<br />
The Production (Prod) VPC is organized in a three-tier architecture spread across two availability zones. It comprises the presentation (or Web) tier, the logic (or App) tier, and the data tier. The presentation tier contains key components responsible for direct user interactions, including the business's e-Commerce website. The logic tier houses essential code that translates user actions into functional application behavior. Meanwhile, the data tier acts as a secure storage medium for the relevant application data. High availability is ensured by deploying all compute and storage resources across two availability zones. Additionally, autoscaling groups are employed for the Web and App tiers, allowing dynamic instance additions or removals based on health checks or scaling policies. This approach ensures continuous availability while optimizing cost management.
<br/>
<br/>
The Development (Non-Prod) VPC serves as a dedicated environment for comprehensive software testing, experimentation with various operating systems, and crucial debugging and troubleshooting activities.

Lastly, a "simulated" on-premises VPC has been implemented to virtually represent the business's physical office space. This VPC hosts a VPN gateway enabling site-to-site VPN connections between the on-premises infrastructure and the cloud environment. This ensures seamless and secure communication between the two environments. <br/>
<br />
<br />
<b>Infrastructure As a Code: </b>
<br />
<br/>
In our AWS cloud infrastructure, we have extensively utilized Terraform for deployment purposes. Terraform empowers us with infrastructure as code (IaC) capabilities, allowing the management and provisioning of AWS resources through declarative code. This approach streamlines the deployment process, eliminating manual errors and ensuring consistency. Moreover, Terraform offers an extensive range of AWS provider resources, facilitating the creation and management of diverse AWS services and configurations. Its modular and reusable code structure further enhances scalability and simplifies maintenance tasks.
<br/>
<br />
<img src="https://github.com/sdkallullathil/capstone_project/blob/9c2cd70727f210d8ad68e6751aac3906599b4c8d/Screenshot%202023-07-22%20at%2011.06.48%20AM.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
