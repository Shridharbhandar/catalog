# IbexCatalog

## Requirements
* Configure Cloudtrail to send logs to a Cloudwatch log group as discussed in the Security Hub documentation
* Create a new SNS topic to send your alerts to.

## Parameters
* AlarmNotificationTopicARN
* CloudtrailLogGroupName

## Description
Cloudformation template which will create all of the needed log filters, metrics and alarms to conform with the CIS framework used by AWS Security hub.
