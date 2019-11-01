# IbexCatalog

* AWS_Inspector --> Template Setup AWS Inspector based on existing tag conventions. It collects the group of instances with the mentioned tags
* ECS-FARGATE --> Template creates a ECS-fargate cluster with containers under auto-scaling scalable target group behind elastic loadbalancer. A test Httpd application container is running in them.
* ECS --> Template creates a ECS-EC2 cluster with nodes under auto-scaling group behind elastic loadbalancer. A test Httpd application container is running in them.
* EKS --> Template creates a Kuberenetes cluster, worker nodes(under auto-sclaing group) with userdata that configures them as kubernetes worker nodes and attaches them to master.
* Elastic Beanstalk --> Template deploys a test application(Php, Nodejs, Java tomcat) depends upon our choice in paramaters
* Enable(Guard duty, security hub, Config rule) --> It enables all the 3 services and creates a bucket for the config enablement as a part of the template for SNS topic.
* Network --> This template deploys the entire Network architecture with 3 subnets each for Public, Private and DB with High Availability in a region.
* S3-CFT --> This CFT creates S3 bucket with encryption enabled by default.
* SSM --> Based on the Cron value the scheduling occurs. The document decides what action is going to be happened on the Resource group or Instance.
* Securityhub Standards --> Cloudformation template which will create all of the needed log filters, metrics and alarms to conform with the CIS framework used by AWS Security hub.
* VPC_Peering --> Cloudformation template peers the VPCs across accounts
* ansible --> The Ansible roles for the creation of Datadog, Newrelic & Jenkins
* cft --> The CloudFormation template is the architecture for the ansible role to create Jenkins, Datadog & NewRelic.
* Cloudfront_s3 --> This template will create a cloudfront Web Distrubition Configured with S3 bucket.


## Network is the base template on which the other templates rely on. This is the template which lays the platform for the remaining templates to execute and create the desired resources & applications.


These are the functionalities of the templates. The detailed informtaion on the Prerequisites, Paramaters, Resources and Outputs can be found inside the each folder.
