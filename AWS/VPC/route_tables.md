# Route Tables

Route tables are the 'roads' between the different subnets inside a VPC.
These roads allow traffic to move between the subnets.  
Route tables are a list of CIDR blocks that the traffic can leave and come from. 

Route tables have subnet associations that show which subnets use which route
table.  A route table can have many subnets, but a subnet can only belong to one
route table.


## Public Subnets and Internet Gateways

A public subnet is a subnet with access to the internet. The public subnet
access the internet through an `internet gateway`.  


## Private Subnets and NAT Gateways 

Private subnets are subnets not exposed to the internet. If anything inside a
private subnet needs to send outbound traffic to the internet, it must be sent
through the Network Address Translation (NAT) gateway.

