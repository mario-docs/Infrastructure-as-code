## Terraform overview

### What is Terraform?
- automates and manages your:
  * infrastructure
  *  platform
  *  services that run on that platform
- open source and declarative (defines what end/final result you want)
	* declarative = defines WHAT end result you want
	* imperative = defines exact steps - HOW

- tool for infrastructure provisioning, managing existing infrastructure, replicating infrastructure

## Tool for infrastructure provisioning
* so, you've started a project, and now you want to set up your infrastructure from scratch on which the
	  application wil run
* you decided to use AWS platform to build you whole infrastructure on
* as you will see, there will be two different tasks, or two seperate steps of creating the whole setup. One 
  is Provisioning infrastructure (or preparing everything so that the application can be deployed), and the other
  is actually Deploying pplications to it - so you might even have two seperate teams which will perfrom these two
  seperate tasks. 
** a possible scenario - DevOps team configures infrastructure, and developers then deploy applications onto
	 	 the prepared infrastructure
** Terraform is used for the first part where you provision the infrastructure, to prepare it for the 
		   application deployment:
		* create VPC
		* create AWS users and permissions
		* install Docker
		* spin up servers
	
1-Prepare infrastructure: 
	* go to AWS and prepare the setup so that the applications can be deployed there 
  a) (create) private network space
  b) (create) ec2 server instances 
	c) install Docker and other tools
  d) (setup) security (on your servers)
2-Deploy applications
	* once the infrastructure is prepared you can now deploy your Docker applications or Docker containers
	   on that prepared infrastructure
	* Terraform vs Anible:
	* terraform: mainly infrastructure provisioning tool, but it also has capabilities to depoly applications in other tools
		      on that infrastructure
	* ansimble: mainly a configuratino tool, so once the infrastructure is provisioned and it's there Ansimble can now be used
		     configure it and deploy applications, update and install software on that infrastructure
	* terraform is better tool for configuring the infrastructure and Terraform is better for setting up the infrastructure.
	  They are also frequently used in the same time, each for their own strengths
