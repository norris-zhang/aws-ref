# aws-ref

```
#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
echo "<h1>Hello World from $(hostname -f)</h1>" > /usr/share/nginx/html/index.html
```


Google aws policy simulator for the tool of testing IAM policies.

Or use CLI --dry-run option to test whether I have the permission, without actually running the command, because sometimes it is expensive if the command is successfully run.

$ aws ec2 run-instances --dry-run --image-id ami-06340c8c12baa6a09 --instance-type t2.micro

If you get an error and the error message is a long encoded text, you run sts decode authorization message command.
```
$ aws sts decode-authorization-message --encoded-message xxxxxxxxxxxxx
```
This will require policy of allowing STS write.
Google sts decode authorization message for detailed usage.

### AWS EC2 Instance Metadata
You can retrieve EC2 Instance Metadata from inside an EC2 instance without having the policy to do so.
```
$ curl http://169.254.169.254/latest/meta-data/
```

### AWS CLI Profiles
```
$ aws s3 ls --profile my-other-aws-account
```
The my-other-aws-account is previously configured profile that uses a different access key ID and secret_access_key from the default one.

### AWS CLI with MFA
```
$ aws sts get-session-token --serial-number arn:aws:iam::387124123361:mfa/stephane<from iam that configures mfa> --token-code 828463<from mfa device>
```
And this will generate a temporary session token which expires in one hour.

### CloudFormation
Resources Documentation:

http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html

### DynamoDB
Query vs Scan
![image](https://user-images.githubusercontent.com/13086073/147718537-f6b068a6-7649-41c1-b5ba-452107e0a01c.png)
