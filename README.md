# CloudFormation
Tool of infrastructure as code in AWS

# Core Concepts: 
Infrastructure as code \
AWS Resource \
Template \
Stack \
Change Sets \

# Create stacks from file
aws cloudformation create-stack --stack-name name --template-body file://${file} \
Notice: must have file://.

# Introduction CloudFormation
https://learn.acloud.guru/course/intro-aws-cloudformation/learn/c22a36d9-b313-5b7c-d42f-23516e9f1ba9/dfe0c502-dbd8-f316-56ab-212f6a155f60/watch

YAML vs JSON: \
https://github.com/arisyang1981/YAML-vs-JSON/edit/main/README.md

# AWS Resources 
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html

# VPC
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html 

# Cloudformation and CI/CD
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/continuous-delivery-codepipeline-basic-walkthrough.html


Question:
# What is 'Ref'?
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html
# What is 'Fn::GetAtt'
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getatt.html
