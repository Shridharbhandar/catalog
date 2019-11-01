# ElasticBeanstalk

## Requirements
* SSLCertificateARN (Update SSL arn if application needs to run on https and can be left it blank if we don't need SSL)
* ElasticBeanstalkServiceRole (to attach to beanstalk environment)
* Approle (to attach to the instances that works behind beanstalk)
* Couple of security groups for beanstalk and loadbalancer)
* Minimum and maximum number of instances in autoscaling group on which application runs
* Application (Php, Nodejs, Java tomcat)
* S3 bucket in the region where we are running with sample application code for Php, Nodejs, Java tomcat

## Parameters
* EnvironmentName (dev/prod/stag)
* Application (Choice of application - PHP or Tomcat or Nodejs)
* InstanceProfile (Created for Approle to attach to instances )
* InstanceType 
* KeyName (Name of keypair to login to EC2 instances)
* Schedule (The Time scheduled for the patching. It should be in this format "DAY:HH:MM")
* AutoScalingGroupSize - Mininmum & Maximum
* AppSubnet1 (Private SubnetId in your Virtual Private Cloud (VPC))
* AppSubnet2 (Private SubnetId in your Virtual Private Cloud (VPC))
* ElbSubnet1 (Public SubnetId in your Virtual Private Cloud (VPC))
* ElbSubnet2 (Public SubnetId  in your Virtual Private Cloud (VPC))
* LbSecurityGroup (Security group for load balancer behind beanstalk)
* Ec2SecurityGroup (Security group for EC2 instances behind beanstalk)
* HealthReportingType (Health reporting system (basic or enhanced))
* RollingUpdateEnabled (If true, Frequent updates to your Elastic Beanstalk software application)
* RollingUpdateType (Allowed Values are Time, Health, Immutable)
  * Time-based rolling updates apply a PauseTime between batches
  * Health-based rolling updates wait for new instances to pass health checks before moving on to the next batch
  * Immutable updates launch a full set of instances in a new AutoScaling group    
* DeploymentPolicy (Choose a deployment policy for application version deployments among AllAtOnce, Rolling, RollingWithAdditionalBatch,   Immutable)  
* UpdateLevel (Type of patch that needs to be updated)
* IsNewApplication 
  * Yes - If application is new
  * No - If application is already created and needs a new environment

## Description
* Before launching this template we should have network, Security groups and IAM roles which would be created using network and IAM templates.
* Aws provided sample code for Php, Nodejs, Java tomcat are stored in S3 bucket named ibexcatalogapplication.
* Template creates a elastic beanstalk application((Php, Nodejs, Java tomcat) depends upon our choice of Application in paramater
* Ec2 instances for would be launched inside private subnets(AppSubnet1 and AppSubnet2) and loadbalancers in pubic subnets(ElbSubnet1 and ElbSubnet2) of VPC(which is created from network template). Ec2SecurityGroup(BeanstalkEC2SecurityGroup) should be attached to EC2 instances and LbSecurityGroup(BeanstalkELBSecurityGroup) to loadbalancer.
* ElasticBeanstalkServiceRole, AppInstanceProfile should be ElasticBeanstalk_ServiceRole and Elasticbeanstalk_Instanceprofile
respectively(which are created from IAM template. Anyways they are mentioned as default in parameters).

![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/Images/Images/Beanstalk.png)
