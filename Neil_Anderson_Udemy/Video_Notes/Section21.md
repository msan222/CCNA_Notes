## Section 21 - VLANS Virtual Local Area Networks

### Campus LAN Design - Core, Distribution, and Access Layers - S21V146

![](images/2025-11-12-10-07-14.png)

![](images/2025-11-12-10-09-40.png)

![](images/2025-11-12-10-11-34.png)

![](images/2025-11-12-10-14-52.png)

![](images/2025-11-12-10-15-42.png)

![](images/2025-11-12-10-16-52.png)

![](images/2025-11-12-10-17-06.png)

- end hosts & LAN security policies on Access Layer switches
- Aggregation point for Access layer & Software policies (QoS) enabled at distribution layer switches
- Core layer designed for speed/resiliency and links all distribution layer

### Spine-Leaf Network - S21V147

![](images/2025-11-12-10-30-58.png)

- ^This would work fine for a data center if it only had mostly north/south traffic flows
- `North/South Traffic Flow` - traffic is mainly flowing up and down - i.e. up and down data center then to clients in other buildings

- BUT in modern data centers a lot of traffic goes East/West - i.e. between actual servers themselves or web based front-end on one server to a backend database on another server - traditional campus design doesn't work for this (what spine/leaf is for)

![](images/2025-11-12-10-36-27.png)

- ^Better scalability and better for East/West traffic 

- Can add additional spine and leaf switches:

![](images/2025-11-12-10-37-24.png)

- Servers only connect to leaf and all leaf switches are connected to all spine switches - if servers need to talk to each other they're only 2 hops away

### Why we have VLANs - S21V48

![](images/2025-11-12-10-52-43.png)

![](images/2025-11-12-10-55-25.png)

![](images/2025-11-12-10-57-03.png)

![](images/2025-11-12-10-58-35.png)

- ^the traffic goes from the switch to the router b/c the destination MAC address will be the engineering PC's default gateway

- Can put security policy on router if you wanted to limit unicast traffic 

![](images/2025-11-12-11-00-48.png)

- ^i.e. an arp request where the traffic would go out everywhere

![](images/2025-11-12-11-01-28.png)

![](images/2025-11-12-11-02-36.png)

![](images/2025-11-12-11-02-48.png)

![](images/2025-11-12-11-04-50.png)

![](images/2025-11-12-11-06-29.png)

- ^Broadcast traffic only gets flooded out ports that are in that VLAN

### VLAN Access Ports - S21V149

![](images/2025-11-12-11-07-34.png)

![](images/2025-11-12-11-12-27.png)

![](images/2025-11-12-11-13-33.png)

![](images/2025-11-12-11-12-44.png)

![](images/2025-11-12-11-18-19.png)

![](images/2025-11-12-11-20-30.png)

![](images/2025-11-12-11-20-57.png)

![](images/2025-11-12-11-21-12.png)

- ^shows all VLANS available on switch and which ports are in which VLAN

![](images/2025-11-12-11-21-52.png)

- See a specific port - sh interface put switchport at the end

### VLAN Access Ports Lab Demo - S21V150

 ![](images/2025-11-12-11-23-50.png)

![](images/2025-11-12-11-24-50.png)

- ^on Sw1 interface F0/1 is configured as an access port on the default VLAN1 (only VLAN configured)

![](images/2025-11-12-11-25-52.png)

![](images/2025-11-12-11-26-29.png)

- if you try to ping Sales PC through 10.10.20.12 it won't work b/c they're in the same VLAN at layer 2 but in different subnets at Layer 3 -> you'd need a router to go between 2 subnets

- But broadcast traffic will flood to the other subnet since the switch isn't Layer 3 aware: 

![](images/2025-11-12-11-29-16.png)

Create VLANs: 

![](images/2025-11-12-11-31-34.png)

Put ENG1 into Engineering VLAN:

![](images/2025-11-12-11-32-21.png)

![](images/2025-11-12-11-33-29.png)

- ^Now if ENG1 tries to ping ENG2 it fails because while they're in the same subnet they're in different VLANs at layer 2, so the switch won't send that traffic

Now add ENG2 PC to the correct VLAN: 

![](images/2025-11-12-11-35-36.png)

Now put sales PC into correct VLAN:

![](images/2025-11-12-11-37-43.png)

Verify everything is correct now:

![](images/2025-11-12-11-38-07.png)

### VLAN Trunk Ports - S21V151

![](images/2025-11-12-11-40-09.png)

- ^Currently all the links b/t switches are on the default VLAN1 
    - PCs in the same VLAN on the same switch can talk to each other but they can't communicate w/ PCs on a different switch even if they're on the same VLAN

![](images/2025-11-12-11-43-00.png)

- ^On links b/t switches instead of configuring them as access ports for only one VLAN, configure them as trunk ports which will carry traffic for all VLANs

![](images/2025-11-12-11-44-19.png)

![](images/2025-11-12-11-45-11.png)

![](images/2025-11-12-11-46-24.png)

![](images/2025-11-12-11-46-42.png)

Sales broadcast Traffic:

![](images/2025-11-12-11-48-55.png)

![](images/2025-11-12-11-49-06.png)

![](images/2025-11-12-11-49-59.png)

- for normal configure switches as access ports
- for ports going to another switch configure it as a trunk
- for VMs configure the port to the host also as a trunk

IP phones: 
    - on an IP phone the phone is connected to the switch and the back of the user
    - only uses one port on your switch
    - want to be able to separate phone calls from data traffic even though they're going through the same cable

![](images/2025-11-12-11-54-04.png)

![](images/2025-11-12-11-54-50.png)

- ^F0/24 is connected to another switch 
- on older switches you have to put the dot1q but you don't need to do it on modern switches
- then you'd need to configure the other side on the other switch too 

If the switch is plugged into an IP phone:

![](images/2025-11-12-11-56-22.png)

- don't configure it as mode 'trunk', put access, even though it is a trunk port
    - you then configure the voice VLAN in `switchport access vlan #` for PC and `switchport voice vlan #`

![](images/2025-11-12-11-58-54.png)

![](images/2025-11-12-12-01-50.png)

- ^dedicated VLAN, no hosts connected no other purpose besides untagged traffic 

![](images/2025-11-12-12-03-15.png)

- says inactive b/c no access ports (as intended)

![](images/2025-11-12-12-03-59.png)

- ^done for security but also performance

- No sales PCs on top switch 
- So, on link b/t 2 switches configure allowed VLAN traffic - yes to account and ENG, no to sales

![](images/2025-11-12-12-05-41.png)

- ^if you don't do this all VLANs will be allowed over the link

### VLAN Trunk Ports Lab Demo - S21V152

![](images/2025-11-12-12-06-47.png)

- Already configured SW1 and put ENG and Sales PC in correct VLAN, nothing else

![](images/2025-11-12-12-09-16.png)

- Gig0/1 to other SW2 isn't configured yet - it's an access port in VLAN1, we need it to be a trunk port

- first configure the native VLAN (not 1)
- create a dedicated VLAN to use as a dedicated one

![](images/2025-11-12-12-11-18.png)

![](images/2025-11-12-12-11-36.png)

Check switch supports dot1q:

![](images/2025-11-12-12-12-31.png)

Configure other side on SW2 to be a trunk:

- First configure VLANs 

![](images/2025-11-12-12-13-38.png)

- Then configure trunk port:

![](images/2025-11-12-12-14-21.png)

- Set the native VLAN or the trunk won't come up properly:

![](images/2025-11-12-12-14-53.png)

Now configure trunk going to SW3:

![](images/2025-11-12-12-15-34.png)

Verify:

![](images/2025-11-12-12-15-51.png)

![](images/2025-11-12-12-16-03.png)

![](images/2025-11-12-12-17-28.png)

- ^make sure you do 'no shutdown on all interfaces'

![](images/2025-11-12-12-16-52.png)

- ^this error comes up because SW3 trunk port hasn't been configured yet

Configure SW3:

![](images/2025-11-12-12-18-14.png)

![](images/2025-11-12-12-18-49.png)

Now configure access ports for PCs on SW3:

![](images/2025-11-12-12-20-04.png)

Check Connectivity:

![](images/2025-11-12-12-20-21.png)

![](images/2025-11-12-12-22-41.png)

- **There's no router here so you can't ping b/t different VLANs

Eng to Sales:

![](images/2025-11-12-12-23-52.png)

### DTP Dynamic Trunking Protocol - S21V153

![](images/2025-11-12-12-39-43.png)

![](images/2025-11-12-12-40-31.png)

![](images/2025-11-12-12-42-46.png)

![](images/2025-11-12-12-43-11.png)

![](images/2025-11-12-12-44-32.png)

- On SW1 Gig0/1 is an access port b/c on the other side where SW2 is the connecting port is also set to auto
    - So, no trunk is formed

Form a trunk:

![](images/2025-11-12-12-45-12.png)

![](images/2025-11-12-12-46-05.png)

- DTP is not recommended 

How you should do it: 

![](images/2025-11-12-12-46-30.png)

### VTP VLAN Trunking Protocol - S21V154

![](images/2025-11-12-13-05-45.png)

- ^i.e. - You go to a VTP server and there's no configuration on any switches yet
    - 1. On the server you create VLAN Eng and VLAN sales
    - that configuration will be pushed to all clients (your switches)
        - VTP saves you from having to configure VLANs on all your different switches
    - if you don't need a VLAN and delete it and it will be automatically deleted on all clients
    - or if you change VLAN 10 to VLAN 100 that will update too

- you still need to perform the port level access or trunk port configuration 
    - switches don't know which port needs to be eng VLAN and which port needs to be sales VLAN

![](images/2025-11-12-13-13-52.png)

- a VTP server is the default and if one with a higher number is introduced into a network that already has one, then the VLANs on the original VTP server will get wiped out and all your PCs will get dropped off the network
    - you'd probably get fired for doing that

![](images/2025-11-12-13-15-56.png)

![](images/2025-11-12-13-19-15.png)

![](images/2025-11-12-13-27-50.png)

![](images/2025-11-12-13-28-27.png)

![](images/2025-11-12-13-28-38.png)

![](images/2025-11-12-13-29-51.png)

### VTP Lab Demo - S21V155

![](images/2025-11-12-13-46-48.png)

- Trunks b/t switches have been configured but no VLANs or access ports created
- VLAN 199 created for native VLAN

Verify: 

![](images/2025-11-12-13-47-32.png)

![](images/2025-11-12-13-47-59.png)

![](images/2025-11-12-13-48-12.png)

We're gonna make SW1 VTP server, SW2 transparent, SW3 as a VTP client

- Need to configure VLANs on the VTP server SW1 and on SW2 b/c it's transparent

1. Configure VTP Client: (currently a server)

![](images/2025-11-12-13-50-26.png)

![](images/2025-11-12-13-50-55.png)

Check:

![](images/2025-11-12-13-51-19.png)

2. Configure SW2:

- it picked up domain name from other switch

![](images/2025-11-12-13-52-11.png)

Now change: 

![](images/2025-11-12-13-52-54.png)

3. Configure SW1:

![](images/2025-11-12-13-53-32.png)

- Now VTP is set up and we have to configure out VLANs (aside from native VLAN for trunks)

![](images/2025-11-12-13-54-30.png)

Now SW3 has those VLANs:

![](images/2025-11-12-13-55-01.png)

VLANs aren't on SW2 b/c it's transparent:

![](images/2025-11-12-13-55-26.png)

4. Configure switchports to the correct VLANs on each switch (SW1 and SW3)

![](images/2025-11-12-13-56-04.png)

![](images/2025-11-12-13-56-30.png)

![](images/2025-11-12-13-57-02.png)

- ENG1 still can't ping ENG3 b/c SW2 (transparent) doesn't know about the Sales and Eng VLANs

![](images/2025-11-12-13-58-50.png)

![](images/2025-11-12-13-59-21.png)

- traffic comes from SW1 into SW2 tagged with Dot1q tag of Eng VLAN, but SW2 doesn't know that VLAN

We need to add the VLANs on SW2 for this to work:

![](images/2025-11-12-14-00-56.png)

Eng1:
![](images/2025-11-12-14-01-41.png)

Sales1 to Sales3:

![](images/2025-11-12-14-02-12.png)

Sales to Eng fails b/c it's in a different subnet and there's no router.













