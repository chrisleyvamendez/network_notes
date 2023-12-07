## application layer

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










