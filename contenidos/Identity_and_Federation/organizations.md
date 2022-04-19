	# Organizations

Manage multiple accounts at once

* Root Organizational Unit (OU) can contain:
  * Management account (admin account)
  * Multiple OU with accounts inside
    * OU inside other OU (with accounts inside)

## OrganizationAccountAccessRole
* If a Member Account is created inside an Organization by a Management Account, a role inside Member Account called **OraganizationAccountAccessRole** will be created.
* If Management Account has to perform admin action in Member Account, it will need to call AssumeRole API to assume **OraganizationAccountAccessRole** role.
* The role can be assumed by IAM users as well
* Automatically added to Member Accounts if created with AWS Organizations. If an external/invited account, it has to be manually added.

## Multiple Account Strategies
* Create accounts per department, cost center, environment (dev/test/prod)
* Tags for billing purposes
* Enable CloudTtrail on all accounts and send logs to a central S3

## Feature Modes
### Consolidated billing features
* Single payment method in all cross accounts
* Pricing benefits from aggregate usage

### All Features (**Default**)
* Includes *Consolidated billing features*, **SCP** (Service Control Policy)
* Invited accounts must approve enable all features
* Apply an SCP to avoid Member accounts leaving the organization
* If All features are enabled **can't** switch back to Consolidated billing features

## Reserved Instances
* All accounts in the organization receive benefits of Reserved Instances (even if they are purchased by any other account). **All accounts** are treated as **one single account**
  * This can be turned off by **Management account**. Reserved Instances won't be shared
* To enable it, both accounts (the one with the Saving plan) and the target, must enable sharing

---

[<small>⬅ Atrás</small>](./index.md)