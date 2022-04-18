# IAM
Identity Access Management

## Policies
* Structure
  * JSON doc
  * Effect
  * Action
  * Resource
  * Conditions
  * Policy Variables

### Policies info
* By default: **DENY** (**ALLOW** has to be specified)
* Utilities
  * **Access Advisor** (See permissions and when were last accessed)
  * **Access Analyzer** (See resources that are shared with external entity) *P.e: S3 Bucket used by another account*
* Managed Policy: AdministratorAccess
  * When a policy has *Action* and *Resorce* on *"*"* it is called **AdministratorAccess**
  ```json
  {
    "Version": "",
    "Statement": [
      {
        "Effect": "Allow",
        "Action":  "*",
        "Resource": "*"
      }
    ]
  }
  ```

* Managed policy: PowerUserAccess
  * Uses *Allow* and ***NotAction*** and *Deny* on certain *Action*
  ```json
  {
    "Version": "",
    "Statement": [
      {
        "Effect": "Allow",
        "NotAction":  [
          "iam:*",
          "account:*",
        ],
        "Resource": "*"
      },
      {
        "Effect": "Allow",
        "Action":  [
          "iam:ListRoles",
          "account:ListRegions",
        ],
        "Resource": "*"
      }
    ]
  }
  ```
  * ⚠ Effect Deny is not used on the first Statement because it will override the second Action because of the **"*"**

### Conditions
* Operators
  * String (StringEquals, StringNotEquals, StringLike...)
  * Numeric (NumericEquals, NumericNotEquals, NumericLessThan)
  * Date (DateEquals, DateNotEquals, DateLessThan)
  * Boolean (Bool)
  * IpAddress/ NotIpAddress
  * ArnEquals, ArnLike
  * Null

### Variables and Tags
* Variables (Global variables or Service specific)
  * `${aws:XXX}` -> `${aws:username}`
  * `${aws:CurrentTime}`
  * `${s3:max-keys}`
* Tags
  * `iam:ResourceTag/key-name`

### IAM Roles vs Resource Based Policies
* For example, *A service in account A wants to access a service in account B.*
  1. Service A can assume a role in account B to access the resource
  2. Service A can access resource B because it has a policy that allows access to service from account A 
  * **Difference**: In scenario 1. if you assume a new role, you give up the original role you had.
  * *When using resource-based policies?* When the service in account A has to interact with services on accounts A and B.

### AWS Permission Boundaries
* For users and roles. **not groups**
* Restricts the permissions, if boundary permission is attached, will "override" other permissions.
  * Only user/role permissions that are included on boundary permission will be allowed to perform.

---

[<small>⬅ Atrás</small>](./index.md)