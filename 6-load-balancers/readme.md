# LOAD BALANCERS
- load balancers are servers that forward traffic to multiple server
- it distributes the traffic equally among the healthy instances
- expose a single point of access DNS to your application
- its a managed load balancer
- aws manages its upgrades, maintenance, HA
- integrated with many aws offerings

- Health Checks are crucial for load balancer
- they enable the load balancer to know if instance it forwards traffic to are available to reply to request
- health check is done on a port and a route (/health is common)
- if the response is not 200 then the instance is unhealthy

# Application Load Balancer (v2)
- alb is layer 7 
- load balancing to multiple  http applications accross machines
- support for http/2 and websockets
- supports redirectis (http to https)
- path based, query sting  and hostname based routing in url

- fixedhostname (XXX.region.elb.amazonaws.com)
- application servers dont see the ip of the client directly
- the true ip of client is inserted in forawrded header

| CLIENT IP --> CONNECTION TERMINATION --> load balancer private ip --> <-- ec2

## HANDS-ON
1. create few private ec2 instances
2. create a target group for these ec2 instances
3. create a ALB (internet facing) in public subnet
4. connect the alb to target group

# Network Load Balancer
- forwards TCP/UDP traffic to your instances
- handle millions of request per second
- less latencty (~100ms) compared to (~400ms ALB)
- NLB has one static IP per Az and supports assigning elastic ip 
- NLB are used for extreme performance, TCP or UDP traffic


# THESE WILL BE USEFUL IN EKS