## Section 9 - Data Link Layer

### S9V58 Local Area Network Layer 2 - Ethernet

![alt text](image-85.png)

- ethernet ubiquitous on LAN


![alt text](image-86.png)

![alt text](image-87.png)

- Preamble: help sender and reciever synchronize
- Layer 2 destination/source - MAC addresses where we're using ethernet
- Ethertype specify what's encapsulated iinside ethernet header (typically IPv4)
FCS - Frame Check Sequence - cyclical redundancy check for integrity of Frame, no corruption during transit
- Layer 2 Ethernet Address - MAC address (48-bit hexadecimal)
    - 2 halves: first 24 bits is `OUI` or Organizationally Unique Identifier (manufacturer of ethernet port)
    - 2nd half is 24 bits, assigned by manufacturer (burned in) 
        - Burned in address on every NIC (Network Interface Card)port is unique.

- NO logical addressing with MAC addresses (just a big flat space, no order)

![alt text](image-88.png)

![alt text](image-89.png)

to get MAC address on windows: ipconfig /all

![alt text](image-90.png)

linux: ifconfig

![alt text](image-91.png)

- IOS: show interface

![alt text](image-92.png)

## Section 10 - OSI Layer 1 - Physical Layer 

### S10V60 Ethernet Connection Media

![alt text](image-93.png)

- Defines cables to be used, interface cards and ethernet ports, or WAN port types 

![alt text](image-94.png)

![alt text](image-95.png)

![alt text](image-96.png)

![alt text](image-97.png)

![alt text](image-98.png)

![alt text](image-99.png)

![alt text](image-100.png)

## Section 11 - Cisco Device Functions

### Hubs & Switches S11V62

![alt text](image-101.png)

- likely to have more than 1 switch in a larger LAN (campus)

![alt text](image-102.png)

![alt text](image-103.png)

![alt text](image-104.png)

![alt text](image-105.png)

![alt text](image-106.png)

![alt text](image-107.png)

### Switch Operation S11V63

![alt text](image-108.png)
![alt text](image-109.png)

- Switch doesn't know 2.2.2 so it sends it out all ports
- 3.3.3 reads that the destination address is 2.2.2 and silently discards it

-2.2.2 is sending back
![alt text](image-110.png)

- knows 1.1.1 so it just sends it there 

![alt text](image-111.png)

![alt text](image-112.png)

![alt text](image-114.png)

![alt text](image-115.png)

![alt text](image-116.png)

Next

![alt text](image-117.png)

![alt text](image-118.png)
![alt text](image-119.png)
![alt text](image-120.png)
![alt text](image-121.png)
![alt text](image-122.png)
![alt text](image-123.png)

### Routers S11V63

![alt text](image-124.png)

- when they are routing they are doing it at layer 3

![alt text](image-125.png)

- routers support many more different types of ports than switches and usually have less available ports

![alt text](image-126.png)

![alt text](image-127.png)

![alt text](image-128.png)

![alt text](image-129.png)

### Other Cisco Devices S11V65

![alt text](image-130.png)

![alt text](image-131.png)

![alt text](image-132.png)

![alt text](image-133.png)

### Section 11 Lab

IOS Commands:

- verify which interface is configured to 4 network
    - `R1: show ip interface brief`
- verify connectivity between routers by pinging
    - `R1: ping (address found with show ip interface brief on other routers)`
- View dynamically learned MAC addresses on a switch and verify they are reachable through expected ports
    - `SW1# show mac address-table dynamic`
- clear table
    - `SW1# clear mac address-table dynamic` 
    - **Mac address table will continue to update as devices talk to each other and occasionally flush old entries
- View routing table
    - `R1# show ip route`
- Configure IP address x on interface x
    - Global Config mode
    - `R1(config-if)# ip address 10.10.20.1 255.255.255.0`
- Verify status of interfaces that are up
    - **router interface status is 'administratively down' by default. For a router interface to be used it must be brought online. 
    - `R1(config-if)# end`
    - ` R1# show ip interface brief`
- Bring an interface online
    - `To negate a command enter the 'no' form of it.`
    - `Typically bring an ip interface online immediately after configuring an IP address. Leave them shutdown until needed`
    - `R1(configure-if)# no shutdown`

- Configure static route to 10.10.30.0/24 with next hop address of 10.10.10.2
    - `R1(config)# ip route 10.10.30.0 255.255.255.0 10.10.10.2`

## Section 12 - Life of a Packet

### DNS Domain Name System - S12V68

-  The packet will get encapsulated with the Layer 4 header, which includes information - is it TCP or UDP, and the port number. 
    - For example, port 80 for HTTP web traffic.

- Then we encapsulate that with the Layer 3 header, which is the IP header, and in that layer, the sender has to put on the source and the destination IP address.
- Now with some applications, it will actually put the IP address directly in there, but quite often, it will use an `FQDN`, a Fully Qualified Domain Name, such as www.cisco.com, and that FQDN has to be resolved to an IP address that we can put into the packet.

![alt text](image-134.png)

