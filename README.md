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
