# Wireshark DNS Lab Answers

This lab uses Wireshark to capture and analyze live DNS query and response traffic, examining transport protocol, port usage, and DNS message structure across several real-world domains.

**Question 4**
**Answer:** The DNS query and response messages were transmitted using the protocol observed in my capture. In my browser capture, DNS traffic used TCP.

![DNS query and response packets for www.ietf.org shown in Wireshark, with Ethernet/IP frame detail](images/fig-01.png)

**Question 5**

![DNS packet list filtered on dns, showing queries and responses for www.ietf.org](images/fig-02.png)

**Answer:** DNS Query Destination Port: 53. DNS Response Source Port: 53.

![TCP segment detail showing source port 38630 and destination port 53 for the DNS query](images/fig-03.png)
![TCP segment detail showing source port 53 and destination port 38630 for the DNS response](images/fig-04.png)

**Question 6**
**Answer:** The DNS query was sent to the configured DNS server shown in ipconfig /all.

![ipconfig /all output showing DHCPv6 Client DUID and configured DNS server addresses](images/fig-05.png)

**Question 7**
**Answer:** The DNS query is a Type A or AAAA query (depending on the packet selected) and contains 0 Answer RRs.

![DNS query packet detail showing an AAAA query for www.ietf.org with 0 Answer RRs](images/fig-06.png)

**Question 8**
**Answer:** The DNS response contained 2 Answer Resource Records (AAAA records) providing IPv6 addresses for www.ietf.org.

![DNS response packet detail showing Answer RRs: 2](images/fig-07.png)
![DNS response Answers section listing two AAAA records for www.ietf.org](images/fig-08.png)

**Question 9**
**Answer:** No TCP SYN packet to the resolved web server IP addresses was observed. The browser appears to have used HTTP/3 (QUIC) or an existing connection.

![Wireshark filtered on the resolved IP addresses showing no matching TCP SYN packets](images/fig-09.png)

**Question 10**
**Answer:** No. The browser reused previously resolved addresses and did not issue a new DNS query before retrieving each image.

![TCP and DNS packet detail showing no new DNS query preceding subsequent image retrieval](images/fig-10.png)

**Question 11**
**Answer:** DNS Query Destination Port: 53. DNS Response Source Port: 53.

![Ethernet/IPv6/UDP frame detail for a DNS query with destination port 53](images/fig-11.png)
![Ethernet/IPv6/UDP frame detail for a DNS response with source port 53](images/fig-12.png)

**Question 12**
**Answer:** The DNS query was sent to the configured local DNS server.

![IPv6 packet detail showing source and destination addresses for the DNS query/response exchange](images/fig-13.png)

**Question 13**
**Answer:** The DNS query is a Type AAAA query for www.mit.edu and contains 0 Answer RRs.

![DNS query packet detail showing an AAAA query for www.mit.edu with 0 Answer RRs](images/fig-14.png)

**Question 14**
**Answer:** The DNS response contains 4 Answer Resource Records: two CNAME records and two AAAA records resolving www.mit.edu through Akamai.

![DNS response detail showing 4 Answer RRs: CNAME and AAAA records resolving www.mit.edu via Akamai](images/fig-15.png)

**Question 15**

![DNS response detail showing 4 Answer RRs: CNAME and AAAA records resolving www.mit.edu via Akamai](images/fig-15.png)
![802.11 wireless management frame showing an Association Request with SSID and supported rates tags](images/fig-16.png)

**Question 16**
**Answer:** The DNS query was sent to the configured local DNS server.

![DNS query packet list filtered on dns, showing an NS query for mit.edu](images/fig-17.png)

**Question 17**
**Answer:** The DNS query is a Type NS (Name Server) query for mit.edu and contains 0 Answer RRs.

![DNS query packet list filtered on dns, showing an NS query for mit.edu](images/fig-17.png)

**Question 18**
**Answer:** The response returned 8 authoritative NS records for mit.edu and included their IPv4 addresses in the Additional Records section.

![DNS response detail listing 8 authoritative NS records for mit.edu and their IPv4 addresses in Additional Records](images/fig-18.png)

**Question 19**

![DNS response detail listing 8 authoritative NS records for mit.edu and their IPv4 addresses in Additional Records](images/fig-18.png)

**Question 20**
**Answer:** The DNS query was sent to 18.0.72.3, which corresponds to bitsy.mit.edu rather than the default local DNS server.

![DNS query packet detail showing destination address 18.0.72.3 for a www.aiit.or.kr query](images/fig-19.png)

**Question 21**
**Answer:** The DNS query is a Type A (Host Address) query for www.aiit.or.kr and contains 0 Answer RRs.

![DNS query packet detail showing destination address 18.0.72.3 for a www.aiit.or.kr query](images/fig-19.png)

**Question 22**
**Answer:** No DNS response containing Answer Resource Records was captured for the www.aiit.or.kr query. Therefore, 0 answers were provided in this capture.

![DNS packet list showing queries to 18.0.72.3 for www.aiit.or.kr with no corresponding response](images/fig-20.png)

**Question 23**

![DNS packet list showing queries to 18.0.72.3 for www.aiit.or.kr with no corresponding response](images/fig-20.png)
