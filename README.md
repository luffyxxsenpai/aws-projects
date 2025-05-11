# AWS PROJECTS

**this repo contains all the aws specific projects**
**each project have their own documentation in thier specific folders**

# 1. VPC-PEERING
  - connecting 2 vpc (eu-central-1) (us-east1) of same account through vpc peering
  - creating 1 ec2 in each private subnet and testing ping before and after peering
  - make sure to choose the correct vpc when creating ec2 and allowing icmpv4 from securing group

# 2. VPC-FLOWLOGS
  - logs all the IP traffic coming in and out in a vpc
  - all the active netwrok interfaces get loggeg
  - cloudwatch, s3, kinesis firehouse can be used to store and monitor logs depending on usecase
  - it does requrie to assume a role with permissions to create and put logs in cloudwatch logs group

# 3. VPC-ENDPOINTS
  - allows to use a secure way to connect to aws resources without traffic leaving the aws network 
  - gateway endpoints only support S3 and DynamoDB and is free of cost 
  - gateway endpoitns simply modify the route table to route traffic using the private ip
  - whereas interface endpoints uses aws privatelink technology to create a dedicated EIP in our subnets
  - gateway incur charges based on hourly usage and data transfer 
  - but it does suppports more services like (kms, ssm, s3, dynamodb, cloudwatch, api gateway, etc.) 

# 4. TRANSIT GATEWAY
  - acts as a central hub to interconnect multiple vpc and on-primise networks
  - can add vpc,vpn,directlink from different accounts also with multi region support
  - aws managed service with High Availability 
  - nees to update the route table for each vpc to cross refrence all the other vpc through the transit gateway route table
  - highly efficient when theres a large number vpc to connect
  - supports transitive property unlike vpc peering with very limited functionality
  - one transit gateway per region 
