
2024-06-08 15:26

Status:

Tags: [[AZ-900]]

# Azure architecture:

## Regions:
	- "A set of datacenters" = each region has more than one data center, which is a psychical location
	- "Latency defined perimeter" = latency is the time it takes data to travel. Also means that datacenters are not "too far" from each other 
	- "regional low-latency network" A fiber connection between data centers in the region 
	**How to choose a region:** Will have to choose which of these 3 are the most important 
		- location = choose a region closets to your users to minimize latency
		- features = some features arent in all regions, if you need a specific feature, some regions might be unavailable 
		- price = the price of services vary from region to region 
	- Paired regions:
		- each region is paired i.e. australia east = australia south 
		- outage failover -> if the primary region has an outage you can failover to the secondary region 
		- planned updates -> only one region in a pair is updated at any one time 
		- replication -> some services used paired regions for replication 
### Availability Zones:
	- physical location -> each vailability zone is a physical location within a region 
	- independent -> each zone has its own power, cooling and networking
	- zones -> each region has a minimum of 3 zones (can show a drawing)
### Resource Groups:
	- each resource can only exist in 1 resource group
	- add or remove resources to any source group at any time 
	- move any resource from one resource group 
	- resources from multiple regions can be in one resource group 
	- you can give users access to a resource group and eveything in it 
	- resources can interact with other resources in different resource groups
	- a resource group has a location, or region, as it stores meta data about the resources in it
	- resource group => container that hold resources and isnt a resource itself 
	- All resources belong to a resource group. it isnt a resource, but helps structure your Azure architecture 
### Azure Resource Manager(ARM):
	- group resource handling -> you can deploy, manage and monitor resources as a group 
	- consistency -> deploying resources from various tools will always result in the same consistent state 
	- dependencies -> define dependencies between resources to make sure they don't get in a fight 
	- access control -> built-in features in the ARM make it easy to assign access rigts to users 
	- tagging -> tag resources to easily identify them for 
	- All interaction with azure resources go through the ARM. It is the main Azure Architecture component for creating, updating and manipulating resources 




## References
