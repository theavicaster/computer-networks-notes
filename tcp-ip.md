# TCP/IP

It is simpler than the OSI model. It consists of 4 layers.

TCP or Transmission Control Protocol specifies how the message is broken into packets and then forwarded. It is stateful and it maintains a connection b/w client and server till all the packets are sent. It also has mechanisms for flow control as well as data integrity checks and requests for retransmissions in case of errors. It guarantees the ordering of packets as well.

UDP or User Datagram Protocol is an alternative to TCP. It does not have ordering guarantees, or flow control, or redundancy check, hence has low latency. It however does have error check.

IP or Internet Protocol specifies to which location the packets are sent. Every machine has a unique IP address. IP delivers the packets along with address information.

* Application Layer - \(Application, Presentation and Session Layer of OSI\)
* Transport Layer - TCP sits here
* Internet Layer - IP sits here
* Datalink Layer - Bottom Layers of OSI

