
# aws cli installed and configured
```bash
aws --version
```
# eksctl configure installed
```bash
eksctl version
```


# kubectl installed
```bash
kubectl version
```

# Switch to Project Directory
```bash
cd /e/Projects/CLOUD_AWS/EKS-CLOUDFORMATION-SETUP
```

# Create VOC using Cloudformation Tempplate
## Note: Update VPC name, CIDR, Region and other parameters 
```bash
aws cloudformation create-stack --stack-name K-POC-VPC --template-body file://vpc-setup.yml --capabilities CAPABILITY_NAMED_IAM 
```

# Create EKS Cluster
## Note: Update VPC ID, CIDR, Private subnets and SG ID and SSH Key.
```bash
`eksctl create cluster --config-file=eks.yml`
```

# Deploy Application
```bash
kubectl create deployment nginx-deployment --image=nginx --replicas=2
```



