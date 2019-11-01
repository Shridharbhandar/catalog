# IbexCatalog

## Requirements
* Instances which needs assessments should have SSM agentinstalled.

## Paramaters
* EC2TagKey
* EC2TagValue
* SNS TopicName
* SNS SubscriptionEmail(To Send notification for assessment status if SubscriptionProtocol is Email)

## Description
Template Setup AWS Inspector based on existing tag conventions. It collects the group of instances with the mentioned tags and does the following checks. 
* Security Best Practices-1.0
* Network Reachability-1.1
* Common Vulnerabilities and Exposures-1.1
* CIS Operating System Security Configuration Benchmarks-1.0
