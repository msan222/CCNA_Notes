## Section 17

### Dynamic Routing Protocols vs Static RoutesS17V105

![alt text](images/Section17_Images/image.png)

#### Propagate Routes from right to left

![alt text](images/Section17_Images/image-1.png)

![alt text](images/Section17_Images/image-2.png)

![alt text](images/Section17_Images/image-3.png)

![alt text](images/Section17_Images/image-4.png)

![alt text](images/Section17_Images/image-5.png)

![alt text](images/Section17_Images/image-6.png)

#### From Left to right:

- same thing as before just from other side

#### Summary Routes S17V10

![alt text](images/Section17_Images/image-8.png)

![alt text](images/Section17_Images/image-7.png)

![alt text](images/Section17_Images/image-9.png)

![alt text](images/Section17_Images/image-10.png)

![alt text](images/Section17_Images/image-11.png)

![alt text](images/Section17_Images/image-12.png)

### Dynamic Routing Protocols Lab Demo S17V106

![alt text](images/Section17_Images/image-13.png)

- ^ip addresses already configured on all interfaces

- use notepad and templates to help with configurations

Basic RIP configuration:

![alt text](images/Section17_Images/image-14.png)

    - enable on all interfaces on 10.0.0.0 network

![alt text](images/Section17_Images/image-15.png)

- ^Then do it on all interfaces (R1-R5, example is just R1)

Go to router in middle and start a debug rip (R3):

- Command (enable mode: `debug ip rip`

![alt text](images/Section17_Images/image-16.png)

- ^See that rip update is coming in from R2 at 10.1.0.2
- Will also see updates from R4 at 10.1.1.1

![alt text](images/Section17_Images/image-17.png)

- `R3`` should receive updates on  10.0.0.0/24, 10.0.1.1/24, 10.0.3.0/24 and 10.0.2.1/24 networks from `R2`
- R3 will also be sending out updates to R2 and R4

![alt text](images/Section17_Images/image-18.png)

![alt text](images/Section17_Images/image-19.png)

Routing table is updating:

![alt text](images/Section17_Images/image-20.png)

- Turn off debug: `undebug all`

![alt text](images/Section17_Images/image-21.png)

### Routing Protocol Types S17V107

![alt text](images/Section17_Images/image-22.png)

![alt text](images/Section17_Images/image-23.png)

![alt text](images/Section17_Images/image-24.png)

![alt text](images/Section17_Images/image-25.png)

- They both only form adjacency with directly connected neighbors (who they 'talk' to)

- For Distance Vector the updates are from the POV of the neighbor
- For Link State the updates are just all the routers and their links in the network, not the router's POV 
    - routers have full picture of topology and they can make better decisions but put more load on the router

![alt text](images/Section17_Images/image-26.png)

![alt text](images/Section17_Images/image-27.png)

### Routing Protocol Types Demo - S17V108

![alt text](images/Section17_Images/image-28.png)

- We already have RIP configured on all routers 

Command to see what protocols are running: 

![alt text](images/Section17_Images/image-29.png)

Check Configuration: 

- 'sh run' and scroll or 'sh run | section rip' or 'sh run | begin rip'

show info that was received from rip: 

![alt text](images/Section17_Images/image-30.png)

The 3 Things that happen with Routing Protocols:

1. Routers form an adjacency with eachother
2. exchange routes with eachother
3. Best routes will make it into routing table

- to see best routes check routing table to see which ones made it in 'sh ip route'

- **RIP is a Distance Vector Protocol so we just see the info from neighbors from their POV:

![alt text](images/Section17_Images/image-31.png)

#### Configuring OSPF:

![alt text](images/Section17_Images/image-32.png)

- ^do it on all other routers too

With OSPF we can see the other routers and the link info too (Link State): 

Command (global config mode): `sh ip ospf database`

![alt text](images/Section17_Images/image-33.png)

### Routing Protocol Metrics - S17V109

#### Metrics For RIP

![alt text](images/Section17_Images/image-34.png)

- IGP - Interior Gateway Protocol

![alt text](images/Section17_Images/image-35.png)

![alt text](images/Section17_Images/image-36.png)

![alt text](images/Section17_Images/image-37.png)

- RIP: Routing information protocol
    - doesn't take link bandwidth into acct.

![alt text](images/Section17_Images/image-38.png)

![alt text](images/Section17_Images/image-39.png)

![alt text](images/Section17_Images/image-40.png)

![alt text](images/Section17_Images/image-43.png)

![alt text](images/Section17_Images/image-41.png)

![alt text](images/Section17_Images/image-42.png)

- R3 tells R4 10.0.1.0/24 3 hops away, R5 is only 2 hops away so it picks R5
    - The one that has the `lowest metric`
    - we would have preferred the top half with 100 megabits per link

![alt text](images/Section17_Images/image-44.png)

![alt text](images/Section17_Images/image-46.png)

#### Metrics for OSPF & Others

![alt text](images/Section17_Images/image-47.png)

![alt text](images/Section17_Images/image-48.png)

- ^OSPF picked top path

![alt text](images/Section17_Images/image-49.png)

![alt text](images/Section17_Images/image-50.png)

- ^EIGRP is basically like OSPF except u can configure a delay

![alt text](images/Section17_Images/image-51.png)

### Routing Protocols Metrics Lab Demo - S17V110

#### RIP

![alt text](images/Section17_Images/image-52.png)

- ^ips already configured, no routing protocols or static routes configured here

![alt text](images/Section17_Images/image-53.png)

- ^Just connected routes here so definitely no static routes or protocols

1. Paste rip config (highlighted) in on every router:

![alt text](images/Section17_Images/image-54.png)

Rip Routes on R1 verification: 

![alt text](images/Section17_Images/image-55.png)

- Shutdown f3/0 - the routing protocol will reconverge (recalc the next best path):

![alt text](images/Section17_Images/image-57.png)

![alt text](images/Section17_Images/image-56.png)

- Now if you turn it back on it will still take time before rip sees the 'better' path again and moves back to going through R5

![alt text](images/Section17_Images/image-58.png)

#### IS-IS 

- not tested often on CCNA (more common on service provider networks)

Paste it in to every router:

Make sure to change 'net' address every time since every router needs to have a unique net address:

![alt text](images/Section17_Images/image-59.png)

![alt text](images/Section17_Images/image-60.png)

![alt text](images/Section17_Images/image-61.png)

^number 5

- After pasting in IS-IS the IS-IS routes are going to replace the RIP routes in the routing table
    - because of `administrative distance`

![alt text](images/Section17_Images/image-63.png)

![alt text](images/Section17_Images/image-64.png)

- ^It's going along the top path
    - we didn't manually set costs on our links so it behaves like RIP (using hop count b/c links are default same cost)
    - BUT it isn't going along R5 - why?
        - Probably b/c of convergence: R1 has formed adjacency w/ R2 but not with R5 yet
        - When it does learn R5 it will switch to that

- Now going out FE3/0 (like we'd expect for RIP or un-configured IS-IS )

![alt text](images/Section17_Images/image-65.png)

#### OSPF

- Copy & paste OSPF config into each router:

![alt text](images/Section17_Images/image-66.png)

- Again administrative distance has it so OSPF routes replace IS-IS

We have one OSPF adjacency but not all:

![alt text](images/Section17_Images/image-67.png)

Then all: 

![alt text](images/Section17_Images/image-68.png)

- taking bandwidth into account by default

Set links to be lower bandwidth which is why OSPF is preferring top path:

![alt text](images/Section17_Images/image-69.png)

![alt text](images/Section17_Images/image-70.png)

#### EIGRP

- Copy into each router: 

![alt text](images/Section17_Images/image-71.png)

- EIGRP will be chosen over OSPF b/c administrative distance and replace OSPF routes in table 

![alt text](images/Section17_Images/image-72.png)

### Equal Cost Multi Path S17V111

![alt text](images/Section17_Images/image-73.png)

![alt text](images/Section17_Images/image-74.png)
 
- ^R4 will install 2 routes on each path to load balance

Can do the same w/ static (just put in 2+ different next hops):

![alt text](images/Section17_Images/image-75.png)

- IGP same as static for load balancing: 
    - traffic is not going to be load-balanced red-robin style - if you've got a specific host talking to a web server the traffic for that one flow is not going to go through the first packet, R1 then second packet, R2, and so forth
    - If it gets a load balance to R1 all traffic for single flow will go through same router, like R1 for ex

- If you have a different source host talking to a different destination that will be load balanced through a different link

Summary:
    - Same flow always goes through same router
    - different flows go through different routers
    - ** don't want packets for same flow arriving out of order & apps to fail

### Equal Cost Multi Path Lab Demo

![alt text](images/Section17_Images/image-76.png)

- ^have rip and ips configured on all routers

![alt text](images/Section17_Images/image-77.png)

- ^only got one path to 10.0.1.0 because it's a best path

What if we change it so they all have equal costs? :

![alt text](images/Section17_Images/image-78.png)

- first we're gonna leave R5 links slow and add in an R6:

![alt text](images/Section17_Images/image-79.png)

![alt text](images/Section17_Images/image-80.png)

Before R4 just had the 1 route to 10.0.1.0 network behind R1. What happens when we've added in R6?:

![alt text](images/Section17_Images/image-82.png)

- ^Now it's gonna go via **2** paths

Now what happens if we enable OSPF?

- paste in config on all routers: 

![alt text](images/Section17_Images/image-83.png)

- then OSPF routes should replace the rip ones

![alt text](images/Section17_Images/image-84.png)

- ^Now there's just one route again for 10.0.1.0 - why is that?

![alt text](images/Section17_Images/image-85.png)

- OSPF takes bandwidth into account as well as hops so now the 2 routes are not equal anymore.

- To make them equal you have to make the links on R5 100 mgbts too (do it for both interfaces and the ones on R4 and R6)

![alt text](images/Section17_Images/image-86.png)

Now it's converged:

![alt text](images/Section17_Images/image-87.png)

### Administrative Distance S17V113

AD (Administrative Distance) used w/ metrics to determine best path

![alt text](images/Section17_Images/image-88.png)

![alt text](images/Section17_Images/image-89.png)

![alt text](images/Section17_Images/image-90.png)

![alt text](images/Section17_Images/image-91.png)

![alt text](images/Section17_Images/image-92.png)

![alt text](images/Section17_Images/image-93.png)

![alt text](images/Section17_Images/image-95.png)

![alt text](images/Section17_Images/image-96.png)

![alt text](images/Section17_Images/image-97.png)

![alt text](images/Section17_Images/image-98.png)

![alt text](images/Section17_Images/image-99.png)

![alt text](images/Section17_Images/image-100.png)

![alt text](images/Section17_Images/image-101.png)

- ^will work if R3-R4 goes down, but if R3-R2 or R2-R1 goes down R1 will continue sending traffic along the top path and only get as far as the broken link

### Administrative Distance Lab Demo - S17V114

![alt text](images/Section17_Images/image-102.png)

- ^ips are configured, rip is configured for every router except R5

![alt text](images/Section17_Images/image-103.png)

Paste in IS-IS config:

![alt text](images/Section17_Images/image-104.png)

'sh ip protocols' will show rip and IS-IS 
- if you check routing table only IS-IS will show 

- Then do OSPF 
- Then EIGRP

Now Floating Static Route: 

- on R1 is configure a backup route to the 10.1.2.0 network behind R4 to go through R5 instead. 

![alt text](images/Section17_Images/image-105.png)

- would also need a static route from R4, sorry, from R5 to R4, and also static routes coming back in the other direction

![alt text](images/Section17_Images/image-106.png)

It replaced the other one: 

![alt text](images/Section17_Images/image-107.png)

Make it just a backup:

![alt text](images/Section17_Images/image-108.png)

- EIGRP route will be back in routing table now
- static route is in there as a backup now

- you shut down F0/0 EIGRP will detect that and will fail over to the static route we just configured.

### Loopback Interfaces S17V115

![alt text](images/Section17_Images/image-109.png)

![alt text](images/Section17_Images/image-110.png)

![alt text](images/Section17_Images/image-111.png)

![alt text](images/Section17_Images/image-112.png)

![alt text](images/Section17_Images/image-113.png)


#### Do this in the lab (R4)

![alt text](images/Section17_Images/image-114.png)

Create the loopback interface: 

![alt text](images/Section17_Images/image-115.png)

Configure the ip address for it: 

![alt text](images/Section17_Images/image-116.png)

Make sure it's advertised in routing protocol

Not yet:
![alt text](images/Section17_Images/image-117.png)

![alt text](images/Section17_Images/image-118.png)

Now it's in: 

![alt text](images/Section17_Images/image-166.png)

![alt text](images/Section17_Images/image-119.png)

Going along top path:

![alt text](images/Section17_Images/image-120.png)

### Adjacencies and Passive Interfaces - S17V116

![alt text](images/Section17_Images/image-121.png)

![alt text](images/Section17_Images/image-122.png)

![alt text](images/Section17_Images/image-123.png)

![alt text](images/Section17_Images/image-124.png)

![alt text](images/Section17_Images/image-125.png)

![alt text](images/Section17_Images/image-126.png)

![alt text](images/Section17_Images/image-127.png)

![alt text](images/Section17_Images/image-128.png)

### Adjacencies and Passive Interfaces Lab Demo - S17V117

![alt text](images/Section17_Images/image-129.png)

![alt text](images/Section17_Images/image-131.png)

On Router 4 - rip routes going everywhere but nothing to the network behind R1 (no  routing protocols configured on R1 yet):

![alt text](images/Section17_Images/image-132.png)

Now add loopback interface to R1: 

![alt text](images/Section17_Images/image-133.png)

Now we want the router to start sharing routes and learning other routes (add rip):

![alt text](images/Section17_Images/image-134.png)

Make sure that we aren't sharing info with R6 (FE2/0) since it's in another company:

![alt text](images/Section17_Images/image-135.png)

*We haven't enabled rip on the interfaces yet, just globally, so nothing will happen yet.

Add it: 

![alt text](images/Section17_Images/image-136.png)

Now R4 has learned the networks behind R1: 

![alt text](images/Section17_Images/image-137.png)

Even though RIP is configured on R6 it can't learn any of the routes into any of the internal networks:

![alt text](images/Section17_Images/image-138.png)

### Route Precedence - S17V118

- Now we're tying together all these sections and reconfirming how routers find the best paths

![alt text](images/Section17_Images/image-139.png)

![alt text](images/Section17_Images/image-141.png)

![alt text](images/Section17_Images/image-142.png)

![alt text](images/Section17_Images/image-143.png)

![alt text](images/Section17_Images/image-144.png)

![alt text](images/Section17_Images/image-145.png)

![alt text](images/Section17_Images/image-146.png)

![alt text](images/Section17_Images/image-147.png)

![alt text](images/Section17_Images/image-148.png)

![alt text](images/Section17_Images/image-149.png)

![alt text](images/Section17_Images/image-150.png)

![alt text](images/Section17_Images/image-152.png)

![alt text](images/Section17_Images/image-155.png)

![alt text](images/Section17_Images/image-154.png)

![alt text](images/Section17_Images/image-156.png)

![alt text](images/Section17_Images/image-157.png)

![alt text](images/Section17_Images/image-158.png)

- ^/30 is the longest, so 198.168.0.2 will choose the /30 route

![alt text](images/Section17_Images/image-160.png)

![alt text](images/Section17_Images/image-161.png)

Same here:

![alt text](images/Section17_Images/image-162.png)

![alt text](images/Section17_Images/image-163.png)

![alt text](images/Section17_Images/image-164.png)

![alt text](images/Section17_Images/image-165.png)

- **Remember:
    - RIP is a **distance vector** protocol so routers only get their neighbors view
    - OSPF is a **Link State** protocol so it gets all the info for all links and routers it's connected to




