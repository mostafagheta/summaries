# Networking Notes

## Networking
**DHCP** (Dynamic Host Configuration Protocol) 
What DHCP does:  
When a device (client) joins a network:  
IP Address Assignment   
Subnet Mask   
Default Gateway   
DNS Server(s)  

## DHCP Process (DORA):
**Discover**
The client (new device) broadcasts a DHCP Discover message.

**Offer**
A DHCP server on the network responds with a DHCP Offer.  
The offer includes:  
Available IP address  
Subnet mask  
Gateway  
DNS servers  
Lease time  

**Request**
The client replies with a DHCP Request to the server.

**Acknowledge**
The server sends a DHCP Acknowledgment (ACK).  

A DHCP relay agent forwards DHCP requests and responses between clients on
different subnets and a DHCP server  

## NAT (Network Address Translation)
It allows multiple devices on a private network to access the internet using one public IP address.  

1-**Static NAT (One-to-One NAT)**  
Maps one private IP to one public IP.  

2-**Dynamic NAT (Many-to-Many NAT)**  
Maps private IPs to a pool of public IPs dynamically.  

3-**PAT** (Port Address Translation) aka NAT Overload   
Maps many private IPs to a single public IP, but differentiates them using port numbers.  

**NAT64** (Network Address Translation 64) is a translation mechanism that allows IPv6-only clients to communicate with IPv4-only servers.  

**ARP** (Address Resolution Protocol) maps IP addresses to MAC addresses  

**Default gateway** is the router that connects devices in a local network to external
networks 

**routing table** : data structure stored in a router (or computer) that tells it where to forward network packets.
routing table contains information about routes and paths that routers use to
determine the best path for forwarding data to its destination.

**Contents of a Routing Table :**
Destination Network
Subnet Mask 
Gateway
Interface
Metric → Cost/priority of the route (lower = preferred).

**diff between static & dynamic routing ?**
Static routing involves manually configuring routes, while dynamic routing
protocols like OSPF and EIGRP automatically update routing tables based on
network changes.

**OSPF (Open Shortest Path First)** is a link-state routing protocol that calculates the
shortest path to reach network destinations using the SPF (Shortest Path First)
algorithm.

A default route (0.0.0.0/0) is used by routers to send traffic to a next-hop router
when no specific route exists in the routing table.

**Subnetting** is the process of dividing a large network (IP block) into smaller, more manageable sub-networks (subnets).

A **trunk port** is a switch port that carries traffic for multiple VLANs across a single physical link.

**HSRP (Hot Standby Router Protocol)**
HSRP is a Cisco proprietary protocol that provides gateway redundancy at Layer 3.
Multiple routers can work together to appear as a single virtual router.
Standardized alternative: VRRP (Virtual Router Redundancy Protocol, RFC 5798).

troubleshoot a network connectivity:
1-verifying physical connections
2-checking IP configurations, using diagnostic tools like ping and traceroute
3-analyzing log files

------------------------------------------------------------------------------
**ICMP (Internet Control Message Protocol)**
Reports network errors (e.g., destination unreachable, time exceeded).
Provides diagnostic tools (e.g., ping, traceroute).
Helps with network troubleshooting.
Ping → sends ICMP Echo Request, expects Echo Reply.
Traceroute discover the path packets take from your device to a destination
---------------------------------------------------------------------------------
**DNS** (Domain Name System) is a system that translates human-friendly domain names (like google) into IP addresses (like 142.250.190.14)

A DNS cache stores recently resolved DNS queries to improve DNS resolution
speed and reduce network traffic by reducing the need to query DNS servers
repeatedly.
--------------------------------------------------------------------------------
## OSI open system interconnection reference model
The 7 Layers of OSI

## 7. Application Layer (User Interface)

Examples of Application Layer Protocols
**HTTP / HTTPS** → (HyperText Transfer Protocol)
used for transferring hypertext (web pages) between web servers and browsers.
Default Port: 80.
HTTPS (HyperText Transfer Protocol Secure)
Secure version of HTTP.
Adds TLS/SSL encryption on top of HTTP.
Default Port: 443.
 
**FTP / SFTP → file transfer protocol**

**FTP** 
Transfer files between client ↔ server.
20 (data) → for file transfer (active mode).
21 (control) → for commands (login, ls, cd, put, get).

**SFTP (SSH File Transfer Protocol / Secure FTP)**
 Not the same as FTPS!
Purpose: Secure file transfer, built on SSH (Secure Shell).
Port: 22 (same as SSH).

**SMTP, POP3, IMAP → email.**

**MTP vs IMAP vs POP3**
**SMTP** → Simple Mail Transfer Protocol.
Default port: 25
For sending emails (outgoing)
send emails between clients and servers.

**POP3 (Port 110/995)** →
Post Office Protocol version 3
For downloading emails (usually removes from server).

**IMAP (Port 143/993)** → 
Internet Message Access Protocol
For syncing emails across devices (keeps messages on server).

**DNS** → name resolution (domain → IP).

**SNMP** 
Simple Network Management Protocol.
network management.
Used to monitor and manage network devices (routers, switches, servers, printers, etc.).

**Telnet / SSH** → remote login.
**Telnet** : Port: 23 (TCP).
**SSH** : port 22 (TCP)

## 6. Presentation Layer (Data Translation)
Ensures data is in a readable format for applications.
Handles encryption, compression, encoding.

## 5.Session Layer (Connection Management)
Establishes, maintains, and terminates sessions between devices.

## 4. Transport Layer (End-to-End Delivery)
Ensures reliable data delivery.
End-to-End Delivery
Flow Control
Error Detection & Correction

**TCP (Transmission Control Protocol)**
Connection-oriented (3-way handshake).
Reliable: guarantees delivery, order, and error recovery.
Full duplex
Error control Error checking(checksum)

Steps of the 3-Way Handshake
SYN (synchronize) → Client → Server
SYN-ACK (synchronize + acknowledge) → Server → Client
ACK (acknowledge) → Client → Server
Now connection is established → data transfer can start.

**UDP (User Datagram Protocol)**
Connectionless.
Unreliable: no guarantee of delivery or order.
Best effort

data unit:Segment (TCP) / Datagram (UDP)

## 3. Network Layer (Logical Addressing & Routing)

Main Functions:
**Logical Addressing** → Assigns IP addresses (IPv4/IPv6).
**Routing** → Finds the best path for data from source to destination.
**Packet Forwarding** → Moves packets across multiple networks
**Fragmentation & Reassembly** → Splits packets if they’re too large for the data link layer.
Protocols at Network Layer:
**IP (Internet Protocol)** → IPv4, IPv6 (core protocol).

**ICMP (Internet Control Message Protocol)** → Ping, Traceroute.

**IGMP (Internet Group Management Protocol)** :
Used by hosts and routers to manage multicast group memberships.
Unicast → one-to-one communication.
Broadcast → one-to-all communication.
Multicast → one-to-many communication

ARP (Address Resolution Protocol) → Maps IP → MAC (though technically works between Layer 2 & 3).
data: packet

## 2. Data Link Layer (MAC & Switching)
Responsible for node-to-node delivery on the same network.
Switches work at the Data Link Layer
Data Unit: Frame

## 1. Physical Layer (Bits & Media)
Lowest layer → sends raw bits (0s and 1s) over the physical medium.
Data Unit: bits

## IP Address Classes (A–E)
IPv4 addresses are divided into 5 classes based on the first octet (first 8 bits).
## 1. Class A
Range: 1.0.0.0 → 126.255.255.255
Default Subnet Mask: 255.0.0.0 (/8)
First Octet: 1–126
Usage: Very large networks (millions of hosts).
 
## 2. Class B
Range: 128.0.0.0 → 191.255.255.255
Default Subnet Mask: 255.255.0.0 (/16)
First Octet: 128–191
Usage: Medium-sized networks (thousands of hosts).

## 3. Class C
Range: 192.0.0.0 → 223.255.255.255
Default Subnet Mask: 255.255.255.0 (/24)
First Octet: 192–223
Usage: Small networks (up to 254 hosts).
Example: Home, small business networks.

## 4. Class D (Multicast)
Range: 224.0.0.0 → 239.255.255.255
Usage: Reserved for multicast groups (not normal hosts).
Example: Streaming, IPTV, IGMP.

## 5. Class E (Experimental)
Range: 240.0.0.0 → 255.255.255.255
Usage: Reserved for research, experimental.

 Special IPs
**127.0.0.1** → Loopback (localhost).
**169.254.x.x** → APIPA (auto-assigned if no DHCP).
**255.255.255.255** → Broadcast address.

------------------------------------------------------------------------------
**APIPA** 
Automatic Private IP Addressing
Auto configuration IP address
Rang : 169.254.X.X
Subnet Mask: 255.255.0.0
Gateway: No default gateway assigned (so can’t reach outside the local LAN).

**Private IPs** = for internal networks only (10.x.x.x, 172.16–31.x.x, 192.168.x.x).
They save public IP space and require NAT to access the internet.


**Port Numbers** 
Well Known ports
Range from 0 to 1,023 are assigned and controlled by ICANN

Registered ports
Range from 1,024 to 49,151 not assigned or controlled by ICANN but can be registered at ICANN
to avoid duplication

Dynamic ports
Range from 49,152 to 65,535 are neither controlled nor registered

**Socket Address** = IP + Port number
URL is Universal Resource Locator
