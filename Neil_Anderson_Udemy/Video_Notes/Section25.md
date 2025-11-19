## Section 25: STP - Spanning Tree Protocol **Core CCNA Topic**

### Layer 3 Path Selection and Loop Prevention Review - S25V176

- Spanning Tree - Layer 2 technology that prevents loops across layer 2 switch network

Review:
![](images/2025-11-14-14-50-12.png)

- ^switches CD1, CD2, Acc3, Acc,4 are all layer 2 
    - The rest is Layer 3

![](images/2025-11-14-14-54-28.png)

![](images/2025-11-14-14-57-30.png)

- when configuring a backup route it needs to be pointing to the same subnet as the original route

![](images/2025-11-14-14-59-44.png)

![](images/2025-11-14-15-00-34.png)

PCs POV:

- Pcs have 2 gateways available on 10.10.10.0/24 network

![](images/2025-11-14-15-01-57.png)

- Configure HSRP on R1 & R2 so PCs will only need to use 1 gateway

##### How Routing Loops Can Happen

![](images/2025-11-14-15-05-39.png)

![](images/2025-11-14-15-05-47.png)

- will only loop for length of TTLS

![](images/2025-11-14-15-07-34.png)

### Why we have the Spanning Tree Protocol - S25V178

Review Ethernet Path Selection:

![](images/2025-11-14-15-10-47.png)

![](images/2025-11-14-15-18-40.png)

![](images/2025-11-14-15-21-49.png)

![](images/2025-11-14-15-22-38.png)

![](images/2025-11-14-15-23-06.png)

![](images/2025-11-14-15-24-02.png)

![](images/2025-11-14-15-24-11.png)

![](images/2025-11-14-15-31-20.png)

![](images/2025-11-14-15-32-21.png)

![](images/2025-11-14-15-32-57.png)

![](images/2025-11-14-15-33-21.png)

![](images/2025-11-14-15-35-06.png)

![](images/2025-11-14-15-35-57.png)

![](images/2025-11-14-15-36-24.png)

![](images/2025-11-14-15-36-54.png)

- ^Layer 2 traffic will loop forever 

![](images/2025-11-14-15-37-15.png)

![](images/2025-11-14-15-39-11.png)

- BUT before the ports were blocked, we were able to send traffic up to *both* CD1 and CD2 via F0/24 and F0/21 
    - with the ports blocked we're only able to use half the physically available connected uplink bandwidth

![](images/2025-11-14-15-41-54.png)

![](images/2025-11-14-15-42-40.png)

### Spanning Tree Terminology - The Bridge - S25V179

![](images/2025-11-14-15-51-48.png)

![](images/2025-11-14-15-52-53.png)

![](images/2025-11-14-15-54-11.png)


### How Spanning Tree Works - S25V180

![](images/2025-11-14-16-15-53.png)

![](images/2025-11-14-16-21-02.png)

![](images/2025-11-14-16-22-03.png)

![](images/2025-11-14-16-22-25.png)

![](images/2025-11-14-16-24-34.png)

![](images/2025-11-14-16-25-06.png)

![](images/2025-11-14-16-25-32.png)

![](images/2025-11-14-16-30-17.png)

![](images/2025-11-14-16-31-24.png)

![](images/2025-11-14-16-36-52.png)

![](images/2025-11-14-16-38-40.png)

- ^BUT if the direct link b/t SW4 and Root went down, **Spanning Tree is redundant** and the link from SW4 to SW3 would open up so SW4 had a path to the Root

![](images/2025-11-14-16-40-29.png)

- ^you'd have to change the cost on both sides of the link

![](images/2025-11-14-16-42-15.png)

![](images/2025-11-14-16-43-43.png)

![](images/2025-11-14-16-44-38.png)

![](images/2025-11-14-16-45-37.png)

![](images/2025-11-14-16-47-10.png)

20:15

![](images/2025-11-15-10-53-06.png)

![](images/2025-11-15-10-55-31.png)

![](images/2025-11-15-11-28-32.png)

![](images/2025-11-15-11-46-38.png)

![](images/2025-11-15-11-47-51.png)

![](images/2025-11-15-11-51-42.png)

How Failover Works:

![](images/2025-11-15-11-52-18.png)

![](images/2025-11-15-11-52-36.png)

- ^if CD2 loses access to the root, then it will no longer be able to send better BPDUs which is why the blocked ports will stop receiving traffic

![](images/2025-11-15-11-55-01.png)

- ^Once the designated port starts receiving better BPDUs from the previously-blocked port it will transition into being a *Root Port*

![](images/2025-11-15-11-56-45.png)
![](images/2025-11-15-11-57-54.png)

![](images/2025-11-15-11-58-34.png)

![](images/2025-11-15-12-01-36.png)

![](images/2025-11-15-12-02-00.png)

![](images/2025-11-15-12-02-29.png)

### Spanning Tree Versions - S25V181

![](images/2025-11-15-12-10-40.png)

![](images/2025-11-15-12-13-09.png)

![](images/2025-11-15-12-14-41.png)

![](images/2025-11-15-12-16-15.png)

- cisco versions PVST+ and Rapid PVST+ put a bit more load on the switch since it has to calculate the Spanning Tree instances at the VLAN level (each one) than at the group level

![](images/2025-11-15-12-18-59.png)

![](images/2025-11-15-12-19-26.png)

- **PVST+ and RPVST+ use same configuration and verification commands
    - if a switch is updated from PVST+ to RPVST+ all the spanning tree configurations previously made will carry over and work the same.
    - sh commands are the same too

![](images/2025-11-15-12-24-21.png)

![](images/2025-11-15-12-26-06.png)

- on newer 'blocked port' is known as 'Alternate'

### Verification - Show Spanning Tree - S25V182

![](images/2025-11-15-12-58-20.png)

![](images/2025-11-15-13-01-12.png)

![](images/2025-11-15-13-44-39.png)

![](images/2025-11-15-13-44-50.png)

![](images/2025-11-15-13-48-26.png)

![](images/2025-11-15-13-50-04.png)

Status of all the switches interfaces that are connected to other switches:

![](images/2025-11-15-13-50-38.png)

![](images/2025-11-15-13-51-24.png)

Lab Example:

![](images/2025-11-15-13-54-04.png)

- uses F0/21 (root port) (cost 19) to get to root bridge

![](images/2025-11-15-13-55-15.png)

- `sh spanning tree vlan 1` is best command to see everything 

![](images/2025-11-15-14-00-44.png)

![](images/2025-11-15-14-01-44.png)

### Verification - show mac address-table - S25V183

![](images/2025-11-15-14-17-27.png)

- We're going to check the direction traffic is traveling from PC1 -> R1
    - should be PC1 -> Acc3 -> CD1 -> R1

![](images/2025-11-15-14-19-05.png)

`sh mac address table` - check what interface traffic is coming out of

### Manipulating the Root Bridge Election - S25V184

![](images/2025-11-15-14-32-21.png)

![](images/2025-11-15-14-32-51.png)

![](images/2025-11-15-14-33-31.png)

![](images/2025-11-15-14-34-32.png)

![](images/2025-11-15-14-38-36.png)

- ^Not great

![](images/2025-11-15-14-39-36.png)

![](images/2025-11-15-14-39-48.png)

![](images/2025-11-15-14-40-57.png)

![](images/2025-11-15-14-41-16.png)

![](images/2025-11-15-14-42-07.png)

![](images/2025-11-15-14-42-16.png)

![](images/2025-11-15-14-42-52.png)

![](images/2025-11-15-14-43-28.png)

![](images/2025-11-15-14-43-50.png)

![](images/2025-11-15-14-44-57.png)

### Spanning Tree and HSRP Alignment - S25V185

![](images/2025-11-15-14-48-38.png)

- CD1 (root primary) and CD2 (root secondary)

![](images/2025-11-15-14-49-42.png)

Example of Load Balancing:

![](images/2025-11-15-14-51-48.png)

- half traffic goes along left, other half goes along right. If one path fails it will fail over to the other path w/out outages

- Using RoaS interfaces^

![](images/![](images/![](images/2025-11-15-15-42-52.png).png).png)

### Portfast, BPDU Guard and Root Guard - S25V186

![](images/2025-11-15-15-55-48.png)

- ^i.e. a PC isn't a bridged connection since it won't forward frames like a switch
    - SO we know the port on the PC will never form a loop

![](images/2025-11-15-15-58-45.png)

![](images/2025-11-15-15-59-18.png)

![](images/2025-11-15-16-00-43.png)

![](images/2025-11-15-16-02-11.png)

![](images/2025-11-15-16-03-42.png)

![](images/2025-11-15-16-04-26.png)

![](images/2025-11-15-16-04-42.png)

![](images/2025-11-15-16-06-16.png)

![](images/2025-11-15-16-06-36.png)

![](images/2025-11-15-16-07-07.png)

![](images/2025-11-15-16-07-58.png)

![](images/2025-11-15-16-09-23.png)

### Portfast and BPDU Guard Lab Demo - S25V187

![](images/2025-11-15-16-23-14.png)

![](images/2025-11-15-16-26-31.png)

![](images/2025-11-15-16-31-50.png)

- G0/0 & G0/3 are configured as a trunks
- G0/1 & G0/2 are connected to PCs 

![](images/2025-11-15-16-37-26.png)

- PCs won't be able to ping default gateways yet b/c the switch port is shut down. (b/c of spanning tree)

- Port connected to ENG1 is G0/1 sp we can enable portfast there:

![](images/2025-11-15-16-39-29.png)

Enable BPDU Guard too:

![](images/2025-11-15-16-40-03.png)

Check:

![](images/2025-11-15-16-40-16.png)

![](images/2025-11-15-16-40-26.png)

- with portfast edge, if a port receives a BPDU it just stops being a portfast port a
- with BPDU Guard the port shuts down entirely

Now we're going to bring our ports up:

![](images/2025-11-15-16-42-53.png)

![](images/2025-11-15-16-43-39.png)

![](images/2025-11-15-16-44-03.png)

- Sales1 takes longer b/c we didn't put portfast on it

### Root Guard Lab Demo - S25V188

Configure spanning tree root guard 

![](images/2025-11-18-09-17-18.png)

Eng dept in subnet 10.10.10.10 in VLAN 10 

- Eng default gateway is at R1
    - HSRP b/t R1/2

- R2 is in subnet 10.10.10.11 for sales (VLAN 11) (default gateway)

- CD2 Root bridge for VLAN 11, CD1 as root bridge for VLAN 10 (reverse as backup for each other)

- Want to make sure that Access switches never become root bridges 

- **Spanning tree enabled but not configured yet - but since CD1 has lowest MAC address it will end up being the root bridge for both VLANs 

Start of Lab

1. Verify:  `sh spanning tree vlan 10` (or 11)

![](images/2025-11-18-09-18-35.png)

![](images/2025-11-18-09-18-56.png)

![](images/2025-11-18-09-22-30.png)

- see that CD1 is root bridge for both VLANs

2. Give CD1 best priority for VLAN 10 (2nd best for VLAN11) and CD2 priority for VLAN 11 and 2nd best for VLAN 10 

![](images/2025-11-18-09-23-20.png)

![](images/2025-11-18-09-19-55.png)

got to global config

    `spanning-tree vlan 10 root primary` 

    `spanning tee vlan 11 root secondary`

check - `sh run | include spanning`

- but now CD2 is the root bridge for both VLANs 

on CD2 in global config:

    `spanning-tree vlan 11 root primary` 
    `spanning-tree vlan 10 root secondary`

- Now we're set with the correct root bridges and backups 

What if a network admin makes a mistake? (Gives a switch a value of zero by accident) - Access 3 will become the root bridge 

How we stop this from happening: 

    - on CD1 and CD2 we enable root guard on the interfaces down towards the Access layer switches to make sure that they never become the root

CD2 & CD1 - enable on G0/0 & G0/3

in global config:

    - int G0/0 and G0/3

`spanning-tree guard root` 

Verify on both CD1 and CD2:

`sh spanning-tree vlan 10` or 11 to see change in root bridge

- port down to access 3 will be made 'root inconsistent' 

- **Access 3 still thinks it has the best priority for the root bridge and is sending BPDUs but they are now getting rejected 

    - do `sh spanning-tree vlan 10` on Access 3 and it will say that it is still the root 

- Eng PCs can't ping default gateway b/c Access3 is now blackholed by root guard 

on Access3:

`sh run | include spanning`

- here we can see that it has the wrong spanning-tree priority set 

Fix: 
    - global config then `no spanning-tree vlan 10 (or 11) priority 0`

- **Now that the problem has been fixed and the interfaces on CD1 and CD2 are no longer receiving superior BPDUs, root guard will unblock Access3
    - PCs will now be able to ping default gateways 

### CCNA v1.1: BPDU filter  - S25V189

#### Spanning Tree BPDU Filter 

![](images/2025-11-18-09-24-33.png)

- while switches send BPDUs hosts do *not* 

![](images/2025-11-18-09-25-01.png)

BPDU filter is similar to Root Guard in the way that it detects unexpected BPDUs 

    - BPDU brings down the interfaces/ports that are sending them while BPDU filter filters BPDUs on ports but does NOT bring them down 

- BPDU Filter works differently whether you enter it globally or on an interface 
    - If enabled on global config (Applies to just interfaces that have portfast configured on them)
        - Sends initial BPDUs then stops sending them 
        - if a BPDU is received then it will remove portfast, disable BPDU filtering and act as a normal interface - it will then go through the different spanning tree stages to see if there's a loop there (Similar to portfast edge) 
    - if enabled on just an interface 
        - Will *not* send BPDUs and will ignore incoming BPDUs (effectively disables spanning tree)
    - **Not** Recommended to enabled a BPDU filter 
        - use case: if you have just a single down stream connection to a legacy switch that's causing STP issues 
- Normally for interfaces connected to end hosts you will want to just enable spanning tree, portfast, and BPDU guard 

Example of Use Case (unlikely irl) (***IN CASE ITS ON THE EXAM***): 

![](images/2025-11-18-09-25-24.png)

- network of three regular cisco switches sw1 sw2 sw3 all connected. On ports where they are connected we are running spanning tree (block one port on SW3-Sw2 to prevent a loop)
- SW3 is connected to a legacy switch
    - Not configurable, low MAC address so it keeps trying to become the root bridge and we can't stop that 
- **Notice that the legacy switch is acting like an end host (no loop is forming here)

So, what we will do is disable spanning tree on the port of SW3 that is leading to the legacy switch - the legacy switch will still think it's the root bridge but it won't affect the rest of the network 

Commands to do this:

`sw3(config)# spanning-tree portfast bpdufilter default`
`sw3(config)# interface g0/10 (interface that is linking SW3 and legacy)`
`sw3(config)# spanning-tree bpdufilter enable`

### CCNA v1.1: Loop Guard - S25V190

![](images/2025-11-18-09-26-42.png)

![](images/2025-11-18-10-02-49.png)

![](images/2025-11-18-10-09-56.png)

![](images/2025-11-18-10-35-19.png)

![](images/2025-11-18-10-48-46.png)

![](images/2025-11-18-10-49-24.png)

To Prevent This:

![](images/2025-11-18-10-49-39.png)

- UDLD sends 'keepalives' in both directions on a link and it both aren't receiving them then it knows that there's a unidirectional link problem

![](images/2025-11-18-10-54-20.png)

![](images/2025-11-18-10-59-18.png)

![](images/2025-11-18-11-06-45.png)

![](images/2025-11-18-11-09-43.png)

![](images/2025-11-18-11-29-33.png)

![](images/2025-11-18-11-30-34.png)

![](images/2025-11-18-11-30-58.png)

![](images/2025-11-18-11-34-30.png)

When Loop Guard Does detect a unidirectional link failure and places a port into 'inconsistent' state:

![](images/2025-11-18-11-36-59.png)

### CCNA v1.1: PVST+ vs RPVST+ Convergence - S25V191

- Convergence in the sense of how Spanning Tree builds loop-free paths throughout the topology & how it recovers from any link failures

![](images/2025-11-18-11-57-14.png)

![](images/2025-11-18-12-05-49.png)

![](images/2025-11-18-12-06-51.png)

- *UplinkFast and BackboneFast are not covered in the CCNA - easiest way to get them is just to enable RPVST+

![](images/2025-11-18-12-08-55.png)

- 802.1D and PVST+ are *slow*

![](images/2025-11-18-12-11-04.png)

![](images/2025-11-18-12-16-12.png)

- RSTP, RPVST+, and MSTP are much faster

![](images/2025-11-18-12-17-19.png)

![](images/2025-11-18-12-20-02.png)

![](images/2025-11-18-12-20-41.png)

- should change it to rapid-pvst (RPVST+) OR if you want to group your VLANs into spanning tree instances, then you should pick MST (the ones listed above are the 'plus') versions

![](images/2025-11-18-12-24-07.png)

### CCNA v1.1: RPVST+ and Hub Interoperability - S25V192

![](images/2025-11-18-12-32-51.png)

![](images/2025-11-18-12-34-09.png)

![](images/2025-11-18-12-44-50.png)

![](images/2025-11-18-12-51-37.png)

![](images/2025-11-18-13-00-48.png)

- ^using 802.1D or PVST+ here will take 30sec for failover if there's an outage
- On Acc4 it has 'backup' ports going upstream and downstream (F0/24 and F0/11) 
    - BUT if we were to do a 'sh' command there's no way of telling which backup port is for upstream and which is for downstream

If we switch to RSTP (RPVST+ or MSTP on Cisco):

![](images/2025-11-18-13-15-23.png)

- we now have an actual backup port F0/11 facing towards the hub downstream

![](images/2025-11-18-13-17-31.png)

- if we were to do a 'sh' command here on Acc4 we would see that F0/24 is an alternate port

![](images/2025-11-18-13-18-41.png)

### STP Troubleshooting Lab Notes:

![](images/2025-11-18-15-07-20.png)

![](images/2025-11-18-15-23-33.png)

![](images/2025-11-18-15-28-14.png)

![](images/2025-11-18-15-29-31.png)

![](images/2025-11-18-15-29-45.png)

- To get to internet PC1 will have to go:

PC1 -> Acc3 -> CD1 -> R1 -> SP1

- ^This is fine

- PC2's path is not fine:

PC2 -> Acc4 -> CD1 -> Acc3 -> CD1 -> R1

![](images/2025-11-18-15-52-43.png)





