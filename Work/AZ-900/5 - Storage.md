
2024-06-08 15:47

Status:

Tags: [[AZ-900]]

# Storage

## Overview:
	- storage account = unique azure namespace 
		- every object in azure has its own web address 
		- i.e acloudguru.<storage-type>.core.windows.net
## Blob:
	- "Binary Large Object"
	- Scenarios:
		- Images => store various sizes and formats as a single image storage 
		- All types => store any kind of files and have distributed acess through the azure cloud storage 
		- Streaming => stream audio and video directly from your blob storage 
		- Log files => write to log files regardless of size and frequency 
		- Data store => store any kind of data at scale, such as for archiving, backup, restore and disaster recovery
	- Azure supports 3 types of blobs:
		- Block => store text and binary data up to 4.7TB made up of individualy managed blocks of data 
		- Append => block blobs that are optimized for append operations. Works well for logging where data is constantly appended 
		- Page => store files up to 8TB. Any part of the file could be accessed at any time, for example a virtual hard drive 
	- Blob (Pricing Tiers):
		- Hot => frequently accessed files. Lower access times and higher access costs 
		- Cool => Lower storage costs and higher access times. Data remains here for at least 30 days
		- Archive => Lowest costs and highest access times 
		
## Disk:
	- Azure Manages => You don't have to worry about backup and uptime 
	- Size and Performance => Microsoft and azure guarantees size and performance as per your agreement with them 
	- Upgrade => Easy to upgrade your disk size and type 
	- Disk Types:
		- HDD => Spinning hard drive. Low cost and suitable for backups
		- Standard SSD => Standard for production. Higher reliability, scalability and lower latency over HDD
		- Premium SSD => Super fast and high performance. Very low latency. Use for critical workloads 
		- Ultra Disk => For the most demanding, data-intensive workloads. Disks up to 64TB

## File:

	- On-Premises Storage:
		- Constraints => you only have a limited amount of storage 
		- Backups => Time and resources spent on maintaining backups
		- Security => It ca be hard to keep all data secure at all times. Specialist assistance often needed 
		- File sharing => Can be difficult to share files across teams and organizations 
	- File Benefits:
		- Sharing => Share access to the azure file storage across machines and provide access to your on-prmises infrastructure 
		- Managed => You dont have to worry about hardware or operating system 
		- Resilient => Network and Power outages wont affect your storage 
	- Scenarios:
		- Hybrid => Supplement or replace your existing on-premises file storage solution 
		- Lift and Shift => Move your existing file storages and related services to Azure 

## Archive:
	- Overview:
		- Requirement => Policies, legislation and recovery can be requiremnets for archiving data. These can be very large amounts of data 
		- Lowest Prices => The archive tier is the lowest price for storage on Azure. A few dollars a month can get you terabytes of space 
		- Features => Durable, encrypted and stable. perfectly suited for data that is accessed infrequently 
		- Free Up Premium Storage => with cheap archive storage you can free up your more premium on-premises storage 
		- Secure => Fully secure to allow for any personal data such as financial records, medical data and more 
		- Blob => Archive storage is blob storage, so the same tools will work for both 

## Storage Redundancy:
	- If one copy fails/is inaccessible, data is still available 
	- Azure storage always creates multiple copies of your data:
		- Automatic
		- Minimum of three copies 
		- Invisible to end user 
		
	Multiple Redundancy Options:
		- Different location Scopes
			- Single zone, multiple zones, multiple regions 
			
	Single Region:
		- Locally Redundant Storage (LRS)
			- LRS is our lowest cost redundancy option because it creates 3 copies of your data within a single location or, in other words, 
				within a single data center or a single availability zone
			- lowest cost option if cost is a factor
			- will protect against a single disk failure, specifically these copies that are located on different storage racks in your single data center
			- this option does not protect against temporary zone or region-wide outages
		- Zone-Redundant Storage (ZRS)
			- 3 copies of your data, instead of being hosted in a single location or availability zone, it instead spans 3 different availability zones. 
				- one copy of our data in each availability zone within that region.
			- This increases our reliability or high-availability in that it will protect against a zone outage, in which if AZ1 is unavailable, our data is still accessible because AZ2 and AZ3 also hosts our data. 
				However, it does not protect against a region-wide outage because all of our data is replicated within a single zone
	Multi-Region:
		- Geo-Redundant Storage (GRS)
			- With geo-redundant storage, we have 3 copies in 2 different regions. 3 copies will be in our primary region physical location in an LRS or a single zone configuration, 
				and we have an additional 3 copies, or 6 total
			- increases our reliability in that it helps protect against a primary region failure. In other words, if Region 1 becomes unavailable, Azure Storage will then failover to Region 2.
			- no primary region zone redundancy 
			- can configure read access from secondary region for high availability 
		- Geo-Zone-Redundant Storage (GRZS)
			- COpy across three availability zones in primary region (ZRS)
			- Three copies in secondary region physical location/zone (LRS)
			- protect against primary region failure and primary region zone failure 
			-  can configure read access from secondary region for high availability  
	All options include:
		- Three copies in primary region 
		- Three copies in secondary region (multi-region options)

## Moving Data:
	Concept: Moving data into and out of azure storage 
	- Different solutions based on: 
		- Transfer frequency (occasional/continous)
		- Data Size 
		- Network bandwidth 
	
	- AzCopy
		- Transfer blobs and azure files 
		- useful for scripting data transfers 
	- Azure Storage Explorer 
		- Downloaded application
		- User-friendly graphical interface 
			- drag-and-drop interaction 
		- Move al storage account formats 
	- Azure File Sync 
		- synchronize azure files with on-premises file servers 
		- local file server performance + cloud availability 
		- Use cases:
			- Backup local files server
			- Synchronize files between multiple on-premises locations
			- Remotes users access azure files 

## Additional Migrations Options:
	- Scenario: Transfer LOTS of data and/or limited bandwidth 
		- Lots = Too much to transfer over the internet 
		- Relative to available network bandwidth
	- Offline data transfer to/from Azure 
	- Copy data to physical data storage device (Data Box)
		- Encrypted 
		- Rugged
	- Ship Data Box to/from Azure 
		- To Azure: Data Box data transferred to storage account 
		- From Azure: Data Box delivered to on-premises location for on-site transfer 
	- Data Box Use Cases:
		- Initial bulk data migration 
		- Disaster recovery 
			- Restore Azure backup to on-premises location 
		-Security requirements 
			- Sensitive data that cannot be sent over the internet 
## Premium Performance Options:
	- stored on SSDs
		- separate considerations from managed disk types 
	- key considerations:
		- available storage types for each performance option 
		- redundancy options 
			- trade more performance for less redundancy 
	- standard:
		- the default - supports all storage types 
		- all redundancy options 
	- Premium:
		- premium block blobs: Redundancy = LRS/ZRS only
			- ideal for low-latency blob storage workloads (AI applications, IoT analytics etc)
		- premium page blobs: Redundancy = LRS only single zone 
			- unmanaged virtual disk 
		- premium file shares: Redundancy = LRS/ZRS only
			- ideal for high-performance enterprise (file server) applications 
			- supports both server message block (SMB) and network file system (NFS) file shares 



## References
