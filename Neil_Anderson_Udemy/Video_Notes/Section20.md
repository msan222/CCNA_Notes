## Section 20 - OSPF - Open Shortest Path First

### OSPF Characteristics - S20V130

![](images/2025-11-07-10-35-40.png)

![](images/2025-11-07-10-36-19.png)

![](images/2025-11-07-10-37-08.png)

![](images/2025-11-07-10-44-34.png)

![](images/2025-11-07-10-51-33.png)

![](images/2025-11-07-10-51-18.png)

![](images/2025-11-07-10-52-51.png)

![](images/2025-11-07-10-59-20.png)

![](images/2025-11-07-11-01-10.png)

![](images/2025-11-07-11-03-56.png)

![](images/2025-11-07-11-05-13.png)

![](images/2025-11-07-11-05-58.png)

- `Wildcard mask is just the opposite of the subnet mask`

![](images/2025-11-07-11-08-37.png)

![](images/2025-11-07-11-08-59.png)

![](images/2025-11-07-11-09-31.png)

![](images/2025-11-07-11-11-42.png)

![](images/2025-11-07-11-12-02.png)

![](images/2025-11-07-11-12-18.png)

![](images/2025-11-07-11-13-13.png)

![](images/2025-11-07-11-14-01.png)

![](images/2025-11-07-11-14-43.png)

### OSPF Basic Configuration Lab Demo - S20V132

![](images/2025-11-07-11-16-44.png)

![](images/2025-11-07-11-18-05.png)

- ^paste in all routers

Now verify it:

![](images/2025-11-07-11-18-49.png)

Check Protocols:

![](images/2025-11-07-11-19-10.png)

Check Neighbors:

![](images/2025-11-07-11-19-34.png)

Check Routes:

![](images/2025-11-07-11-19-55.png)

Check Database for troubleshooting:

![](images/2025-11-07-11-20-51.png)

Can also check interfaces ospf has been enabled on:

![](images/2025-11-07-11-21-32.png)

### OSPF Advanced Topics - S20V133

- Router ID, Passive Interfaces, Default route injection

![](images/2025-11-07-11-24-00.png)

![](images/2025-11-07-11-24-55.png)

![](images/2025-11-07-11-25-20.png)

![](images/2025-11-07-11-26-17.png)

![](images/2025-11-07-11-26-57.png)

![](images/2025-11-07-11-29-11.png)

![](images/2025-11-07-11-29-52.png)

- Once a default route is injected, it will show up as an `external route` in OSPF
    - means that the route was redistributed into OSPF 
    - `redistribution` - we take a route from another source (like a static route or another protocol) and we 'inject' it into OSPF

### OSPF Advanced Topics Lab Demo - S20V134

#### Configure the Router ID

![](images/2025-11-07-11-35-13.png)

- ^R4 is connected to internet at FE3/0 at 293.0.113.1

- Check router ID in R4 now:

![](images/2025-11-07-11-36-51.png)

R4 has taken the highest ip address as its ID since there is no loopback (it's back practice for it to do that):

![](images/2025-11-07-11-39-06.png)

Add a loopback address: 
(it does no shutdown automatically)

![](images/2025-11-07-11-40-01.png)

- ^needs to be manually reset to update to loopback 

Reset OSPF so that the router ID update to the new loopback addy:

![](images/2025-11-07-11-41-45.png)

- ^also have to paste config back in

Can also set the id manually (still have to reset for it to show up):

![](images/2025-11-07-11-42-43.png)

Reload ospf (similar to removing and re-enabling the config):

![](images/2025-11-07-11-44-47.png)

#### Passive Interface 

![](images/2025-11-07-11-46-26.png)

- ^on R4 FE 3/0 the network 203.0.113.1/24 is not being advertised in OSPF 
    - We want to advertise it to our routers on the inside so we'll make FE3/0 a passive interface

![](images/2025-11-07-11-49-59.png)

- ^first set the interface to passive then put in the network command so that it'll be advertised internally

Now it's converged & other routers have learned it:

![](images/2025-11-07-11-51-43.png)

#### Static Default Route Injection

![](images/2025-11-07-11-53-19.png)

- `ip route 0.0.0.0 0.0.0.0 203.0.113.2` - static route saying for everything that doesn't have a more specific route, so 0.0.0.0 0.0.0.0 with the next hop address of 203.0.113.2

Then go into the ospf 1 -> `router ospf 1`

- `default-information originate` - this command injects the default static route into ospf

Can check and see if route was added to other routers:

![](images/2025-11-07-11-58-06.png)

### OSPF Areas - S20V135

![](images/2025-11-07-12-15-54.png)

![](images/2025-11-07-12-17-01.png)

![](images/2025-11-07-12-17-30.png)

![](images/2025-11-07-12-18-43.png)

![](images/2025-11-07-12-19-35.png)

![](images/2025-11-07-12-20-17.png)

- `Intra-area Routes` - destination network is in same area

- `inter-area Routes` - destination network is in different area

- `External Route` - a route that was redistributed into OSPF

![](images/2025-11-07-12-25-40.png)

![](images/2025-11-07-12-25-59.png)

- **Summarization** is always done in **ABRs**

![](images/2025-11-07-12-32-49.png)

![](images/2025-11-07-12-33-24.png)

- Not only do you need to configure the different areas, you also need to configure summarization on your ABRs to get any benefits:

![](images/2025-11-07-12-35-08.png)

- ^R2 is our ABR there

- if 10.0.0.0/24 link went down, all routers in Area 1 would have to recalculate/re-converge, but R1's route 10.0.0.0/16 would just stay the same.

![](images/2025-11-07-12-42-13.png)

![](images/2025-11-07-12-42-52.png)

![](images/2025-11-07-12-43-25.png)

![](images/2025-11-07-12-43-41.png)

- ^`ASBR` - the router is running OSPF and it's distributing from another source into OSPF
    - i.e. router is also running RIP and EIGRP and we're taking our RIP routes and redistributing them into OSPF so the OSPF neighbors 

![](images/2025-11-07-12-46-28.png)

- Doesn't mean it's outside an org or enterprise but it was redistributed into OSPF

### OSPF Areas Lab Demo - S20V136

![](images/2025-11-07-12-48-54.png)

- ^segment into Area 0 and Area 1

![](images/2025-11-07-12-53-23.png)

- Remember `Backbone` routers are the ones that have *all* their interfaces in `Area 0`
    - `normal` routers have all their interfaces in other Areas

- Put R2 FE0/0 on the right into Area 1
- Put R5 FE3/0 into Area 1 
- On R1 we need to put all its interface into Area 1

![](images/2025-11-07-12-58-11.png)

- ^all routers already have OSPF and all the routes are set to intra area routes

First Configure ABRs:

![](images/2025-11-07-12-59-28.png)

- ^R2 has been configured with process 1 and it's putting all its network interfaces into Area 0 (10.0.0.0)

- We'll have 10.1.0.0 in Area 0 and 10.0.0.0 in Area 1

1. Remove the original network statement and add in the two new ones:

![](images/2025-11-07-13-03-49.png)

- ^make sure that network statements don't overlap & wildcard masks are correct

- Getting a mismatched Area id because we haven't changed R1 yet (R1's id doesn't match the area that's just been set up for it)

Before doing R1 set up R5 as an ABR (FE2/0 is 10.1.0.0/16 and FE3/0 is 10.0.0.0/16):

- check original network statements and remove it:

![](images/2025-11-07-13-08-32.png)

- put in new network statements:

![](images/2025-11-07-13-09-53.png)

Now Configure R1:

- remove network statement:

![](images/2025-11-07-13-10-47.png)

- New network statement: 

![](images/2025-11-07-13-11-19.png)

Now the 10.0.0.0 networks will show up as an inter-area route on R4

![](images/2025-11-07-13-12-12.png)

**^We still haven't configured summarization - so it still shows up as traffic from Area 1 is coming from 4 different routes (no benefits yet)

Configuring Summarization on ABRs:

- On R2 summarize all individual 10.0.X.X/24 networks into 10.0.0.0/16 and advertise that into Area 0
- On R5 summarize all individual networks 10.1.X.X/24 networks into 10.1.0.0/16 and advertise that into Area 1

On R2:

- When summarizing use `subnet mask` 
- When doing network statement use `wildcard mask`

![](images/2025-11-07-13-19-00.png)

On R5: 

![](images/2025-11-07-13-19-30.png)

Now we can see that the 4 10.0.0.0/24 routes have been summarized into one 10.0.0.0/16 route on R4:

![](images/2025-11-07-13-21-12.png)

Same on R1:

![](images/2025-11-07-13-21-57.png)

### Bandwidth vs Clock Rate and Speed - S20V137

![](images/2025-11-07-13-23-12.png)

![](images/2025-11-07-13-24-35.png)

![](images/2025-11-07-13-25-34.png)

![](images/2025-11-07-13-26-36.png)

- ^i.e. You configure a QoS policy which guarantee video traffic 1/3 of the bandwidth on the interface. 
    - You tell the router how much bandwidth is actually there using the `bandwidth` command
    - **Normally you want the bandwidth to actually match the physical interface
    - `Ethernet` does this by default anyway

- Serial interface always defaults to 1.544 Mgbts/sec 

- If an interface was actually at 64 Kbps or 128 Kbps and not the default you'd use the 'bandwidth' command to set the bandwidth so that it matches physically
    - Sometimes you wouldn't want it to match so you'd just have it be different than they physical

### OSPF Cost Metric - S20V138

![](images/2025-11-07-13-33-51.png)

![](images/2025-11-07-13-34-23.png)

![](images/2025-11-07-13-34-47.png)

![](images/2025-11-07-13-35-14.png)

![](images/2025-11-07-13-39-18.png)

- ^For R4 -> R1 along top path
    - use the outbound interface on the other side of the link
- **Make sure to set the cost the same on both sides of the link so traffic doesn't become asynchronous

![](images/2025-11-07-13-42-52.png)

- 30 cost from R2 -> R3 -> R1
- 60 cost from R2 -> R1
- So it would choose the bottom path even though there are more hops

![](images/2025-11-07-13-44-40.png)

- *T1 is a serial interface 100/1.544 = 64

![](images/2025-11-07-13-46-03.png)

- ^top R1 F0/0 is Fast ethernet (cost =1)
- Bottom G1/0 on R2 and R3 G0/0 are also set to 1 even though Gigabit Ethernet is faster

To Fix this:

![](images/2025-11-07-13-49-30.png)

- set it to a high value so that when Ethernet gets higher in the future you won't have to change it all again

![](images/2025-11-07-13-52-08.png)

![](images/2025-11-07-13-52-57.png)

![](images/2025-11-07-13-53-28.png)

- ^Changing the bandwidth on a serial interface

![](images/2025-11-07-13-54-16.png)

Verify Cost:

![](images/2025-11-07-13-54-32.png)

### OSPF Cost Metric Lab Demo - S20V1239

![](images/2025-11-07-13-55-52.png)

- already have ospf on all routers

![](images/2025-11-07-13-56-52.png)

- ^ going to the 10.2.0/24 network via bottom path at 10.0.3.2 on R5 (path is shorter) 
    - AD (Administrative Distance): 110 (OSPF default)
    - Cost: 3 (all interfaces are FastEthernet so they all cost 1)

- We're going to set a higher reference bandwidth so that Gigabit And 10GigabitEthernet will be preferred in the future.
    - make sure to configure this on all the routers

![](images/2025-11-07-14-18-13.png)

![](images/2025-11-07-14-19-29.png)

- ^now the costs are changed

Now we're going to change the path (it's currently going along the bottom path via R5)

- Change on the bottom to higher since there are 2 links (FE2/0 FE3/0) - set it so that each link is 2000 instead of 1000 
    - Bottom = 2000 + 2000 + 1000 (end link)
    - Top = 4000
    - Will choose top

- Make sure to do it on all interfaces:

![](images/2025-11-07-14-22-56.png)

![](images/2025-11-07-14-23-17.png)

![](images/2025-11-07-14-23-30.png)

Now it should be going via R2:

![](images/2025-11-07-14-23-53.png)

### OSPF Adjacencies - S20V140

- how OSPF routers form adjacencies and build LSDB (link state databases)

![](images/2025-11-07-14-24-44.png)

![](images/2025-11-07-14-25-33.png)

![](images/2025-11-07-14-26-25.png)

![](images/2025-11-07-14-26-56.png)

![](images/2025-11-07-14-27-24.png)

![](images/2025-11-07-14-28-54.png)

![](images/2025-11-07-14-30-52.png)

 ![](images/2025-11-07-14-33-02.png)

 ![](images/2025-11-07-14-35-24.png)

 ![](images/2025-11-07-14-37-05.png)

 - MTU is max packet size - if a router needs to send a packet larger than the MTU it will just break it up into smaller packets

- this is not an OSPF setting this is a setting on the router's interface

![](images/2025-11-07-14-40-34.png)

-  `show interface GigabitEthernet0/0`- will show the interface MTU

- `show ip interface (interface number)` - to see the ip MTU

- if you need to check the MTU, the 'show interface' command won't work, you need to do the 'show *ip* interface'

![](images/2025-11-07-14-45-45.png)

- ^if you were to put ospf on both routers they would become neighbors but they would not be able to actually share any ospf routes with each other

![](images/2025-11-07-14-56-28.png)

![](images/2025-11-07-14-57-52.png)

![](images/2025-11-07-14-58-17.png)

- highest router id starts exchange

![](images/2025-11-07-15-13-36.png)

![](images/2025-11-07-15-20-14.png)

![](images/2025-11-07-15-20-38.png)

![](images/2025-11-07-15-20-53.png)

### OSPF Adjacencies Lab Demo - S20V141

![](images/2025-11-07-15-22-09.png)

- R2 has ospf already

![](images/2025-11-07-15-22-50.png)

- R2 is actually an ABR

- R1 will be normal router in Area 1

![](images/2025-11-07-15-24-12.png)

- Configure OSPF on R1 and since we want to see the adjacency process we'll use the command `debug ospf adj` - turns debug on

![](images/2025-11-07-15-25-48.png)

![](images/2025-11-07-15-26-22.png)

- ^2way communication

![](images/2025-11-07-15-26-49.png)

- going into exchanging Database descriptors

![](images/2025-11-07-15-27-27.png)

- ^exchange done 

![](images/2025-11-07-15-28-10.png)

- ^now it's done and has gone from LOADING to FULL

`u all` - turn off debug

Show neighbors to check:

![](images/2025-11-07-15-29-02.png)

#### Create Problem to Prevent Adjacency

- At R2 GE0/0 is facing R1

- Go into GE0/0 and set different OSPF Hello Timer - `ip ospf hello-interval X`

![](images/2025-11-07-15-32-39.png)

Also Change interface MTU too:

![](images/2025-11-07-15-33-03.png)

- ^You can also see that the timer had already expired and the neighbor R1 was 'down'

Verify the change:

Other interfaces - 

![](images/2025-11-07-15-37-14.png)

GE0/0 - 

![](images/2025-11-07-15-38-53.png)

- Notice how GE0/0 is now at the 5 that we set while the others remained at the default
    - you use `sh ip ospf int` to see it because when you change it, the change is at the interface level

- Try to look at the MTU via `sh int Gig 0/0`

![](images/2025-11-07-15-40-54.png)

- it's still at the default, why can't we see it?

- Need to look at `sh ip int Gig 0/0` and include *ip* 

![](images/2025-11-07-15-42-45.png)

- ^Now we can see where we changed the default MTU

Now when we do `sh ip ospf neighbor` we won't see anything:

![](images/2025-11-07-15-43-50.png)

Can debug this with `debug ip ospf hello`(irl you should first check the configurations on each interface on the link)

`debug ip ospf hello` - debugs any issues with ospf hello packets

![](images/2025-11-07-15-46-10.png)

- ^we can see that it's mismatched here
- Then check the hello timers on each router (irl speak to network designer and figured out exactly how it should be configured not just pick one)

Fix it:

![](images/2025-11-07-15-48-20.png)

![](images/2025-11-07-15-48-36.png)

- ^speeds things up in lab, don't do irl b/c it brings all ospf down 

Now we see the state of exchange:

![](images/2025-11-07-15-49-16.png)

- ^they're stuck in the exchange (commonly caused by MTU mismatch)

check that with `debug ip ospf adj` 
- (irl you would compare the running configurations to try to find the issue, *then* you would do the debug)

We can see the neighbor has a smaller MTU: 

![](images/2025-11-07-15-51-33.png)

- Then compare MTU interface on both sides:

![](images/2025-11-07-15-52-01.png)
![](images/2025-11-07-15-52-38.png)

- Might need it to be set to 1460

Change it on R1 to match then:

![](images/2025-11-07-15-53-38.png)

Now it's made it to FULL:

![](images/2025-11-07-15-54-04.png)

### OSPF DR and BDR Designated Routes - S20V142

![](images/2025-11-07-15-55-11.png)

(DR) Designated Router - Master Router that receives all full info and updates all the others
BDR - Backup in case the DR goes down 

- *DR and BDR act at the *interface* level, not the entire router level
    - if one of the routers had another interface that was connected to anther ethernet segment that interface would also have its own DR and BDR

![](images/2025-11-07-15-58-46.png)

![](images/2025-11-07-16-00-52.png)

- Typically irl you'd leave it and the highest Router ID is used 

- **In the CCNA might be asked to configure one as a DR though

![](images/2025-11-07-16-02-49.png)

- Election just happens on multi-access segments - On a router it knows if an interface is an ethernet interface and it will need a DR elected there. 
    - If there was a serial interface with a point-to-point link the router would know that it doesn't need a DR

- some old interfaces you need to specify p2p or multi access segment

![](images/2025-11-07-16-06-20.png)

- ^at interface level

- need to restart ospf (`clear ospf` or shut it down)

![](images/2025-11-07-16-07-41.png)

![](images/2025-11-07-16-08-50.png)

- 224.0.0.6 is the multicast addy for all Designated Routers (just DR and BDR)
    - if other routers see a change it will send it to that address

- 224.0.0.5 - multicast to 'all OSPF routers'

### OSPF DR and BDR Lab Demo - S20V143

![](images/2025-11-07-16-17-21.png)

- ^all connected to Ethernet segment in middle which is on the 172.12.0.0/24 network

- OSPF is on all routers but only w/ a network statement for loopback interfaces so ospf isn't enabled yet

- Verify everything then enable OSPF on ethernet interfaces

Dr - R9, BDR - R8 (using highest router ID which is the loopback address)

- Check interfaces and OSPF config (example on R6):

![](images/2025-11-07-16-21-41.png)

![](images/2025-11-07-16-22-15.png)

- Can see ospf hasn't been enabled on FE interface b/c there's no matching network statement for 172.16.0.0: 

![](images/2025-11-07-16-23-22.png)

Check ospf is running and router id is on loopback address's interface: 

![](images/2025-11-07-16-24-25.png)

Enable OSPF on Ethernet interface:

![](images/2025-11-07-16-25-08.png)

![](images/2025-11-07-16-25-40.png)

^do this on R6, R7, R8, R9

should be able to see neighbors:

![](images/2025-11-07-16-26-15.png)

- ^showing 2WAY then full 

![](images/2025-11-07-16-26-50.png)

- ^ can see that all the relationships with other routers are full and R8 is BDR b/c R9 is the DR
    - R6 and R7 are marked as DROTHER Designated Router, Other because they are neither the DR nor the BDR

Figure out which Router is DR from any router on the segment:

`sh ip ospf interface` and or get more targeted and enter the interface that's on the segment

![](images/2025-11-07-16-30-37.png)

![](images/2025-11-07-16-31-22.png)

View from others (full with R8 and R9 but not others):

![](images/2025-11-07-16-31-40.png)

Now force R7 to become DR:

![](images/2025-11-07-16-32-37.png)

Priority will change but have to force election again via 'clear ip ospf process' 

Now R7 is the DR:

![](images/2025-11-07-16-33-59.png)

- **Notice BDR doesn't change - won't unless you reboot all routers

What happens if DR goes down:

- powered off DR
- Check R8: 

 ![](images/2025-11-07-16-35-36.png)

 - switches from R7 to R8 is now DR and R9 is the BDR

Lab Notes:

network 10.0.0.0 0.0.255.255

- ^What it means is look for interfaces with an IP address which falls within that range. So any interface in this example that has got an IP address that begins with 10.0, and then anything after that would be a match.

R1: network 10.0.0.0 0.255.255.255 Area 1
    - Any interface that begins with 10

R2: 
















































 




