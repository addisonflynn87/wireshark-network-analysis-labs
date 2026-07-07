# Wireshark 802.11 Lab - Submission Answers

This lab uses Wireshark to capture and analyze IEEE 802.11 (WiFi) traffic, examining beacon frames, authentication, association, and probe request/response exchanges between a wireless client and an access point.

## Question 1

The two SSIDs issuing most beacon frames are '[REDACTED-SSID]' and 'linksys12'.

![Wireshark packet detail pane showing an 802.11 beacon frame with SSID and BSSID fields expanded](images/fig-01.png)

## Question 2

The beacon interval for the [REDACTED-SSID] access point is 0.102400 seconds (102.4 ms).

![Wireshark packet list showing repeated beacon frames with beacon interval column](images/fig-02.png)

![Wireshark packet detail pane showing the Fixed Parameters section with Beacon Interval field](images/fig-03.png)

## Question 3

The source MAC address on the beacon frame from [REDACTED-SSID] is 00:16:b6:xx:xx:xx.

![Wireshark packet detail pane showing beacon frame source address field](images/fig-03.png)

## Question 4

The destination MAC address on the beacon frame from [REDACTED-SSID] is ff:ff:ff:ff:ff:ff (broadcast).

![Wireshark packet detail pane showing beacon frame destination address field](images/fig-03.png)

## Question 5

The BSS ID on the beacon frame from [REDACTED-SSID] is 00:16:b6:xx:xx:xx.

![Wireshark packet detail pane showing beacon frame BSS Id field](images/fig-03.png)

## Question 6

Supported rates: 1, 2, 5.5, and 11 Mbps. Extended supported rates: 6, 9, 12, 18, 24, 36, 48, and 54 Mbps.

![Wireshark packet detail pane showing expanded Supported Rates and Extended Supported Rates tags](images/fig-03.png)

![Wireshark packet detail pane showing Supported Rates tag with individual rate values listed](images/fig-04.png)

## Question 7

TCP SYN frame: Host MAC 00:13:02:xx:xx:xx, AP MAC 00:16:b6:xx:xx:xx, Router MAC 00:16:b6:xx:xx:xx. Source IP 192.168.1.109. Destination IP 128.119.245.12.

![Wireshark packet detail pane showing 802.11 QoS Data frame addresses and encapsulated TCP SYN segment](images/fig-05.png)

## Question 8

TCP SYN/ACK frame: Source IP 128.119.245.12, Destination IP 192.168.1.109. The sender MAC does not correspond to the original TCP sender; it corresponds to the AP forwarding traffic on the WLAN.

![Wireshark packet detail pane showing IP header of the TCP SYN/ACK segment](images/fig-06.png)

![Wireshark packet detail pane showing TCP SYN/ACK segment IP addresses](images/fig-07.png)

## Question 9

The host sends a DHCP Release and then an 802.11 Deauthentication frame to disconnect from the AP. A Disassociation frame might also be expected.

![Wireshark packet list showing DHCP Release followed by an 802.11 Deauthentication frame](images/fig-08.png)

## Question 10

Sixteen Authentication messages were observed from the host to linksys_SES_24086.

![Wireshark packet list showing repeated 802.11 Authentication frames between host and access point](images/fig-09.png)

## Question 11

The host requests Open System Authentication.

![Wireshark packet detail pane showing Authentication Algorithm field set to Open System](images/fig-10.png)

## Question 12

No Authentication reply was observed from linksys_SES_24086.

![Wireshark packet list showing outgoing Authentication frames with no corresponding reply](images/fig-11.png)

## Question 13

Authentication exchange with [REDACTED-SSID] occurred around 63.169 seconds. Response: 63.169071. Request: 63.169707.

![Wireshark packet list showing Authentication request and response frame timestamps](images/fig-12.png)

## Question 14

Association Request: 63.169910 seconds. Association Response: 63.192101 seconds.

![Wireshark packet list showing Association Request and Association Response frame timestamps](images/fig-13.png)

## Question 15

The host and AP both support rates from 1 Mbps through 54 Mbps.

![Wireshark packet detail pane showing Association Request SSID and Supported Rates tags](images/fig-14.png)

![Wireshark packet detail pane showing Association Response Supported Rates and Extended Supported Rates](images/fig-15.png)

## Question 16

Probe Requests are sent by clients searching for APs. Probe Responses are sent by APs advertising their capabilities and availability.

![Wireshark packet list showing 802.11 Probe Request and Probe Response frames](images/fig-16.png)
