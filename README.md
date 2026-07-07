# Wireshark Network Analysis Labs

Hands-on packet capture and protocol analysis labs completed with [Wireshark](https://www.wireshark.org/) for a college Networking with TCP/IP course, based on the Kurose & Ross *Computer Networking: A Top-Down Approach* Wireshark lab series.

Each lab is a full write-up with questions, answers, analysis, and annotated packet-capture screenshots taken from live captures and supplied trace files. Together they cover the protocol stack from the link layer up through the application layer.

## Labs

| # | Lab | Protocols & Topics |
|---|-----|--------------------|
| 01 | [Introduction to Wireshark](lab-01-intro-wireshark/README.md) | Packet capture basics, HTTP/TCP/TLS identification, RTT calculation, header inspection |
| 02 | [Ethernet & ARP](lab-02-ethernet-arp/README.md) | Ethernet II frame structure, MAC addressing, ARP request/reply resolution |
| 03 | [IP](lab-03-ip/README.md) | IPv4 header fields, TTL handling, datagram fragmentation |
| 04 | [DHCP](lab-04-dhcp/README.md) | DHCP Discover/Offer/Request/ACK exchange, IP address leasing |
| 05 | [NAT](lab-05-nat/README.md) | Network Address Translation, LAN-side vs. WAN-side capture comparison, checksum recalculation |
| 06 | [ICMP](lab-06-icmp/README.md) | Echo Request/Reply, TTL Exceeded, `ping` and `traceroute` at the packet level |
| 07 | [UDP](lab-07-udp/README.md) | UDP header structure, connectionless transport behavior |
| 08 | [802.11 WiFi](lab-08-80211/README.md) | Beacon frames, authentication, association, probe request/response |
| 09 | [DNS](lab-09-dns/README.md) | DNS query/response structure, transport protocol and ports, record types |
| 10 | [TCP](lab-10-tcp/README.md) | Connection setup, sequence/ACK numbers, RTO estimation, flow control, congestion control |

## Skills Demonstrated

- Capturing live network traffic and working with supplied trace files
- Applying display filters to isolate protocol conversations
- Reading and interpreting protocol headers at every layer of the TCP/IP stack
- Correlating request/response pairs and calculating timing metrics (RTT, RTO)
- Documenting technical findings clearly with supporting evidence

## About

Completed by Addison Flynn, Summer 2026.
