# SSO
* With **Single Sign-On** you can:
  * Access Multiple AWS Accounts
  * Access Bussiness Applications
  * SAML 2.0-based applications
* Integrated with AWS Organizations
* The Identity Source can be:
  * SSO-built in (manage users and groups)
  * Active Directory (AWS Managed Microsoft AD or AD Connector)
  * External Identity Provider -> any SAML 2.0 Identity Provider
* Centralized permission management
* CloudTrail logs

## SSO vs AssumeRoleWithSAML
* The **SSO** integrates directly with Identity Store and the login is returned to the client
* With **AssumeRoleWithSAML** the client performs the login with the Identity Provider and the SAML assertion has to be sent to STS to get temporally credentials.

## SSO with Active Directory
### Set up an **integration** between SSO and Active Directory
* Use AWS Managed Microsoft AD
* AWS Managed Microsoft AD with 2-way forest trust with on-premise AD
* AD Connector to on-premise AD

---

[<small>⬅ Go Back</small>](./index.md)