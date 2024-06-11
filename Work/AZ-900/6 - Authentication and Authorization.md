
2024-06-08 15:55

Status:

Tags: [[AZ-900]]

# 6 - Authentication and Authorization

## Identity Services:
	- Authentication:
		- Making sure you are you
		- Confirming identity
		- first test for access 
	- Authorization:
		- Comes after authentication 
		- Do you get access 
		- Granular Control 
	- Know the difference to create effective access management 
	- Access management is critical to ensure only the right people and processes have access  
## Azure Active Directory:
	- Active directory was designed for traditional office use with computers and printers 
	- The web is a concept or service was not part of the design for Active Directory. web services were not part of the original vision for active directory in 2000.
	- Active Directory authentication uses services that arent available on Azure 
	- Azure Active Directory (AAD) is not the same as Active Directory, vice versa 
	- AAD can help users both in the cloud on Azure and on your premises 
	- Exam Tips:
		- AAD is not the same as Azure Active Directory
		- Different skillset from AD to Azure AD
		- Every Azure account will have an azure AD Service 
		- A Tenant is a dedicated instance of Azure AD. It represents your organization in Azure 
		- A user can be a member or guest of up to 500 tenants 
		- A subscription is a billing entity. All resources belong to a single subscription 
## Zero Trust Concepts:
	- Trusted Perimeter = corporate network -> devices within the corporate network are trusted and secure 
	- Challenges with trusted perimeter model:
		- Remote work is challenging thus VPN is required
		- Mobile device access even more challenging
	- what is `zero trust`:
		- all users are assumed untrustworthy unless proven otherwise 
		- trusted by identity 
		- regardless of location (trusted/untrusted networks)
		- least privilege - just enough permissions to perform job 
		- simplified, centralized management 
	Zero Trust = Trusted Identities 
## Multi-Factor Authentication:
	- kinda the same as zero trust -> user enters credentials -> user will be emailed or texted a number to enter in order to gain access 
## Conditional Access:
	- If/Then policy to grant access [i.e if user meets condition/s then grant access]
	- often paired with multi-factor authentication 
	- Create conditional Access Policy:
		- Assign signals (conditions)
			- users/groups
			- Application to grant/deny access 
			- Location (IP)
			- Approved devices 
		- Access decisions (grant/block access)
			- grant access 
			- block access 
			- require MFA
			
## Passwordless Authentication:
	- objectively less convenient 
	- More steps to log in:
		- password and device/biometric
	- Microsoft Authenticator App
## External Guest Access: 
## Azure Active Directory Domain Services:
## Single Sign-On:


## References
