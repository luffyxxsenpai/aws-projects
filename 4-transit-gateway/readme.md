# AWS TRANSIT GATEWAY
VPC Peering is all nice and cool but it has some limitations, like gateway vpc peering only supports s3 and dynamodb but if you need other services then you have to go with interface gateway which does provide some extra services but at cost and still with all this vpc peering is not transitive which means if you want all your vpc to act like a mesh network then peering will be a mess.

![img](https://docs.aws.amazon.com/images/vpc/latest/tgw/images/transit-gateway-overview.png)

- TRANSIT GATEWAY comes in the picture
- AWS TRANSIT GATEWAY acts like a central hub for all the connected VPCs
- it is used to interconnect multiple vpcs and on-premise network
- as the name suggests, it creates a transitive connection among the vpcs
- it supports cross account, multi region connection
- since its an aws managed service  there is no single point of failure
- key components are transit gateway, transit gateway attachment and trasit gateway route table

# HOW TO SETUP
1. have some vpcs atleast 3 to 4 in multiple regions for a better practicle
2. launch 1 ec2 in each vpc, make sure you can ssh into them so better create them in public subnets 
3. now if we try to ping another ec2 by their private ip, it will simply timeout

4. in the vpc dashboard go to transit gateway and create one in all the region your vpc belongs to
5. create a transit gateway attachment for each vpc of each region so if we have 1 vpc in ap-south-1 and 2 in us-east-1 we will have total of 3 attachment accros 2 regions
6. now next step is to create another transit gateway attachment but this time choose peering option instead of vpc and send a peering request to another transit gateway
7. accept the transit gateway request from another region
8. now in transit gateway route table, select the route and from action click on create static route and add the vpc cidr of opposing vpc for each vpc cidr
9. now we have to update our route table of each vpcs of each region to cross refrence all the vpc cidr in each route table and choosing the transit gateway as the target 
10. if everything goes well, we will we able to ping our ec2 using private ip 

**i forgot to take screenshots and transit gateway can get confusing especially when doing route table updates so i ll try to make a video of this hands on later**