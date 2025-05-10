# VPC FLOWLOGS
VPC FlowLogs allows us to capture the logs about IP traffic going to and from out vpc network.

- it captures all the incoming and outgoing ip traffics on the active network interfaces 
- it can help us to monitor traffic patterns, verify compliance requirements and for security and troubleshooting purposes
- Logs contatins
    - Source/Destination IP
    - Ports
    - Protocol
    - Packet sizes
    - Timestamps
    - Action (ACCEPT/REJECT)
    - Traffic direction

- Logs can be stored in CloudWatch Log group, S3 buckets or Kinesis Data Firehouse depending on the requriements

- FlowLogs requrie CloudWatch log group policies to create log groups and put logs in the log group

## HANDS ON
- create a vpc with 1 public subnet and internet gateway


- launch an EC2 in this vpc

- in cloudwatch create a log group

- now go to vpc 

- select your vpc -> go to action tab -> create Flow Logs

- select cloudwatch log group and auto create the permission for vpc to access log group

- and now all the traffics coming to and from on all the network interfaces of that vpc will be logged in the cloud watch log group selected
