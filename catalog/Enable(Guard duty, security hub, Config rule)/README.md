# CFT to enable Guard duty, security hub, Config rule

## Parameters

* IncludeGlobalResourceTypes - Indicates whether AWS Config records all supported global resource types. Only Boolean values are allowed.
* DeliveryChannelName - The name of the delivery channel.
* Frequency - The frequency with which AWS Config delivers configuration snapshots. You can select a desired value based upon whihc the updates will be tracked.
* TopicArn - The Amazon Resource Name (ARN) of the Amazon Simple Notification Service (Amazon SNS) topic that AWS Config delivers notifications

## It enables all the 3 services and creates a bucket for the config enablement as a part of the template for SNS topic 

## Flow Diagram

![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/images/Images/Enable-3.png)
