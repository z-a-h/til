# Security Groups

Security groups protect resources at the server level rather than the subnet
level.

Unlike Network ACLS, security groups only care about whether traffic is
permitted to enter or leave the server.

Security Groups cannot explicitly deny traffic.

Security Groups are stateful, any responses to outbound traffic from inside our
VPC is allowed back in (even if the security group doesn't specifically allow
traffic from that IP address)

Security Groups can allow each other.

- The same rule can be applied to one group and used on multiple services.
- The servers and services can have multiple security groups.
 
