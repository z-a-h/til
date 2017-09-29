# Virtual Private Clouds

VPC are a private network the servers in the cloud. 

VPC give users more control over their infrastructure and provide extra security.

VPC define a range of IP address using CIDR block notation.

## CIDR Block Notation

CIDR block notation is used to divide the IP address into sub address 
using a 'subnet mask'. The mask specifies the range of the sub sets. 
The notation follows the format `IP-Address/mask`

Examples of ranges for `10.0.0.0/x`

```
10.0.0.0/8 = 10.0.0.0 - 10.255.255.255 (16777216 IP addresses)
10.0.0.0/16 = 10.0.0.0 - 10.0.255.255 (65536 IP addresses)
10.0.0.0/20 = 10.0.0.0 - 10.0.15.255 (4096 IP addresses)
10.0.0.0/32 = 10.0.0.0 (1 IP address)
```

## RFC1918 Private Ranges

Range of IPs officially set aside for private networking

| CIDR Notation   | Lower Bound   | Upper Bound       |
| --------------- | ------------- | ----------------- |
| `10.0.0.0/x`    | `10.0.0.0`    | `10.255.255.255`  |
| `192.168.0.0/x` | `192.168.0.0` | `192.168.255.255` |
| `172.16.0.0/x`  | `172.16.0.0`  | `172.31.255.255`  |

## Components

1. AWS Default VPC

2. Our VPC - 

3. Subnets - smaller networks within the VPC, divided by roles


