# RAM
Resource Access Manager

* Share resources (you own) with other AWS Account (*Any account or accounts within your Organization*)
* Avoid duplication

## What can you share?
* VPC Subnets
  * Launch all resources (**from the same AWS Organization**) in the same subnets
  * **NOT** Share security groups and default VPC
  * Participants can manage **own** resources but **no other participant's or owner's** resources
* AWS Transit Gateway
* Route 53
* License Manager Configurations
* Aurora 
* AWS Glue
* EC2
* *(...)*

## Use cases

### VPC

* Different Accounts access to the same VPC and **can** "communicate" with each other but **cannot** "view". 
* As the Network is shared they can "talk" with each other accessing with **private IP**
* Security groups can be referenced across accounts

---

[<small>⬅ Go Back</small>](./index.md)