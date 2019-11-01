# IbexCatalog

## Requirements
* Private subnets for EKS Worker nodes
* eksServiceRole (Role for EKS to make calls to other AWS services on your behalf to manage the resources that you use with the service)
* NodeInstanceRole (Role for The Amazon EKS worker node kubelet daemon makes calls to AWS APIs on your behalf. Worker nodes receive permissions for these API calls through an IAM instance profile and associated policies)

## Parameters
* KeyName (Key for login to worker nodes)
* VpcId
* NodeInstanceType (Type for instance for worker node)
* NodeAutoScalingGroupMinSize (Minimum size of worker node Autoscaling group)
* NodeAutoScalingGroupMaxSize (Maximum size of worker node Autoscaling group)
* CustomerName (Name of customer(arbitary))
* NodeGroupName (Unique identifier for the Node Group(arbitary))
* Subnets (Private subnets where workers can be created)
* NodeInstanceProfile (INstance profile attached to NodeInstanceRole)
* NodeInstanceRole (To attach to worker nodes to communicate with EKS cluster)
* eksServiceRole (To attach to EKS cluster to make API calls to other AWS services)
* Securitygroupforcluster(Allow http to client host)
* ClusterControlPlaneSecurityGroup(Allow pods to communicate with the cluster API Server)
* NodeSecurityGroup(Security group for all nodes in the cluster)

## Description
* Before launching this template we should have network, Security groups and IAM roles which would be created using Network, Securitygroups and IAM templates.
* Template creates a Kuberenetes cluster, worker nodes(under auto-sclaing group) with userdata that configures them as kubernetes worker nodes and attaches them to master.
* Worker nodes would be launched inside private subnets(Subnets).
* NodeInstanceRole, eksServiceRole, NodeInstanceProfile should be EKS-NodeInstanceRole , EKS_ServiceRole and EKS-NodeInstanceProfile respectively(which are created from IAM template. Anyways they are mentioned as default in parameters).

