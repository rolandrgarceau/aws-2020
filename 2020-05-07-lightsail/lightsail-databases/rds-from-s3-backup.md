## Restore DB Cluster from S3

Procedure to get up and operational through RDS. Be aware of client logins to database is not authorized. We develop in Django using their model view controller and migrate/makemigrations. Get the schema down then dump it to an S3 bucket.

Basic idea is that we have a backup in a format readable by RDS. We then use the console to bring it up, or have automation in place for this.

## [Setup for RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_SettingUp.html)

## Requirements

* DB Instance as an endpoint. See instance classes [here](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.DBInstanceClass.html). We can probably start with db.m1, and they may ask vcpu and core count and hyperthread/ threads per core questions for xeon.

#### Note: AWS Nitro System (db.m5, db.r5, db.t3) are throttled on combined read plus write workload. 

We can talk IOPS and custom throughput later.

* Control network access to a DB instance through a security group.

## VPC, subnet, and security group

Define this first:
* in a default VPC, 
* in a user-defined VPC, or 
* outside of a VPC

Default VPC is per Region still.

* Use either [Amazon EC2 API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/Welcome.html) or Security Group option on the VPC console to create the VPC.

I need a user with admin privelages (best assigned to an admin group) and profile on your AWS account to do work here. Did we get that taken care of?

## User

Admin privelages. Watch cli perms and/or console use.

I added a group and assigned my IAM user to the group with Amazon RDS administrative permissions... nope I did not. Backtrack here. Get it right now and not make a big stinking mess!

We then access AWS from a special URL using the credentials for the IAM user.

* IAM policy
* Security group to access through VPC

Watch deploy region for compliance. See notes on FedRAMP etc.


### [RDS](https://console.aws.amazon.com/rds/home?region=us-east-1#restore-from-s3:) Console link.

## Write audit logs to S3:

* Defines destination folder and optional prefix.

### SQLSERVER_BACKUP_RESTORE

Specifies the file path prefix. No prefix means we use the root folder defined for the S3 bucket. This will be where the RDS launching engine builds the destination folder.

### SQLSERVER_AUDIT:

The dest for the audit logs.

