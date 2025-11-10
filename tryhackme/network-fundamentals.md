# TryHackMe: Network fundamentals - completion Report

## Overview 
This report contains my writeup for the network fundamentals rooms covering OSI model , TCP/IP Protocols , DNS ,HTTP and Putting it all together. Which makes the essential foundation for understanding how network communicate and where security vulnerabilities exist.
 
---

### OSI model and its functions**

| Layer | Name | Function | Protocols/Examples |
|-------|------|----------|-------------------|
| 7 | Application | User interface | HTTP, FTP, SMTP, DNS |
| 6 | Presentation | Data formatting | SSL/TLS, JPEG, ASCII |
| 5 | Session | Connection management | NetBIOS, RPC |
| 4 | Transport | End-to-end delivery | TCP, UDP |
| 3 | Network | Routing & addressing | IP, ICMP, OSPF |
| 2 | Data Link | MAC addressing | Ethernet, Wi-Fi |
| 1 | Physical | Physical transmission | Cables, signals |

**Application**  : Provide interface for the program or application for data input and then it passed down into the presentation layer

**Presentation** : Receives the data and translates into a standardised format by handling encryption , compression and data format that application understands. The formatted data passed down to session layer. 

**Session**      :	Sets up the connection with device across the network for data transmission. once the connection is established it maintains the session to synchronise communication between the devices for further transmission and upon failure it throws an error. 

**Transport**    :	After establishing a connection , the transport layer choose the protocol over which the data is to be transmitted. The common protocols are TCP and UDP. After selection of the protocol the transport layer divides the data into bite-sized pieces to transmit and signals the network layer for locating the destination.

**Network**      :	It locates the destination of the device's ip address and figures the best route for transmission across the internet.

**Data link**    :	It receives the data from the network layer which is reduced to packets and adds in the physical address (MAC)  of the destination's device. The layer also ensures the data is not corrupted during the transmission.

**Physical**     :	The physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.


###  IP addressing, TCP, UDP protocols

**IP Addressing:**
- **IPv4:** 192.168.1.1 (32-bit, 4.3 billion addresses)
- **IPv6:** 2001:0db8:85a3::8a2e:0370:7334 (128-bit, virtually unlimited)
- **Private ranges:** 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16
- **Subnetting:** CIDR notation (/24, /16, /8)

**TCP vs UDP:**

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | Best-effort |
| Speed | Slower (overhead) | Faster (no overhead) |
| Use cases | HTTP, FTP, SSH | DNS, streaming, gaming |
| Header size | 20 bytes | 8 bytes |

**TCP 3-Way Handshake:**
Client Server
│ │
├─── SYN ──────→│ (Client: "Let's connect")
│ │
│←── SYN-ACK ───┤ (Server: "OK, ready")
│ │
├─── ACK ──────→│ (Client: "Connected")
│ │

### Packet structure and network topology

**Packet Anatomy:**
┌─────────────────────────────────────┐
│ Header (Source/Dest IP, Port, etc.)│
├─────────────────────────────────────┤
│ Payload (Actual data being sent) │
├─────────────────────────────────────┤
│ Footer (Error checking) │
└─────────────────────────────────────┘

**Network Topologies:**
- **Star:** All devices connect to central switch
- **Bus:** Single cable connecting all devices
- **Ring:** Devices in circular loop
- **Mesh:** Every device connects to every other device

---

### 4. Introduction to LAN 
**Key Concepts:**
- **LAN:** Local Area Network (home, office)
- **WAN:** Wide Area Network (internet)
- **MAC Address:** Physical hardware address (48-bit)
- **ARP:** Maps IP addresses to MAC addresses
- **Switch:** Forwards traffic based on MAC addresses
- **Router:** Routes traffic between networks

**ARP Process:**
Computer A: "Who has IP 192.168.1.5?"
Computer B: "I do! My MAC is AA:BB:CC:DD:EE:FF"
Computer A: [Stores in ARP cache]

### 5. HTTP in Detail ✅

**HTTP Methods:**
- **GET:** Request data from server
- **POST:** Send data to server (forms, uploads)
- **PUT:** Update existing resource
- **DELETE:** Remove resource
- **HEAD:** Get headers only (no body)

**HTTP Status Codes:**

| Code | Meaning | Example |
|------|---------|---------|
| 200 | OK | Request successful |
| 301 | Moved Permanently | Resource relocated |
| 302 | Found | Temporary redirect |
| 400 | Bad Request | Malformed request |
| 401 | Unauthorized | Authentication required |
| 403 | Forbidden | No permission |
| 404 | Not Found | Resource doesn't exist |
| 500 | Internal Server Error | Server crashed |
| 503 | Service Unavailable | Server overloaded |

**HTTP Request Structure:**
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html

**HTTP Response Structure:**
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>...</html> ```

## DNS in Detail 

DNS Hierarchy:

text
Root (.)
  ↓
TLD (.com, .org, .net)
  ↓
Domain (example.com)
  ↓
Subdomain (www.example.com, mail.example.com)

DNS Query Process:
1. You type: www.google.com
2. Check local DNS cache
3. If not cached, ask DNS resolver
4. Resolver asks root DNS servers
5. Root points to .com TLD servers
6. TLD points to google.com nameservers
7. Nameserver returns IP: 142.250.185.46
8. Browser connects to that IP


DNS Record Types:

A: Domain → IPv4 address

AAAA: Domain → IPv6 address

CNAME: Alias to another domain

MX: Mail server for domain

TXT: Text records (SPF, verification)

NS: Nameserver for domain


## How This Applies to Security:

Port Scanning (nmap):

Uses TCP/UDP to probe ports

Identifies running services

Maps network topology

Foundation for vulnerability assessment

Web Exploitation:

HTTP knowledge enables SQL injection, XSS attacks

Understanding status codes helps identify misconfigurations

Cookie manipulation requires HTTP header knowledge

Network Forensics:

Wireshark analysis requires protocol understanding

Packet inspection reveals malicious traffic

DNS logs show C2 communication

Malware Analysis:

Network traffic reveals malware communication

DNS queries show infected hosts

HTTP/HTTPS analysis exposes data exfiltration
