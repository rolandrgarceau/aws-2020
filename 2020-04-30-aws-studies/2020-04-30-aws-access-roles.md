# Cross Account Access

Delegate with [roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html)

## Basic concepts:

* Users in the Development account (the trusted account) that are allowed to assume a specific role in the Production account.
* A role in the Production account (the trusting account) that is allowed to access a specific Amazon S3 bucket.
* The productionapp bucket in the Production account.

## Flow

1. User gets temp creds based off a [role We create](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html#tutorial_cross-account-with-roles-1)

2. We grant granular access to the role, starting by deny statements for the Tester which are part of the PowerUser group with a policy that limits access. Testers are denied access to the UpdateApp role.

3. Change roles by switching and testing to see if it works as a Developer. 
