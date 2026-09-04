# Wireshark-Network-Traffic-Analysis

#Project Goal

To learn how network communication works by using the application Wireshark. To capture and analyze network traffic, a focus was placed on DNS queries, TCP connections, IP addresses, ports and HTTPS encryption


#Tools Used

-Wireshark
-Firefox Web Browser
-TCP/IP
-DNS
-HTTPS

#Project Overview

While accessing websites, I captured network traffic and analyzed their packets with the use of Wireshark. This analysis focused on understanding how DNS resolves domain names, how TCP establishes connections and how HTTPS encryption affects packet visibility

## 1. DNS Analysis
# What I investigated
-DNS queries and responses
-Domain names
-DNS server
-IP addresses returned by DNS

##Findings 

I queried the domain example.com, and my computer communicated with the DNS server at 192.168.238.2. In response to my standard query, the DNS server responded with the website's IP address 172.66.157.237. My computer could then use this IP address to establish a connection with the website. 


## 2. TCP Three-Way Handshake
# What I Investigated

I analyzed the TCP connection establishment process and identified the SYN, SYN/ACK, and ACK packets

##Findings

- SYN packet: Found
- SYN/ACK packet: Found
- ACK packet: Found

To access this handshake, I first set the Wireshark filter to tcp.flags.syn == 1 so it was only filtered to TCP packets where the synchronized (SYN) flag was turned on.

Afterwards, I tried to scope an initial SYN packet and tried to find its corresponding SYN/ACK with the same ports. The initial source port is 56172 and the destination port was 80, and my computer acted as the client and attempted to establish a connection with the server. The server responded with a SYN/ACK packet to accept the connection, with the source and destination ports reversed. Lastly, my computer acknowledged the reply and sent an ACK packet to complete the connection and completed the TCP three-way handshake. 

To view the final ACK packet, the SYN filter is removed. 

## 3. HTTPS Traffic

# What I Investigated

I examined traffic sent over HTTPS and compared what information could be observed at the packet level

## Findings

To view websites specifically using HTTPS in the filter for Wireshark I inputed tcp.port == 443. 

Within this I discovered that I couldn't read the actual website traffic due to HTTPS/TLS encryption. In comparison to HTTP, websites without encryption protection would have their attributes easily readable such as GET requests for website resources such as CSS files within the information section. However, when attempting to view HTTPS packets I am only able to view information such as the protocols being used, IP address, ports and TCP flags, but nothing specific to the contents of the communication. 

## Key Takeaways

- DNS translates domain names into IP addresses
- TCP uses a three way handshake to establish a connection
- IP addresses identify the source and destination of network traffic
- Ports help identify network services and connections
- HTTPS encrypts application data, preventing the contents from being viewed directly in a packet capture

 
