# IbexCatalog
  
  This CloudFormation Template creates VPC Flowlogs for existing VPC.

# Parameters
1. LogsDestinationType

    S3 (Default)
    
    CloudWatch
    
2. VPC (Existing VPC Ids in the AWS Region)
    
    14 (Default)
    
3. RetentionInDays
4. TrafficType
    
    ALL
    
    ACCEPT
    
    REJECT (Default)

# Description
This template creates VPC Flow Logs to the existing VPC. It asks for destination type of the logs and run accordingly. If User selects s3 then S3 Bucket and Log group is created with VPCFlowlogs-{VPCid}. Else Only Log group is created. User can also select particular traffic type to be logged. Also, customize the retention days of the Log group. 

# Outputs
1. Name of S3 bucket if S3 is chosen in log destination type
2. Name of LogGroup
3. ARN of LogGroup
