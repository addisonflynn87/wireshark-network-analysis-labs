# wireshark-network-analysis-labs
Wireshark packet-analysis labs (Ethernet/ARP, IP, DHP, NAT, ICMP, UDP, 802.11) from a TCP/IP networking ourse.
# Wireshark Network Analysis Labs

A set of hands-on packet-analysis projects covering the protocol stack from the link layer up through application-layer traffic b   Ethernet/ARP, IP, DHCP, NAT, ICMP, UDP, and 802.11 wireless. Each one captures live traffic on my own network (or works from a provided reference trace where noted), and documents the investigation with the actual Wireshark evidence behind each finding.

**Background:** U.S. Navy veteran and graduate of the Joint Cyber Analysis Course (JCAC), currently completing a B.A.S. in Cybersecurity/IT and transitioning into SOC analyst / cybersecurity analyst / network administrator roles. This repo is where I'm building and documenting the packet-level analysis skills behind that transition.

## Projects

| # | Project | Covers |
|---|---|---|
| 01 | [Wireshark Fundamentals](01-wireshark-fundamentals/) | Capture, filtering, and reading packet timing |
| 02 | [Ethernet & ARP Analysis](02-ethernet-and-arp-analysis/) | Ethernet II framing, the ARP request/reply cycle, ARP cache behavior |
| 03 | [IPv4 & Fragmentation Analysis](03-ip-protocol-analysis/) | IPv4 header structure, TTL, and fragmentation of oversized packets |
| 04 | [DHCP Lease Cycle Analysis](04-dhcp-lease-analysis/) | Full DHCP lease cycle (Discover/Offer/Request/ACK) and related ARP traffic |
| 05 | [NAT Traffic Analysis](05-nat-traffic-analysis/) | Comparing home-side vs. ISP-side captures to see exactly what NAT rewrites |
| 06 | [ICMP & Traceroute Analysis](06-icmp-traceroute-analysis/) | Ping and traceroute mechanics, Time Exceeded messages, hop latency |
| 07 | [UDP Protocol Analysis](07-udp-protocol-analysis/) | UDP header structure and request/reply port behavior |
| 08 | [802.11 Wireless Analysis](08-80211-wireless-analysis/) | Beacon frames, authentication/association handshake, AP forwarding behavior |

## Skills demonstrated

- Reading and interpreting packet captures at the Ethernet, IP, and transport layers
- Building and applying Wireshark display filters to isolate relevant traffic
- Tracing multi-step protocol exchanges (ARP resolution, DHCP leases, TCP/NAT translation, 802.11 association)
- Identifying anomalies and behavior changes across a network boundary (e.g., NAT address rewriting, latency jumps at backbone transitions)
- Correlating header fields across related packets (Identification/Fragment Offset in IP fragmentation, transaction IDs in DHCP, sequence numbers in ICMP)
- Documenting technical findings clearly, with evidence, for a reader who wasn't in the room

## Tools

Wireshark, Windows command-line utilities (`arp`, `ipconfig`), Windows Registry Editor.

## A note on redaction

Screenshots are otherwise unedited. Where my own laptop's or home router's MAC address appeared, the vendor prefix is left visible (e.g. `Dell_xx:xx:xx`) but the device-specific suffix is blacked out, in both the plain-text write-ups and the raw hex bytes in the packet-bytes pane. IP addresses, broadcast/multicast addresses, and identifiers belonging to remote servers or reference traces are left as captured, since they aren't personally identifying.
