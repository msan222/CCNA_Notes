## Section 17

### Dynamic Routing Protocols vs Static RoutesS17V105

![alt text](image.png)

#### Propagate Routes from right to left

![alt text](image-1.png)

![alt text](image-2.png)

![alt text](image-3.png)

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

#### From Left to right:

- same thing as before just from other side

#### Summary Routes S17V10

![alt text](image-8.png)

![alt text](image-7.png)

![alt text](image-9.png)

![alt text](image-10.png)

![alt text](image-11.png)

![alt text](image-12.png)

### Dynamic Routing Protocols Lab Demo S17V106

![alt text](image-13.png)

- ^ip addresses already configured on all interfaces

- use notepad and templates to help with configurations

Basic RIP configuration:

![alt text](image-14.png)

    - enable on all interfaces on 10.0.0.0 network

![alt text](image-15.png)

- ^Then do it on all interfaces (R1-R5, example is just R1)

Go to router in middle and start a debug rip (R3):

![alt text](image-16.png)

- ^See that rip update is coming in from R2 at 10.1.0.2
- Will also see updates from R4 at 10.1.1.1

![alt text](image-17.png)

- `R3`` should receive updates on  10.0.0.0/24, 10.0.1.1/24, 10.0.3.0/24 and 10.0.2.1/24 networks from `R2`
- R3 will also be sending out updates to R2 and R4

![alt text](image-18.png)

![alt text](image-19.png)

Routing table is updating:

![alt text](image-20.png)

- Turn off debug: `undebug all`

![alt text](image-21.png)

### Routing Protocol Types S17V107

![alt text](image-22.png)

![alt text](image-23.png)

![alt text](image-24.png)

![alt text](image-25.png)

- They both only form adjacency with directly connected neighbors (who they 'talk' to)

- For Distance Vector the updates are from the POV of the neighbor
- For Link State the updates are just all the routers and their links in the network, not the router's POV 
    - routers have full picture of topology and they can make better decisions but put more load on the router

![alt text](image-26.png)

![alt text](image-27.png)

### Routing Protocol Types Demo - S17V108

![alt text](image-28.png)

- We already have RIP configured on all routers 

Command to see what protocols are running: 

![alt text](image-29.png)

Check Configuration: 

- 'sh run' and scroll or 'sh run | section rip' or 'sh run | begin rip'

show info that was received from rip: 

![alt text](image-30.png)

The 3 Things that happen with Routing Protocols:

1. Routers form an adjacency with eachother
2. exchange routes with eachother
3. Best routes will make it into routing table

- to see best routes check routing table to see which ones made it in 'sh ip route'

- **RIP is a Distance Vector Protocol so we just see the info from neighbors from their POV:

![alt text](image-31.png)

#### COnfiguring OSPF:

![alt text](image-32.png)

- ^do it on all other routers too

With OSPF we can see the other routers and the link info too (Link State):

![alt text](image-33.png)

### Routing Protocol Metrics - S17V109

#### Metrics For RIP

![alt text](image-34.png)

- IGP - Interior Gateway Protocol

![alt text](image-35.png)

![alt text](image-36.png)

![alt text](image-37.png)

- RIP: Routing information protocol
    - doesn't take link bandwidth into acct.

![alt text](image-38.png)

![alt text](image-39.png)

![alt text](image-40.png)

![alt text](image-43.png)

![alt text](image-41.png)

![alt text](image-42.png)

- R3 tells R4 10.0.1.0/24 3 hops away, R5 is only 2 hops away so it picks R5
    - The one that has the `lowest metric`
    - we would have preferred the top half with 100 megabits per link

![alt text](image-44.png)

![alt text](image-46.png)

#### Metrics for OSPF & Others

![alt text](image-47.png)

![alt text](image-48.png)

- ^OSPF picked top path

![alt text](image-49.png)

![alt text](image-50.png)

- ^EIGRP is basically like OSPF except u can configure a delay

![alt text](image-51.png)

### Routing Protocols Metrics Lab Demo - S17V110

#### RIP

![alt text](image-52.png)

- ^ips already configured, no routing protocols or static routes configured here

![alt text](image-53.png)

- ^Just connected routes here so definitely no static routes or protocols

1. Paste rip config (highlighted) in on every router:

![alt text](image-54.png)

Rip Routes on R1 verification: 

![alt text](image-55.png)

- Shutdown f3/0 - the routing protocol will reconverge (recalc the next best path):

![alt text](image-57.png)

![alt text](image-56.png)

- Now if you turn it back on it will still take time before rip sees the 'better' path again and moves back to going through R5

![alt text](image-58.png)

#### IS-IS 

- not tested often on CCNA (more common on service provider networks)

Paste it in to every router:

Make sure to change 'net' address every time since every router needs to have a unique net address:

![alt text](image-59.png)

![alt text](image-60.png)

![alt text](image-61.png)

^number 5

- After pasting in IS-IS the IS-IS routes are going to replace the RIP routes in the routing table
    - because of `administrative distance`

![alt text](image-63.png)

![alt text](image-64.png)

- ^It's going along the top path
    - we didn't manually set costs on our links so it behaves like RIP (using hop count b/c links are default same cost)
    - BUT it isn't going along R5 - why?
        - Probably b/c of convergence: R1 has formed adjacency w/ R2 but not with R5 yet
        - When it does learn R5 it will switch to that

- Now going out FE3/0 (like we'd expect for RIP or un-configured IS-IS )

![alt text](image-65.png)

#### OSPF

- Copy & paste OSPF config into each router:

![alt text](image-66.png)

- Again administrative distance has it so OSPF routes replace IS-IS

We have one OSPF adjacency but not all:

![alt text](image-67.png)

Then all: 

![alt text](image-68.png)

- taking bandwidth into account by default

Set links to be lower bandwidth which is why OSPF is preferring top path:

![alt text](image-69.png)

![alt text](image-70.png)

#### EIGRP

- Copy into each router: 

![alt text](image-71.png)

- EIGRP will be chosen over OSPF b/c administrative distance and replace OSPF routes in table 

![alt text](image-72.png)

### Equal Cost Multi Path S17V111

![alt text](image-73.png)

![alt text](image-74.png)
 
- ^R4 will install 2 routes on each path to load balance

Can do the same w/ static (just put in 2+ different next hops):

![alt text](image-75.png)

- IGP same as static for load balancing: 
    - traffic is not going to be load-balanced red-robin style - if you've got a specific host talking to a web server the traffic for that one flow is not going to go through the first packet, R1 then second packet, R2, and so forth
    - If it gets a load balance to R1 all traffic for single flow will go through same router, like R1 for ex

- If you have a different source host talking to a different destination that will be load balanced through a different link

Summary:
    - Same flow always goes through same router
    - different flows go through different routers
    - ** don't want packets for same flow arriving out of order & apps to fail

### Equal Cost Multi Path Lab Demo

![alt text](image-76.png)

- ^have rip and ips configured on all routers

![alt text](image-77.png)

- ^only got one path to 10.0.1.0 because it's a best path

What if we change it so they all have equal costs? :

![alt text](image-78.png)

- first we're gonna leave R5 links slow and add in an R6:

![alt text](image-79.png)

![alt text](image-80.png)

Before R4 just had the 1 route to 10.0.1.0 network behind R1. What happens when we've added in R6?:

![alt text](image-82.png)

- ^Now it's gonna go via **2** paths

Now what happens if we enable OSPF?

- paste in config on all routers: 

![alt text](image-83.png)

- then OSPF routes should replace the rip ones

![alt text](image-84.png)

- ^Now there's just one route again for 10.0.1.0 - why is that?

![alt text](image-85.png)

- OSPF takes bandwidth into account as well as hops so now the 2 routes are not equal anymore.

- To make them equal you have to make the links on R5 100 mgbts too (do it for both interfaces and the ones on R4 and R6)

![alt text](image-86.png)

Now it's converged:

![alt text](image-87.png)

### Administrative Distance S17V113

AD (Administrative Distance) used w/ metrics to determine best path

![alt text](image-88.png)

![alt text](image-89.png)

![alt text](image-90.png)

![alt text](image-91.png)

![alt text](image-92.png)

![alt text](image-93.png)

![alt text](image-95.png)

![alt text](image-96.png)

![alt text](image-97.png)

![alt text](image-98.png)

![alt text](image-99.png)

![alt text](image-100.png)

![alt text](image-101.png)

- ^will work if R3-R4 goes down, but if R3-R2 or R2-R1 goes down R1 will continue sending traffic along the top path and only get as far as the broken link

### Administrative Distance Lab Demo - S17V114

![alt text](image-102.png)

- ^ips are configured, rip is configured for every router except R5

![alt text](image-103.png)

Paste in IS-IS config:

![alt text](image-104.png)

'sh ip protocols' will show rip and IS-IS 
- if you check routing table only IS-IS will show 

- Then do OSPF 
- Then EIGRP

Now Floating Static Route: 

- on R1 is configure a backup route to the 10.1.2.0 network behind R4 to go through R5 instead. 

![alt text](image-105.png)

- would also need a static route from R4, sorry, from R5 to R4, and also static routes coming back in the other direction

![alt text](image-106.png)

It replaced the other one: 

![alt text](image-107.png)

Make it just a backup:

![alt text](image-108.png)

- EIGRP route will be back in routing table now
- static route is in there as a backup now

- you shut down F0/0 EIGRP will detect that and will fail over to the static route we just configured.