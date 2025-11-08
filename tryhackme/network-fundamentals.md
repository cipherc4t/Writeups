# TryHackMe: Network fundamentals - completion Report

## Overview 
This report contains my writeup for the network fundamentals rooms covering OSI model , TCP/IP Protocols , DNS ,HTTP and Putting it all together. Which makes the essential foundation for understanding how network communicate and where security vulnerabilities exist.
 
---

### 1. Introduction to Networking
 
**OSI model and its functions**

| Layer | Name | Function | Protocols/Examples |
|-------|------|----------|-------------------|
| 7 | Application | User interface | HTTP, FTP, SMTP, DNS |
| 6 | Presentation | Data formatting | SSL/TLS, JPEG, ASCII |
| 5 | Session | Connection management | NetBIOS, RPC |
| 4 | Transport | End-to-end delivery | TCP, UDP |
| 3 | Network | Routing & addressing | IP, ICMP, OSPF |
| 2 | Data Link | MAC addressing | Ethernet, Wi-Fi |
| 1 | Physical | Physical transmission | Cables, signals |

*Application:*	Provide interface for the program or application for data input and then it passed down into the presentation layer

*Presentation*	Receives the data and translates into a standardised format by handling encryption , compression and data format that application understands. The formatted data passed down to session layer. 

*Session*	Sets up the connection with device across the network for data transmission. once the connection is established it maintains the session to synchronise communication between the devices for further transmission and upon failure it throws an error. 

*Transport*	After establishing a connection , the transport layer choose the protocol over which the data is to be transmitted. The common protocols are TCP and UDP. After selection of the protocol the transport layer divides the data into bite-sized pieces to transmit and signals the network layer for locating the destination.

*Network*	It locates the destination of the device's ip address and figures the best route for transmission across the internet.

*Data link*	It receives the data from the network layer which is reduced to packets and adds in the physical address (MAC)  of the destination's device. The layer also ensures the data is not corrupted during the transmission.

*Physical*	The physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.

