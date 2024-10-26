
# aws cli installed and configured
aws --version

# eksctl configure installed
eksctl version

# kubectl installed
kubectl version

# Switch to Project Directory
cd /e/Projects/CLOUD_AWS/EKS-CLOUDFORMATION-SETUP

# Create VOC using Cloudformation Tempplate
# Note: Update VPC name, CIDR, Region and other parameters 

aws cloudformation create-stack --stack-name K-POC-VPC --template-body file://vpc-setup.yml --capabilities CAPABILITY_NAMED_IAM 


# Create EKS Cluster
# Note: Update VPC ID, CIDR, Private subnets and SG ID and SSH Key.

eksctl create cluster --config-file=eks.yml 

# Deploy Application

kubectl create deployment nginx-deployment --image=nginx --replicas=2





unset AWS_SECRET_ACCESS_KEY
unset AWS_ACCESS_KEY_ID
unset AWS_REGION


eksctl scale nodegroup --name=K-POC-NODEGROUP --cluster=K-POC-CLUSTER --nodes=0 --nodes-min=0 --nodes-max=3


aws console access for root user for eks
arn:aws:iam::869935075639:root


delete all component fron cluster of karpenter