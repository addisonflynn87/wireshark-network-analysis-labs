# Wireshark Lab - IP

This lab uses Wireshark to examine the fields of the IPv4 header and to observe how ICMP-over-IP behavior (TTL handling and datagram fragmentation) shows up in captured packets.

## Question 1

**Answer:** My computer's IP address is 192.168.1.137.

![Wireshark frame detail for an ICMP echo request, showing the local host's source IP address 192.168.1.137](images/fig-01.png)

## Question 2

**Answer:** The upper layer protocol field contains ICMP (1).

![Wireshark IP header detail with the Protocol field set to ICMP (1)](images/fig-02.png)

## Question 3

**Answer:** IP Header Length = 20 bytes. Total Length = 92 bytes. Payload = 92 - 20 = 72 bytes.

![Wireshark IP header detail showing the Header Length field (20 bytes)](images/fig-03.png)

![Wireshark IP header detail showing the Total Length field (92 bytes)](images/fig-04.png)

## Question 4

**Answer:** The datagram was not fragmented. Flags = 0x0 and Fragment Offset = 0.

![Wireshark IP header detail showing the Flags field (0x0)](images/fig-05.png)

![Wireshark IP header detail showing the Fragment Offset field (0)](images/fig-06.png)

## Question 5

**Answer:** Fields that change: TTL, Identification, and Header Checksum.

![Wireshark packet list and frame detail showing changing Identification, TTL, and Header Checksum values across successive ICMP echo request datagrams](images/fig-07.png)

![Wireshark frame detail for a second ICMP echo request datagram, showing different Identification, TTL, and Header Checksum values compared to the previous packet](images/fig-08.png)

## Question 6

**Answer:** Fields that remain constant: Source Address, Destination Address, Protocol, Header Length, and Total Length. Fields that change: TTL, Identification, and Header Checksum.

![Wireshark packet list and frame detail illustrating which IP header fields stay constant across datagrams](images/fig-09.png)

![Wireshark frame detail for a second datagram used to compare constant and changing header fields](images/fig-10.png)

## Question 7

**Answer:** The Identification field increases sequentially as new datagrams are transmitted.

![Wireshark packet list and frame detail showing the Identification field increasing sequentially across consecutive datagrams](images/fig-11.png)

![Wireshark frame detail confirming the incremented Identification value in the next captured datagram](images/fig-12.png)

## Question 8

**Answer:** Nearest router TTL-exceeded reply: Identification = 10156, TTL = 64.

![Wireshark packet list and frame detail for the ICMP Time-to-live-exceeded reply from the nearest router](images/fig-13.png)

## Question 9

**Answer:** TTL remains the same for replies from the same router, while Identification changes because each packet is a separate datagram.

![Wireshark packet list and frame detail comparing TTL and Identification fields across multiple Time-to-live-exceeded replies from the same router](images/fig-14.png)

## Question 10

**Answer:** Yes. The 2000-byte ICMP Echo Request was fragmented across multiple IP datagrams.

![Wireshark packet list showing a large ICMP Echo Request fragmented into multiple IP datagrams, with the fragments reassembled by Wireshark](images/fig-15.png)

## Question 11

**Answer:** First fragment: Total Length = 1500 bytes, More Fragments flag set, Fragment Offset = 0.

![Wireshark frame detail for the first fragment, showing Total Length of 1500 bytes, the More Fragments flag set, and Fragment Offset of 0](images/fig-16.png)

## Question 12

**Answer:** Second fragment: Fragment Offset > 0, indicating it is not the first fragment. It is typically the final fragment for a 2000-byte packet.

![Wireshark frame detail for the second fragment, showing a non-zero Fragment Offset](images/fig-17.png)

## Question 13

**Answer:** Fields that change between fragments: Total Length, Fragment Offset, Flags, and Header Checksum. Identification remains the same.

![Wireshark frame detail comparing header fields between fragments, showing differing Total Length, Fragment Offset, Flags, and Header Checksum while Identification stays constant](images/fig-18.png)

## Question 14

**Answer:** The 3500-byte ICMP Echo Request was fragmented into 3 fragments.

![Wireshark packet list showing a 3500-byte ICMP Echo Request reassembled from three IP fragments](images/fig-19.png)

## Question 15

**Answer:** Fields that change among the fragments: Fragment Offset, Total Length, Flags (More Fragments), and Header Checksum. Identification remains the same.

![Wireshark frame detail comparing header fields across the three fragments of the 3500-byte ICMP Echo Request](images/fig-20.png)
