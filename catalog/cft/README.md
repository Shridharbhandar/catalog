# CSL

## Requirements
* ClientName - The Customer name
* ServiceName - The service/application which we're going to deploy
* InstanceType - The type of instance to be launched
* VpcId - The VPC in which the instance is launched
* Subnets - The subnets type - Public, Private & DB
* ImageId - The AMI image
* Ec2key - The Key used to launch the EC2 instance
* Max & Min - The Maximum & minimum number of instances going to be launched in Auto-scaling group
* Environment - The kind of environment. Ex : Production, Development, etc
* Security Groups - The security groups for the instances

## Description
Template creates the end service - Jenkins, Datadog & NewRelic

## Output
The endpoint of the service launched
