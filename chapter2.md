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


***note: neither UDP or TCP provide any encryption in the box, data needs to be encrypted before sending out through the network*** 


