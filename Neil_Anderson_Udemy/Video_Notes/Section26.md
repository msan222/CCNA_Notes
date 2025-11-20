## Section 26 - Etherchannel

### Why we have Etherchannel - S26V196

![](images/2025-11-19-15-29-39.png)

 ![](images/2025-11-19-15-34-28.png)

![](images/2025-11-19-16-04-41.png)

- `subscription ratio: (client)/(uplink) : 1`
- 48Gbps (client) / 20 Gbps (uplink) = 2.4:1

![](images/2025-11-19-16-09-14.png)

![](images/2025-11-19-16-11-25.png)

Bundle multiple physical ports into a single logical port on inter-switch links w/ Etherchannel:

![](images/2025-11-19-16-13-43.png)

Can do the same thing on servers:

![](images/2025-11-19-16-13-55.png)

![](images/2025-11-19-16-16-00.png)

### EtherChanel Load Balancing - S26V197

![](images/2025-11-19-16-37-45.png)

![](images/2025-11-19-16-46-15.png)

![](images/2025-11-19-16-47-12.png)

![](images/2025-11-19-16-48-20.png)

![](images/2025-11-19-16-48-49.png)

![](images/2025-11-19-16-49-48.png)

![](images/2025-11-19-16-50-33.png)

### Etherchannel Protocols and Configuration - S26V198

![](images/2025-11-19-16-52-02.png)

![](images/2025-11-19-16-52-32.png)

![](images/2025-11-19-16-52-53.png)

- ^good if connecting to another vendor than cisco

![](images/2025-11-19-16-53-55.png)

![](images/2025-11-19-16-54-36.png)

![](images/2025-11-19-16-55-39.png)

- set native vlan, allowed vlans, port type (access, trunk, etc) at portchannel configuration level

![](images/2025-11-19-17-00-21.png)

![](images/2025-11-19-17-00-55.png)

![](images/2025-11-19-17-01-24.png)

![](images/2025-11-19-17-02-06.png)

![](images/2025-11-19-17-02-49.png)

![](images/2025-11-19-17-04-32.png)

- Point of using Etherchannel is to avoid spanning tree shutting down some of your links

![](images/2025-11-19-17-06-38.png)

### Etherchannel Lab Demo - S26V199

![](images/2025-11-19-17-08-47.png)

- ^VLANs and trunks already set up
- CD1 is spanning-tree root bridge primary
- CD2 is spanning-tree root bridge secondary

![](images/2025-11-19-17-12-51.png)

![](images/2025-11-19-17-13-05.png)

![](images/2025-11-19-17-13-24.png)

![](images/2025-11-19-17-14-33.png)

![](images/2025-11-19-17-15-04.png)

#### Create Portchannel (first LACP Config):

![](images/2025-11-19-17-15-59.png)

![](images/2025-11-19-17-16-21.png)

Settings:

![](images/2025-11-19-17-17-05.png)

Do it on other side:

- *grouped interfaces don't have to be the same number on each side 

![](images/2025-11-19-17-18-34.png)

![](images/2025-11-19-17-20-43.png)

![](images/2025-11-19-17-20-56.png)

#### Now do PAgP Portchannel config: (Acc3->CD2)

Create Portchannel on Acc3 and do settings:

![](images/2025-11-19-17-22-57.png)

![](images/2025-11-19-17-23-44.png)

Now do other side on CD2:

![](images/2025-11-19-17-24-59.png)

![](images/2025-11-19-17-25-20.png)

Check:

![](images/2025-11-19-17-25-31.png)

#### Now Do static portchannel on Acc4:

![](images/2025-11-19-17-26-33.png)

Now do other side on CD2:

![](images/2025-11-19-17-33-07.png)

![](images/2025-11-19-17-33-50.png)

![](images/2025-11-19-17-33-59.png)

### StackWise, VSS and vPC - S26V200

![](images/2025-11-19-17-35-31.png)

![](images/2025-11-19-17-36-35.png)

![](images/2025-11-19-17-37-36.png)

![](images/2025-11-19-17-38-04.png)

![](images/2025-11-19-17-38-27.png)

![](images/2025-11-19-17-38-48.png)

![](images/2025-11-19-17-39-09.png)

- ^CD1 & CD2 need to be advanced level switches that support talking to each other and having a `shared port channel` going downstream

![](images/2025-11-19-17-44-00.png)

![](images/2025-11-19-17-44-37.png)

- not expected to configure for CCNA -> higher levels like CCNP & data center

### Layer 3 EtherChannel - S26V201

![](images/2025-11-19-17-49-05.png)

- ^configuration is same only difference is that you use 'no switchport' to make it a layer 3 port 

![](images/2025-11-19-17-50-59.png)

- ^normally there would be Layer 2 links b/t Access Layer switches & Distribution Layer switches 
    - and Default Gateway for end hosts would be on Distribution Layer 
    - Would have Spanning-Tree running b/t Access & Distribution layer since they'd be Layer 2 links

Current Trend: Instead, put Layer 3 Links in Everywhere so you don't have to use Spanning-Tree:
    - Possible b/c Layer 3 switches have gotten cheaper

- **Now** you would have the Default Gateway at the Access Layer switches since there would be different subnets between the Access Layer and the Distribution Layer





