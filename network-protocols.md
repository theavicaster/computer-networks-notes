# Network Protocols

**HTTP -** 

* It is a client server protocol, the foundation of data exchange over the internet.
* Between the client and server may be proxies - with function as load balancing, caching, authentication, filtering, logging
* HTTP is stateless. However it is not sessionless. A session needs to be built for the connection b/w client and server. But knowledge of previous sessions is not kept \(unless there are cookies\)
* The underlying transport protocol is often TCP, as it needs to be reliable. But HTTP can be done on UDP too. For every HTTP request,  a TCP connection is established.

**HTTPS -**

* Secure version of HTTP. All data is encrypted.
* TLS \(Transport Layer Security\) is the protocol responsible for this.
* A TLS handshake goes on before exchange of messages.
* Server contains a TLS certificate \(verifying the ownership of a public key\)
  *  After client reaches out to server, server responds with certificate and it's public key.
  * Client then verifies the authenticity from the certificate authority. 
  * It then generates a symmetric key, encrypts with server's public key and sends it.
  * Server can then decrypt using it's private key, receives the symmetric key.
  * From then all communications between client and server are done with the symmetric key.

**TCP \(Transmission Control Protocol\)-**

* Connection oriented protocol - ensures ordering of packets, error check, flow control, gives reliability.
* Data is broken into TCP segments - header + data
* Header contains information like source and destination port, ACK and SYN bit, sequence number and checksum
* STEP 1 : Establish a connection
  * Client sends packet with SYN bit on
  * Server sends packet with SYN and ACK bit on
  * Client sends packet with ACK bit on, 3 way handshake is complete
* STEP 2 : Send Data
  * Each packet is sent along with its seq. number by client
  * Client can handle if packet was losr enroute via detecting an ACK from server
* STEP 3 : Close Connection
  * Client sends FIN bit to server
  * Server replies with FIN and ACK
  * Client replies with ACK
* Detecting lost packets:
  * After sending each packet, client starts a timer
  * If within a time limit an ACK is not received, packet was lost, it retransmits
  * If the ACK comes after a while, duplicate was sent, no problem
* Handling out of order packets : 
  * Server always sends back ACK with a corresponding seq. number
  * Because of seq no. server can always rearrange packets, and missing packets are taken care of by client's retransmissions.

**UDP \(User Datagram Protocol\) -** 

* UDP headers only contain source and destination ports and checksum. Hence it has error checks.
* Without all the overhead, it is unreliable, connectionless and suitable for low latency.

**IP \(Internet Protocol\) -** 

* Tasked with delivering packets from source host to desination host based upon ID addresses.
* IP Routing involves sending the packet forward to a router. The router then sees a prefix of the destination IP address and sends forward to another router, until the IP packet reaches the destination.

