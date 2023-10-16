# What is a Network?
	Network is a group of interconnected devices.
### OSI Model
	It's a model that determines how Systems Communite, it contains 7 leyers:
- Physical
- Presentation
- Session
- Transport
- Network
- Data Link
- Application
#### Physical Layer
	It's how we connect the devices, either wireless or ethernet.
	Also Network Topology(the way devices are connected)
e.g
- Star Topology
- Ring Topology
- Bus Topology
#### Data Link
	It determines how device communicate with each other inside the same
	network using MAC Adreess, and in which Switches and Access Points
	operates.

	Switch uses CAM table to decide which device the data is being sent to
##### ARP Protocol
	Finding the MAC address of an IP.
- A device broadcasts an `ARP` request to all devices in the networking looking for an `IP`.
- The device with that IP responds with its `MAC address`
	- `ARP` accepts responses without requests, this is used in `ARP Spoofing` attacks.

#### Network Layer
	Connects different networks together using Routers.
##### IPV4
	Is the version 4 of IPs and it consists of 4 numbers all which are 8 bits(0-255).
[IPV4 classes](https://en.wikipedia.org/wiki/Classful_network#Introduction_of_address_classes)
[IPV4 special-use addresses](https://en.wikipedia.org/wiki/Internet_Protocol_version_4#Special-use_addresses)
##### DHCP(Dynamic Host Configuration Protocol)
	Automatically assigns necessary IPs to network devices.
##### Routing
	The process of transforming packets through different networks 
	to its destination.
- TTL(Time to Live): Determines how many times the packet travels until it returns a failed request, this is used to prevent infinite loops
- Routing Table: Determines the next network(known as Gateway) the packet will travel to.
##### NAT
	Creates one or more IP from main IP address
##### ICMP Protocol
	Test connectivity(ping test)




#### Transport Layer
	Ensures realiable data transfer between hosts, determine whether the
	transfer was successful or not.
	Retransmit faild ones and reorder the packets to form the original message.

	Provide ports for different services and consists of two protocols:
- TCP
	Used for accurate data transfer; when every packet is needed to be successfully transmitted.
-  UDP
	Used for fast transmission cases where if some packets failed it won't affect the message.



#### Session Layer
	Creates and terminates unique connections between hosts.
#### Presentation Layer
	Encoding and decoding, and displaying the messages in its right format.
#### Application Layer
	End-user interface e.g web browser, mail client.
##### DNS(Domain Name System)
	Used to convert Hostname to IP Address.
	Operates on UDP PORT 53.
mail.google.com
- Top Level Domain i.e `.com`
- Second Level Domain i.e `google`
- Sub-domain i.e `mail`
**Record types**
- A: IP address
- MX: Mail Server
- NS: DNS Server