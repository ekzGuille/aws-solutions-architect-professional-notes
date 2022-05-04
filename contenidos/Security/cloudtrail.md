# AWS CloudTrail

* Enabled by default in **all regions** (can be set in only a single region). **Audit** tool.
* History of Events/API Calls made in the Account by:
  * Console
  * SDK
  * CLI
  * AWS Services
* Logs can be PUT in **CloudWatch** or **S3** (if you want to store them for more than **90 days**)

## CloudTrail Events
### Management Events
* By default **yes** logged
* Operations performed on resources in your Account
* **Read** Events and **Write** Events

### Data Events
* By default **not** logged (high volume operations)
* AWS **S3** Object activity: **Read** Events and **Write** Events
* **Lambda** function execution activity

### CloudTrail Insights Events
* If enabled -> Pay for it
* Detects **unusual** activity in the account
  * Example: *Hitting service limits*
* How it works:
  * Analyzes normal account behaviour and creates baselines
  * It will analyze **write** events to detect unusual patterns
  * Anomalies:
    * Will appear in CloudTrail console
    * Can be sent to S3
    * **An EventBridge will be generated**

## CloudTrail Events Retention
* Stored for **90 days**
* Use **S3** to store permanently
* Use **Athena** to Analyse the data

## CloudTrail in Organizations
* Setting a **Organizational Trail** in the management account will *record* all Organization Unit's Trails

## Fastest way to access CloudTrail Logs
(Because they may take up to 15 min to be logged)

### CloudWatch Events
* Most reactive way. **Fastest**

### CloudTrail Delivery in CloudWatch Logs
* Stream of events
* Metric filtering

### CloudTrail Delivery in S3
* Events delivered every 5 min.
* Long term storage. Data can be Analyzed with **Athena**

---

[<small>⬅ Go Back</small>](./index.md)