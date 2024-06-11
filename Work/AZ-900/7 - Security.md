
2024-06-08 15:57

Status:

Tags: [[AZ-900]]

# 7 - Security

## Defense in depth:
	1. Single security measure is insufficient: Having just one security measure for cloud infrastructure is inadequate. Multiple layers of defense are necessary.
	2. Historical analogy: Using the example of a castle with various layers of defense to protect the king as an illustration of defense in depth.
	3. On-premises infrastructure: Similar to protecting physical assets like buildings and hardware, on-premises infrastructure requires multiple security layers, including physical access controls, usernames, passwords, firewalls, etc.
	4. Azure cloud security layers:
		- Physical: Access to Azure data centers is restricted to authorized personnel.
		- Identity and access: Managed by Azure Active Directory, controlling access and identity management.
		- Perimeter: Protection against various attacks like DDoS, protocol attacks, etc.
		- Network: Filtering traffic to and from Azure using virtual networks and applying security standards.
		- Compute: Protecting virtual machines and databases from intruders.
		- Application: Security provided to Azure applications through application gateways and firewalls.
		- Data: Encryption and protection of data stored on Azure against unauthorized access.
	5. Conclusion: Microsoft Azure offers multiple layers of security for cloud infrastructure, akin to a layered cake, ensuring comprehensive protection.
## Securing Network connectivity:
	1. Network Connectivity in Azure: 
		- All services on Azure rely on network connectivity to function, facilitating communication with users, processors, and other Azure services. Thus, securing this network connectivity is paramount to ensure the integrity and availability of services.
	2. Azure Firewall: 
		- This fundamental security component operates akin to a bridge, controlling access to resources. It enforces rules to determine whether network traffic is permitted, akin to a town's entrance gate. Unauthorized traffic is denied, safeguarding Azure resources from potential threats.
	3. DDoS Attacks: 
		- Distributed Denial-of-Service (DDoS) attacks inundate servers with an overwhelming volume of traffic, rendering services inaccessible. Notable instances of such attacks underscore the importance of robust defense mechanisms.
	4. Azure DDoS Protection Service: 
		- Azure offers a specialized service to mitigate the impact of DDoS attacks. It detects and deflects malicious traffic away from Azure services, ensuring uninterrupted service delivery. This service operates globally, allowing for effective mitigation regardless of the attack's origin.
	5. Network Security Groups (NSGs): 
		- NSGs serve as personalized firewalls for Azure resources, enabling granular control over network traffic. They define rules governing resource access and can be applied to various components, including virtual networks, subnets, and network interfaces.
	6. Application Security Groups (ASGs): 
		- ASGs extend the capabilities of NSGs to protect specific applications. By grouping virtual machines and defining network security policies based on application structure, ASGs enhance security and streamline management.
	7. Securing Azure Networks: 
		- A comprehensive approach to securing Azure networks involves leveraging firewalls, DDoS protection, and NSGs. These measures collectively form the first line of defense against unauthorized access and malicious activity.
	8. Importance of Security Measures: 
		- Given the potential ramifications of security breaches, including financial losses and damage to reputation, prioritizing network security is essential for safeguarding Azure resources and ensuring operational continuity.
			
## public and private endpoints: 
	1.- **Securing Network Access to Azure Managed Services**:
	  - Focus on securing access to Platform as a Service (PaaS) services through public and private endpoints.
	  - By default, PaaS services in Azure are publicly reachable over the internet.
	  - Accessing these services over a virtual network may still involve traffic traversing the public internet.
	  - Public endpoints do not mean that resource contents are accessible to the public; authentication is still required.

	2.- **Public and Private Endpoints**:
	  - Public endpoints expose PaaS services to the public internet, potentially posing security risks for sensitive content.
	  - Two native services available for limiting or removing public exposure: Service Endpoints and Private Endpoints.

	3.- **Service Endpoints**:
	  - Allows private connections from virtual network subnets to Azure PaaS services.
	  - Traffic from subnet resources to the managed service travels over Microsoft's private backbone, enhancing security.
	  - Optional configurations include restricting access to managed services only from endpoint-enabled subnets and limiting access from specific public IP addresses.
	  - Limitations include providing secure access only to Azure virtual networks, public endpoint still exists, and access is granted to the entirety of a managed service, not specific instances.

	4.-**Private Endpoints**:
	  - Acts as a managed network interface within a virtual network subnet, providing private connections to specific instances of services.
	  - Offers truly private connectivity, including access from hybrid or on-premises networks, and enables private connectivity to other paired virtual networks.
	  - Provides the ability to completely disable public access to connected services, ensuring complete privacy.
	  - Overcomes limitations of service endpoints, offering enhanced security and privacy for accessing Azure managed services.

	5.- **Implementation Scenario**:
	  - Example scenario involving an existing VPN connection from a home office to an Azure virtual network.
	  - Requirement to privately access sensitive Azure SQL databases and completely disable public internet exposure.
	  - Solution involves using private endpoints to establish private connections, ensuring secure access and reducing public exposure.

	6.- **Conclusion**:
	  - Discussion emphasizes the importance of properly securing access to Azure managed services through private endpoints.
	  - Private endpoints offer superior security and privacy compared to public endpoints, ensuring sensitive data remains protected.
	  - Understanding and implementing private endpoints is crucial for enhancing the security posture of Azure deployments.
## Microsoft Defender for cloud: 
	1.- **Microsoft Defender for Cloud**:
	  - Formerly known as Azure Security Center, it provides a comprehensive solution for managing security features on Azure.
	  - Offers a unified view of security posture by alerting and protecting against threats detected by Azure.
	  - Works in hybrid cloud setups, monitoring virtual machines both on-premises and on Azure or other cloud providers.
	  - Monitors policy compliance, assigns secure scores, and integrates security information from other cloud providers using SIEM tools.
	  - Requires Azure Arc for multi-cloud integration.
	  - Alerts users about security vulnerabilities such as outdated software or unnecessary public-facing endpoints.
	  - Follows a three-step process: defining security policies, actively protecting resources, and responding to security incidents.
	  - Streamlines regulatory compliance requirements through the regulatory compliance dashboard.
	  - Assesses resource security hygiene and recommends fixes to improve security best practices.

	2.- **Defender for Cloud Features**:
	  - **Policy and Compliance Monitoring**: Defines security policies and evaluates the validity of service configurations.
	  - **Active Protection**: Monitors policies and takes action on outcomes to limit exposure to threats.
	  - **Incident Response**: Raises security alerts and requires users to investigate and adjust Azure implementations accordingly.
	  - **Regulatory Compliance Dashboard**: Tracks compliance with regulatory standards related to cloud computing.
	  - **Resource Security Hygiene**: Assesses resource configurations in relation to security best practices and recommends fixes for improvement.
## Azure Key Vault: 
	1. Secure hardware:
		- key vault hardware is secure too
		- not even microsoft can access the keys in it
	2. Application isolation:
		- application cant pass on secrets, nor access another application's secrets
	3. Global scaling:
		- scale globally like any other managed azure service 
## Azure Information protection:
	1.- **Azure Information Protection (AIP)**:
		  - A service designed to enhance the security of documents, emails, and other data shared outside the organization.
		  - Addresses concerns about data access, especially when stored on company servers and resources.
		  - Enables classification of data based on sensitivity, either automatically through policies or manually by users.
		  - Allows tracking of activities on shared data and provides the ability to revoke access if necessary.
		  - Integrates with Office 365 and other Microsoft applications, providing controls for protecting and classifying data.
		  - Offers one-click securing of data and documents directly within Microsoft Office and other apps.
		  - Example scenario: Melanie uses AIP to secure a sensitive attachment before sending an email to Tony, ensuring that only authorized users can access the document.
## Azure Sentinel: 	
	- **Purpose**: Azure Sentinel is a security information and event management (SIEM) tool 
		designed to assist in managing security concerns within Azure cloud infrastructure.

	- **Functionality**:
	  1. **Data Collection**:
		 - Collects data from various sources including network controllers, virtual machines, DNS traffic managers, etc.
		 - Aggregates and normalizes the collected data for usability.
	  2. **Analysis**:
		 - Analyzes the aggregated data to detect any potential threats.
		 - Utilizes behavioral analytics powered by artificial intelligence to identify abnormal patterns and behaviors.
	  3. **Response**:
		 - Identifies security breaches and threats, allowing for investigation and appropriate action.
		 - Streamlines the investigation process by handling 90% of the initial heavy lifting.
	  4. **Integration**:
		 - Integrates seamlessly with AWS services, allowing data from AWS to be fed directly into Sentinel for analysis and threat detection.
	  5. **Scalability**:
		 - Takes advantage of Azure's vast resources to offer limitless speed and scale, matching the needs of any infrastructure.
	  6. **Additional Features**:
		 - Offers features tailored to the needs of security professionals, such as comprehensive behavioral analytics and seamless AWS integration.

	- **Benefits**:
	  - Reduces the workload on security teams by automating the detection of security threats.
	  - Enhances security posture by leveraging advanced analytics and integration capabilities.
	  - Ensures scalability to accommodate growing infrastructure needs.
	  - Simplifies the investigation process by providing actionable insights into potential threats.
	  - Offers peace of mind through comprehensive threat detection and response capabilities.

	- **Conclusion**:
	  - Azure Sentinel serves as a powerful tool for protecting cloud infrastructure, offering advanced threat detection, seamless integration, and scalability. 
		It significantly reduces the burden on security teams and provides comprehensive security coverage for Azure environments.
## Azure Dedicated Hosts: 
	- **Purpose**: Azure Dedicated Hosts offer a solution for users who require dedicated hardware for their virtual machines (VMs) due to compliance requirements or a lack of trust in shared hardware.

	- **Functionality**:
	  - Provides full physical servers with complete control for users.
	  - Allows provisioning similar to VMs in Azure but with significant differences and benefits.
	  - Ensures hardware isolation at the physical layer, preventing unauthorized access to the server.
	  - Only VMs chosen and created by the user are placed on the dedicated hardware.
	  - Offers control over maintenance schedules, allowing for reduced impact on sensitive workloads.
	  - Enables compliance with stringent requirements by giving users control over the hardware.
	  - Allows users to leverage cloud computing benefits such as availability zones, fault isolation, high availability, and scale sets.
	  - Supports various VM image options including Windows, Linux, and SQL Server.
	  - Provides cost savings by allowing the use of existing software licenses, such as those for Windows Server or SQL Server.

	- **Considerations**:
	  - While Azure Dedicated Hosts offer benefits for hardware-conscious users and those with compliance requirements, they can be expensive.
	  - Users should use Dedicated Hosts judiciously to optimize cost-effectiveness.

	- **Conclusion**:
	  - Azure Dedicated Hosts serve as an ideal solution for users who require dedicated hardware for their VMs, 
		offering complete control, enhanced security, compliance support, and cost-saving opportunities. 
		However, users should carefully assess their usage to ensure cost-effectiveness.


## References
