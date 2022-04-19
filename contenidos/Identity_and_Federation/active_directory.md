# Active Directory

* Database of **objects** (User, Accounts, Computers...)
* Objects are organized in **trees**
* Group of trees is a **forest**

## ADFS (AD Federation Services)
* Provides SSO
* SAML accross 3rd party apps

## AWS Directory Services
* AWS Managed Microsoft AD
  * Create your own AD in AWS
  * Supports MFA
* AD Connector
  * Links Cloud AD and On Premise AD (proxy)
  * Users are created in On Premise AD
* Simple AD
  * AD Standalone (doesn't connect to any On Premise AD) -> **cheaper**

## AWS Managed Microsoft AD
* Microsoft AD in a VPC
  * EC2 Windows instances with Windows apps (Sharepoint, etc)
  * Seamlessly Domain Join Amazon EC2
* Integrations
  * RDS for SQL Server
  * SSO
* Multi AZ deployment (minimum of 2 AZ)
* Automated Backups
* Automated Multi region

### Connect to On Premise AD
* Connects Active Directory to AWS Managed Microsoft AD
* Connected by Direct Connect (DX) or VPN
* Forest trusts (**NOT Synchronization**) -> They can "talk" between each other to check if the user is in one AD or another
  * One Way
    * AWS -> On Premise
    * On Premise -> AWS
  * Two Way
    AWS <=> On Premise

### Solution Architecture: Active Directory Replication
* Create AD replica on EC2
* Establish trust between AWS Managed Microsoft AD and EC2

## AD Connector
* Redirect requests to On Premise AD
* No cache
* No MFA
* Connection with VPN or DX

## Simple AD
* **inexpensive** and basic
* Supports EC2 instances, manages users and groups
* No support for RDS SQL server, MFA, AWS SSO
* No trust relationship
* Small (500) or large (5000) users