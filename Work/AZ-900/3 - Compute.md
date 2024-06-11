
2024-06-08 15:39

Status:

Tags: [[AZ-900]]

# Compute

## Virtual Machines:
	- Part of the IaaS service
	- Azure portal to manage large numbers of VMs and even hybrid clouds 
	- Azure blueprints to make your VMs comply with comapny guidelines 
	- Azure recommends better security, higher availability and greater performance 
	- VMs; can choose amount of RAM, number of CPUs and the type of OS
	### Pros: 
		- use VMs when you need to control all aspects of an environment or machine 
		- Install specific applications on windows or linux machines 
		- move existing resources and VMs to azure from on-premises or another cloud provider 
	Cons:
		- if you can use another azure service instead, it is often worth it
		- A lot of maintenance with VMs, operating system updates, patches and security concerns  
	- VMs is your machine exclusively 
	- pricing goes up as resources go up
## Scale Sets:
	- simple to manage mulktiple identical VMs using a load balancer
	- One VM fails or stops, the others in the scale set will keep working 
	- automatically match demand by adding or removing VMs from the scale set 
	- run up to 1000 VMs in a single set 
	- no added cost for using scale sets 
	Scale sets are taking VMs to the next level. And keeping your sanity.
	- resource usage increases, more VMs are activated to take the load (users etc)
## App Services:
	- app services are a PaaS offering on Azure 
	- web Apps are used to host web sites and web applications
	- web apps for containers can host your existing container images 
	- API Apps can host your data backend services 
	### Web App:
		- runs on both windows and linux platforms
		- supports a lot of languages such as C#, JAVA, C++, Node, Ruby, Python, PHP etc.
		- azure integration for easier deployment
		- Auto-scaling and load balancing 
	### Web App for Containers:
		- a container is completely self-contained 
		- all dependencies are shipped inside the container 
		- deploy anywhere with a consistent expereince 
		- reliable between environments 
	### API Apps:
		- use a range of programming languages 
		- connect other applications programmatically
## Azure Container Instances:
	### Features:
		- Manage Application Dependencies:
			- all the dependencies for an application are included in the container image 
			- you can manage the application and its dependencies with confidence 
		- Increased Portability:
			- Applications running in containers can be deployed easily to multiple different OSs and hardware platforms 
		- Consistency:
			- the operations team can rely on containers being the same every time, no matter which target they are being deployed 
		- Less Overhead:
			- VMs require a lot more maintenance and updates 
			- containers dont have any components relating to the OS that require maintenance
		- Efficiency:
			- development, deployment and maintenance are all more efficient when using containers 
			- scaling and patching is much simpler 
		- use containerized applications to process data on demand, by only creating the container image when you need it. save some cash in the process 
## Azure Kubernetes Service:
	- open source = anyone can contribute to the code base 
	- keeps track of lots of parts of a system, makes sure containers are configured correctly to work together.
	- will deploy more images of containers as needed 
	- automatic monitoring of application to determine when to scale the number of containers used 
	- reuse container architecture by managing it in kubernetes => makes setup quicker and confidence in the system increase 
	- dont have to worry about the infrastructure and hardware. Get identity and access management, elastic provisioning and much more.
## Azure Container Registry (ACR):
	- Keep track of current valid container images 
	- Manages files and artifacts for containers 
	- feeds container images to ACI and AKS
	- Use Azure identity and security features 
## Windows Virtual Desktop:
	- Reuse windows 10 Licenses => reduce costs and streamline license usage 
	- multiple users can use the same VM instance 
	- access anywhere and on any device with an internet browser 
	- use azure storage to secure your data 
## Functions:
	### IaaS and PaaS:
		- install your own applications
		- access to the operating system 
		- resource visibility
		an app service has no OS access, but has resource access 
	### Function:
		- smallest compute service on Azure 
		- a single function of compute 
		- called, or invoked, via a standard we address (URL)
		- runs once and stops 
	- its serverless so only focus on functionality 
	- only runs when theirs data to process i.e. no traffic = no resource usage 
	- no resource running = no cost 
	- function fails => wont affect other function instances 




## References
