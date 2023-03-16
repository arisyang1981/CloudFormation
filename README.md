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
#YAML vs JSON \
https://github.com/arisyang1981/YAML-vs-JSON/edit/main/README.md 

#Introduction to AWS CloudFormation : \
https://learn.acloud.guru/course/intro-aws-cloudformation/dashboard 

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
Check out KeyPairId. \
aws ec2 describe-key-pairs --filters Name=key-name,Values=${name} --query 'KeyPairs[*].[KeyPairId]' --output text \
Pull out KeyPair file from AWS System Manager Parameter Store. \
aws ssm get-parameter --name /ec2/keypair/${KeyPairId} --with-decryption --query Parameter.Value --output text > new-key-pair.pem

Question:
# What is 'Ref'?
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html
# What is 'Fn::GetAtt'
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html


# The second time start on 3/11/2023.
#3/11, read https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html. \
Q1: Delete a stack, but how keep resources created by stack? \
Questions from the section 'Simplify infrastructure management' in https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html. \
A1: In template, specify DeletePolicy to retain for each resource. \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-deletionpolicy.html \
DeletePolicy is very imporant. \
It applies to delete stack, but want to keep resource. \
Also, it applies to update stack which need to delete resource first. So very imporant, if don't know if update stack will delete resource.

#3/13/2023 \
Referfer other resources: \
Q: How to reference other resource under the same template? \
A: - !REF other_resources_name \
Q: How to reference ohter resource in different templates? \
A: - Existing_Resource. \
Or define existing_resource in 'Parameters' section. \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html \

Q: What is the logical name and the phisical name of a resource? \
A: The logical name of the resource is the resource name in template. \
The physical name of the resource is the combination of the logical name, the stack name, and a unique ID. \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html \

#Intrinsic function \
#Hard for me, please study few more times. \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html \

#Input parameters in template \
https://learn.acloud.guru/course/intro-aws-cloudformation/learn/05254203-32a5-4bc1-de73-72d26874efc7/99f41daf-cb46-b596-d906-97cc01d4e232/watch \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-cli-creating-stack.html

#pseudo parameter \
Q: What is pseudo parameter? \
A: Pseudo parameters are parameters that are predefined by AWS CloudFormation. \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/pseudo-parameter-reference.html 

#Mapping \
https://learn.acloud.guru/course/intro-aws-cloudformation/learn/05254203-32a5-4bc1-de73-72d26874efc7/db751f2a-88ad-f32d-a997-e8c54e622a50/watch \
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html \

#3/15/2023 \
#Advanced \
Q: Cloudformation helper.  
A: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-helper-scripts-reference.html\
