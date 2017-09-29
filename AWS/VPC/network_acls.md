# Network ACLS 

The Network Access Control Lists (ACLS) are the security gates for subnets.
 They dictate what traffic can enter and leave a subnet. 

## Properties 

1. Inbound Rules
 - CIDR of ports and protocols allowed or denied incoming traffic

2. Outbound Rules
 - CIDR of ports and protocols allowed or denied outgoing traffic

3. Subnet Associations
  - A list of subnets that the Network ACL applies to
  - Network ACLS apply to many subnets, but subnets can only have one Network
    ACL

## Route Tables vs Network ACLS

  - Route tables describe what subnets are reachable. 
  - Network ACLS describe what traffic can enter a subnet.

