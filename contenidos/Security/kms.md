# KMS
Key Management Service

## KMS Key Types
### Symmetric
* (AES-256 Keys)
* Used by AWS Services that has KMS Encryption
* **NO** access to KMS unencrypted (**must call KMS API** to use it)

### Asymmetric
* (RSA ECC key pairs)
* Public Key (*Encrypt*) and Private Key (*Decrypt*)
* Use for Sign operatinos

## Types of KMS Keys
### Customer Managed Keys
* Create, User, enable or disable
* Key rotation (optional **every year**)

### AWS Managed Keys
* Used by AWS Services
* Rotation every **3 years**

### AWS Owned Keys
* Managed by AWS (made for protecting resources)
* Used in multiples accounts but **not in the account** (***internal***)
* Cannot be viewed

## KMS Key Material Origin
* Identifies the source of the KMS Key
* Cannot be changed after creation

### KMS (AWS_KMS) - *default*
* Managed by AWS
### External (EXTERNAL)
* Has to be imported into AWS
* Bring Your Own Key (BYOK)
* Must be **Symmetric**
* Rotation has to be **manual**
### Custom Key Store (AWS_CLOUDHSM)
* Created in a custom key store (CLudHSM Cluster) that you manage
* Recommended using 2 active HSMs for high availability

## Multi-Region Keys
* Identical keys in different regions
* Encrypt in one region and Decrypt in other region
* Not global -> Replicas of a Primary one (**only one primary at a time**, replicas can be promoted into primary)


---

[<small>⬅ Go Back</small>](./index.md)
