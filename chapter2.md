## application layer
___

Network applications run on end-systems & communicate over the Network
network-core devices do not run user applications, only end-systems can be developed only

### client server architecture
***server*** 
always on host --waiting to receive request from a 'client'
set IP address
clusters of servers considered virtual servers for scaling client input

***clients*** 
first to contact, considered to be the client
intermittent connections (no need to be always on)
dynamic IP address
communicate through the server, never directly to each other

### peer to peer architecture
No always-on server 
scaling, cost-efficient
peers request service from other peers & provide service as well in return
peers intermittently connect and change IP addresses

*BitTorrent* 

## Processes communicating
A process is a program running inside a host, processes can communicate with other processes
this is called ***inter process communication*** 

| client process   | server process    |
|--------------- | --------------- |
| process that initiates conversation   | process that waits to be contacted   |

Processes in different hosts communicate by exchanging messages over the network

## interface connecting the processes & networks

Processes send messages through the network through a software interface known as the ***socket***
this is known as the API

Sockets are the interface between the ***application layer*** and the ***transport layer*** in the host
**application programming interface** is what we call this software interface

#### addresses
for information to be sent, two pieces of information need to specified

| address of the host   | identifier that specifies the receiving process in destination host    |
|--------------- | --------------- |
| ip address   | port number   |

The ***IP address***  is going to be used to uniquely identify the host
the ***port number*** is used to identify the specific process being received

<center>port numbers like 80 are commonly used for to identify web-servers</center>

#### what services are available to the network applications
The application will send a message through the transport layer protocol, the application pushes the message through the socket


The type of transport protocol one uses is based on their needs
- data transfer
- through-pout
- timing
- security

##### reliability of data transfer
Due to the fact that packets *can* get lost (e.g. buffer overload) if a protocol can transport this data securely it is said to have ***reliable data transfer***

If some data *can* be lost (the developer doesn't need the most reliable data) then these are called ***loss tolerant applications***

##### throughput 
> ***throughput*** : *the rate at which bits of data can deliver bits to the receiving process*
a transport layer protocol *could* provide some **certainty** to the rate of this throughput, essentially guaranteed minimum *r bits/ sec*

Important for ***bandwidth sensitive applications***: you would want your voice calling app to at least have enough throughput to carry a voice  along the network

If you are dealing with an application that does not require dedicated bandwidth minimums, then you are handling a ***elastic application*** can make use of as much or as little bandwidth that they have available

##### timing
> ***timing***: timing guarantees receivers obtains transmitted message at a minimum *n* time in *ms*

This is important multiplayer games, where you want low things such as **ping** 

##### security
encryption, levels of security based on how sensitive the data is, things like end-point authenticity to ensure data integrity

## TCP or UDP
___
### TCP

***TCP service***: client & server communicate with each other before any application-level messages flow , this is called **handshaking** a way to prepare before they send each other packets.
Once the handshake is completed, a ***TCP Connection*** now exists, this connection is **full duplex**
> ***full duplex connection***: data flows from both directions simultaneously
Once both the connections are finished sending messages back and forth, the connection will be **torn down** 

***reliable data transfer***: TCP is used for reliable data transfer, sending packets in proper **order** *and* **without errors** (no missing or duplicate bytes)

***congestion control algorithm***: when the network is congested between sender/ receiver the algorithm purposely throttles the sending of messages

### UDP
**lightweight & minimal**, it is a *connectionless* protocol, meaning there is **no handshaking**
due to the lightweight nature, it provides **unreliable data transfer** providing no guarantees that the data will arrive to the given destination

| pros   | cons    |
|--------------- | --------------- |
| lightweight   | messages may be received out of order   |
| no handshaking required   | messages can get lost   |

*no congestion control mechanism* 

***note: neither UDP or TCP provide any encryption in the box, data needs to be encrypted before sending out through the network*** 


#### application layer protocols
>***application-level protocols***: how an apps processes, running on different end-systems pass messages to each other 


The application layer protocol defines 4 things

| APL   | meaning    |
|--------------- | --------------- |
| type   | the types of messages exchanged   |
| syntax   | syntax of message types, what fields are allowed   |
| semantics   | meaning of the information in the fields   |
| rules for how   | rules for determing when and how a process sends messages and responds to them  |

Some web application protocols like **http** are an example of this, if a developer follows the rules in https, they can send messages through the network


**Distinguishing: network applications and application layer protocols**
The application layer protocol is a piece of a network application, w web browser is a network app that uses HTTPS and HTML


#### HTTP
https is broken up into two programs, a client program and server program, they talk to eachother on different end systems. They do so by **exchanging HTTP messages**

**TCP** is used as the underlying transport protocols, the http client will initiate a **TCP Connection** with the server through their socket interface

The server will now send and receive HTTPS through their socket interface, this is how they will exchange HTTP messages

**State Changes** on the client side are unknown, HTTP is a **stateless** protocol by default


##### persistent/ non-persistent connections
developer needs to decide if connections made over http will be either persistent or non-persistent
**non-persistent**: each response/request pair is sent through a new *separate*  **TCP** connection 



***round-trip-time (RTT)*** is the time it takes for a packet to send to the server *and* for a response to be sent *back*, this is calculated using
- packet prop-delay
- packet process-delay
- packet queue-delay

When a user clicks on a hyperlink, browser initiates TCP connection, initiates ***three-way handshake***
- client sends small TCP segment to server
- server acknowledges and responds with its own TCP segment
- client *then* sends a **HTTP request** combined with the **acknowledgement of TCP connection** 
 
Finally, the server will respond with a **TCP** response containing the HTML file
*the total response time*: **two RTTs + transmission time at the server of HTML file**  


*non-persistent connections* may cause strain on the server due to the amount of TCP connections needed, where a machine may be servicing hundreds of clients, especially due to a new connection being needed ***per request*** 


***how do persistent connections solve this issue?***:

**Pipe-lining**:
HTTP/1.1 established the use of persistent connections, the server will leave the TCP connection open after sending a response, all subsequent requests & responses will be sent through this same connection, **requests can be made back to back *without* the need for replies to pending requests **

HTTP defines 2 types of message formats: **requests** & **responses**

###### REQUEST (GET)

A typical http request message will contain the following fields

1. **GET**
2. **Host**
3. **Connection**
4. **User-agent**
5. **Accept-language**




































  
