## Section 18 - Connectivity Troubleshooting

### Basic Connectivity Troubleshooting - S18V121

![](images/2025-11-05-16-40-17.png)

![](images/2025-11-05-16-41-39.png)

![](images/2025-11-05-16-42-09.png)

![](images/2025-11-05-16-42-20.png)

![](images/2025-11-05-16-50-59.png)

![](images/2025-11-05-16-52-38.png)

![](images/2025-11-05-16-54-59.png)

#### Traceroute

![](images/![alt%20text](image.png).png)

![](images/2025-11-05-16-58-40.png)

![](images/2025-11-05-16-59-33.png)

![](images/2025-11-05-16-59-52.png)

![](images/2025-11-05-17-00-04.png)

![](images/2025-11-05-17-00-32.png)

![](images/2025-11-05-17-01-03.png)

![](images/2025-11-05-17-02-32.png)

![](images/2025-11-05-17-03-01.png)

![](images/2025-11-05-17-03-11.png)

![](images/2025-11-05-17-03-24.png)

## Section 19 - IGP Interior Gateway Protocol Fundamentals

- OSPF is main focus of CCNA but you still need to know fundamentals of RIP and EIGRP

### RIP the Routing Information Protocol - S19V124

![](images/2025-11-05-17-33-20.png)

![](images/2025-11-05-17-35-21.png)

![](images/2025-11-05-17-37-10.png)

![](images/2025-11-05-17-37-28.png)

![](images/2025-11-05-17-38-26.png)

- ^defaults to the default class subnet mask, this is not helpful

![](images/2025-11-05-17-40-03.png)

- on router R2, you see that all of the 10.1.X.X networks are over to the left, out interface FastEthernet1/0. All of the 10.0.X.X networks are over to the right, out interface FastEthernet0/0 on router R2. So, what we're going to do in the example is R2 is going to advertise all of the 10.0.X.X networks to R3 as a single summary route.

- configure the summary on the interface that you are going to advertise on, not the interface everything is actually coming out of

![](images/2025-11-05-17-46-06.png)

![](images/2025-11-05-17-46-56.png)

![](images/2025-11-05-17-47-11.png)

![](images/2025-11-05-17-47-52.png)

- good to check the rip routes and why/why not they're in the routing table

![](images/![alt%20text](image-1.png).png)

![](images/2025-11-05-17-49-39.png)

![](images/2025-11-05-17-50-10.png)

![](images/2025-11-05-17-50-45.png)

### RIP Lab Demo - S19V125

- Goal: Configure & verify rip 

![](images/2025-11-05-17-52-17.png)

Make sure no protocols are running on the routers already:

![](images/2025-11-05-17-53-35.png)

Configure rip on each router:

![](images/2025-11-05-17-54-56.png)

#### Configure the Summarization: 

The 10.1 networks are all accessible through R2 or R5

![](images/2025-11-05-17-58-23.png)

![](images/![](images/2025-11-05-17-59-40.png).png)

- configure summarization on both, summarize as 10.1.0.0 /16
    - R2 FE0/0
    - R5 FE3/0

![](images/2025-11-05-18-05-21.png)

Commands:

![](images/2025-11-05-18-11-45.png)

Give Internet Connectivity Everywhere:

![](images/2025-11-05-18-11-12.png)

inject:

![](images/2025-11-05-18-12-32.png)

Add a route for all routers to 203.0.113.0 (service provider) - make FE3/0 on R4 a passive interface

![](images/2025-11-05-18-17-29.png)

### EIGRP - The Enhanced Interior Gateway Routing Protocol S19V126

![](images/2025-11-05-18-24-38.png)

![](images/2025-11-05-18-25-35.png)

![](images/2025-11-05-18-26-21.png)

![](images/2025-11-05-18-27-13.png)

![](images/2025-11-05-18-28-32.png)

![](images/2025-11-05-18-29-36.png)

- ^What it means is look for interfaces with an IP address which falls within that range. So any interface in this example that has got an IP address that begins with 10.0, and then anything after that would be a match.

![](images/2025-11-05-18-31-42.png)

![](images/2025-11-05-18-33-41.png)



