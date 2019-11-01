# SSM CFT

## Parameters

* TagValue - The value through which the monitoring of an Instance or Target group is decided
* TagType - The tag and it's key such as Environment, Application, Name, etc.  It should be in this form tag:Key 
    #### Example - "tag:<name>"
* TargetType - The type through which the monitoring of an Instance or Target group is decided
* Document - The document policy based on which the SSM is enabled and process functionality

## Functionality

Based on the Cron value the scheduling occurs. The document decides what action is going to be happened on the Resource group or Instance. It'll create various resources in the SSM such as Window, Targets & Tasks.

## FlowDiagram

![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/images/Images/SSM.png)
