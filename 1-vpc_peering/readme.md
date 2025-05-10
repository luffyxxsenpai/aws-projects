# VPC PEERING
VPC peering is a networking connection between two Virtual Private Clouds (VPCs) that enables you to route traffic between them using private IPv4 or IPv6 addresses. Instances in either VPC can communicate with each other as if they were within the same network. lets say we have out frontend in us-east-1 and out backend in ap-south-1 they cannot directly communicate using the private network and this is where peering comes in picture where it connect both vpc like they belong to same network and our traffic routes through the private network.

![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/vpc-peering.png)
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
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/rmap.png)
- create 1 ec2 in each vpc with icmp inbound rule open in both of ec2's security group

- send a peering request from vpc1 to vpc2
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/create-peer.png)
- switch to vpc regin2 -> peering connection and from action button accept the peering request
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/request.png)
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/pending.png)
- update the route table of both vpc to use the new peering connection route 
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/rt-1.png)
- now both vpc can talk to each other which can be tested by pinging  any ec2-1 to ec2-2
**before**
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/f-ping.png)
**after succesfull peering**
![rmap](https://github.com/luffyxxsenpai/aws-projects/blob/main/1-vpc_peering/img/s-ping.png)

**make sure to choose the correct vpc while creating the ec2 by editing the netwrok options**
**allow icmpv4 protocol in security group**
**if somehow you cannot connect to any of ec2 cause its private and no ssh keys, update 1vpc with a internet gateway and route to internet, then you can use instance connect but will need to recreate the ec2 or attach any public ip**

---