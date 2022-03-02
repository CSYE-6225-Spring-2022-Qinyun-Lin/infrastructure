# infrastructure


## command for configure profile
```
aws configure --profile=dev

aws configure --profile=demo

aws configure --profile=demo set region us-east-1
```

## command for creating vpc
```
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --instance-tenancy default --no-amazon-provided-ipv6-cidr-block
```

## command for creating stack
Use default ciderblock
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml
```

Use given AMI id
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml --parameters ParameterKey=AMIid,ParameterValue="ami-02437b1f201ff8643"
```

Use given ciderblock
```
aws cloudformation create-stack --profile=dev --stack-name myVpc --template-body file://csye6225-infra.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.0.0.0/16" ParameterKey=SubCidrBlockA,ParameterValue="10.0.0.0/24" ParameterKey=SubCidrBlockB,ParameterValue="10.0.1.0/24" ParameterKey=SubCidrBlockC,ParameterValue="10.0.2.0/24" 
```

## command for deleting stack
```
aws cloudformation delete-stack --profile=dev  --stack-name myVpc
```

## Other useful command
check ```AvailabilityZone``` for your profile
```
aws ec2 describe-availability-zones --profile=[profile_name]
```

 