# Subnets 

Example Subnet Architecture 

| CIDR Notation   | Description     | IP Range                  | Number of IPs |
| --------------- | :-----------:   | -----------------         | :-----------: |
| `10.0.0.0/21`   | VPC             | `10.0.0.0 - 10.0.7.255`   | 2048
| `10.0.1.0/24`   | Public Subnet   | `10.0.0.0 - 10.0.0.255`   | 256
| `10.0.1.0/25`   | Private Subnet  | `10.0.1.0 - 10.0.1.127`   | 128
| `10.0.1.128/26  | Database Subnet | `10.0.1.128 - 10.0.1.191` | 64
| `10.0.1.192/26` | Spare Subnet    | `10.0.1.192 - 10.0.1.255` | 64

