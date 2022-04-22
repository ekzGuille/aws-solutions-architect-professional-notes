# SCP

Service Control Policies

* AllowList or BlockList of IAM actions
  * SCP must have explicit **Allow** (by default don't allow)
* Applied at the **OU** (Organization Unit) or **Account** level
  * OU denials are inherited from parent OU. **If an account has an explicit Allow but the OU Denies it, the Account won't have access**.
* Do **not** apply to Management Account
* Apply to **all** Users and Roles. Including **root** user.
* Service-linked Roles (enable other AWS services to integrate with AWS Organizations)

### Evaluation Logic
* **Deny** evaluation | *if **Deny** YES: **DENY** | if **Allow** YES: next check* ->
  * -> Organizations SCP's | *if **ALLOW** NO: **DENY** | if **Allow** YES: next check* ->
    * -> Resource-based policies | *if **ALLOW** NO: **DENY** | if **Allow** YES: **ALLOW*** ->
      * -> IAM Permissions boundaries | *if **ALLOW** NO: **DENY** | if **Allow** YES: next check*->
        * -> Session Policies | *if **ALLOW** NO: **DENY** | if **Allow** YES: next check*->
          * -> Identity-based policies | *if **ALLOW** NO: **DENY** | if **Allow** YES: **ALLOW***

### Restricting Tags with IAM Policies
* Check if resource has specific tags 
* **aws:TagKeys** Condition Key
* `ForAllValues` and `ForAnyValues`
  * `ForAllValues:StringEquals` and `ForAnyValues:StringEquals`

### SCP Restrict create resources without appropiate Tags
* If resource doesn't have specific tag, resource creation won't be allowed
```json
  "Condition": {
    "Null": {
      "aws:RequestTag/TAG_NAME": "true"
    }
  }
```
* **SCP ONLY**

### Tag Policies
* Standardize resources. Consistent tags
* Define tags and allowed values
```json
{
  "tags": {
    "costcenter": {
      "tag_key": {
        "@@assign": "TAG_NAME"
      },
      "tag_value": {
        "@@assign": "TAG_VALUE" // ["TAG_VALUE1¨", "TAG_VALUE2"]
      },
      "enforced_for": {
        "@@assign": ["secrestsmanager:*"] // AWS Resource
      }
    }
  }
}
```

### AI services Opt-out Policies
* Allow AI services to take the input data as a continuous improvement
* Enforces the setting to All Member Accounts and all AWS Regions
* Opt-out all services or selected services
  * All
  ```json
  {
    "services": {
      "default": {
        "opt_out_policy": {
          "@@assign": "optOut"
        }
      }
    }
  }
  ```
  * Selected
  ```json
  {
    "services": {
      "lex": {
        "opt_out_policy": {
          "@@assign": "optOut"
        }
      },
      "rekognition": {
        "opt_out_policy": {
          "@@assign": "optOut"
        }
      }
    }
  }
  ```
* Can be attached to Organization Root, specific OU, or individual Member Account

### Backup Policies
* Enables the creation of Backup Plans that define how to backup resources
* Control of backing up
  * Frequency
  * Region
* Can be attached to Organization Root, specific OU, or individual Member Account
* Appear on Member Account but **view only**. Modification can only be done in Management Account

---

[<small>⬅ Go Back</small>](./index.md)