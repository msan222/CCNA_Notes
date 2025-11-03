## Section 9 - Data Link Layer

### S9V58 Local Area Network Layer 2 - Ethernet

![alt text](images/image-85.png)

- ethernet ubiquitous on LAN


![alt text](images/image-86.png)

![alt text](images/image-87.png)

- Preamble: help sender and reciever synchronize
- Layer 2 destination/source - MAC addresses where we're using ethernet
- Ethertype specify what's encapsulated iinside ethernet header (typically IPv4)
FCS - Frame Check Sequence - cyclical redundancy check for integrity of Frame, no corruption during transit
- Layer 2 Ethernet Address - MAC address (48-bit hexadecimal)
    - 2 halves: first 24 bits is `OUI` or Organizationally Unique Identifier (manufacturer of ethernet port)
    - 2nd half is 24 bits, assigned by manufacturer (burned in) 
        - Burned in address on every NIC (Network Interface Card)port is unique.

- NO logical addressing with MAC addresses (just a big flat space, no order)

![alt text](images/image-88.png)

![alt text](images/image-89.png)

to get MAC address on windows: ipconfig /all

![alt text](images/image-90.png)

linux: ifconfig

![alt text](images/image-91.png)

- IOS: show interface

![alt text](images/image-92.png)

## Section 10 - OSI Layer 1 - Physical Layer 

### S10V60 Ethernet Connection Media

![alt text](images/image-93.png)

- Defines cables to be used, interface cards and ethernet ports, or WAN port types 

![alt text](images/image-94.png)

![alt text](images/image-95.png)

![alt text](images/image-96.png)

![alt text](images/image-97.png)

![alt text](images/image-98.png)

![alt text](images/image-99.png)

![alt text](images/image-100.png)

## Section 11 - Cisco Device Functions

### Hubs & Switches S11V62

![alt text](images/image-101.png)

- likely to have more than 1 switch in a larger LAN (campus)

![alt text](images/image-102.png)

![alt text](images/image-103.png)

![alt text](images/image-104.png)

![alt text](images/image-105.png)

![alt text](images/image-106.png)

![alt text](images/image-107.png)

### Switch Operation S11V63

![alt text](images/image-108.png)
![alt text](images/image-109.png)

- Switch doesn't know 2.2.2 so it sends it out all ports
- 3.3.3 reads that the destination address is 2.2.2 and silently discards it

-2.2.2 is sending back
![alt text](images/image-110.png)

- knows 1.1.1 so it just sends it there 

![alt text](images/image-111.png)

![alt text](images/image-112.png)

![alt text](images/image-114.png)

![alt text](images/image-115.png)

![alt text](images/image-116.png)

Next

![alt text](images/image-117.png)

![alt text](images/image-118.png)
![alt text](images/image-119.png)
![alt text](images/image-120.png)
![alt text](images/image-121.png)
![alt text](images/image-122.png)
![alt text](images/image-123.png)

### Routers S11V63

![alt text](images/image-124.png)

- when they are routing they are doing it at layer 3

![alt text](images/image-125.png)

- routers support many more different types of ports than switches and usually have less available ports

![alt text](images/image-126.png)

![alt text](images/image-127.png)

![alt text](images/image-128.png)

![alt text](images/image-129.png)

### Other Cisco Devices S11V65

![alt text](images/image-130.png)

![alt text](images/image-131.png)

![alt text](images/image-132.png)

![alt text](images/image-133.png)

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
    - Now with some applications, it will actually put the IP address directly in there
    - More often it will use an `FQDN`, a `Fully Qualified Domain Name`, such as www.cisco.com, and that `FQDN has to be resolved to an IP address` that we can put into the packet.

![alt text](images/image-134.png)

- Enterprises will typically have internal DNS server to resolve IP addresses of internal hosts
    - Hosts send DNS queries to server
    - If DNS server can't resolve a query, will forward to public DNS servers on internet
    - Normally sent using UDP (user datagram protocol) port 53 (and can fail over to TCP)

Windows System:

![alt text](images/image-135.png)
![alt text](images/image-136.png)

- DNS domain that he's part of above part of is FlackboxA.lab

Windows:

![alt text](images/image-137.png)

![alt text](images/image-138.png)

^All these hosts are in FlackboxA.lab domain 

Configure if FQDN request resolves to public IP (Windows): 

![alt text](images/image-139.png)
![alt text](images/image-140.png)
![alt text](images/image-141.png)

^ Then hit edit and put in IP address of a public DNS server

Linux:

![alt text](images/image-142.png)
![alt text](images/image-143.png)

^ping works fine bc were able to resolve it
    - ping with FQDN or IP

### DNS on Cisco Routers - S12V69

#### Router DNS commands

- You'd configure a router to be a DNS Client so that the router itself could resolve FQDNs to hostnames
    - Ex: wan to ping Linux from router, would need to set it up as a DNS client
    - ** Do not need to set it up as a DNS client to have DNS traffic pass through it

![alt text](images/image-144.png)

- `ip domain-lookup` allows it to lookup/use a DNS server
- `ip name-server` allows to loop up address of DNS server (configure where DNS server is)
- `ip domain-name XXX` - primary domain name
- `ip domain-list XXX` - additional suffixes

If you wanted it to be your DNS server you'd enter the same DNS client commands and then enter address records for everything you'd want it to be able to resolve (ip host XXX XXX)

- won't usually make a Cisco router to be a DNS server

![alt text](images/image-145.png)

![alt text](images/image-146.png)

To make the Cisco Router a DNS server:

![alt text](images/image-147.png)

Enter Addresses for host we want to resolve:

![alt text](images/image-148.png)

Enter FQDNs: 

![alt text](images/image-149.png)

Now Config R1 to be DNS Client:

![alt text](images/image-150.png)

Test with ping: 

![alt text](images/image-151.png)
![alt text](images/image-152.png)

### ARP Address Resolution Protocol S12V69

#### IP to MAC Address Resolution

- sender can either send directly to an IP Address or can send to FQDN (i.e. www.cisco.com) (if FQDN needs to be resolved to IP via DNS)

- Sender needs to know receiver's IP address and MAC address to form packet 4 sending
- DNS Domain Name System maintains mapping of FQDNs to IP addresses (Happens @ layer 3)
- `ARP (Address Resolution Protocol)` is used to map the IP address to MAC address (happens at layer 2)
**Since MAC addresses aren't logical user can't enter it themselves and it can't really be configured into the application - prob ARP solves

- ARP Request is a Layer 2 (Data Link) Broadcast

![alt text](images/image-153.png)

- Need the receiver MAC address to finish composing the packet (layer 2). Sends out an ARP request to get that info
- The ARP request says, "Hey, I'm looking for 172.23.4.2, what's your MAC address?" 
    - That will come from the sender's MAC address of 1111.2222.3333, and it goes to a destination MAC address of FFFF.FFFF.FFFF. 
    - That is the Layer 2 broadcast address. 

- Obviously,the sender has to send it out `everywhere` because it doesn't know what the intended destination's MAC address is yet. 
    - That will come into the switch. 
    - The switch will see that it is broadcast traffic, so it will flood it at all ports. 
- It `will hit everything` plugged into that switch, including, in our example, the receiver on the right, which will process that ARP request. 
- It will see that it's looking for 172.23.4.2, and that is its own IP address, so it will respond to the ARP request. 
- It `will send an ARP reply back, saying, "I'm 172.23.4.2, and here's my MAC address."` 
    - This will come from come from source MAC address 2222.3333.4444 and the destination MAC address is the original sender's unicast MAC address of 1111.2222.33333.
    - Receiver knows where to send it back because 

![alt text](images/image-154.png)

![alt text](images/image-155.png)

![alt text](images/image-156.png)

![alt text](images/image-157.png)

![alt text](images/image-158.png)

### ARP for Routed Traffic S12V71

- Can't do it by the way you would on same subnet because there the ARP request is a layer 2 broadcast and wouldn't get forwarded by the router so it wouldn't hit the receiver. 

- Instead sends and ARP request for its default gateway

![alt text](images/image-159.png)

![alt text](images/image-160.png)

- Router will then hold packet as it makes the ARP request for receiver
    - Source MAC is the router's IP 
![alt text](images/image-161.png)

![alt text](images/image-162.png)

![alt text](images/image-163.png)

- The IPv4 information in the packet never changes. The source IP address is always the original sender, which is 172.23.4.1

- the MAC address source and destination will change physical hop by physical hop

![alt text](images/image-164.png)

![alt text](images/image-165.png)

![alt text](images/image-166.png)

### Life of a Packet Example Pt 1 - DNS S12V72

- review of Section 12 so far

![alt text](images/image-167.png)

- Sending HTTP traffic from Host A to www.flackbox.com
    - will use FQDN to send that traffic, will need DNS

#### Resolving the FQDN to IP by DNS

![alt text](images/image-168.png)

![alt text](images/image-169.png)

![alt text](images/image-170.png)

![alt text](images/image-171.png)

![alt text](images/image-172.png)

![alt text](images/image-173.png)

![alt text](images/image-174.png)

![alt text](images/image-175.png)

![alt text](images/image-177.png)

![alt text](images/image-178.png)

![alt text](images/image-179.png)

![alt text](images/image-180.png)

![alt text](images/image-181.png)

![alt text](images/image-182.png)

![alt text](images/image-183.png)

![alt text](images/image-184.png)

![alt text](images/image-185.png)

![alt text](images/image-186.png)

![alt text](images/image-187.png)

![alt text](images/image-188.png)

![alt text](images/image-189.png)

![alt text](images/image-190.png)

![alt text](images/image-191.png)

![alt text](images/image-192.png)

![alt text](images/image-193.png)

![alt text](images/image-194.png)

![alt text](images/image-195.png)

![alt text](images/image-196.png)

![alt text](images/image-197.png)

![alt text](images/image-198.png)

![alt text](images/image-199.png)

![alt text](images/image-200.png)

![alt text](images/image-201.png)

#### Life of a Packet Example Pt 2 - S12V73

#### HTTP

![alt text](images/image-202.png)

![alt text](images/image-203.png)

![alt text](images/image-204.png)

![alt text](images/image-205.png)

 ![alt text](images/image-206.png)

 ![alt text](images/image-207.png)

 ![alt text](images/image-208.png)

 ![alt text](images/image-209.png)

 ![alt text](images/image-210.png)

 ![alt text](images/image-211.png)

 ![alt text](images/image-212.png)

 ![alt text](images/image-213.png)

 ![alt text](images/image-214.png)

 ![alt text](images/image-215.png)

 ![alt text](images/image-216.png)

 ![alt text](images/image-217.png)

 ![alt text](images/image-218.png)

 ![alt text](images/image-219.png)

 ![alt text](images/image-220.png)

 ![alt text](images/image-221.png)

 ![alt text](images/image-222.png)

 ![alt text](images/image-223.png)

 ![alt text](images/image-224.png)

 ![alt text](images/image-225.png)

 ![alt text](images/image-226.png)

 ![alt text](images/image-227.png)

 ![alt text](images/image-228.png)

 ![alt text](images/image-229.png)

 ![alt text](images/image-230.png)
 