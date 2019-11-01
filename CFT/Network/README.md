# Network CFT

## Parameters
* CustomerName 
* Environment(development/staging/production)
* CIDR (CIDR Block to use for VPC)

## Description
Template creates following
* VPC 
* 9 subnets 3 each for Public,App(Private) and DB subnets
* Couple of NAT gateways and routetables for DB and App subnets
* 3 route tables each for Public,Private and DB subnets with respective subnet associations
* 3 NACLs for three respective subnets.
Cidr ranges for subnets randomly picks up from VPC CIDR range. 

![Alt Text](https://github.com/ibexlabs/IbexCatalog/blob/images/Images/Network.png)


