
## Steps

Create Key Pair

```bash
  aws ec2 create-key-pair --key-name linux --query 'KeyMaterial' --output text > linux.pem
```
it will create a linux.pem file 

Create Security Group

```bash
  aws ec2 create-security-group --group-name MySecurityGroup --description "My Security Group"
```
Add inbound rule to SSH in the security group from UI

Launch EC2

```bash
  aws ec2 run-instances --image-id ami-xxx --count 1 --instance-type t2.micro. --key-name linux --security-groups MySecurityGroup
```

View the Instance

```bash
  aws ec2 describe-instances
```

Connect the Instance using SSH

```bash
  chmod 600 <pem_file>
```

```bash
  ssh -i <path_to_key_pair/pem file> ubuntu@<public_ip>
```

Terminate the Instance

```bash
  aws ec2 terminate-instances --instance-ids <instance_id>
```

