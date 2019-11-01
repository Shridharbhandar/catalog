# IbexCatalog

### Requirements
* Private subnets for ECS EC2 instances and public subnets for elastic load balancers.
* ECSServiceRole (to attch to the ECS cluster to describe and register/deregister ELB and EC2 instances)
* AutoscalingRole (to attach to the application autoscaling scalable to targets to maintain the container count depends on default count)
* EC2Role (to attach to EC2 nodes of ECS cluster to work with cluster )
* Security group (for communiction between instances and load balancer)

## Parameters
* Keyname
* VpcId
* CustomerName
* ECSSubnetId (Atleast two private subnets EC2 instances to launch)
* ELBSubnetId (Atleast two public subnets EC2 instances to launch elastic loadbalancer)
* DesiredCapacity (Number of instances to launch in your ECS cluster)
* EcsSecurityGroup (SecurityGroup Ids to associate with Instance)
* LoadbanacerSecurityGroup (SecurityGroup Ids to associate with Instance)
* DesiredContainerCount (Number of containers to launch in your ECS cluster)
* MaxSize (Maximum number of instances that can be launched in your ECS cluster)
* ECSServiceRole (Role to be attached to the ECS service to communicate with loadbalancers)
* EC2Role (Role to be attached to the ECS EC2 instance to communicate with ECS cluster)
* AutoscalingRole (Role to be attached to the ServiceScalingTarget to auto-scale containers) 
* EC2InstanceProfile (Instance profile created for EC2Role)
* InstanceType (Intance type for ECS EC2 instance)


## Description
* Before launching this template we should have network, Security groups and IAM roles which would be created using Network, Securitygroups and IAM templates.
* Template creates a ECS-EC2 cluster and EC2 instances  with  associated to master(ECS Cluster) under auto-scaling group behind elastic loadbalancer. Containers would be recognizing ECS cluster with userdata mentioned in template.
* Containers will be launched on EC2 instances with desired container count given in parameters.
* ECS-EC2 instances would be launched inside private subnets and loadbalancers in pubic subnets of VPC(which is created from network template). EcsSecurityGroup should be attached to EC2 instances and LoadbanacerSecurityGroup to loadbalancer. 
* EC2Role,AutoscalingRole,EC2InstanceProfile should be ECSEC2Role, ECSAutoscalingRole and ECSEC2InstanceProfile respectively(which are created from IAM template. Anyways they are mentioned as default in parameters).
* We are using sample httpd container image from dockerhub for containers running in EC2 instances.

## Output
DNS endpoint for elastic load balancer which points application running in containers

## Flow-diagram
![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/images/Images/ECS-Designer.png)
