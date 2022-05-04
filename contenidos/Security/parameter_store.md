# Parameter Store
* Secure storage for configuration and secrets
* Optional encryption using KMS
* Versioning of configuration and secrets

## SSM Parameter Store hierarchy
* Similar to file system paths
```
  /project-A/
    app-A/
      dev/
        ddb-url
        ddb-password
      pre/
        ddb-url
        ddb-password

  /project-B/
    app-B/
      pro/
        ddb-url
        ddb-password
```

## Tiers
### **2** Tiers
* Standard -> **FREE**
* Advanced -> **PAID**

## Parameters Policies
* **Only for Advanced Tier**
* Allow assigning a TTL to a parameter
* Multiple policies can be assigned at a time

---

[<small>⬅ Go Back</small>](./index.md)