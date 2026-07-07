# Wireshark Lab - DHCP

This lab uses Wireshark to capture and analyze the DHCP Discover/Offer/Request/ACK message exchange a host uses to obtain an IP address lease from a DHCP server.

## 1. Are DHCP messages sent over UDP or TCP?

DHCP messages are sent using UDP. DHCP clients use UDP port 68 and DHCP servers use UDP port 67.

![Wireshark packet list filtered on bootp showing the DHCP message exchange, with a DHCP Request packet expanded in the detail pane](images/fig-01.png)

## 2. Draw the DHCP Discover/Offer/Request/ACK exchange.

```
Client (0.0.0.0:68) -> Server (192.168.1.1:67): DHCP Discover
Server -> Client: DHCP Offer
Client -> Server: DHCP Request
Server -> Client: DHCP ACK
```

Ports are the standard DHCP ports 67 and 68.

![Wireshark packet list showing the four DHCP Discover, Offer, Request, and ACK packets in sequence](images/fig-02.png)

## 3. What is the link-layer address of your host?

30:d0:42:xx:xx:xx

![Wireshark packet detail pane showing the client's Ethernet source MAC address in a DHCP packet](images/fig-03.png)

## 4. What values differentiate Discover from Request?

The Request contains Option 50 (Requested IP Address 192.168.1.137), Option 54 (DHCP Server Identifier 192.168.1.1), and DHCP Message Type=Request.

![Wireshark packet detail pane showing DHCP Request options, including Requested IP Address and Server Identifier](images/fig-04.png)

![Wireshark packet detail pane showing additional DHCP Request option fields](images/fig-05.png)

## 5. Transaction IDs and purpose

First exchange: 0x7befa33c. Second Request/ACK exchange: 0x8fa4071a. Transaction IDs associate DHCP messages with the same conversation.

![Wireshark packet list showing DHCP exchanges with different Transaction ID values](images/fig-06.png)

## 6. Source and destination IP addresses

Discover: 0.0.0.0 -> 255.255.255.255; Offer: 192.168.1.1 -> 192.168.1.137; Request: 0.0.0.0 -> 255.255.255.255; ACK: 192.168.1.1 -> 192.168.1.137.

![Wireshark packet detail pane showing DHCP source and destination IP addresses](images/fig-07.png)

![Wireshark packet detail pane showing the DHCP Offer packet's IP header with server and client addresses](images/fig-08.png)

## 7. DHCP server IP

192.168.1.1

![Wireshark packet detail pane showing the DHCP server IP address](images/fig-09.png)

## 8. Offered IP address

192.168.1.137

![Wireshark packet detail pane showing the client's offered IP address](images/fig-10.png)

## 9. Relay agent

No relay agent present. Relay Agent IP = 0.0.0.0.

![Wireshark packet detail pane showing the Relay Agent IP address field set to 0.0.0.0](images/fig-11.png)

## 10. Purpose of router and subnet mask

Router identifies the default gateway (192.168.1.1). Subnet mask (255.255.255.0) identifies the local network.

![Wireshark packet detail pane showing the DHCP Offer's Router and Subnet Mask options](images/fig-12.png)

## 11. Did the client accept the offer?

Yes. The client requested 192.168.1.137 and received a DHCP ACK.

![Wireshark packet detail pane showing the DHCP ACK confirming the offered address](images/fig-13.png)

## 12. Lease time

The lease time is 12 hours (43200 seconds).

![Wireshark packet detail pane showing the DHCP IP Address Lease Time option set to 12 hours](images/fig-14.png)

## 13. Purpose of DHCP Release

It informs the server the client is giving up the address. If lost, the address remains leased until expiration.

![Wireshark packet detail pane showing DHCP Offer option fields used to reason about lease release behavior](images/fig-15.png)

## 14. ARP packets observed

Yes. ARP Probes, Requests, and Announcements were observed to detect duplicates and announce ownership of 192.168.1.137.

![Wireshark packet detail pane related to address conflict detection discussion](images/fig-16.png)

![Wireshark packet list filtered on arp showing ARP Probe, Request, and Announcement packets for 192.168.1.137](images/fig-17.png)
