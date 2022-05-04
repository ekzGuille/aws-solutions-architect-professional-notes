# Secrets Manager
* Storing secrets
* Secrets can be **rotated** every X days
* Manage the access from a resource to a secret with **Resource-based Policy**

## Parameter Store vs Secrets Manager
### Secrets Manager
* More expensive
* Automatic rotation with Lambda
  * Secrets Manager triggers Lambda that will update *associated* secret in the target resource (**automatic**)
* Mandatory KMS Encryption

### Parameter Store
* Simple API
* No automatic rotation (only triggered by Lambda with CloudWatch Events)
  * CloudWatch Event/EventBridge Rule has to be set to trigger a Lambda and the Lambda has to update Parameter Store and target resource.
* *SSM Parameter Store API can fetch Secrets Manager*

---

[<small>⬅ Go Back</small>](./index.md)