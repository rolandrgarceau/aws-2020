# Launch Lightsail with Database

* Pull up [docs](./rds-from-s3-backup.md)
* Go to [RDS](https://console.aws.amazon.com/rds/home?region=us-east-1#restore-from-s3:) Console link in your account.

## We will launch a RDS managed DB with PostgreSQL

Engine options do not have PostgreSQL. This conflicts with [docs](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_PostgreSQL.html)?

## SQL client

We need a client to run commands for the instance from your client computer like pgAdmin or psql. Amazon RDS doesn't allow direct host access to a DB instance by using Telnet or Secure Shell (SSH). 

* it can build HIPAA-compliant applications.
* FedRAMP also for Federal Risk and Authorization Management Program.
  * Joint Authorization Board (JAB) Provisional Authority to Operate (P-ATO) at the FedRAMP HIGH Baseline within the AWS GovCloud (US-West) Region