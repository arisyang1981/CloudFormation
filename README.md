# CloudFormation
Tool of infrastructure as code in AWS

# Core Concepts: 
Infrastructure as code \
AWS Resource \
Template \
Stack \
Change Sets \

# Create stacks from file
file=/home/cloudshell-user/test.yaml \
aws cloudformation validate-template --template-body file://${file} \
aws cloudformation create-stack --stack-name name --template-body file://${file} \
Notice: must have file://.

# Introduction CloudFormation
#Introduction to AWS CloudFormation : \
https://learn.acloud.guru/course/intro-aws-cloudformation/learn/c22a36d9-b313-5b7c-d42f-23516e9f1ba9/dfe0c502-dbd8-f316-56ab-212f6a155f60/watch

#YAML vs JSON \
https://github.com/arisyang1981/YAML-vs-JSON/edit/main/README.md 

#CloudFormation Deep Diver \
https://learn.acloud.guru/course/d8a92be0-dbab-4498-a2af-375a7a591ae8/dashboard 

#Mastering AWS CloudFormation \
https://learn.acloud.guru/course/mastering-aws-cloudformation/dashboard

# AWS Resources 
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html

# VPC
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html 

# Cloudformation and CI/CD
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/continuous-delivery-codepipeline-basic-walkthrough.html

# Key Pair
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html#create-key-pair-cloudformation \
Create key pair using cloudformation, the private key is saved to AWS Systems Manager Parameter Store. It's /ec2/keypair/${KeyPairId}. \
When create key pair using GUI, please save key pair by yourself. \
Create Key Pair from KP.yaml \
aws cloudformation create-stack --stack-name stack-lab-kp --template-body file://~/KP.yaml \
Check out KeyPairId. 
aws ec2 describe-key-pairs --filters Name=key-name,Values=${name} --query 'KeyPairs[*].[KeyPairId]' --output text \
Pull out KeyPair file from AWS System Manager Parameter Store. \
aws ssm get-parameter --name /ec2/keypair/${KeyPairId} --with-decryption --query Parameter.Value --output text > new-key-pair.pem

Question:
# What is 'Ref'?
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html
# What is 'Fn::GetAtt'
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html
