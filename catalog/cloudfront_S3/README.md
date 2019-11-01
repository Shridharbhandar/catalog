# IbexCatalog
  
  * This s3_cloudfront.yml template is for cloudfront configured with s3 to host static web content
  
# Prerequisites
 
 * To run the above template in cloudformation you need to have the below
    
    * FQDN(Fully Qualified Domain)
    * ARN of SSL Certificate in AWS
    
   ## Note
   
      * The ARN of SSL Certificate Should be from the same region where the Cloudformation Stack is running
      
   # Parameters
   
    * As a parameter we will give Dimain Name and ARN of SSL Certificate
      
   # What the template does
   
    * This template will create a cloudfront Web Distrubition Configured with S3 bucket. What ever web content is placed in s3 bucket 
      that content will displayed via Clodfront Domain Name. And it will also Create a Log S3 bucket to store the access logs
      
      
   # Outputs Of Clodformation Stack
   
      * as a outputs you will get the below things
      
        * Name of S3 bucket to hold website content
        * The URL of the newly created website
        * Name of cloudfront logdelivery bucket
      
