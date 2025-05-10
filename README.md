# AWS PROJECTS

**this repo contains all the aws specific projects**
**each project have their own documentation in thier specific folders**

# 1. vpc-peering
  - connecting 2 vpc (eu-central-1) (us-east1) of same account through vpc peering
  - creating 1 ec2 in each private subnet and testing ping before and after peering
  - make sure to choose the correct vpc when creating ec2 and allowing icmpv4 from securing group

# 2. vpc-flowlog
  - logs all the IP traffic coming in and out in a vpc
  - all the active netwrok interfaces get loggeg
  - cloudwatch, s3, kinesis firehouse can be used to store and monitor logs depending on usecase
  - it does requrie to assume a role with permissions to create and put logs in cloudwatch logs group

