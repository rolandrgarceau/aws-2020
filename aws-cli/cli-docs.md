# AWS CLI [reference manual](https://docs.aws.amazon.com/cli/latest/userguide/aws-cli.pdf) 

## CLI errors on pg 152

Basic way to view verbose info on request is to add the `--debug`

```sh 
# this will spit out cli info including the python versioning 
aws iam list-groups --profile MyTestProfile --debug
```

## CLI access denied

This may be different than an HTTPS request a browser may be reporting about when attempting to access resources within an account. First place to check is that the [IAM identity](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html) doesn't have permission to perform the operation. We can also see our local config inside the hidden directory. For a mac it should be in $HOME, but we need to make sure our cli install is pointing to the right locations. I believe version 2 install was to the below path, and I did still have a config dir in ~.

See setup run rules for how to config the profile on the local machine.

### Watch out for the 755 

```sh
# this may not solve our problem...
chmod +x ~/.local/bin/aws
```

