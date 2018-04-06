# VPC Templates for AWS CloudFormation

Find the documentation here: http://templates.cloudonaut.io/en/stable/vpc/

## Developer notes

### RegionMap
To update the region map execute the following lines in your terminal:

```
$ regions=$(aws ec2 describe-regions --query "Regions[].RegionName" --output text)
```

#### AMI
```
$ for region in $regions; do ami=$(aws --region $region ec2 describe-images --filters "Name=name,Values=amzn-ami-hvm-2017.09.1.20180115-x86_64-gp2" --query "Images[0].ImageId" --output "text"); printf "'$region':\n  AMI: '$ami'\n"; done
```

#### NATAMI
```
$ for region in $regions; do ami=$(aws --region $region ec2 describe-images --filters "Name=name,Values=amzn-ami-vpc-nat-hvm-2017.09.1.20180115-x86_64-ebs" --query "Images[0].ImageId" --output "text"); printf "'$region':\n  NATAMI: '$ami'\n"; done
```
