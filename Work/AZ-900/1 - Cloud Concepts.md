
2024-06-08 15:09

Status:

Tags: [[AZ-900]]

# Cloud Concepts

### High Availability;
	- Traditional vs Cloud 
	T = You own the hardware
		you have physical access 
		you cant "just add servers."
	C = you dont own the hardware 
		add more servers with a click 
		if hardware fails, replace it instantly 
		use clusters to ensure high availability
	- High Availability does not necessarily mean infinite availability 
	- High Availability doesn't guarantee 0 downtime 

### Reliability;
	- refreed to as fault tolerance or disaster recovery is a term used to describe the resilience of cloud computing 
	- Resilience = ability of a system to recover from failures and continue to function 
	- Deploy in multiple Locations:
		- Global-scale computing 
		- Protects against regional failure/disaster 
	- No single point of failure =
		- Resources in multiple locations 
		- If one computer goes down, others pick up the load 
		
### Scalability;
	- Automatically adjust resorces to meet demand i.e. scale up when its busy and scale down when theirs no traffic to the application
	
	- Don't overpay for services:
		- Automatically reduce resources when demand drops 
	- Horizontal (H) vs Vertical Scaling (V):
		H = Adding additional VMs/Containers, "scaling out"
		V = Increasing power (e.g. CPU/RAM) of existing VMs, "scaling up"
	- 'Typical' cloud model = Horizontal scaling
	
### Predictability;
	- Predictable performance and cost:
		- consistent expereince for customers regardless of traffic 
		- autoscaling, load balancing, and high availability provide a consistent expereince 
	- costs:
		- No unexpected surprises 
		- track and forecast resource usage (costs) in real time
		- analytics provide patterns/trends to optimize usage 

### Management:
	- Security:
		- full control of the security of your cloud environment. Patches, maintenance, network control, and more!
	- Governmance:
		- standarlized environments
		- regulartory requirements
		- audit for compliance 
	- Manageability:
		- Management of the cloud: Autoscaling, Monitoring, Template-based deployments 
		- Management in the cloud: Portal, CLI, APIs 
	
	Exam tips: Cloud computing has terms that are specific and critical to understanding it.



### Economy of cloud computing:
	- Capital Expenditure:
		- is buying hardware outright, paid upfront as a onetime purchase 
		- def: Money spent by a business or organisation on acquiring or maintaining fixed assets, such as land, buildings, and equipment 
	- Operational Expenditure:
		- is ongoing costs needed to run your business 
		def: an going 
	Consumption-based:
		- pay only for what you use 
		- pricing lets you pay only for what you use 
		

### 3 cloud service models:

 1. Infrastructure-as-a-Service (IaaS):
	- Infrastructure = actual servers/virtual servers 
	- scaling is fast 
	no ownership of hardware
	
 2. Platform-as-a-Service (PaaS):
	- Superset of IaaS
	- PaaS supports web application life cycle 
	- Avoids software license hell 
	
 3. Software-as-a-Service (SaaS):
	- Providing a managed service 
	- pay an access fee to use 
	- no maintenance and latest features
	
4. Serverless:
	- Dont have to manage servers (effectively using someone else's)
	- Azure functions is the best know serverless service 
	- serverless architecture takes PaaS to the most extreme by fully abstracting away the server, 
	in such a way that a single function of code can be hosted, 
	deployed, run and managed without even having to maintain a full application  
	
## Identifying cloud service models:

### IaaS:
	- organisation has complete control of the infrastructure 
	- dynamic and flexible. can do anything
	- cost varies depending on consumptin
	- services are highly scalable 
	- multiple users share a single piece of hardware
	examples = VM, VNet, Storage 

### PaaS:
	- resources are virtualized and can easily be scaled uo or down as needed
	- services often assist with the development, testing and deployment of apps 
	- multi-user access via the same development application
	- integrates web services and databases 
	examples: app services, azure CDN, Cosmos DB

### SaaS: 
	- managed from a central location 
	- hosted on a remote server 
	- accessible over the internet 
	- users not responsible for hardware or software updates 
	- rate limiting/Qos
	examples: microsoft 365

## Shared Responsibility Model:
	- Physical Infrastructure (PI), Operating System(OS), Network Controls (NC), Identity and Directory(ID), Application Management(AM), Information and Data(IData), Devices and Accounts (DA)
	- SaaS Azure for (PI, OS, NC, AM), 50/50 for ID - Azure and you, IData = you and DA = you
	- PaaS Azure for (PI, OS), 50/50 for NC, ID and the rest is you 
	- IaaS Azure for (PI) and the rest is on you
	- On-Premises all of it is your responsibility

## Exam tips: 
	Service is the core of Azure, and there are three main ways to go about it. 
	- IaaS provides servers, storage, and networking as a service
	- PaaS is a superset of IaaS and also includes middleware, such as database management tools
	- SaaS is when a service is built on top of PaaS, like office 365
	- Serverless means that you don't have any servers. Let's a single function be hosted, deployed, run and managed on its own
	
### Private cloud:
	- is azure on your own hardware in a location of your choice
	- All the benefits of public cloud, but you can lock it down
	- A lot of staff required 

### public cloud: 
	- is azure, aws, gcp
	- no upfront costs, but monthly usage 
	- little control over services and infrastructure

### Hybrid cloud:
	- model is the best of private and public, but could be complex 




## References
