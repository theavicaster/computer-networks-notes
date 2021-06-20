# OSI Model

**Open Systems Interconnection** model standardizes the steps of communication b/w computer networks. It provides abstractions in terms of layers, which specify how data is transformed and where it goes when communicating between two machines. It is nothing but a conceptual framework. This separation into layers provides a few benefits including -

* Allowing multiple vendors to each focus on a layer
* We can localize a problem to one layer when debugging
* We can change implementation of one layer independently of other layers, as long as the layer still has correct output.

The modern internet does NOT follow OSI. It follows TCP/IP

7 layers - Application, Presentation, Session, Transport, Network, Data Link, Physical

Mnemonic - **All People Seem To Need Data Processing**

If A wants to communicate with B -&gt; data goes from Application layer to Physical layer for A, then from Physical to Application layer again for B.

**Application \(Layer 7\) -** 

* Interacts with data from user. Involves data manipulation to show meaningful data to user -&gt; eg. parse the data into a csv for a table. It can also involve the user sending out the data. It does NOT involve the client application like a browser.
* Protocols include SMTP \(sending emails\), HTTP \(hitting a REST endpoint\), FTP\(upload/download files\)

**Presentation \(Layer 6\) -**

* Serialization/Deserialization -&gt; Decode XML / Base 64 encoded etc.
* Encryption/Decryption
* Compression of data

**Session \(Layer 5\) -** 

* Provides mechanism for opening and maintaining sessions between local and remote applications. This session can be oneway/bidirectional \(duplex\). 
* Synchronizes data transfer with checkpoints. If a 100 megabyte file is being transferred, the session layer could set a checkpoint every 5 megabytes. In the case of a disconnect or a crash after 52 megabytes have been transferred, the session could be resumed from the last checkpoint.

**Transport Layer \(Layer 4\) -** 

* It guarantees the end-to-end connection between the hosts.
* Takes data - breaks it into smaller segments, and provides flow control, i.e monitors the rate of transfer of these segments. Conversely, also handles reassembly of segments.
* Avoids congestion of traffic as well.
* When it receives segments, it can request retransmission if there's errors in the segments received.
* Protocols include TCP and UDP.

**Network Layer \(Layer 3\) -**

* It is for communication across hosts on the different networks.
* Divides segments into packets - and forwards them or finds best physical path for them - called routing.
* The IP address is at the network level. ARP \(Address Resolution Protocol\) turns IPv4 addresses into Ethernet MAC addresses \(layer 2\)

**Data Link \(Layer 2\) -**

* Transfers data between data on the same network.
* Breaks packets into frames. 
* It also does flow control and error control at intra network level.

**Physical \(Layer 1\)-**

* Frames transferred as 0s and 1s \(binary\)
* Convention of which signal is 0, which is 1 is agreed upon
* Eg. WiFi sends signals between devices















