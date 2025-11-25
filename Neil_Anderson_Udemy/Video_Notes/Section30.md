## Section 30 - IPv6 Addressing and Routing

### Why We Need IPv6 S30V231

![](images/2025-11-24-13-20-52.png)

![](images/2025-11-24-13-22-43.png)

![](images/2025-11-24-13-25-20.png)

![](images/2025-11-24-13-25-38.png)

![](images/2025-11-24-13-26-10.png)

![](images/2025-11-24-13-27-00.png)

![](images/2025-11-24-13-27-20.png)

![](images/2025-11-24-13-27-37.png)

![](images/2025-11-24-13-28-03.png)

![](images/2025-11-24-13-28-34.png)

![](images/2025-11-24-13-29-03.png)

- Because the information was included in the higher level traffic within our voice protocols, the phones don't know to use a public IP address. They're told to use that private IP address. There's no connectivity, so the call fails.

![](images/2025-11-24-13-32-57.png)

![](images/2025-11-24-13-35-36.png)

![](images/2025-11-24-13-35-51.png)

### The IPv6 Address Format - S30V232

![](images/2025-11-24-13-37-48.png)

![](images/2025-11-24-13-39-41.png)

![](images/2025-11-24-13-42-17.png)

![](images/2025-11-24-13-43-32.png)

![](images/2025-11-24-13-45-30.png)

### IPv6 Global Unicast Address - S30V233

![](images/2025-11-24-13-53-35.png)

![](images/2025-11-24-13-56-07.png)

![](images/2025-11-24-13-56-36.png)

![](images/2025-11-24-13-57-44.png)

![](images/2025-11-24-14-01-06.png)

![](images/2025-11-24-14-01-43.png)

![](images/2025-11-24-14-07-32.png)

![](images/2025-11-24-14-08-20.png)

![](images/2025-11-24-14-10-25.png)

### IPv6 Global Unicast Addresses Lab Demo - S30V234

![](images/2025-11-24-14-12-38.png)

![](images/2025-11-24-14-15-24.png)

![](images/2025-11-24-14-17-19.png)

![](images/2025-11-24-14-17-30.png)

Configure F2/0 First:

![](images/2025-11-24-14-19-15.png)

Now do F0/0:

![](images/2025-11-24-14-19-45.png)

Verify:

![](images/2025-11-24-14-19-55.png)

Now do R2:

![](images/2025-11-24-14-21-26.png)

![](images/2025-11-24-14-21-41.png)

Check Connectivity:

![](images/2025-11-24-14-22-22.png)

### EUI-64 Addresses - S30V235

![](images/2025-11-24-14-23-33.png)

![](images/2025-11-24-14-24-36.png)

![](images/2025-11-24-14-25-41.png)

![](images/2025-11-24-14-26-21.png)

![](images/2025-11-24-14-31-58.png)

![](images/2025-11-24-14-32-37.png)

- You don't want your routers to have random IP addresses which is what's going to happen if you use the EUI-64 addresses.

- EUI-64 is good for end hosts since you don't want to have to configure addresses for every single one 
    - Can use DHCP to do this (like for IPv4) or feature called `SLAAC` that automatically generates the address on the interface

Configure EUI-64 on interfaces b/t R2 and R3 - F1/0 on R2 and F1/9 on R3

![](images/2025-11-24-14-37-55.png)

![](images/2025-11-24-14-38-48.png)
![](images/2025-11-24-14-39-13.png)

Verify:

![](images/2025-11-24-14-39-24.png)

![](images/2025-11-24-14-39-52.png)

- Then you'd do it on R3 too

### Unique Local and Link Local Addresses - S30V236

![](images/2025-11-24-14-41-44.png)

![](images/2025-11-24-14-42-32.png)

![](images/2025-11-24-14-43-11.png)

![](images/2025-11-24-14-45-16.png)

![](images/2025-11-24-14-45-36.png)

![](images/2025-11-24-14-46-02.png)

![](images/2025-11-24-14-46-12.png)

![](images/2025-11-24-14-46-46.png)

- Link local not on F1/0 and F3/0 b/c IPv6 is not enabled on those interfaces yet

![](images/2025-11-24-14-48-25.png)

- ^how to manually configure link-local address and override EU-64

![](images/2025-11-24-14-49-23.png)

- ^latest IPv4 address will overwrite the ones before it
- 'secondary' keyword will allow for more then one IPv4 address on a router (uses primary) (Not common, max 2 addresses)

Can have multiple IPv6 addresses on an interface:

![](images/2025-11-24-14-52-26.png)

- ^dual-stack router

![](images/2025-11-24-14-53-48.png)


### Link Local Addresses Lab Demo - S30V237

![](images/2025-11-24-14-54-59.png)

- ^network already has IPv4, we're going to make it dual-stack by adding IPv6. Someone else is doing R2 and R3 so we just need to do R1.

![](images/2025-11-24-14-56-26.png)

![](images/2025-11-24-14-56-33.png)

![](images/2025-11-24-14-56-55.png)

![](images/2025-11-24-15-03-34.png)

![](images/2025-11-24-15-03-48.png)

![](images/2025-11-24-15-04-01.png)

![](images/2025-11-24-15-04-09.png)

- ^interfaces were automatically given EUI-64 addresses

Put in manual link local addresses instead:

![](images/2025-11-24-15-07-32.png)

![](images/2025-11-24-15-07-46.png)

Verify:


![](images/2025-11-24-15-09-03.png)

![](images/2025-11-24-15-09-16.png)

- ^asks which one since it's on both interfaces

![](images/2025-11-24-15-10-01.png)

- ![](images/2025-11-24-15-10-29.png)

- ^Doesn't work b/c it's a link local address (only valid on its own link)

### SLAAC Stateless Address Auto Configuration - S30V238

![](images/2025-11-24-15-11-48.png)

![](images/2025-11-24-15-12-52.png)

![](images/2025-11-24-15-14-12.png)

- ^how the hosts can learn what the network portion is on that link, and they can use that to generate their full 128-bit IPv6 address

![](images/2025-11-24-15-15-52.png)

![](images/2025-11-24-15-16-19.png)

- when SLAAC was designed, there's no mechanism for giving out other information other than the router address.
    - PC cannot learn DNS server from SLAAC

![](images/2025-11-24-15-21-37.png)

![](images/2025-11-24-15-22-09.png)

![](images/2025-11-24-15-23-05.png)

![](images/2025-11-24-15-23-37.png)

![](images/2025-11-24-15-23-51.png)

- ^haven't generated traffic to Global Unicast Addresses yet
    - So discovers Link Local Addresses and uses them as the source
    - won't discover Global Unicast until traffic is sent

![](images/2025-11-24-15-25-20.png)

### IPv6 Static Routes - S30V239

![](images/2025-11-24-15-26-18.png)

![](images/2025-11-24-15-27-23.png)

![](images/2025-11-24-15-27-30.png)

![](images/2025-11-24-15-31-03.png)

![](images/2025-11-24-15-31-15.png)

- ^I can see the connected route is 10.10.0.0/24. And the matching local route is 10.10.0.1/32. So I know that the IP address in the interface is 10.10.0.1/24.

![](images/2025-11-24-15-33-19.png)

![](images/2025-11-24-15-34-07.png)

![](images/2025-11-24-15-35-29.png)

![](images/2025-11-24-15-35-54.png)

![](images/2025-11-24-15-36-20.png)

![](images/2025-11-24-15-37-44.png)

![](images/2025-11-24-15-38-38.png)

![](images/2025-11-24-15-39-19.png)

![](images/2025-11-24-15-39-37.png)

![](images/2025-11-24-15-40-00.png)

![](images/2025-11-24-15-42-24.png)

### IPv6 Static Routes Lab Demo - S30V240

![](images/2025-11-24-15-44-57.png)

- ^Dual-stack network. IPv4 has already been completely configured, using EIGRP for routing.
- IPv6 addresses have been set but no routing configured yet

![](images/2025-11-24-15-46-00.png)

![](images/2025-11-24-15-46-17.png)

![](images/2025-11-24-15-46-24.png)

![](images/2025-11-24-15-46-32.png)

![](images/2025-11-24-15-46-40.png)

![](images/2025-11-24-15-48-10.png)

![](images/2025-11-24-15-48-17.png)

- R1 is PC1's default gateway, IPv6 facing PC1 is 2001:DB0:0:0::/64

![](images/2025-11-24-15-49-13.png)

![](images/2025-11-24-15-49-52.png)

- ^default static route for default gateway

![](images/2025-11-24-15-50-27.png)

Configure R1:

Verify Connected Routes - 

![](images/2025-11-24-15-52-39.png)

Configure static Routes:

![](images/2025-11-24-15-53-26.png)

![](images/2025-11-24-15-53-40.png)

Now do R2: 

![](images/2025-11-24-15-55-20.png)

Now R3:

![](images/2025-11-24-15-56-24.png)

Now PC2:

Add default gateway address:

![](images/2025-11-24-15-57-11.png)

NO CONNECTIVITY - What's wrong?:

Troubleshoot from PC1:

![](images/2025-11-24-15-58-29.png)

^it's not getting anywhere

![](images/2025-11-24-15-59-07.png)

Ping R1:

![](images/2025-11-24-15-59-32.png)

Ping R2:

![](images/2025-11-24-15-59-45.png)

So, all IPv6 addresses are configured, all static routes are configured, but PC1 can't ping PC2 - Why? 

What's Missing:

![](images/2025-11-24-16-01-57.png)

ANSWER: IPv6 routing isn't enabled on the routers!!
    - need `ipv6 unicast-routing` in global config

![](images/2025-11-24-16-03-12.png)

- ^do on all routers



