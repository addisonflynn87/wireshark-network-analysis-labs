# Wireshark Lab: NAT v7.0

This lab compares two synchronized packet captures — one taken on the home LAN side of a router and one taken on the ISP (WAN) side — to observe how Network Address Translation (NAT) rewrites a packet's source/destination IP address and recalculates its checksum while leaving TCP ports and higher-layer data unchanged.

## Question 1

What is the IP address of the client?

**Answer:**

The client IP address is 192.168.1.100.

**Proof:**

The IPv4 header of the HTTP GET packet shows:

Source Address: 192.168.1.100

![Wireshark detail pane showing the Ethernet and IP headers of the HTTP GET packet, LAN-side capture](images/fig-01.png)

## Question 2

**Filter Used:**

```
http && ip.addr == 64.233.169.104
```

This filter displays only HTTP traffic between the client and the Google server (64.233.169.104).

![Packet list filtered to the HTTP GET/response exchange between the client and the Google server](images/fig-02.png)

## Question 3

Consider the HTTP GET sent from the client to the Google server at time 7.109267.

**Answer:**

The HTTP GET packet was sent at time 7.109267.

- Source IP Address: 192.168.1.100
- Destination IP Address: 64.233.169.104
- Source TCP Port: 4335
- Destination TCP Port: 80

**Proof:**

The selected HTTP GET packet shows:

- Time: 7.109267
- Source Address: 192.168.1.100
- Destination Address: 64.233.169.104
- Source Port: 4335
- Destination Port: 80

![TCP header detail showing the client's source port 4335 for the GET request](images/fig-03.png)
![IP header detail highlighting the destination address of the GET request](images/fig-04.png)
![IP header detail highlighting the source address of the GET request](images/fig-05.png)
![Frame detail showing the capture timestamp of the GET request](images/fig-06.png)
![TCP header detail showing the destination port 80 for the GET request](images/fig-07.png)

## Question 4

At what time is the corresponding HTTP 200 OK message received from the Google server?

**Answer:**

The HTTP 200 OK response was received at time 7.158797.

- Source IP Address: 64.233.169.104
- Destination IP Address: 192.168.1.100
- Source TCP Port: 80
- Destination TCP Port: 4335

**Proof:**

The HTTP/1.1 200 OK packet shows:

- Time: 7.158797
- Source Address: 64.233.169.104
- Destination Address: 192.168.1.100
- Source Port: 80
- Destination Port: 4335

![TCP header detail showing the server's source port 80 in the HTTP 200 OK response](images/fig-08.png)
![Ethernet, IP, and TCP header detail for the HTTP 200 OK response, LAN-side capture](images/fig-09.png)
![IP header detail showing the destination address of the 200 OK response](images/fig-10.png)
![IP header detail showing the source address of the 200 OK response](images/fig-11.png)
![Frame detail showing the capture timestamp of the 200 OK response](images/fig-12.png)

## Question 5

Recall that before a GET command can be sent to an HTTP server, TCP must first set up a connection using the three-way handshake.

**Answer:**

The TCP SYN segment was sent at time 7.075657.

- Source IP Address: 192.168.1.100
- Destination IP Address: 64.233.169.104
- Source Port: 4335
- Destination Port: 80

The SYN/ACK response was sent at time 7.108986.

- Source IP Address: 64.233.169.104
- Destination IP Address: 192.168.1.100
- Source Port: 80
- Destination Port: 4335

The ACK completing the TCP three-way handshake was received at time 7.109053.

- Source IP Address: 192.168.1.100
- Destination IP Address: 64.233.169.104
- Source Port: 4335
- Destination Port: 80

**Proof:**

- Packet 53 = SYN
- Packet 54 = SYN/ACK
- Packet 55 = ACK

![Packet list and hex dump for the TCP SYN segment (packet 53) of the three-way handshake, LAN-side capture](images/fig-13.png)
![Packet list and hex dump for the TCP SYN/ACK segment (packet 54) of the three-way handshake, LAN-side capture](images/fig-14.png)
![Packet list and hex dump for the TCP ACK segment (packet 55) completing the three-way handshake, LAN-side capture](images/fig-15.png)

## Question 6

In the NAT_ISP_side trace file, find the HTTP GET message corresponding to the GET at time 7.109267 in NAT_home_side.

**Answer:**

The corresponding HTTP GET appears at time 6.091618.

- Source IP Address: 71.192.xx.xx *(redacted — author's real public/WAN IP)*
- Destination IP Address: 64.233.169.104
- Source TCP Port: 4335
- Destination TCP Port: 80

**Comparison with Question 3:**

Same Fields:
- Destination IP Address (64.233.169.104)
- Source Port (4335)
- Destination Port (80)

Different Fields:
- Source IP changed from 192.168.1.100 to 71.192.xx.xx (the router's public/WAN address)

**Proof:**

![ISP-side capture: Ethernet and IP header detail for the HTTP GET packet showing the router's translated public source IP](images/fig-16.png)
![ISP-side capture: TCP header detail for the same HTTP GET packet](images/fig-17.png)
![ISP-side capture: IP header detail confirming the translated public source address on the GET packet](images/fig-18.png)
![ISP-side capture: packet list showing the repeated HTTP exchanges using the translated public IP address](images/fig-19.png)
![ISP-side capture: hex dump and Ethernet/IP/TCP header detail for the GET packet](images/fig-20.png)

## Question 7

Are any fields in the HTTP GET message changed?

**Answer:**

The HTTP GET message itself was not changed.

The following IP header fields were examined:

- Version: No Change
- Header Length: No Change
- Flags: No Change
- Checksum: Changed

The checksum changed because NAT modified the source IP address. Since the IP header changed, the checksum had to be recalculated.

**Proof:**

![ISP-side capture: IP/TCP header detail reused from Question 6 to compare against the LAN-side packet](images/fig-19.png)
![LAN-side capture: IP header detail reused from Question 3 to compare against the ISP-side packet](images/fig-05.png)

## Question 8

In the NAT_ISP_side trace file, at what time is the first HTTP 200 OK message received from the Google server?

**Answer:**

The first HTTP 200 OK message was received at time 6.117570.

- Source IP Address: 64.233.169.104
- Destination IP Address: 71.192.xx.xx *(redacted — author's real public/WAN IP)*
- Source TCP Port: 80
- Destination TCP Port: 4335

**Comparison with Question 4:**

Same Fields:
- Source IP Address
- Source Port
- Destination Port

Different Fields:
- Destination IP Address changed from 192.168.1.100 to 71.192.xx.xx

**Proof:**

![ISP-side capture: hex dump and TCP/Ethernet header detail for the HTTP 200 OK response](images/fig-21.png)
![ISP-side capture: IP header detail for the 200 OK response showing the translated destination address](images/fig-22.png)
![ISP-side capture: frame and Ethernet header detail for the 200 OK response](images/fig-23.png)

## Question 9

In the NAT_ISP_side trace file, at what time were the client-to-server TCP SYN segment and the server-to-client TCP SYN/ACK segment captured?

**Answer:**

Client-to-Server SYN:
- Time: 6.035475
- Source IP Address: 71.192.xx.xx *(redacted — author's real public/WAN IP)*
- Destination IP Address: 64.233.169.104
- Source Port: 4335
- Destination Port: 80

Server-to-Client SYN/ACK:
- Time: 6.067775
- Source IP Address: 64.233.169.104
- Destination IP Address: 71.192.xx.xx
- Source Port: 80
- Destination Port: 4335

ACK:
- Time: 6.068754
- Source IP Address: 71.192.xx.xx
- Destination IP Address: 64.233.169.104
- Source Port: 4335
- Destination Port: 80

**Comparison with Question 5:**

Same Fields:
- Source Port
- Destination Port

Different Fields:
- Private IP 192.168.1.100 was translated to Public IP 71.192.xx.xx

**Proof:**

![ISP-side capture: Ethernet/IP/TCP header detail for the ACK packet completing the handshake, showing the translated public source IP](images/fig-24.png)
![ISP-side capture: frame timing and Ethernet/IP header detail for the ACK packet](images/fig-25.png)
![ISP-side capture: TCP header detail for the SYN/ACK packet](images/fig-26.png)
![ISP-side capture: frame timing detail for the SYN/ACK packet](images/fig-27.png)
![ISP-side capture: IP header detail for the SYN packet showing the translated public source IP](images/fig-28.png)
![ISP-side capture: frame timing detail for the SYN packet](images/fig-29.png)
