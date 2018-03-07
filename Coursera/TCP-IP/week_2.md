# Week 2

## TCP / IP Layers & Operations 

OSI 7 Layer Model:
7. Application 
6. Presentation 
5. Session
4. Transport
3. Network 
2. Data Link
1. Physical

TCP/IP 5 Layer Model:
5. Application
4. Transport 
3. Internet 
2. Network Access
1. Physical 

## OSI - Open Systems Interconnection 

- Used to characterize and standardize communication functions of a telecom or
  computing system
- Standardized as ISO/EIC 7498 and ITU-T Standard X.200 

## TCP/IP 

- Simpler than OSI
- Developed for ARPANET 
- Currently maintained by the IETF and IAB.

## TCP/IP Network Operations 

Application File Transfer Example: 

1. Application on computer H1 creates a file that needs to be transfered to H2
2. Application data file is divided into payload segments based on the Maximum
Transfer Unit (MTU) size of the IP packet and Ethernet frame requests
3. TCP header is added to the data segment 
 - Three Way Handshake: 
   1. H1 sends Synchronize (SYN) message to H2
   2. H2 sends it's own SYN message and a Acknowledgement (ACK) message
   3. H1 replies with it's ACK message 
 - TCP Flow and Error Control is only controlled e2e via H1 and H2
4. IP header is added to create an IP packet 
 - Header includes source and destination address
 - IPv4 = 32bits IPv6 = 128bits 
5. Ethernet header and trailer are added to IP packet 
 - Used by internal switches 
 - Ethernet switches conduct control flow
 - Other protocols use their own header and trailer
6. Routers use the IP address to route IP packets
 - Routers use routing tables to determine where to send packets
 - Optimal paths are set up using routing algorithms
7. Ethernet frame is received at H2 Network Interface Card (NIC)
 - Header and trailer are used to detect errors in the frame
 - If error is detected, frame is discarded and frame retransmission is
   requested
8. Ethernet header and trailer are removed to reveal the IP packet
 - IP Packet contains many network control functions that are checked
9. IP Header is removed to reveal TCP header
 - TCP will control window size to increase or decrease the data transfer rate 
 - TCP includes the port address to connect the data to the app on H2
10. TCP Header is removed to reveal the Payload Segment 
11. Payload Segments are combined to make the Data File 
12. Data file is delivered to Application on H2 

## TCP/IP Layers

Mailing books as a metaphor for TCP/IP

5. Application Layer
 - Sending a bunch of books to a friend
 - Books = File

4. Transport Layer
 - Divide the books into Boxes and Numbers => 1/3,2/3,3/3
 - Boxes = TCP Payload Segments 
 - Box Numbering => TCP Sequence Numbers 
 - Box numbers are used at destination to reorder books and find missing boxes

3. IP Layer
 - Add Sender and Receiver Address
 - Sender address => Source IP Address
 - Receiver address => Destination IP Address
 - IP address are used to route the packet to the destination address

2. Network Access Layer
 - Like: Air Mail, Surface Mail, Priority Mail
 - Real Life: Satellite, Mobile, Optical Fiber Network, Ethernet, Wifi,
   Bluetooth

1. Physical Layer 
 - Like: The airplane, truck, ship
 - Wired Electrical Signal & Cable
 - Wireless RF Signal & Antenna 
 - Optical Laser Signal & Optical Fiber

## TCP/IP Networking Functions 

5. Application 
 - Communications of applications and services between separate computers and
   hosts

4. Transport 
 - Port delivery to the application at the destination computer and more
 - TCP or UDP

3. Internet Protocol 
 - Internet is shorthand for Inter-Network
    * Provides inter-connection for networks using different Layer 2 protocols
 - Enables packets to go through multiple different interconnected networks 
 - Supports addressing & routing functions

2. Network Access Layer
 - Providers communication within a single type of network (Ethernet, Wifi, etc)
 - Within a network it provides device addressing, Priority Control, Error
   Control, Flow Control, etc
 - In Local Area Networks, the NAL device address is called the Medium Access
   Control (MAC) 

1. Physical Layer
 - Physical interface of devices and network to support sending and receiving 
 - Medium & Channel 
    - Wired / Cables (CAT5), Wireless, Optics/Lasers, Acoustic, Electro Magnetic
 - Modem aka Modulator + Demodulator 
    - RF, Microwave, Millimeter Wave, Light, Infrared, Lasers & Photodetectors
 - Antenna 
    - Single Antenna, Multiple / Array Antenna
    - Omni-directional Antenna, Directional Antenna 

## IPv4 Protocol 

Network Protocol Terminology 
- 1 Octet = 1 Byte = 8 bits
- Word = Group of multiple bits
- Flag = 1 bit control function 
  - value of 1 = set, 0 = clear 
- Datagram = IP Packet 
  - Defined as a self-contained independent entity of data containing sufficient
    information to be routed from the source to the destination without reliance
    on earlier exchanges between source, destination computers, and transporting
    network

- IPv4 Packet = Header + Payload 
  - Header = IPv4 Header
  - Payload = TCP/UDP Header + Payload Segment (Data)

### IPv4 Packet Header 

![IPv4-Header](https://github.com/zacaytion/til/coursera/TCP-IP/IPv4_header.jpg)

#### Version 
- 4 bits 
- Used to distinguish different IP packet versions
- IPv4 packets include the version value of 4

#### Internet Header Length (IHL)
- 4 bits 
- Length of an IPv4 header in words ( 1 word = 4 octets = 4 bytes = 32 bits)
- Minimum value is five, therefor minimum header length is 20 octets (5 x 4)

#### Differentiated Services (DS) & Explicit Congestion Notification (ECN)

- DS field is the first 6 bits 
  - Distinguishes service priority assignments 
- ECN field is the 2 bits following DS field 
  - used to signal congestion of the network to slow down the speed of packets
    being transmitted when delay or congestion are detected

#### Total Length 

- 16 bits 
- Describes the total length of the IP packet in units of octets
- Max IP packet length is 65,535 octets = 525,280 bits
- Packet size is limited by Layer 2 frame size

Maximum Transfer Unit: 
- Ethernet = 1500 octets of MTU 
- Wi-Fi = 2304 octet max size MAC Service Data Unit (MSDU) MTU
  - MAC Protocol Data Unit includes 
    - Frame Control (FC), Duration ID, Addresses, MSDU and FCS

#### Identification 

- 16 bits
-Sequence of numbers to uniquely identify the IPv4 packet 
- Used together with Source Address, Destination Address and Protocol Fields

#### Flags & Fragment Offset 

- Used in packet fragmentation 
- Divide a packet if the packet is too large to pass through a certain type of
  network 

FLAGS: 
- 3 bits 
- Only two bits are used
- Bit 0: Reserved, set to 0
- Bit 1: Don't Fragment (DF)
  - 1 = Don't Fragment, 0 = May Fragment 
- Bit 2: More Fragments (MF)
  - 1 = More Fragments, 0 = Last Fragment 

FRAGMENT OFFSET: 
- 13 bits
- Indicates where the current fragment belongs in the original datagram (in 64
  bit units)
  - Fragment other than the last fragment must contain a data field that is a
    multiple of 64 bits in length 

#### Time to Live (TTL)

- 8 bits
- Specifies the time length that a datagram is allowed to remain in the Internet
- Every router that the IP packet passes through should decrease the TTL by
  at least one.
- Similar to hop count

#### Protocol 

- 8 bits 
- Identifies the type of the next header in the packet directly following the
  IPv4 header 
- i.e ICMP, TCP, UDP, IGMP

#### Header Checksum

- 16 bits
- Error Detection code to protect the packet header from errors
- Does not protect the payload portion of the packet
- Errors are checked by the Header Checksum at each router
- Checking is needed because IP header fields may change when the packet is sent
  out a router (e.g TTL, Flags, Fragmentation)

#### Source & Destination Addresses

- Each address is 32 bits
- Classful Addresses of Class A, B, C, D, E 
- Classless Inter-Domain Routing (CIDR)

CIDR:
- Replaces Classful addresses because they were too large (wasting IP addresses)
- Makes the internet more scalable because networks can be assigned proper
  subnet sizes
- Enables IPv4 & IPv6 address block allocation to organizations based on actual
  network size and short-term predicted needs
- Uses Variable Length Subnet Masking (VLSM)

Addresses are assigned by the Internet Assigned Numbers Authority (IANA)
The Regional Internet Registry (RIR) assigns CIDR blocks to countries and
territories 

RIRs are subdivided into Local Internet Registry (LIR) subnets, which are
further divided into subnets for local network sizes.

#### Options

- Variable size
- Includes the options requested by the sending host computer

#### Padding

- Variable Size
- Used to make sure that the IPv4 packet header is a multiple of 32 bit word
  units in length 
- IHL is in 32 bit word units and padding helps to match the length 


### IPv6 Protocol 

- Uses Hexadecimal (Ox) numbering 

[IPv6 Header](https://github.com/zacaytion/til/coursera/TCP-IP/IPv6_header.png)

#### Version

- 4 bits
- For IPv6 the value is 6

#### DS & ECN 

- 8 bits 
- First 6 bits are for DS
- Following 2 bits are for ECN 

#### Flow Label

- 20 bits 
- Originally created to provide special support for real-time applications 
- Currently used to inform routers and switches not to change the routing path
  because reordering packets is difficult for the receiver 

#### Payload Length 

- 16 bits
- Size of the payload in octets, including extension headers
- Max payload size = 2^16 - 1 = 65,534 octets

IPv6 Jumbogram! 
- max payload size of (2^32 -1) octets = 4,294,967,295 = 4GB 
- payload length field is set to 0
- provides enhanced performance over networks that can support it
- packets need to use the Jumbo Payload Option extension header

#### Next Header

- 8 bits
- Specifies the type of the next header (Extension or Transport Layer header)
- i.e. ICMP, IGMP, TCP, UDP, ENCAP,
- Multiple extension headers can be added 
- Each extension header has a different format, but most follow the format of:
  - TLV: Type, Length, Value (padding)

Extension Headers:
- Hop-by-Hop Options
- Routing
- Fragment 
- Encapsulating Security Payload (ESP)
- Authentication Header (AH)
- Destination Options
- Mobility 

#### Hob Limit

- 8 bits 
- Value is decreased by one at each intermediate node that the packet passes
  through
- Packet is discarded when HL=0

#### Source & Destination Addresses 

- 128 bit addresses 
- Uses CIDR 

IPv6 Addresses:
- 8 groups of 16 bits = 4 hex digits 
- 1 : 2 : 3 : 4 : 5 : 6 : 7 : 8

IPv6 Address Representation:
- zeros in front of the 4 hex digits can be omitted 
- One or more consecutive groups of zeros may be replaced with two consecutive
  colons '::' only once in an IPv6 address 

examples: 
- 2ac1:05b8:123e:0000:0000:0000:03a0:c234
- 2ac1:5b8:123e::3a0:c234

Frequently used addresses 
- Unspecified Address ::/128
  - All zero address 
  - Equivalent to 0.0.0.0/32 in IPv4
- Default Route ::/0
  - All zero route address and all zero subnet mask covering all addresses
  - Equivalent to 0.0.0.0/0 in IPv4
- IPv4 mapped to IPv6 address ::fff:0:0/96


### UDP Protocol 

[UDP Header](https://github.com/zacaytion/til/coursera/TCP-IP/UDP_header.png)

- Provides port information for application connection 
- Connectionless: UDP does not establish an e2e connection manager to check on
  the received packets

#### Port 

- 16 bits each for source and destination
- Includes the source port and destination port

#### Length 

- 16 bits
- Contains the length of the entire UDP segment, which includes the UDP header
  and data

#### Checksum 

- 16 bits
- Used to detect bit errors in the UDP header
- Uses the same error checking algorithm as TCP and IPv4 headers
- If error is detected the segment is discarded and no error recovery action is
  taken
- Use of checksum field is optional
- When not used, all bits are set to zero


### TCP Protocol 

[TCP Header](https://github.com/zacaytion/til/coursera/TCP-IP/TCP_header.png)

- Max length of 20 octets 
- Contains various data segment flow control functionalities

#### Checksum 

- 16 bits
- Error Detection code added to protect the TCP header from errors
- Once the packet is complete, the sum is added to the checksum

Checksum Computation 
- TCP Pseudo Header : IP Addresses, Reserved, Protocol, TCP length 
- TCP Header (Checksum bits preset to zeros)
- TCP Data 

#### Data Offset 

- 4 bits 
- Number of 32 bit words in the TCP header
  - Min header length is 20 octets
- When additional Options are used, padding may be added to make the TCP header
  length a multiple of 32 bit words

#### Reserved

- 4 bits 
- Reserved for future use

#### Source & Destination Ports

- 16 bits each 
- i.e. SMTP, DNS, HTTP, NTP, FTP, Telnet

#### PSH Flag 

- 1 bit 
- Push function 
- PSH = 1 pushes the data segment to the receiving application
- Push enables the received data segments to be quickly used by the application

#### Urgent Flag (URG) 

- 1 bit
- URG = 1 indicates that the Urgent Pointer field is in use

#### Urgent Pointer (UP)

- 16 bits 
- points to the urgent data location
- enables the receiver to know how much urgent data is coming
- SN + UP = Urgent data's last SN   

