# Creating a VPC

## Availability Zones

Availability zones are individual data centers inside a AWS Region. 

Subnets should be distributed throughout all the availability zones of the
region. There needs to be at lwest one subnet in each availability zones.

This is to provide fault tolerance of the VPC, in case one availability zone
goes down. 

## Deciding on Size of Subnets

Ideally the VPC will have subnets for each type (Public, Private, DB, Spare)
inside every AZ. Additionally, address space for development versions will be
required as well.


### Subnet Calculator

[IP Address Guide](http://www.ipaddressguide.com/cidr)
[MX Toolbox](http://mxtoolbox.com/subnetcalculator.aspx)


### AWS Reserved IPs

The first four IPs and the last IP address in each subnet CIDR block are
reserved by AWS.  The first four addressed, in order, are used as:
- Network address
- VPC router
- DNS Server for the VPC
- Reserved for future AWS use

The last IP address is the Network broadcast address, which is not supported in
a VPC.

## Example Subnet Architecture 

 ### Availability Zone: us-west-1a

|    CIDR         |   Subnet Name    |
| -------------   | ---------------- |
| `10.0.0.0/24`   | vpcity-a-public  |
| `10.0.1.0/25`   | vpcity-a-private |
| `10.0.1.128/26` | vpcity-a-db      |
| `10.0.1.192/26` | vpcity-a-spare   |

 ### Availability Zone: us-west-1c

|    CIDR         |   Subnet Name    |
| -------------   | ---------------- |
| `10.0.2.0/24`   | vpcity-c-public  |
| `10.0.3.0/25`   | vpcity-c-private |
| `10.0.3.128/26` | vpcity-c-db      |
| `10.0.3.192/26` | vpcity-c-spare   |


## Auto Assign Public IP Addresses to Public Subnets 

In AWS, in order to expose public subnets to the internet, enable auto-assigning
of IPv4 address to all instances launched in a subnet.
This is used to connect the instances to the public internet. 


## Elastic IP Address 

- Free-form IP address that can be associated and disassociated with different
  instances.
- You can only have 5 Elastic IP address per each region.


## Internet Gateway 

An internet gateway is used to connect the public subnets to the internet.
Create an new Internet Gateway and attach it to the VPC. 

## Route Tables

A route table is created by default when creating a new VPC. This is the 'main'
route table and by default all subnets are connected to the 'main' route table.
Create a new route table for the public subnet. Inside the route table, create
a new route with the destination `0.0.0.0/0` and target the recently created 
internet gateway.

After connecting the route table to the internet gateway, create subnet
associations for each public subnet in the VPC. 

## NAT Gateway 

Create a NAT Gateway inside of a subnet that uses a route table connected to an
internet gateway. The NAT gateway needs to use an Elastic IP, so create one and
assign it to the NAT gateway. 

Lastly, add a new route to the private route table, connecting `0.0.0.0/0` to
the NAT gateway. 
