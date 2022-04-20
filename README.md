# infrastructure


## command for configure profile
```
aws configure --profile=dev

aws configure --profile=demo

aws configure --profile=demo set region us-east-1
```

## command for creating stack
Create CI-CD Stack
```
aws cloudformation create-stack --capabilities CAPABILITY_NAMED_IAM --profile=demo --template-body file://CI-CD-Resouce.yml --stack-name myCICD
```

Create VPC & Webservice Stack Using default ciderblock
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml
```

Create VPC & Webservice Stack Using given AMI id
```
aws cloudformation create-stack --profile=demo --capabilities CAPABILITY_NAMED_IAM --template-body file://csye6225-infra.yml --parameters ParameterKey=AMIid,ParameterValue="ami-064b2971d3e69a5ab" ParameterKey=CurrentProfile,ParameterValue="demo" --stack-name myVpc
```

Create VPC & Webservice Stack Using given ciderblock
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=SubCidrBlockA,ParameterValue="10.0.0.0/24" ParameterKey=SubCidrBlockB,ParameterValue="10.0.1.0/24" ParameterKey=SubCidrBlockC,ParameterValue="10.0.2.0/24" 
```

## command for deleting stack
```
aws cloudformation delete-stack --profile=demo  --stack-name myVpc
```

delete bucket before deleting stack
```
aws --profile=demo s3 rm s3://0d969d70-a038-11ec-b6a1-12e24c93dc83.prod.linqinyun.me --recursive
```

## command for creating vpc
```
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --instance-tenancy default --no-amazon-provided-ipv6-cidr-block
```

## Other useful command
check ```AvailabilityZone``` for your profile
```
aws ec2 describe-availability-zones --profile=[profile_name]
```

 