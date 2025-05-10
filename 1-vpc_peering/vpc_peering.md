# VPC PEERING
VPC peering is a networking connection between two Virtual Private Clouds (VPCs) that enables you to route traffic between them using private IPv4 or IPv6 addresses. Instances in either VPC can communicate with each other as if they were within the same network. lets say we have out frontend in us-east-1 and out backend in ap-south-1 they cannot directly communicate using the private network and this is where peering comes in picture where it connect both vpc like they belong to same network and our traffic routes through the private network.

![from_aws](https://docs.aws.amazon.com/images/vpc/latest/peering/images/peering-intro-diagram.png)

- vpc peering works for both ipv4 and ipv6
- peering can be done accros 2 diffrent account or vpcs in 2 different region belonging to same account 
- AWS uses the existing infrastructure of a VPC to create a VPC peering connection
- it is neither a gateway nor a VPN connection, and does not rely on a separate piece of physical hardware. 
- There is no single point of failure for communication or a bandwidth bottleneck. 
- vpc peering does not have any charges like the creation of peering, time the connection exist are all free
- we only pay for the data transfer accross the vpc both side. prices vary depending on the inter/intra peering connection and region 

- connecting vpcs must not have overlapping IP addresses
- peering is not transitive (if vpcA<->vpcB, vpcB<->vpcC are peered then we cannout route traffic between vpcA and vpcC), they also have to be peered
- if vpcB has a NAT gateway and vpcA doesn't, then after peering also vpcA wont be able to access internet through NAT of vpcB


## HANDS-ON
- create 2 vpc with 1 private subnet in 2 different region like one vpc in us-east-1 and another in eu-central-1
- create 1 ec2 in each vpc with icmp inbound rule open in both of ec2's security group
- send a peering request from vpc1 to vpc2
- switch to vpc regin2 -> peering connection and from action button accept the peering request
- update the route table of both vpc to use the new peering connection route 
- now both vpc can talk to each other which can be tested by pinging  any ec2-1 to ec2-2



