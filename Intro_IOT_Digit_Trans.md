# Intro to IoT and Digital Transformation

## CISCO Beginner Course

### Intro 1.0 

#### 1.0.1 Objectives

- Explain meaning and impact of digital transformation
- Apply basic programming to support IoT
- Explain how data provides value to business & ppl
- Explain benefits of automation
- Explain need for security
- Discover opportunities 

#### 1.0.4 Examples of Networks

- social media 
- city power grid
- grove of aspen trees w/ root system shared
- internet: a network of networks. Some of those are made up of numerous things (i.e. IoT)

#### 1.0.5 What Will Learn for this Module

1. How digital transformation affects business, industry, lives. 
2. How networks provide platform for such
3. Describe exponential growth of connected IoT devices. 
4. Configure devices to communicate in the IoT
 
### 1.1 Digitization Transforms Business

#### 1.1.1 Evolution of Digital Transformation

- IoT systems contribute to: environmental controls, retails, transit, healthcare, agriculture 
- number of IoT devices in use across all relevant industries is forecasted to grow to more than 8 billion by 2030
- More applications: autonomous vehicles, IT infrastructure, asset management, electric utility smart grid
- Modern Digital Networks allow for all these devices to be connected 

#### 1.1.3 Impact of Digital Trans. on Business

- Smart home
- Smart building: Can shop online, order things, book travel, etc. Sensors generate data. 
- Business: determine buying patterns, forecast new trends, streamline production
- Government: monitor environment, forecast population trends, predict crime rates, plan for social services. 

#### 1.1.4 Thinking Smart Devices

- Smart City: Barcelona uses sensors to control infrastructure systems including traffic flow, parking, water, utilization, hydro. 
- weight sensors for smart parking lot
- sensors on traffic lights can detect traffic congestion, can modify flow of traffic

### Globally Connected Through Networks 1.2

#### 1.2.1 Networking is Foundation

- 30 billion things provide trillions of gigabytes of data
- Methods we use to communicate continue to evolve: what was once cables and plugs wireless and digital has broken through & become available
- Networks can be in all shapes and sizes (i.e. two computers to millions of devices)
- Simple home networks enable internet connectivity, share resources (printers, documents, pics, etc) between a few local computers
- In businesses and large organizations networks can provide customers products/services through an internet connection 
- Networks can also be used on a broader scale to do consolidation, storage, access to info on network servers
- Can also be used for email, IM, collaboration 
- Internet is the largest network in existence: term internet means 'network of networks'. Collection of public & private networks

#### 1.2.2 Network Types

1. `Personal Area Network (PAN)`:  
    - Small network
    - Connected wireless devices within personal reach. (i.e. phone to car with bluetooth) 
    - Other wireless protocols used: Zigbee and Ultra-Wide Band (UWB)

2. `Local Area Network (LAN)`:
    - Small area like home, business, department within a large corp., etc. (Think a LAN center)
    - Can connect 2+ devices including computers, printers, wireless devices.
    - Provide access to `larger wide area networks (WANs)` and the internet

3. `Wide Area Network (WANs)`:
    - A collection of LANs that provide inter-LAN  and internet connectivity for businesses and govs. 
    - Internet
        - multi-layer global network connects 100s of millions of computers, not owned by anyone or anything
        - made of multiple local & global networks serving private/public/business/gov/academic/etc
        - more than 100 linked countries 
        - has text, multi-media data, email, online chat, VoIP, file transfer & sharing, ecommerce, gaming  
    - Wireless Networks 
        - Computer networks that use `electromagnetic waves`instead of wires to carry signals over parts of the network
        - Can be: PANs, LANs, WANs (depend on scope)
- **See notebook for diagram and table

- `The Cloud`
    - not a type of network but a collection of `data centers` or `groups of connected servers`
    - store/analyze data, access to on-line apps, provide backup services

- `The Edge`
    - Boundary between org's network and the internet 
    - Defines place where network admin'ed by one org connects to another admin'ed by dif. org.
    - i.e. where corporate network connects to internet
    - Org may have more than 1 network edge depending on size/location

#### 1.2.3 Questions

- `Edge Computing`: Allows local data to be pre-processed at the edge of a network

#### 1.2.4 Lab - Map the Internet

- Determine network connectivity to destination host then trace a route to a remote server using tracert
- Need internet access & cmd line
- Route tracing software lists networks that data crosses from user's end device to destination device. 
- Commands below determine the route taken by packets across an IP network
    - Execution Commands: 
        - (Windows) 

            tracert \<destination network name or end device address>
        - (UNIX, Linux, CISCO devices) 
        
            traceroute \<destination network name or end device address>

- `Tracert/traceroute` is often used for network troubleshooting. 
    - Shows list of routers that a packet has traveled so you can see the path it took to reach a spot across a network or networks
    - Each router represents point where one network connects to another and the packet was forwarded 
    - `number of routers traveled is called "number of hops"`
    - Output list of routers helps solve data problems when trying to access stuff like website or when downloading data
        - i.e. tracing mirror of a file to see which one is the fastest

`1. Pt 1 - Check Network Connectivity to Target Host`
    
    C:\Users\Madeline S:> ping www.cisco.com
    
    Pinging e2867.dsca.akamaiedge.net [184.28.2.110] with 32 bytes of data:

    Reply from 184.28.2.110: bytes=32 time=51ms TTL=50

    Reply from 184.28.2.110: bytes=32 time=6ms TTL=50

    Reply from 184.28.2.110: bytes=32 time=40ms TTL=50
    
    Reply from 184.28.2.110: bytes=32 time=27ms TTL=50

    Ping statistics for 184.28.2.110:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    
    Approximate round trip times in milli-seconds:
        
        Minimum = 6ms, Maximum = 51ms, Average = 31ms

Now ping one of the Regional Internet Registry (RIR) websites located in different parts of the world to determine if it is reachable:

    Africa:                 www.afrinic.net

    Australia:             www.apnic.net

    Europe:               www.ripe.net

    South America:    www.lacnic.net

    North America:     www.arin.net

    The website you selected will be used in Part 2 for use with the tracert command.

    C:\Users\Madeline S> ping www.ripe.net

    Pinging e337066.dscb.akamaiedge.net [23.59.88.228] with 32 bytes of data:
    Reply from 23.59.88.228: bytes=32 time=85ms TTL=50
    Reply from 23.59.88.228: bytes=32 time=6ms TTL=50
    Reply from 23.59.88.228: bytes=32 time=17ms TTL=50
    Reply from 23.59.88.228: bytes=32 time=7ms TTL=50

    Ping statistics for 23.59.88.228:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    Approximate round trip times in milli-seconds:
        Minimum = 6ms, Maximum = 85ms, Average = 28ms

`1. Pt 2 - Trace a Route to a Remote Server Using Tracert`
    
- The `PC sends 3 ICMP echo request packets` to the remote host.
    - `The Internet Control Message Protocol (ICMP)` is a protocol that devices within a network use to communicate problems with data transmission
- Each router in the path decrements the time to live (TTL) value by 1 before passing the packet on
- When TTL=0 the router sends an ICMP Time Exceeded message back to source with IP and current time. 
- When final destination is reached ICMP echo reply sent to source host

        Example: 
        - Source host sends 3 ICMP echo request packets to 1st hop (192.168.1.1) with TTP=1
        -Router 192.168.1.1 recieves echo request packets, decrements to TTL=0
        - Router then sends ICMP Time Exceeded message to source
        - Process continues until source hosts sends the last 3 ICMP echo request packets with TTL=8 (hop #8), which is the final destination
        - After After ICMP echo request packets arrive at final destination, router responds to source with ICMP echo replies

        - For hops 2 and 3 the IP addresses are private. These routers are the typical setup for Point-of-Presence (POP) ISP.
            - POP devices connect users to ISP network

        - http://whois.domaintools.com/ can be used to determine domains traveled from source to destination


A. Next Part - Tracing to CISCO

        C:\Users\Madeline S>tracert www.cisco.com

        
    Tracing route to e2867.dsca.akamaiedge.net [184.27.178.116]
    over a maximum of 30 hops:

    1    44 ms     4 ms    34 ms  192.168.4.1
    2     8 ms     3 ms     *     10.248.14.1
    3    28 ms    55 ms     6 ms  100.122.0.93
    4    49 ms    47 ms    62 ms  65.182.49.5
    5    49 ms     4 ms     *     65.182.49.2
    6    90 ms     5 ms    41 ms  65.182.49.209
    7     *        8 ms     *     e0-44.switch1.sea2.he.net [64.71.158.141]
    8     *        *        *     Request timed out.
    9    38 ms    44 ms     9 ms  six-sea2.netarch.akamai.com [206.81.80.168]
    10     *        *        *     Request timed out.
    11     *        *        *     Request timed out.
    12     *        *        *     Request timed out.
    13    37 ms     4 ms    64 ms  a184-27-178-116.deploy.static.akamaitechnologies.com [184.27.178.116]

    Trace complete.

B. Now trace RIR site (www.ripe.net)

        
    C:\Users\Madeline S>tracert www.ripe.net

    Tracing route to e337066.dscb.akamaiedge.net [23.59.88.237]
    over a maximum of 30 hops:

    1     5 ms     6 ms     6 ms  192.168.4.1 (Private IP, prolly local network)
    2    25 ms     4 ms     4 ms  10.248.14.1 (possible ISP network gateway)
    3    20 ms     5 ms    35 ms  100.122.0.93 (Carrier Grade NAT IP (100.64.0.0/10 block) used for IPv4 addy conservation)
    4    41 ms     6 ms    33 ms  65.182.49.69 (Public IP address, belongs to ISP)
    5    37 ms    38 ms     7 ms  65.182.49.2 (hop within same ISP network)
    6     6 ms    66 ms     5 ms  65.182.49.209 (likely core router of ISP)
    7    58 ms    37 ms    13 ms  e0-44.switch1.sea2.he.net [64.71.158.141] (router from Hurricane Electric, sea2=seattle, Seattle internet exchange point)
    8     *        *        *     Request timed out. (hop doesn't respond to traceroute probes, prolly security)
    9    14 ms   102 ms     9 ms  six-sea1.netarch.akamai.com [206.81.80.113] (now in Akamai's network at the seattle internet exchange, is a CDN)
    10     *        *        *     Request timed out.
    11     *        *        *     Request timed out.
    12     7 ms    55 ms     5 ms  a23-59-88-237.deploy.static.akamaitechnologies.com [23.59.88.237] (Edge server for www.ripe.net, packet reached target)

    Trace complete.

- Reflection: 
    - tracert can be affected by: network outages, high traffic, firewalls blocking ICMP packets, ACL on intermediary devices preventing ICMP packets & asymmetric forwarding paths.
    - `A network access control list (ACL)` is made up of rules that either allow access to a computer environment or deny it.
    - `Asymmetric routing` is where packets take different paths to and from a destination


#### 1.2.5 Video - Determining End Device IP Addresses w/ Packet Tracer

- Find Device IP: 
    - Device>Config>FastEthernet0>Static IPv4 and subnet mask. Settings will show default gateway.
    - Desktop tab>cmd> ipconfig
    - Dynamic Host Configuration Protocol (DHCP) - device can make a request to a DHCP server to be assigned an address

#### 1.2.6 Video - Device Connection Types w/ Packet Tracer 

- PC to switch: straight through cable, fastEthernet0 (NIC), connect to port FastEthernet0/1
- Connect 2 switches: normally 2 like devices are connected with a crossover cable but it can vary depending on the device and port.
    - Use GigabitEthernet0 port
- Connect switch to router: straight through, connecting unlike devices
    - switch use other GigabitEthernet port use first on router.
    - red means you need to activate the router interface
- Connect PC0 to router using console cable 
    - PC select RS32 port, on router select console port.
    - Allows you to manage the router using terminal interface software
- Wireless connections are managed from the devices themselves

#### 1.2.7 Packet Tracer - Create Simple Network 

- Part 1: Build Simple Network
- Part 2: Configure end devices & verify connectivity

`***See Packet Tracer Course Notes***`


### 1.3 Growth of IoT Devices

#### 1.3.1 What is IoT

- Definition: Collection of millions of smart devices and sensors connected through internet.
- IoT has been possible thanks to cheap processors and wireless networks

#### 1.3.5 How are IoT Devices Connected to the Network?

- `Sensors`: Can either have a wired ethernet connection or a wireless connection to a controller
    - Can use wireless ethernet but Bluetooth LE, Zigbee, or LoRa are more practical and save power
    - When 'out in field' power consumption is important 
- `Controllers` - are responsible for collecting data from sensors and providing network or internet connectivity. 
    - Have the ability to make immediate decisions or can send data back to more powerful computer for analysis. 
    - More powerful computer could be in same LAN as controller or only accessible through internet connection. 
- `Actuator` - Takes electrical input and transforms input into physical sensation
    - i.e. sensor detects temp, send to microcontroller, sends data to actuator to change temp. 

### 2.0 Everything is Programmable 

- 


















