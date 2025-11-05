## Section 13 - The Cisco Troubleshooting Methodology

### The Cisco Troubleshooting Methodology - S13V76
![alt text](images/image-231.png)

![alt text](images/image-232.png)

![alt text](images/image-233.png)

![alt text](images/image-234.png)

### Cisco Troubleshooting Method - Lab Example S13V77

![alt text](images/image-235.png)

- User on PC behind R1 router complains DNS isn't working
- DNS Server is on R3 router

1. Check the actual problem to make sure it's not a user error

![alt text](images/image-236.png)

![alt text](images/image-237.png)

- it isn't reachable

2. Do a traceroute

![alt text](images/image-238.png)
![alt text](images/image-239.png)

- problem seems to be at R2 so lets look over there now

3. Go onto R2 and try to ping R3

![alt text](images/image-240.png)

4. Check R3 routing table 

![alt text](images/image-241.png)

- no route to 10.10.30.1 

5. Add route to 10.10.30.0

![alt text](images/image-242.png)

6. Try to ping again, ping works

![alt text](images/image-243.png)

![alt text](images/image-244.png)

- ping & traceroute help with Layer 3 (Network) issues
- telnet helps with Layer 4 (Transport) issues

![alt text](images/image-245.png)

- Tells us if DNS (port 53) is running on R3
    - if it wasn't open it would mean that the service isn't running at that destination

![alt text](images/image-246.png)


## Section 14 - Cisco Router and Switch Basics

### Basic Router and Switch Configuration S14V80

- `**Connected Routes`: automatically created when IP address is assigned to an interface & represent the subnet the interface is connected to. 
- `**Local Routes`: represent the ip address of the interface itself and the mask is `always /32`
    - Since a Local Route identifies only that specific interface, the Subnet Mask, too, identifies only that specific interface's IP address. 
    - Therefore, it gets as specific as it can in identifying that interface with a /32 Subnet Mask.
    - **Example**
        - You've got a router with 2 interfaces: 
            - Gi0/0 with an IP address of 192.0.2.1/24 - Gi0/1 with an IP address of 198.51.100.254/24 
        - Exactly what will happen when:
            - Router receives a packet on *Gi0/0* destined for *198.51.100.1*?
            - Router receives a packet on *Gi0/0* destined for *198.51.100.254*?
        - Answer: 
            - Router will use connected route to forward *out of* Gi0/1 as the destination is in that subnet
            - Router will use local route to *process the packet itself* as the destination is the ip interface's address
    - **Analogy**
        - If you were at a shipyard, and each pier had a ship that goes to a unique country, the **Local Route would tell you which pier you're boarding at**, and the **Connected Route would tell you which country it's going to.**
        - The Local Route's Subnet is /32 because that interface is on your local device. 
            - Devices use Subnet masks to distinguish the network address from the host address - - When it comes to choosing a Route, it wants to use the most specific route it can.

![alt text](images/image-247.png)

![alt text](images/image-248.png)

![alt text](images/image-249.png)

![alt text](images/image-250.png)

- ^Configure router

![alt text](images/image-251.png)

- ^Configure switch

![alt text](images/image-252.png)

- ping router to check connection

![alt text](images/image-253.png)

- Configure switch gateway so you can get to other subnets as well

![alt text](images/image-254.png)

![alt text](images/image-255.png)

![alt text](images/image-257.png)

![alt text](images/image-256.png)

### The Setup Wizard S14V81

#### Same lab as last lesson

![alt text](images/image-258.png)

When booted up:

![alt text](images/image-259.png)

- Or do this to set up
    - it's going to put a hostname and configure an IP address for management
    - People normally just do it manually like we did before

![alt text](images/image-260.png)

![alt text](images/image-261.png)

![alt text](images/image-262.png)
![alt text](images/image-263.png)

![alt text](images/image-264.png)

![alt text](images/image-265.png)

- now do it to switch

![alt text](images/image-266.png)

![alt text](images/image-267.png)

- check by pinging router

![alt text](images/image-268.png)

- note that it didn't prompt for default gateway so can't get to other subnets yet

![alt text](images/image-269.png)

### Speed and Duplex Settings S14V82

![alt text](images/image-270.png)

- ^Either speed/duplex auto or manual but have to do both on both sides
    - if not will cause performance issues on link

![alt text](images/image-271.png)

![alt text](images/image-272.png)

![alt text](images/image-273.png)

![alt text](images/image-274.png)

![alt text](images/image-275.png)

![alt text](images/image-276.png)

![alt text](images/image-277.png)

![alt text](images/image-278.png)

- ^ shows entire running configuration on switch

![alt text](images/image-279.png)

- ^ Just see one part of the configuration

![alt text](images/image-280.png)

- ^ look at a specific interface (shows if traffic is passing thru and errors)

![alt text](images/image-281.png)

### CDP and LLDP S14V83

- CDP - Cisco Discovery Protocol

![alt text](images/image-282.png)

![alt text](images/image-283.png)

- cdp enabled by default. can turn it off since it can be a security concern (like in a bank, don't want ppl to see what devices are plugged in)
    - Can disable it on just single interfaces (like doing it for internal ones but not for external ones)
- neighbors will show attached devices

![alt text](images/image-284.png)

- port ID is the device that is plugged in 

![alt text](images/image-285.png)

![alt text](images/image-286.png)

- ^ disable an interface

![alt text](images/image-287.png)

- disable on entire interface

- LLDP - Link Layer Discovery Protocol

![alt text](images/image-288.png)

![alt text](images/image-289.png)

- ^ disable transmit and receive separately 

### Basic Layer 1 and 2 Troubleshooting S14V84

![alt text](images/image-290.png)

![alt text](images/image-291.png)

![alt text](images/image-292.png)

![alt text](images/image-293.png)

- ^issue with FastEthernet 0/2 and 0/3
    - 0/2 is down/down likely a layer 2 prob
    - 0/3 is up/down likely a configuration mismatch 

![alt text](images/image-294.png)

![alt text](images/image-295.png)

![alt text](images/image-296.png)

![alt text](images/image-297.png)

![alt text](images/image-298.png)

### Basic L1 and L2 Troubleshooting - Lab Demo S14V85

- SW1 is connected to R1. 
    - On the SW1's side, it's on interface fastEthernet0/1.
    - On R1 it's interface fastEthernet0/0.

![alt text](images/image-299.png)

- description is there but everything else is default

![alt text](images/image-300.png)

- ^VLAN1 interface is configured w/ ip addy 192.168.0.10 and FastEthernet0/1 is up/up

![alt text](images/image-301.png)

- ^ ping is good 

![alt text](images/image-302.png)

![alt text](images/image-303.png)

- ^is good

Messing it up on purpose:

![alt text](images/image-304.png)
![alt text](images/image-305.png)

![alt text](images/image-306.png)

- ^Go back to switch and check, interface FastEthernet0/0 is down/down because it was shutdown on the other side (our router)
    - down/down normally means layer 1 issue (cable issue, interface is shut down)

Show interface stats:

![alt text](images/image-307.png)

![alt text](images/image-308.png)

![alt text](images/image-309.png)

Go back to SW1 mess it up on purpose by setting mismatched speeds:

![alt text](images/image-310.png)

Set speed on R1 to 100:

![alt text](images/image-311.png)

Interface is down/down b/c we made a speed mismatch:

![alt text](images/image-312.png)

![alt text](images/image-313.png)

- ^turn it back on to show the mismatch error

![alt text](images/image-314.png)

- up/down

![alt text](images/image-315.png)

- down/down on the switch, mismatch brought it completely down

- fix it by setting speeds correctly

Change the duplex to mismatch to generate error:

![alt text](images/image-316.png)
![alt text](images/image-317.png)

CPD warns you abt the mismatch:

![alt text](images/image-318.png)

- **only warns you if you're directly connected by console cable, not Telnet
    - can view it if you do a 'show log'

![alt text](images/image-319.png)

- speed mismatch will bring interface down by duplex mismatch will leave it up 
    - performance will be super bad tho bc you'll get lots of collisions
    