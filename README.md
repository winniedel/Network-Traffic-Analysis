# Basic Network Analysis Using Wireshark

# Project Goal

To learn how network communication works by using the application Wireshark. To capture and analyze network traffic, a focus was placed on DNS queries, TCP connections, IP addresses, ports and HTTPS encryption


# Tools Used

- Wireshark
- Firefox Web Browser
- TCP/IP
- DNS
- HTTPS

# Project Overview

While accessing websites, I captured network traffic and analyzed their packets with the use of Wireshark. This analysis focused on understanding how DNS resolves domain names, how TCP establishes connections and how HTTPS encryption affects packet visibility

## 1. DNS Analysis
# What I investigated
- DNS queries and responses
- Domain names
- DNS server
- IP addresses returned by DNS

## Findings 

I queried the domain example.com, and my computer communicated with the DNS server at 192.168.238.2. In response to my standard query, the DNS server responded with the website's IP address 172.66.147.243. My computer could then use this IP address to establish a connection with the website. 

### Figure 1: DNS; Standard Query and Response

<img width="1373" height="377" alt="DNS " src="https://github.com/user-attachments/assets/3a0271ad-0c19-4da6-b24b-a8148032964a" />

## 2. TCP Three-Way Handshake
# What I Investigated

I analyzed the TCP connection establishment process and identified the SYN, SYN/ACK, and ACK packets

## Findings

- SYN packet: Found
- SYN/ACK packet: Found
- ACK packet: Found

To access this handshake, I first set the Wireshark filter to tcp.flags.syn == 1 so it was only filtered to TCP packets where the synchronized (SYN) flag was turned on.

### Figure 2: TCP Filter

<img width="1376" height="264" alt="TCP Filter" src="https://github.com/user-attachments/assets/3da0a2ee-8506-41d9-9d6d-bd3a4266aa92" />

## TCP Three-Way Handshake Continued

Afterwards, I tried to scope an initial SYN packet and tried to find its corresponding SYN/ACK with the same ports. The initial source port is 59820 and the destination port was 80. My computer acted as the client and attempted to establish a connection with the server. The server responded with a SYN/ACK packet to accept the connection, with the source and destination ports reversed. Lastly, my computer acknowledged the reply and sent an ACK packet to complete the connection therefore completing the TCP three-way handshake. 

### Figure 3: TCP Three-Way Handshake

<img width="1437" height="65" alt="TCP Three-Way Handshake" src="https://github.com/user-attachments/assets/5cda403f-ffd7-405b-a1a0-255c2779d7e6" />


## 3. HTTPS Traffic

# What I Investigated

I examined traffic sent over HTTPS and compared what information could be observed at the packet level

## Findings

To view websites specifically using HTTPS in the filter for Wireshark I inputed tcp.port == 443. Within this I discovered that I couldn't read the actual website traffic due to HTTPS/TLS encryption. The only information available are the protocols being used, IP addresses, as well as ports and TCP flags


### Figure 4: HTTPS Encryption

<img width="1422" height="468" alt="HTTPS Encryption" src="https://github.com/user-attachments/assets/4aac85cd-77a7-4a92-80f9-01f0e937a075" />


## HTTPS Traffic Continued

In comparison to HTTP, websites without encryption protection would have their attributes easily readable such as GET requests for the website in the info section. 

### Figure 5: HTTP

<img width="1430" height="224" alt="HTTP" src="https://github.com/user-attachments/assets/941ea8e1-1a48-4ce3-93f4-bd3c97e675d2" />


## Key Takeaways

- DNS translates domain names into IP addresses
- TCP uses a three way handshake to establish a connection
- IP addresses identify the source and destination of network traffic
- Ports help identify network services and connections
- HTTPS encrypts application data, preventing the contents from being viewed directly in a packet capture

 
