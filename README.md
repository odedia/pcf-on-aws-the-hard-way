# pcf-on-aws-the-hard-way
Installation instructions for PCF on AWS with as minimal UI interaction as possible. Initial instructions expect macOS, but after a few initial commands activity is done on a remove Linux VM on AWS.

Install AWS CLI:
`sudo pip install awscli`

Login:

Go to https://console.aws.amazon.com/iam/home?#/users

Click your username
Click "Security Credentials"
Click "Create Access Key"

Note the Access key and secret and keep in a safe location like LastPass.

From command line:
`aws configure`

You should provide your access key and secret for first two parameters. Third parameter is to choose a region or enter to select default. Approve 4th option of json output.

Create a security group:

`aws ec2 create-security-group --group-name jumpbox-access --description "security group for accessing the jumpbox"`

Enable SSH access:

`aws ec2 authorize-security-group-ingress --group-name jumpbox-access --protocol tcp --port 22 --cidr 0.0.0.0/0`

Create an SSH key:

```aws ec2 create-key-pair --key-name jumpbox-key --query 'KeyMaterial' --output text > jumpbox-key.pem
chmod 400 jumpbox-key.pem```




