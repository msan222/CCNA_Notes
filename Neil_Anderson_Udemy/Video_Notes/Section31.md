## Section 31 - WAN - Wide Area Networks

### WAN Overview - S31V243

![](images/2025-11-25-13-38-36.png)

![](images/2025-11-25-13-41-19.png)

![](images/2025-11-25-13-42-02.png)

![](images/2025-11-25-13-42-41.png)

### VPN - Virtual Private Network - S31V244

![](images/2025-11-25-13-44-19.png)

![](images/2025-11-25-13-44-29.png)

![](images/2025-11-25-13-44-50.png)

![](images/2025-11-25-13-45-19.png)

![](images/2025-11-25-13-47-44.png)

![](images/2025-11-25-13-48-16.png)

![](images/2025-11-25-13-48-44.png)

![](images/2025-11-25-13-49-27.png)

![](images/2025-11-25-13-50-17.png)

![](images/2025-11-25-13-52-38.png)

![](images/2025-11-25-15-03-06.png)

- `Cisco Group Encrypted Transport VPN`(GET VPN) is a set of features that are necessary to secure IP multicast group traffic or unicast traffic over a private WAN that originates on or flows through a Cisco IOS device. 
    - GET VPN combines the keying protocol **Group Domain of Interpretation (GDOI)** with **IP security (IPsec) encryption** to provide users with an efficient method to secure IP multicast traffic or unicast traffic.
    - GET VPN enables the router to apply encryption to *nontunneled* (that is, “native”) IP multicast and unicast packets and `eliminates the requirement to configure tunnels to protect multicast and unicast traffic`.

### WAN Connectivity Options - S31V245

![](images/2025-11-25-13-55-33.png)

![](images/2025-11-25-13-56-09.png)

- `Multiprotocol label switching (MPLS)` is a technique for setting up long-range network connections
    - MPLS, on the other hand, sends packets along predetermined network paths. (instead of sending packets along each router)
    - Routers do not have to decide where to forward each packet, and packets take the same path every time. 

![](images/2025-11-25-13-57-19.png)

![](images/2025-11-25-13-57-56.png)

![](images/2025-11-25-13-59-15.png)

- `backhaul connections`: Connections b/t service provider's main locations. Internal Internet Service Provider, require a lot of bandwidth. 

![](images/2025-11-25-14-01-09.png)

![](images/2025-11-25-14-02-12.png)

![](images/2025-11-25-14-02-58.png)

![](images/2025-11-25-14-04-03.png)

![](images/2025-11-25-14-05-09.png)

![](images/2025-11-25-14-06-18.png)

![](images/2025-11-25-14-07-54.png)

### Leased Lines - S31V246

![](images/2025-11-25-14-29-34.png)

![](images/2025-11-25-14-30-31.png)

![](images/2025-11-25-14-31-16.png)

![](images/2025-11-25-14-31-40.png)

![](images/2025-11-25-14-32-09.png)

![](images/2025-11-25-14-32-47.png)

![](images/2025-11-25-14-33-26.png)

![](images/2025-11-25-14-35-27.png)

![](images/2025-11-25-14-36-25.png)

**Don't need for CCNA:

![](images/2025-11-25-14-37-09.png)

![](images/2025-11-25-14-38-35.png)

![](images/2025-11-25-14-39-02.png)

![](images/2025-11-25-14-39-29.png)

### MPLS Multi Protocol Label Switching - S31V247

![](images/2025-11-25-15-15-59.png)

- So this is a VPN service because it's traffic from multiple customers using the same shared underlying infrastructure.
    - the customers are kept strictly separate from each other so it is a virtual private network.

- A VPN going over the internet could be passing through multiple service providers, so it's impossible to get a single unified SLA for the end to end traffic.
    - But when you're using an MPLS VPN, it's going to be with one service provider that owns the MPLS network.
- So that service provider can give you guarantees for the uptime, for the delay and the loss.

![](images/2025-11-25-15-20-21.png)

![](images/2025-11-25-15-20-32.png)

![](images/2025-11-25-15-22-29.png)

- this is a *VPN technology* because we've got multiple customers going over that same shared network and it's *Layer 3* because each site is in a different IP subnet.

![](images/2025-11-25-15-28-55.png)

![](images/2025-11-25-15-29-45.png)

![](images/2025-11-25-15-33-19.png)

- **Configure CS routers you just configure them as if the PE is another normal customer router

![](images/2025-11-25-15-41-00.png)

![](images/2025-11-25-15-49-44.png)

![](images/2025-11-25-15-50-30.png)

![](images/2025-11-25-15-55-22.png)

![](images/2025-11-25-15-55-38.png)

![](images/2025-11-25-15-56-35.png)

- VPWS only gets 2 sites, VPLS gets more than 2

### PPPoE Point to Point Protocol over Ethernet - S31V248

![](images/2025-11-25-15-59-32.png)

![](images/2025-11-25-16-01-03.png)

![](images/2025-11-25-16-01-40.png)

![](images/2025-11-25-16-02-03.png)

![](images/2025-11-25-16-02-35.png)

### WAN Topology Options - S31V249

![](images/2025-11-25-16-10-12.png)

![](images/2025-11-25-16-14-38.png)

![](images/2025-11-25-16-15-55.png)

![](images/2025-11-25-16-16-08.png)

![](images/2025-11-25-16-16-53.png)

![](images/2025-11-25-16-18-58.png)

![](images/2025-11-25-16-19-38.png)

![](images/2025-11-25-16-19-58.png)

