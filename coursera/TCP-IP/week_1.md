# Yonesi University TCP/IP Course

## Week 1

### Internet Setup

* IP addresses are assigned to each interface port
* An IPv4 address is 32 bits 
* One IP address is required for each interface (WiFi, ethernet, 4G, Bluetooth) 

_Subnet Mask_

* Subnet Mask is based on the size of the Subnet that the client is connected to
* Used to filter the IP address to easily determine if the packet belongs to the subnet

_Default Gateway_

* Dedicated internet router that will receive all internet IP packets for machine
* Machine accesses internet through this Gateway

_DNS_

* Domain Name Server 
* Converts host-names to IP addresses

### Dynamic Host Configuration Process

* DHCP enables a machine to automatically contact the local DHCP server an request 
 an IP address and networking params to connect to the Internet  
* When DHCP is used, setup is automatic. 
* DHCP services dynamically assign 
 - IP address
 - Subnet Mask
 - Default Gateway IP address 
 - DNS server IP address 
* enables reuse of IP addresses
* DHCP operates on a client-server model

_DHCP Setup Messages & Operaion_

1. Client connects to network
2. DHCP uses UDP (User Datagram Protocol) with Client Port 68 and DHCP Server
port 67
3. Client DHCP program broadcasts a 'Server Discovery' message requesting for
network information.
4. Any DHCP server on the network can provide service by replying an 'IP Lease
Offer' message to the client]
5. Client will send an 'IP Lease Request' back to the DHCP Server that sent the
'IP Lease Offer' message
6. That DHCP Server will send back an 'IP Lease Acknowledgement' enabling use of
an IP Address and network parameters for a limited time duration.

- When a client tried to reconnect to the Internet 
  * If a computer needs an IP address again, the DHCP server tried to give the
  same IP address that was used before by that computer
  * A different IP address may be assigned if that IP address is being used by
    another device or due to a network admin assignment policies

### IP Gateway/Router Configuration 

Subnet Mask = Net Mask

Subnet size must be represent at 2 to the power of something
i.e. 2^6 = 64, 2^5 = 32

In a subnet, assign highest IP to Broadcast IP, second highest IP to gateway
interface and lowest IP to network destination 

_CIDR_: Classless Inter-Domain Routing
