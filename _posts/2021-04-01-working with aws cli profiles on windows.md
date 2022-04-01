## Working with AWS profiles

In order to see which your default AWS CLI profile is, run the aws configure list command. The command shows the name of the default profile, the profile's security credentials and region.

```shell
aws configure list
```

In this case the name of the default profile is set using the AWS_PROFILE environment variable, which has higher precedence than the settings in the credentials file.

You can find the Access Key ID and Secret Access Key of the profile in the credentials file:

```shell
# on Linux and macOS
~/.aws/credentials

# on Windows
C:\Users\USERNAME\.aws\credentials
```


In order to change the current working profile. Below shows how to change the profile to default. 

```shell
# on Windows 
set AWS_PROFILE=default
```

To verify whether an Environment variable is set on your machine, run the echo command that corresponds to your operating system:

```shell
# Linux and macOS
echo $AWS_PROFILE

# on Windows with CMD
echo %AWS_PROFILE%

# on Windows with PowerShell
echo $Env:AWS_PROFILE
```

