## Section 37 - Wireless Networking Fundamentals

### Wireless Network Types - S37V297

![](images/2025-12-02-13-20-17.png)

![](images/2025-12-02-13-26-12.png)

![](images/2025-12-02-13-29-06.png)

![](images/2025-12-02-13-29-53.png)

![](images/2025-12-02-13-30-26.png)

![](images/2025-12-02-13-31-24.png)

![](images/2025-12-02-13-31-51.png)

![](images/2025-12-02-13-32-18.png)

![](images/2025-12-02-13-34-15.png)

Wifi Direct:
    - is an extension of infrastructure mode
    - is a WPAN (Wireless Personal Area Network)

![](images/2025-12-02-13-36-08.png)

![](images/2025-12-02-13-37-04.png)

![](images/2025-12-02-13-38-00.png)

### Infrastructure Mode and Wireless Access Points - S37V298

![](images/2025-12-02-13-39-41.png)

- If your devices are communicating through a wireless access point they are in *infrastructure mode*

![](images/2025-12-02-13-40-25.png)

![](images/2025-12-02-13-40-50.png)

IBSS = no wireless access point BSS = with WAP

![](images/2025-12-02-13-43-35.png)

![](images/2025-12-02-13-44-08.png)

![](images/2025-12-02-13-44-16.png)

![](images/2025-12-02-13-44-30.png)

![](images/2025-12-02-13-44-57.png)

![](images/2025-12-02-13-46-05.png)

![](images/2025-12-02-13-46-50.png)

![](images/2025-12-02-13-49-33.png)

### Wireless LAN Controllers and CAPWAP - S37V299

![](images/2025-12-02-13-52-08.png)

![](images/2025-12-02-13-52-45.png)

![](images/2025-12-02-13-52-56.png)

![](images/2025-12-02-13-54-18.png)

![](images/2025-12-02-13-55-18.png)

![](images/2025-12-02-14-00-15.png)

![](images/2025-12-02-14-02-03.png)

- should have authentication on each AP so service will be dropped during roaming when you have to re-authenticate to the new AP
- BUT if you use a WLC it can avoid that since the auth will just go thru that

![](images/2025-12-02-14-04-13.png)

![](images/2025-12-02-14-05-31.png)

![](images/2025-12-02-14-06-48.png)

![](images/2025-12-02-14-08-04.png)

![](images/2025-12-02-14-09-13.png)

![](images/2025-12-02-14-10-34.png)

![](images/2025-12-02-14-11-13.png)

![](images/2025-12-02-14-11-51.png)

![](images/2025-12-02-14-12-06.png)

![](images/2025-12-02-14-14-14.png)

### Switch Configuration for Wireless Networks - S37V300

![](images/2025-12-02-14-16-54.png)

![](images/2025-12-02-14-17-21.png)

![](images/2025-12-02-14-17-33.png)

![](images/2025-12-02-14-17-49.png)

![](images/2025-12-02-14-18-13.png)

![](images/2025-12-02-14-18-21.png)

![](images/2025-12-02-14-19-08.png)

![](images/2025-12-02-14-19-43.png)

![](images/2025-12-02-14-20-31.png)

![](images/2025-12-02-14-22-10.png)

![](images/2025-12-02-14-23-31.png)

![](images/2025-12-02-14-23-42.png)

- Now the WLC is doing all the tagging - SO link b/t the switch and the WLC needs to be a trunk but NOT the WAP to the WLC 

![](images/2025-12-02-14-25-00.png)

![](images/2025-12-02-14-26-21.png)

![](images/2025-12-02-14-27-36.png)

![](images/2025-12-02-14-28-05.png)

![](images/2025-12-02-14-28-28.png)

![](images/2025-12-02-14-31-12.png)

![](images/2025-12-02-14-31-41.png)

### Wireless Channels and Radio Frequencies - S37V301

![](images/2025-12-02-14-33-10.png)

![](images/2025-12-02-14-34-17.png)

![](images/2025-12-02-14-38-32.png)

![](images/2025-12-02-14-41-27.png)

![](images/2025-12-02-14-42-30.png)

![](images/2025-12-02-14-42-56.png)

![](images/2025-12-02-14-44-31.png)

- ^if you have neighboring APs you wan to use non-overlapping channels to avoid interference w/ each other

![](images/2025-12-02-14-45-30.png)

![](images/2025-12-02-14-46-42.png)

![](images/2025-12-02-14-47-00.png)

![](images/2025-12-02-14-47-33.png)

![](images/2025-12-02-14-49-12.png)

![](images/2025-12-02-14-50-26.png)

### Wireless Security - S37V302

![](images/2025-12-02-14-52-52.png)

![](images/2025-12-02-14-53-44.png)

WPA - Wifi Protected Access 

![](images/2025-12-02-14-56-52.png)

![](images/2025-12-02-14-59-08.png)

- ^WPA Enterprise gives more granularity 

### Switch Configuration for Wireless - Lab Demo - S37V303

- Configure a switch to support wireless networks with a WLC

![](images/2025-12-02-15-01-45.png)

- will configure Guest & Corporate WLANs
    - Need VLANs for both 
    - also create a management VLAN for wireless traffic (also when WLC is communication w/ APs)

- WLC1-Switch = trunk port
- APs-Switch = Access ports in management VLAN

![](images/2025-12-02-15-05-10.png)

#### Create VLANs

Create Management VLAN:

- Create Management VLAN 10
- Also create a SVI in VLAN 10 w/ its own ip - b/c the multi-layer switch is going to be the default gateway for all the different VLANs and ip Subnet (routing traffic b/t them)

![](images/2025-12-02-15-07-13.png)
![](images/2025-12-02-15-07-30.png)

APs and management IP address for WLC are going to be in VLAN 10 & subnet
    - So APs can connect to WLC and download configs

For the APs to get connectivity to the WLC we need to configure a DHCP scope - could do an external server but we will do it on the switch

Subnet is 192.168.10.0/24
- Already using 192.168.10.1 for SVI 
- We will allocate .101-.254 for DHCP (exclude .1-.100)
- Name it management
- add in default gateway

![](images/2025-12-02-15-22-06.png)

- We need to tell the APs where their WLC is:

![](images/2025-12-02-15-28-18.png)
![](images/2025-12-02-15-27-58.png)

- B/c the APs and WLC are in the same VLAN and subnet we didn't *need* to tell them where since the APs could have found the WLC through broadcast traffic
    - if they were on a different subnet you definitely need to add the option 43 to the DHCP scope 

Create VLANs for Wireless Networks: 

- 1 for corporate (VLAN 22) 1 for guest (VLAN 23)
    - create an interface for it since the switch is the default gateway, and give it an ip address

![](images/2025-12-02-16-12-59.png)

- Need a DHCP scope for wireless clients that will connect to VLAN 22 - do it on WLC instead of switch

Create VLAN for Guest (23)

![](images/2025-12-02-16-17-08.png)

check VLANs:

![](images/2025-12-02-16-17-42.png)

Check VLAN interfaces:

![](images/2025-12-02-16-17-58.png)

- no switchports on the VLANs yet which is why they aren't up yet

#### Configure Switchports

Configure: switchport to WLC as trunk, connections to APs as Access ports

Configure One to WLC:

- *We know we'll never have a spanning-tree loop since the connection to the wireless LAN controller is not doubling back into other switches again. 
    - enable portfast to disable spanning-tree on this port

![](images/2025-12-02-16-23-21.png)

Configure Connections to APs:

![](images/2025-12-02-16-24-43.png)

### Wireless Network Configuration - Lab Demo - S37V304

Now configure all wireless network setting on the WLC

![](images/2025-12-02-16-36-42.png)

- WLANs for Corporate & Guest
    - Corporate they need a username/password which will be authenticated by the Radius Server using 802.1x -WPA Enterprise
    - Guests just enter a pre-shared key - WPA Personal

![](images/2025-12-02-16-40-15.png)

- WLC is already set up w/ admin laptop

![](images/2025-12-02-16-40-52.png)

1. COnfigure integration w/ Radius Server

![](images/2025-12-02-16-41-18.png)

![](images/2025-12-02-16-42-23.png)

- ^WLC has already been added to Radius Server

Add Radius to WLC:

![](images/2025-12-02-16-43-46.png)

![](images/2025-12-02-16-44-00.png)

![](images/2025-12-02-16-44-15.png)

Configure DHCP scope for Guest/Corporate WLANs on WLC:

![](images/2025-12-02-16-45-56.png)

![](images/2025-12-02-16-46-23.png)

![](images/2025-12-02-16-46-41.png)

![](images/2025-12-02-16-46-52.png)

![](images/2025-12-02-16-47-37.png)

- ^put DNS irl

Now it will give out addresses to devices on the Corporate VLAN

![](images/2025-12-02-16-48-34.png)

![](images/2025-12-02-16-48-58.png)

Now will give out addresses to devices on Guest VLAN

Configure Virtual Interfaces on WLC (one for each WLAN):

- once they are configured need to associate them w/ the correct physical port connected to the switch

![](images/2025-12-02-16-51-09.png)

- ^port 1

- **irl use LAG/Etherchannel to bundle multiple ports to get additional bandwidth

![](images/2025-12-02-16-52-11.png)

![](images/2025-12-02-16-52-28.png)

![](images/2025-12-02-16-55-14.png)

- When you configure a multi-layer switch, you're going to have your VLAN interfaces on there if it's acting as the default gateway.
    - On those VLAN interfaces, you're going to have the DHCP address so that the clients can get to the DHCP server.

Essentially the same thing here:

- When the wireless clients connect to the WLAN, they need to get access to their DHCP server.

- So we configured the logical interface here:
    - give it an IP address
    - specify the address of the DHCP server.

Now Make a new Interface for Guest:

![](images/2025-12-02-17-02-47.png)

![](images/2025-12-02-17-04-19.png)

Now we can configure out WLANs:

Corporate:

![](images/2025-12-02-17-05-23.png)

![](images/2025-12-02-17-05-55.png)

![](images/2025-12-02-17-07-39.png)

*^remember to configure security before enabling the WLAN

![](images/2025-12-02-17-09-05.png)

![](images/2025-12-02-17-09-41.png)

![](images/2025-12-02-17-10-10.png)

![](images/2025-12-02-17-10-25.png)

Guest:

![](images/2025-12-02-17-10-53.png)

![](images/2025-12-02-17-11-05.png)

![](images/2025-12-02-17-11-28.png)

![](images/2025-12-02-17-12-31.png)

![](images/2025-12-02-17-12-50.png)

Now Check everything:

![](images/2025-12-02-17-13-11.png)

![](images/2025-12-02-17-14-25.png)

![](images/2025-12-02-17-15-31.png)

![](images/2025-12-02-17-16-03.png)

![](images/2025-12-02-17-16-26.png)




 

















