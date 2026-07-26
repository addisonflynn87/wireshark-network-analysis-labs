# Wireshark HTTP Lab - Submission Answers

This lab uses Wireshark to capture and analyze HTTP traffic, examining request/response headers, conditional GET (caching), persistent connections, retrieving objects referenced by an HTML page, and HTTP authentication.

## Question 1

Browser: HTTP/1.1. Server: HTTP/1.1.

![Wireshark packet detail pane showing the HTTP GET request with request version HTTP/1.1](images/fig-01.png)

## Question 2

The browser indicates it accepts U.S. English and English (Accept-Language: en-US,en;q=0.9).

![Wireshark packet detail pane showing the HTTP GET request with request version HTTP/1.1](images/fig-01.png)

## Question 3

Client IP: 192.168.1.137. Server IP: 128.119.245.12.

![Wireshark packet detail pane showing the HTTP GET request with request version HTTP/1.1](images/fig-01.png)

## Question 4

The server returned status code 200 OK.

![Wireshark packet detail pane showing the HTTP 200 OK response headers](images/fig-02.png)

## Question 5

The HTML file was last modified on Tue, 28 Oct 2025 05:59:01 GMT.

![Wireshark packet detail pane showing the HTTP 200 OK response headers](images/fig-02.png)

## Question 6

The server returned 128 bytes of content (Content-Length: 128).

![Wireshark packet detail pane showing the HTTP 200 OK response headers](images/fig-02.png)

## Question 7

Yes. One example is the ETag header.

![Wireshark packet detail pane showing the HTTP 200 OK response headers](images/fig-02.png)

## Question 8

No. The first HTTP GET request does not contain an If-Modified-Since header.

![Wireshark packet list and hex dump showing the first HTTP GET request for HTTP-wireshark-file2.html](images/fig-03.png)

## Question 9

Yes. The server returned the HTML file. This is confirmed by the 200 OK response and the Line-based text data section.

![Wireshark packet detail pane showing the HTTP 200 OK response and line-based text data for HTTP-wireshark-file2.html](images/fig-04.png)

## Question 10

Yes. The second GET contains an If-Modified-Since header with the timestamp of the cached file (or use the supplied trace if your browser did not generate a conditional GET).

![Wireshark packet list and hex dump showing the first HTTP GET request for HTTP-wireshark-file2.html](images/fig-03.png)

## Question 11

The response is 304 Not Modified. The server does not resend the file because the browser's cached copy is still valid.

![Wireshark packet list and detail pane showing the HTTP request/response exchange for HTTP-wireshark-file2.html](images/fig-05.png)

## Question 12

One HTTP GET request was sent for the Bill of Rights page. The GET request is packet 668.

![Wireshark packet list and detail pane showing the HTTP request/response exchange for HTTP-wireshark-file2.html](images/fig-05.png)

![Wireshark packet detail pane showing packet 668, the GET request for HTTP-wireshark-file3.html](images/fig-06.png)

## Question 13

Packet 680 contains the response status code and phrase.

![Wireshark packet list and detail pane showing packet 680 with the reassembled TCP segments and HTTP 200 OK response for HTTP-wireshark-file3.html](images/fig-07.png)

## Question 14

The response status is 200 OK.

![Wireshark packet list and detail pane showing packet 680 with the reassembled TCP segments and HTTP 200 OK response for HTTP-wireshark-file3.html](images/fig-07.png)

## Question 15

Four TCP segments (#676, #677, #679, and #680) carried the HTTP response.

![Wireshark packet list and detail pane showing packet 680 with the reassembled TCP segments and HTTP 200 OK response for HTTP-wireshark-file3.html](images/fig-07.png)

## Question 16

Three HTTP GET requests were sent: the HTML page, pearson.png, and 8E_cover_small.jpg.

![Wireshark packet list and detail pane showing the three HTTP GET requests for the HTML page, pearson.png, and 8E_cover_small.jpg](images/fig-08.png)

## Question 17

The images were downloaded in parallel because the browser issued the image requests almost immediately after receiving the HTML.

![Wireshark packet list and detail pane showing the three HTTP GET requests for the HTML page, pearson.png, and 8E_cover_small.jpg](images/fig-08.png)

## Question 18

The server responded with HTTP/1.1 401 Unauthorized.

![Wireshark packet list showing the GET request for the protected page followed by the 401 Unauthorized response](images/fig-09.png)

## Question 19

The second HTTP GET includes an Authorization: Basic header containing the Base64-encoded credentials.

![Wireshark packet list showing the GET request for the protected page followed by the 401 Unauthorized response](images/fig-09.png)

![Wireshark packet detail pane showing the second GET request with the decoded Authorization: Basic header](images/fig-10.png)
