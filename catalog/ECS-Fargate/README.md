# IbexCatalog

## Requirements
* Private subnets for ECS fargate containers and public subnets for elastic load balancers that loadbalances containers.
* ECSFargetExecutionRole (Role for fargate to allow your Fargate tasks to make API calls to Amazon ECR)
* ECSFargetTaskRole (Role that grants containers in the task permission to call AWS APIs on your behalf)
* AutoScalingRole (Role needed for ApplicationAutoScaling scalable targets to scale the containers)

## Parameters
* VPC
* ELBSubnets (Atleast two public subnets EC2 instances to launch elastic loadbalancer)
* FargateSubnets (Atleast two private subnets EC2 instances to launch)
* CustomerName
* LoadBalancerSecurityGroup(The list of SecurityGroup Ids for loadbalancing)
* ContainerSecurityGroup (The list of SecurityGroup Ids for ECS containers)
* Image (Docker image)
* ExecutionRole (Role to be attached to task definition for fargate to allow your Fargate tasks to make API calls to Amazon ECR)
* TaskRole(Role to be attached to task definition to grants containers in the task permission to call AWS APIs on your behalf)
* AutoScalingRole (Role to be attached to AutoScalingTarget scalable targets to scale the containers )
* ServiceName 
* ContainerPort (Container port on which application is running)
* LoadBalancerPort (Loadbalancer port on which application is exposed)
* HealthCheckPath (Path on which target group checks health of container)
* MinContainers (Min number of containers for application)
* MaxContainers (Max number of containers for application)
* AutoScalingTargetValue (Indicates the threshold for CPU utilization to autoscale containers)

## Description

* Before launching this template we should have network, Security groups and IAM roles which would be created using Network, Securitygroups and IAM templates.
* Template creates a ECS-fargate cluster with containers which auto-scales with auto-scaling scalable target group behind elastic loadbalancer. 
* ECS-Fargate containers would be launched inside private subnets(FargateSubnets) and loadbalancers in pubic subnets(ELBSubnets) of VPC(which is created from network template). ContainerSecurityGroup should be attached to containers using service and LoadbanacerSecurityGroup to loadbalancer. 
* ExecutionRole, TaskRole, AutoScalingRole should be ECSFargetExecutionRole, ECSFargetTaskRole and ECSFargetAutoScalingRole respectively(which are created from IAM template. Anyways they are mentioned as default in parameters).
* We are using sample httpd container image(mentioned as default in parameter) from dockerhub for fargate containers.

## Output
DNS name of elastic load balancer which points application running in containers

## Flow-Diagram
![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/Images/Images/Fargate.png)
