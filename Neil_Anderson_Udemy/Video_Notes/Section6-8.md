## Section 6 - OSI Layer 3 - Network Layer

### The IP Header S6V30

#### The Network layer

- responsible for routing packets to destination & Quality of service (voice/vid needs better quality than email )
- IP is the best known layer 3 protocol
- IPv4 - connectionless protocol w/ no acknowledgements @ layer 3
- Other layer 3 protocols: ICMP (Internet Control Message Protocol) and IPSec

#### IP Addressing

- IP Addressing is logical scheme (layer 3)
- network designer uses IP addressing to partition network into smaller 'subnets'
    - subnets help w/ performance, security, trouble shooting
- Layer 2 MAC addresses are one big flat scheme, no separation here - it's done @ layer 3

####  IP Header

![alt text](image-33.png)

- Type of service - router can take action later
- w/ dif media types there is a max size of the packet
    - i.e. ethernet is 1500 byte MTU, if it's bigger than that it has to get split up into `'fragments'`
    
- `8-bit TTL` - decreases by 1 when it goes through a router, when it gets to 0 is dropped.
    - used to prevent routing loops
- `8-bit protocol` - specifies layer 4 info (TCP/UDP)
- `16-bit checksum` - check packet wasn't corrupted in transit
- `32-bit source IP, 32 bit destination IP`
- `Header options` - additional info, not commonly used
- `data` - rest of packet

### Unicast, Broadcast, Multicast Traffic S6V30

- 3 main types of traffic: 
    - `Unicast: 1 destination host`
        - For if to multiple hosts: 
            - sends separate copies of traffic to each host (takes a lot more bandwith)
    - `Broadcast: all hosts on subnet`
        - only 1 copy of the traffic
        - once it hits the router it doesn't forward broadcast traffic. (not good for performance/security) 
        ![alt text](image-34.png)
    - `Multicast: multiple interested hosts`
        - receivers have to request it to get it
        - one copy to multiple destinations
            - saves bandwith 

### Converting Decimal to Binary S6V31

- IP addresses written in decimal format
- Computer reads them in binary (electrical on/off impulse)
    - 0 or 1
    - every time you add a column on left value is multiplied by 2 instead of 10 like in decimal

![alt text](image-35.png)

![alt text](image-36.png)

### IPv4 Addresses S6V33

- IPv4 is 32 bits long
- 4 octets in dotted decimal format (192.168.10.15)
- Each octet is 8 bits long (4*8=32)

- `(windows) C:/>ipconfig to see your IP address`
- traffic going to host on same subnet can go directly, if on different subnet it must go thru a router
    - Default Gateway is IP you'd use to get to the router

- `(see ur IP on linux) user@ubuntu:~$ifconfig`
    - doesn't show gateway
- `See your gateway  linux - user@ubuntu:~$ip route`

- get IP on Cisco IOS - 
    `- hostname#show ip interface brief (can see all)`
    - `subnet mask - hostname#show interface or show ip interface written in /24`
    - `no default gate b/c it is a router`

#### Static vs Automatic Addressing

- IP is normally set manually on servers, printers, network devices like routers/switches. 
    - This is good if you never want the IP to change
- Set automatically on PC/laptops using DHCP (Dynamic Host Configuration Protocol)
    - PCs want it automatically b/c it's less tedious
    - Can centralize through DHCP server

### Calculating an IPv4 Address in Binary ***Important

- each octet (8 bits) in an IP address has a value from 0 to 255 

![alt text](image-37.png) 

### Subnet Mast S6V35

- host can send directly to another host on same subnet using switches
- if recipient is on dif. subnet has to go through a router
- host tells if destination is on same subnet or not using subnet mask (32 bits long, decimal/slash notation)

- host's IP is split into network and host portions
- subnet mask tells where boundary is 

![alt text](image-38.png)

![alt text](image-39.png)

![alt text](image-40.png)
![alt text](image-41.png)

- Subnet mask is *always* block of 1s then block of 0s (no mixing them up)
- host portion is available to be given to dif. hosts on same subnet (PCs, Servers, Printers, Routers, etc)
    - host portion always has to be unique
    - Exception: All 0's in host portion or all 1's in host portion (Never 192.168.10.0 or 192.168.10.255)

#### Network Address (Network ID)

- All 0s in host portion of IP designates network address and can't be allocated by host
- Alls 1's (xxxx.xxxx.xxxx.1111) is the directed broadcast - traffic sent here goes to all hosts in subnet

### Slash Notation S6V36

- subnet mask always starts with block of 1's it will be 1 to 32 bits from left to right 
- can write it in slash notation (more convenient)

![alt text](image-42.png)

- 24 bits in a row so you can just write it as /24
- `Ex`: 192.168.10.14 with a subnet mask of 255.255.0.0 can be written as 192.168.10.14/16
- When you configure an IP and subnet on Cisco router/switch you have to write it out fully 

## Section 7 - IP Address Classes

- global coordination of IPv4 is performed by IANA (Internet Assigned Numbers Authority)
    - How it was supposed to go (not big enough):
        - company wants internet, apply for range of IP addresses
        - If they have 600 hosts, ask for a range of IPs big enough + growth
        - Then allocate in their offices
- IPv6 is long term solution (IPv4=32 bit, IPv6=128 bit)

- Private IP addresses w/ network address translation (NAT) are deployed in enterprise networks globally (more common than IPv6 for now)

### Class A IP Addresses S7V38

#### Class A Addresses 

- IPv4 address space was split into separate classes
- `Class A addresses` are for network with large numbers of hosts
    - `high order (first)` bit in class A is always 0 
    - default subnet mask is /8
    - Valid Addresses: 1.0.0.0 to 126.0.0.0/8
        - 126 networks and 16,777,214 hosts
            - 24 host bits, each can be 0 or 1, so total number of combinations is 2^24.

![alt text](image-43.png)

![alt text](image-44.png)

- you can ping 127.0.0.1-127.255.255.254 to test if TCP/IP is working on the local machine 

![alt text](image-45.png)

### IP Addresses Class C and D S7V39

- `Class B`: Medium-large sized networks

![alt text](image-46.png)

- two high-order bits in a class B address are always set to binary 1 0 
- default subnet = /16
- Valid network address are 128.0.0.0 to 191.255.0.0/16
- allows for 16,384 networks and 65,534 hosts per network
- Would also be subnetted irl

-`Class C`: used for small networks

![alt text](image-47.png)

- high order bits are always set to binary 1 1 0
- default subnet mask is /24
- valid addresses range from 192.0.0.0 to 223.255.255.0/24
- allows for 2,0997,152 networks and `254` hosts per network
- could leave as is or subnet

- `Private Addresses in Each Class`
- can assign to hosts but *NOT* routable on the public internet
- intended for hosts in closed private network w/ no internet 
- Class A: 10.0.0.0 to 10.255.255.255
- CLass B: 172.16.0.0 to 172.31.255.255
- Class C: 192.168.0.0 to 192.168.255.255

### IP Address Classes D and E S7V40

- Class D: IP multicast addresses
- four high-order bits are always 1 1 1 0
- not allocated to hosts, no default subnet mask
- Valid addresses: 244.0.0.0 to 239.255.255.255

 ![alt text](image-48.png)

- Class E Addresses - Experimental reserved for future use.
- high order bits are 1 1 1 1
- not allocated to hosts, no subnet mask
- addresses range from 240.0.0.0 to 255.255.255.255
- 255.255.255.255 is broadcast address for 'this network' 

- multicast traffic - can configure router to forward multicast traffic beyond network
- broadcast traffic will not get forwarded by routers by default

#### Summary Chart

![alt text](image-49.png)

`^Need to memorize`

## Section 8 - Subnetting

### CIDR Classless Inter-Domain Routing S8V42

- problem with classful addresses was that people who had just over the number of hosts they'd be bumped up and have a bunch of leftover hosts (waste)
- Classes Inter-Domain Routing (CIDR) was introduced to fix this problem. 
    - It removed the /8, /16, /24 requirements for address classes and allowed them to be split or `subnetted` into smaller networks
    - i.e. 175.10.10.0/20
    - Companies can now be allocated address range that matches needs better

![alt text](image-51.png)

### Subnetting Overview

#### Borrowing Host Bits

- Example:
    - Allocated Class C 200.15.10.0/24, need to split up for 1 business with 4 depts. over 2 offices
    - `To subnet network into smaller subnets need to 'borrow' host bits and add to the network portion of address.`
    - Network address line always moves right when we subnet
    - The further right you go the more subnets you'll have of that size but less hosts

#### Calculating the Number of Networks

- To calc the number of available subnets, formula is 2^subnet-bits
- If Class C uses /28 subnet mask then we've borrowed 4 bits from the default of /24
    - 2^3 = 16 available subnets
- If class B uses /28 mask then we've borrowed 12 bits from default 16. 
    - 2^12 = 4096

![alt text](image-52.png)

#### Calculate # of hosts

- Formula (2^host-bits)-2
    - subtract 2 b/c network and broadcast address
- If class C network uses /28 subnet mask then you have 4 bits for hosts
    - i.e. (2^4)-2 = 14
-If class B network uses /28 subnet then have 4 bits for hosts 
    - (2^4)-2=14 

**Class doesn't matter for hosts

#### Note on 'ip subnet-zero' command

- use to have to subtract 2 from # of available networks too
    - in original internet not allowed to use network bits of all 1's or 0's (just like how you can't do for host bits)
    - unnecessary and a waste of space
- 'ip subnet-zero' command on router overrides the limitation and in enabled by default
- don't -2 for Cisco or CCNA but some online calculators might do that

### Subnetting Class C Networks and VLSM

#### Class C /31 Subnet S8V44-45

![alt text](image-53.png)

- /31 would be written as 255.255.255.254
- need to at least have one bit on the right if you need more than 1 host. Furthest you can go is /31
    - leaves 1 bit for host address, with possible value of 1 or 0
    - borrows 7 bits for network address
    - gives us 128 subnets (2^7) which can accommodate 2 hosts each 

![alt text](image-54.png)

![alt text](image-55.png)

- You can check this by:
    - we're using 200.15.10.0, so the first three octets are never going to change. 
    -The last octet, just start with all 0's, and then it would be 0000001, and then a 0 or a 1, and then 0000010,and then a 0 or a 1, and so on.

![alt text](image-56.png)

![alt text](image-57.png)

![alt text](image-58.png)

![alt text](image-59.png)

- Here it's going up in values of 4 (line is right after the '4'). 
    - The first subnet is going to be a 200.15.10.0, so 200.15.10.0 is the network address.
    - Because the next range starts at 200.15.10.4, the broadcast address must be 200.15.10.3.
    - So if 200.15.10.0 is the network address, and 200.15.10.3 is the broadcast address, the valid host addresses must be 200.15.10.1 and 200.15.10.2.

    - The next subnet starts with 200.15.10.4. 
    - The next subnet after that is at 200.15.10.8, so the broadcast address must be 200.15.10.7.
    - So, network address of 200.15.10.4, broadcast address of 200.15.10.7 -> that leaves the addresses in between of 200.15.10.5 and 200.15.10.6 are available to be assigned to our hosts.

#### /31 vs /30 

- /30 & /31 both accommodate 2 hosts per subnet
    - /31 supports 128 subnets, /30 only 64
- /31 is useful if you need to maximize use of address space
- /30 is more standard and commonly used
- `For CCNA use /30 when a subnet supports 2 hosts is required unless told to use /31`

#### Class C /29 

![alt text](image-60.png)

![alt text](image-61.png)

![alt text](image-62.png)

### Variable Length Subnet Masking Example Pt 1

#### Variable Length Subnet Mask VLSM S8V46

#### Subnetting Considerations

- How many locations? How many hosts in each location?
- IP addressing reqs for each location (dif dept/hosts in dif subnets)
- what size is appropriate?

![alt text](image-63.png)

![alt text](image-64.png)

- work down from largest to smallest
    - IRL leave space in subnets for additional hosts/growth
    - In CCNA do *exactly* the exact number, don't leave space

![alt text](image-65.png)

![alt text](image-66.png)

#### VLSM Examples Pt 2 S8V

![alt text](image-67.png)
![alt text](image-68.png)
![alt text](image-69.png)
![alt text](image-70.png)
![alt text](image-71.png)
![alt text](image-72.png)
![alt text](image-73.png)

#### Subnetting Large Networks S8V48

![alt text](image-74.png)

![alt text](image-75.png)

- Our IP: 135.15.10.138
    - Look at the last octet = 138, and find where it fits:Between 136 and 144

            List the subnet starts in increments of 8:
            0, 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, 128, 136, 144, 152, 160, 168, 176, 184, 192, 200, 208, 216, 224, 232, 240, 248
    
            So the network address = 135.15.10.136

            - When we say the magic number = 8, we’re saying “Each subnet starts every 8 numbers in the octet where subnetting occurs.”

            - So the ‘8’ is the increment (or “block size”) that determines the starting point of each subnet.

#### Subnetting Practice

***See notebook

![alt text](image-76.png)


### Private IP Addresses S8V52

- Internet Engineering Task Force (IETF) documents standards with RFC's (Requests for Comments)
- RFC 1918 specifies private IP address ranges not routable on public internet

Private IP Ranges in Each Class:
- A: 10.0.0.0-10.255.255.255
    - 10.0.0.0/8
- B: 172.16.0.0-172.31.255.255
    - 172.16.0.0/12
    - 172.16.0.0 255.240.0.0
- C: 192.168-192.168.255.255
    - 192.168.0.0/16

![alt text](image-77.png)

![alt text](image-78.png)

IPv6 is 128 bits 
Provides 7.9*(10^28)

![alt text](image-79.png)
![alt text](image-80.png)

![alt text](image-81.png)

![alt text](image-82.png)
![alt text](image-83.png)

![alt text](image-84.png)