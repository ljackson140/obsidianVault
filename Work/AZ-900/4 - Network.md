
2024-06-08 15:46

Status:

Tags: [[AZ-900]]

# Network

## subnets:
	- Resource Grouping:
		- group resources onto the same subnet to make it easier to keep an overview 
	- Address Allocation:
		- more efficient to allocate addresses to resources on a samller subnet 
	- Subnet Security:
		- use network security groups to secure individual subnets 
	Subnet Regions & Subscriptions:
		- a VNet belongs to a sigle region
		- every resource in the VNet must be in the same region
		- a VNet belongs to just one subscription, but a subscription can ahve multiple VNets

## Load Balancer:
	- distributes new inbound flows that arrive on the load balancer's frontend to backend pool instances, according to rules and health probes 
	- inbound flows = traffic from the internat or local network 
	- frontend = the access point for the load balancer. all traffic goes here first 
	- backend = the vm instances recieving traffic 
	- rules & health probes = checks to ensure backend instance can recieve the data	
	scenarios:
		- balance the load of incoming internet traffic into a system or application 
		- a load balancer works well with internal applications 
		- traffic can be forwarded to a specific machine in the backend pool 
		- allow outbound connectivity for backend pool VMs
		

## VPN Gateway:
	- VPN gateway is a specific VNet gateway. it consists of two or more dedicated VMs
	- VNet gateway + "vpn" becomes a vpn gateway
	- sends encrypted data between azure and on premises network 
	- azure gateway subnet, secure tunnel and on-premises gateway makes up a VPN gateway scenario 

## Application Gateway:
	- application gateway is a higher level load balancer
		- works on HTTP request of the traffic, instead of the IP address and port 
		- traffic from a specific web address can go to a specific machine 
		- is a fit for most other azure services 
		- supports auto-scaling, end-to-end encryption, zone redundancy and multi-site hosting 
	- scale application gateway up or down based on the amount of traffic recieved 
	- comply with any security policies. Disable or enable traffic encryption to the backend 
	- span multiple availability zones and improve fault resiliency 
	- use the same application gateway for up to 100 websites 

## Content Delivery Network (CDN):
	- is a distributed network of servers that can deliver web content close to users 
	- improve user expereince and the performance of your application 
	- scale to suit any spikes in traffic, and also protect your main backend server instance from high loads 
	- edge servers will serve request closest to the user. less traffic is then sent to the server hosting your application 
	cache:
		- collection of temporary copies of original files 
		- primary purpose is to optimize speed for an application
		- when a copy expires, a new copy is needed 
	origin server:
		- original location of the files, such as a web application 
		- it is the master copy of your application

## Express Route:
	- direct link between on-premises and azure 
	- enables a private, secure, high-bandwidth, low-latency connection 


## References
