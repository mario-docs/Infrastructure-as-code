## Terraform Overview

### What is Terraform?
- Terraform automates and manages:
  * Infrastructure
  * Platform
  * Services that run on that platform
- An open-source and declarative infrastructure-as-code software tool.
	* Declarative = defines **WHAT** end/final result you want 
	* Imperative = defines exact steps - **HOW**

- A tool for **infrastructure provisioning**, **managing existing infrastructure**, and **replicating infrastructure**.

## Tool for infrastructure provisioning
> So, you've started a project, and now you want to set up your infrastructure from scratch on which the application wil run. Alsp, you decided to use AWS platform to build you whole infrastructure on. And as you'll see, there will be two different tasks, or two seperate steps of creating the whole setup. One is Infrastructure provisioning (or preparing everything so that the application can be deployed), and the other is actually Application deployment - so you might even have two seperate teams which will perform these two tasks. 
  
- A possible scenario - DevOps team configures infrastructure, and developers then deploy applications onto the prepared infrastructure
- Terraform is used for the first part where you provision the infrastructure, to prepare it for the application deployment:
	* Create VPC
	* Create AWS users and permissions
	* Install Docker
	* Spin up servers
	
### 1-Prepare infrastructure: 
 1. (Create) Private network space
 2. (Create) EC2 server instances 
 3. Install Docker and other tools
 4. (Setup) Security (on your servers)
 
### 2-Deploy applications
* Once the infrastructure is prepared you can now deploy your Docker applications or Docker containers on that prepared infrastructure
* Terraform vs Anible:
	* **Terraform**: mainly infrastructure provisioning tool, but it also has capabilities to depoly applications in other tools on that infrastructure
	* **Ansimble**: mainly a configuratino tool, so once the infrastructure is provisioned and it's there Ansimble can now be used configure it and deploy applications, update and install software on that infrastructure
	* **Terraform** is better tool for configuring the infrastructure and for setting up the infrastructure. They are also frequently used interchangeably, each for their own strengths
