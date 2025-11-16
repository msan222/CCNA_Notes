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

- will only loop for length of TTL

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

- `sh spannining tree vlan 1` is best command to see everything 

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








