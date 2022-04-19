# STS

Security Token Service: Assume roles in the same account or in between accounts

## Steps
1. Define the role
2. Define the principals that can access that role
3. With AWS STS retrieve and assume the credentials  -> **AssumeRole API**
  * Credentials are valid between 15min and 12h. 

## Use cases
* Provide access to:
  * IAM Users in the same, other accounts, cross accounts, or third party accounts
  * Services
  * External users

* Revoke active sessions with a time statement or using *AWSRevokeOlderSessions* managed policy.

### Use cases examples
* **Same account** or another account that you **own**
  * User has to assume a specific role in order to terminate an EC2 instance. (In normal conditions user can't perform the task)
* **Cross account**
  1. Admin account A creates the role (Y) that allows accessing a resource to a group (X) in another account
  2. Admin account B grants members of the group (X) permission to assume the role (Y) in account A
* **Third party** accounts
  * Zone of trust -> your accounts/organizations
  * Outside zone of trust -> 3rd parties
  * Requirements for granting access to a 3rd party:
    * Know 3rd party AWS Account ID
    * **Secret** external ID that associates the role between the 3rd party and you. Will be requested when assuming the role
    * Define permissions in IAM policy

### Important API
* AssumeRole
* AssumeRoleWithSAML (logged users with SAML)
* AssumeRoleWithWebIdentity (Google, Facebook, Google, etc)
  * Recommended to use Cognito instead of other 3rd party
* GetSessionToken (MFA)
* GetFederationToken (federation user)

---

[<small>⬅ Go Back</small>](./index.md)