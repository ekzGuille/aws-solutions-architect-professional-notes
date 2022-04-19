# Identity Federation

Users from outside AWS can access resources

### Use cases
* Don't need to create IAM users
  * Can use own identity system
  * External Web/Mobile application

### Types
* SAML 2.0 *(Security Assertion Markup Language)*
* Web Identity Federation with(out) AWS Cognito
* Custom Identity Broker
* SSO

## SAML 2.0
* Standard used by many identity providers
* Supports integration with Microsoft Active Directory Federation Services
* Access AWS Services/Console with temporary credentials
* STS *AssumeRoleWithSAML*
* AWS SSO is the *new way*

## Web Identity Federation - Without Cognito
* **Not recommended** (use Cognito)
* Once is logged with the 3rd party Identity Provider, STS *AssumeRoleWithWebIdentity* API is called so you get granted temporary credentials

## Web Identity Federation - Cognito
* Can create IAM Roles with the least privilege needed
* Once is logged with the 3rd party Identity Provider, you get a Cognito token that has to be passed to STS to get granted temporary credentials
* Supports **anonymous users**
* Supports **MFA**

## Web Identity Federation - IAM Policy
* One authenticated with Web Identity Federation, the user can be identify with a IAM Policy variable. Examples:
  * Google -> `${accounts.google.com:sub}`
  * Cognito -> `${cognito-identity.amazonaws.com:sub}`

---

[<small>⬅ Atrás</small>](./index.md)