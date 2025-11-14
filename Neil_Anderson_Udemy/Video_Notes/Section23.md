## Section 23 - DHCP - Dynamic Host Configuration Protocol

### DCHP Dynamic Host Configuration Protocol - S23V164

![](images/2025-11-13-14-06-24.png)

![](images/2025-11-13-14-14-43.png)

![](images/2025-11-13-14-15-23.png)

![](images/2025-11-13-14-18-15.png)

![](images/2025-11-13-14-18-39.png)

![](images/2025-11-13-14-19-48.png)

### Cisco DHCP Server - S23V165

![](images/2025-11-13-14-24-23.png)

![](images/2025-11-13-14-47-02.png)

![](images/2025-11-13-14-52-54.png)

- ^good to exclude addresses first before configuring the DHCP scope so clients won't be assigned them

![](images/2025-11-13-14-59-47.png)

![](images/2025-11-13-15-00-54.png)

#### Lab Demo

Configure DHCP Server on R1:

![](images/2025-11-13-15-03-23.png)

Verify:

![](images/2025-11-13-15-03-43.png)
![](images/2025-11-13-15-03-53.png)

### External DHCP Server - S23V166

![](images/2025-11-13-15-06-46.png)

![](images/2025-11-13-15-09-25.png)

- Issue here is that Routers by default don't forward broadcast traffic so how does it even reach the DHCP server?

Fix:

![](images/2025-11-13-15-10-16.png)

- ^configure this on the router on the interface that will receive the DHCP request

#### Lab Demo 

![](images/2025-11-13-15-12-08.png)

![](images/2025-11-13-15-12-29.png)

![](images/2025-11-13-15-12-44.png)

- ^DHCP server is set up 

PC1 is set up as a DHCP Client:

![](images/2025-11-13-15-14-00.png)

Fix this on router:

![](images/2025-11-13-15-15-54.png)

All good now:

![](images/2025-11-13-15-28-22.png)

### Windows, MAC, and Linux Client IP Settings - S23V167

#### Configure and Verify IP Settings 

##### Windows

file explorer> right click Network> Properties> Change adapter settings> Can see all network cards

Configure Ethernet 1 Card:

![](images/2025-11-13-15-32-30.png)

![](images/2025-11-13-15-32-54.png)

Default to DHCP (desktop clients always do):

![](images/2025-11-13-15-33-09.png)

- to see ip address in windows: `cmd -> ipconfig /all`
    - shows you MAC address on network cards and the ip address of your DHCP server

##### Mac

- Apple icon> system preferences> network> 

![](images/2025-11-13-15-37-38.png)

- check in cmd: `Terminal> ifconfig` 
    - `netstat -rn` - network stat, 'r' for routes and 'n' for numerical
        - Shows us default gateway

![](images/2025-11-13-15-40-01.png)

##### Linux

GUI:

Show Application (bottom left)> settings> network> click settings on desired NIC card

![](images/2025-11-13-15-42-15.png)

CMD:

`terminal> ifconfig` - on older

`ip address show` - new command 

`ip route show` - see default gateway

![](images/2025-11-13-15-43-25.png)

### Cisco DHCP Client - S23V168

![](images/2025-11-13-15-44-18.png)

![](images/2025-11-13-15-50-20.png)

![](images/2025-11-13-15-51-30.png)

Lab Demo:

![](images/2025-11-13-15-55-37.png)

- ^ISP is already configured as DHCP server
- Time to configure R1 as the DHCP client

![](images/2025-11-13-15-56-48.png)

We know it worked:

![](images/2025-11-13-15-57-58.png)

![](images/2025-11-13-15-58-05.png)

![](images/2025-11-13-15-58-15.png)























