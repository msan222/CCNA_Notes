## Section 27 - Switch Security **CCNA - port security config & workings is important - just need to know others in theory**

### DHCP Routing - S27V204

![](images/2025-11-20-16-06-43.png)

![](images/2025-11-20-16-07-08.png)

- Remember - if DHCP Clients aren't on same subnet as DHCP server need to configure helper address on router
    - DHCP requests are broadcast traffic

Problem: Rogue DHCP Server 

![](images/2025-11-20-16-09-18.png)

- ^b/c rogue server's default gateway is 10.10.10.254 (same as DNS server) PCs will have an invalid default gateway and can't connect to the network

How to prevent this: `DHCP Snooping`
    - enabled on access layer switches
    - configure ports DHCP server is connected to as 'trusted ports' 

![](images/2025-11-20-16-12-42.png)

### DAI Dynamic ARP Inspection - S27V205

Review ARP - Address Resolution Protocol

![](images/2025-11-20-16-15-28.png)

![](images/2025-11-20-16-15-38.png)

![](images/2025-11-20-16-15-55.png)

![](images/2025-11-20-16-16-20.png)

![](images/2025-11-20-16-16-42.png)

![](images/2025-11-20-16-19-44.png)

- ^is normally a malicious attack 
    - in same ip subnet, sends out a 'gratuitous ARP' 
    - spoofing the router's ip address & PC's ip 

![](images/2025-11-20-16-20-28.png)

![](images/2025-11-20-16-20-58.png)

![](images/2025-11-20-16-21-15.png)

![](images/2025-11-20-16-21-23.png)

![](images/2025-11-20-16-21-42.png)

- Can also use this do DDOS and just drop the traffic 
- Hackers use tool called 'Cain and Abel'

How we stop this: Dynamic ARP Inspection

![](images/2025-11-20-16-27-09.png)


![](images/2025-11-20-16-28-48.png)

### 802.1X Identify Based Networking - S27V206

![](images/2025-11-20-16-34-00.png)

- Authentication is username and password

![](images/2025-11-20-16-34-38.png)

- all modern OS support being an 802.1X supplicant

- The authentication server is typically also integrated itself with an Active Directory domain controller, which is where your user database is. 

- Once the username and password has been authenticated, it's a valid username and password that can be mapped to a VLAN as well.
   
    - The authentication server can send that information down to the authenticator switch 
    - Will then update the port that the client is plugged into with the correct VLAN. 
    - At that point, it acts just like a normal switch port in the correct VLAN, and the user get their normal access to the network.

### Preventing Unauthorized Devices with Port Security - S27V207

![](images/2025-11-20-16-40-39.png)

![](images/2025-11-20-16-41-09.png)

![](images/2025-11-20-16-42-14.png)

![](images/2025-11-20-16-42-22.png)

![](images/2025-11-20-16-43-56.png)

![](images/2025-11-20-16-45-48.png)

Configure at interface level but you should do all ports: 

![](images/2025-11-20-16-46-11.png)

![](images/2025-11-20-16-46-30.png)

![](images/2025-11-20-16-47-33.png)

![](images/2025-11-20-16-50-24.png)

![](images/2025-11-20-16-51-17.png)

![](images/2025-11-20-16-51-26.png)

![](images/2025-11-20-16-52-11.png)

- This means how to, what we're going to do to recover from an error-disabled interface if the cause, the cause it to go error-disabled was a port security violation 

- errdisable recovery interval 600 means that after it first goes to error-disabled, after 600 seconds, it will automatically come out of error-disabled and start forwarding traffic again.

### Preventing Unauthorized Devices w/ Port Security Lab Demo - S27V208

![](images/2025-11-20-16-54-27.png)

- on SW have configured spanning-tree and added a hostname

Configure Port Security for all: 

- Can only configure port sec. on *Non-Dynamic* Ports

![](images/2025-11-20-16-56-25.png)

Configure on Access Ports:

![](images/2025-11-20-16-56-47.png)

![](images/2025-11-20-16-57-14.png)

Creating the Problem (adding a new user):

![](images/2025-11-20-16-59-14.png)

PC3 ping fails & Port shuts down:

![](images/2025-11-20-17-00-10.png)

![](images/2025-11-20-17-01-01.png)

![](images/2025-11-20-17-01-13.png)

Getting Fa0/2 back up:

![](images/2025-11-20-17-02-38.png)

![](images/2025-11-20-17-02-52.png)

![](images/2025-11-20-17-03-26.png)

![](images/2025-11-20-17-03-36.png)

![](images/2025-11-20-17-03-52.png)

![](images/2025-11-20-17-04-02.png)

### Locking Ports to Hosts with Port Security - S27V209

![](images/2025-11-20-17-04-58.png)

![](images/2025-11-20-17-06-12.png)

![](images/2025-11-20-17-06-39.png)

![](images/2025-11-20-17-07-31.png)

![](images/2025-11-20-17-09-38.png)

![](images/2025-11-20-17-10-10.png)

### Locking Ports to Hosts with Port Security Lab Demo - S27V210 

![](images/2025-11-20-17-11-43.png)

Lock F0/1 to MAC 0.1.1 :

Enable generic default port security 1st:

![](images/2025-11-20-17-13-14.png)

Now lock it to this specific MAC address: 

![](images/2025-11-20-17-14-27.png)

![](images/2025-11-20-17-14-44.png)

Check:

![](images/2025-11-20-17-14-56.png)

- MAC Address hasn't been learned yet (no traffic yet)

Check it:

![](images/2025-11-20-17-15-16.png)

After a ping:

![](images/2025-11-20-17-15-40.png)

Stick Address vs Not Putting a MAC Address:

![](images/2025-11-20-17-19-15.png)

![](images/2025-11-20-17-19-22.png)

Switch doesn't care which host is plugged in as long as it's only 1 at a time:

![](images/2025-11-20-17-21-09.png)

Set sticky: 

![](images/2025-11-20-17-22-07.png)

- Now the switch the MAC address that is plugged in

- PC2 can ping PC1 

![](images/2025-11-20-17-22-40.png)

- Even if you switch the interface to PC3 now it will fail:

![](images/2025-11-20-17-23-55.png)

See violation: 

![](images/2025-11-20-17-24-14.png)


