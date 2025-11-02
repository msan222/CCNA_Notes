## Section 15 - Cisco Device Management

### The Boot Up Process S15V88

![alt text](image-320.png)

- Flash on newer devices is removable card, older is in a chassis

![alt text](image-321.png)

![alt text](image-322.png)

- If an IOS image can't be found in flash then the device will show the ROMMON prompt at the command line.
    - Can be used to recover a missing or corrupted software image - can boot from USB or an external Trivial File Transfer Protocol (TFTP) server to recover device

![alt text](image-323.png)

![alt text](image-324.png)

![alt text](image-325.png)

![alt text](image-326.png)

![alt text](image-327.png)

![alt text](image-328.png)


### Boot Up Process Lab Demo S15V89


![alt text](image-329.png)

![alt text](image-330.png)
![alt text](image-331.png)

![alt text](image-332.png)

![alt text](image-333.png)

![alt text](image-334.png)

- ^only 1 system image

![alt text](image-335.png)
![alt text](image-336.png)

- still works while running since it's using RAM while running

![alt text](image-337.png)

- ^problem comes when you try to boot up again

Recover System Image:

![alt text](image-338.png)

![alt text](image-339.png)

![alt text](image-340.png)

Since startup-config isn't loaded need to configure ip connectivity at rommon prompt:

![alt text](image-341.png)

- ^if router is on same subnet as TFTP server just put the TFTP (Trivial File Transfer Protocol) server's ip down for default gateway

![alt text](image-342.png)

![alt text](image-343.png)

![alt text](image-344.png)

- ^already IOS system images on the TFTP server 
    - In the real world can download a free TFTP server, or use a paid one

### Factory Reset and Password Recovery S15V90

#### Factory Reset

![alt text](image-345.png)

![alt text](image-346.png)

- ^hostname is R1 in running/startup config

Just change name in running: 

![alt text](image-347.png)

![alt text](image-348.png)

![alt text](image-349.png)

#### Password Recovery 

![alt text](image-350.png)

![alt text](image-351.png)

- ^When you've lost the enable prompt password

![alt text](image-352.png)

- important to copy into running config
- important to copy-register 0x2102 so router will not booth like a factory reset next time

![alt text](image-353.png)

### Password Recovery Lab Demo S15V91

- recovering from a lost enable password or sec ret

- Save a running config: `copy running-config startup-config`

![alt text](image-354.png)
![alt text](image-355.png)

- secret is encrypted password is not
    - secret overrides password

1. Boot Router into rommon mode with 'Ctrl + Break'
    - do it from normal config (can't actually do it irl)

![alt text](image-356.png)

![alt text](image-357.png)

2. Once in rommon mode we need to tell the router to bypass startup-config while booting 

![alt text](image-358.png)

![alt text](image-359.png)

3. Set new enable secret or remove

![alt text](image-360.png)

4. Copy running config

![alt text](image-361.png)

5. In global config reset the register

![alt text](image-362.png)

6. reload again to double-check that it works

**it didn't for this lab??**

- Why: It was originally an 'enable password' and we did 'disable secret' so it's still asking for a password.
    - You would normally add a secret so that wouldn't happen

### Backing up System Image and Configuration S15V92

![alt text](image-363.png)

- helps if you don't want to download it again later
- Backup config helps if you want to rollback
- Can't just copy into running config because they will merge

Steps:

1. Factory reset

2. Take copy of config file (`copy flash tftp` `copy running-config tftp`, etc)

![alt text](image-364.png)

1. Back up system image and running config to TFTP server 

    - Check system image name
    ![alt text](image-365.png)

    - Make sure it's not already on TFTP (Trivial File Transfer Protocol) server (it's not)
    ![alt text](image-366.png)

![alt text](image-367.png)
![alt text](image-368.png)

On router

![alt text](image-369.png)

2. Take a backup to flash then restore it

Router: 

None Yet, copy running config (useful in lab or test environment)
    - Lab: 
        1. Save startup config to flash, do lab exercises
        2. To get back to original startup config do `write erase` 
        3. then `show flash` 
        4. then `copy flash start` with the flash file you saved
        5. Reload
         
![alt text](image-370.png)

![alt text](image-371.png)
![alt text](image-372.png)

### Upgrading IOS S15V93

![alt text](image-373.png)

1. Get new software image
    ![alt text](image-374.png)
2. copy to device's flash using tftp
3. delete old image or use boot system command 

![alt text](image-375.png)

Check current:

![alt text](image-376.png)
![alt text](image-377.png)

Upgrade to new:

See new one in TFTP:
![alt text](image-378.png)

TFTP server is at 10.10.10.10 want to keep same name:
![alt text](image-379.png)

![alt text](image-380.png)

- Now we're gonna keep the old one jic 

- do boot system flash command now it should be good: 
![alt text](image-381.png)

- When system boots up it loads image into RAM so we need to reload the new system image:

![alt text](image-382.png)
![alt text](image-383.png)

Both images are still there: 

![alt text](image-384.png)

Now we're running 15.0: 
![alt text](image-385.png)

## Section 16 - Routing Fundamentals

### Connected and Local Routes - S16V96

![alt text](image-386.png)

![alt text](image-388.png)

![alt text](image-390.png)

![alt text](image-391.png)

- '`show ip route'` doesn't actually show the ip that is configured on the interface, just the subnets - to find the ip you'd have to do `'show ip interface brief'`

### Connected & Local Routes Lab Demo - S16V97

![alt text](image-392.png)

Build Routing Table

- Configure Interfaces with ips: 

![alt text](image-394.png)
![alt text](image-395.png)
![alt text](image-396.png)

- Now we have both our connected and local routes:

![alt text](image-397.png)

![alt text](image-398.png)

- Should be able to ping:

![alt text](image-399.png)

Check Connectivity between PCs & PCs and gateway (confirms 2-way connectivity):

![alt text](image-400.png)
![alt text](image-401.png)
![alt text](image-402.png)

Check route:

![alt text](image-403.png)

### Static Routes - S16V97

![alt text](image-404.png)

- ^R2 doesn't know how to get to 10.1.0.2/24 so we need to add a route to tell it 

![alt text](image-406.png)

- R2 directly connected to 10.1.0.0/24 and 10.0.0.0/24
    - can send traffic to them directly as soon as configured the IP addresses
- Going to need routes to 10.0.1.0/24 and 10.0.2.0/24 behind router R1

![alt text](image-407.png)

- ^command for R1 to get to the 10.1.0.0 network
- command to add static route is `ip route`

![alt text](image-408.png)

- ^For R1 to send traffic to network 10.1.0.0 needs to send out of F0/0 interface, send it to 10.0.0.2 on R2

Now we do the routes on R2:

![alt text](image-409.png)

- Now we can route traffic b/t all the networks here

Adding another router: 

![alt text](image-410.png)

- ^Now we need to let R3 get to the networks behind R2 and R1

Get to network behind R2:

![alt text](image-411.png)

To get to behind R2: 

![alt text](image-412.png)

- **Don't point directly at R1** bc when you add a target route it has to be reachable on a directly connected interface
    - For R3 to get to R1 it has to send the signal to R2, which it is directly connected to 

![alt text](image-414.png)
![alt text](image-415.png)
![alt text](image-416.png)

- ^Now R2 needs a route to get behind R1 & R3

![alt text](image-417.png)

- ^Routes for R1

### Static Routes Lab Demo - S16V99

![alt text](image-418.png)

ips are already configured:

![alt text](image-419.png)

Connected and local routes for all 3 routers are already added:

![alt text](image-420.png)

![alt text](image-421.png)

![alt text](image-422.png)

R1 will need a route for 10.1.0.0 behind R2 and 10.1.1.1 behind R3:

![alt text](image-423.png)

- reachable at 10.0.0.2 (don't point directly at R3):

![alt text](image-424.png)

Adding those on R1: 

![alt text](image-425.png)

- Try to ping those now, but can't:

![alt text](image-428.png)

- check on R3 to see what's going on: 

![alt text](image-426.png)
![alt text](image-427.png)

- ^Use `debug ip icmp` b/c ping uses icmp
        - shows pings coming in
    - pings get to R3 but b/c route isn't set on R3 it can't get back to R1

R1 has everything added:

![alt text](image-429.png)

Now R2 needs routes to behind 3 (1) and R1 (2)

![alt text](image-430.png)
![alt text](image-431.png)

Now configure R3 (behind R2 and R1):

![alt text](image-432.png)

R1 Route Table:

![alt text](image-433.png)

R2 Route Table:

![alt text](image-434.png)

R3 Route Table:

![alt text](image-435.png)

Can check with traceroutes:

![alt text](image-436.png)
![alt text](image-437.png)


### Summarization, Longest Prefix Match, Default Routes - S16V100

![alt text](image-438.png)

![alt text](image-439.png)

- ^Summarize at classful boundary

![alt text](image-440.png)

- ^in case you don't want all the routes
- Only summarizing 10.1.0.0 to 10.1.3.0 and used the value of 255.255.252.0
- know that it's going to begin with 255.255 because all of the subnets we're pointing at begin with 10.1.
    - summarizing on the next octet

- how does 255.255.253 equate to 10.1.0.0-10.1.3.0?
    - subnetting goes up from from 252 to 254, and then to 255 -> so we've used 2 bits.
    - 2 bits give us 4 possible values (1 or 0 times 2)

#### Longest Prefix Match

![alt text](image-441.png)

![alt text](image-442.png)

- Path traffic would take to get to R5 at 10.1.3.2 or anything 10.1.3 would be R1 -> R2 -> R3 -> R4 -> R5   
    - b/c route is pointing at 10.0.0.2
- BUT if we want to go to 10.0.3.2 subnet we want to go directly to R5 since it's shorter than going through R2, etc.

![alt text](image-443.png)

- All traffic for the 10.1 networks will go via R2 *unless* it is 10.1.3, which will go via R5
- `Most Specific Route will Win`

![alt text](image-444.png)

![alt text](image-445.png)

### Summary Routes and Longest Prefix Match Lab Demo - S16V101

![alt text](image-446.png)

R1 Static:

![alt text](image-447.png)

R2:

![alt text](image-448.png)

R3: 

![alt text](image-449.png)

R4: 

![alt text](image-450.png)

^R1 - R2 - R3 - R4 

Remove Individual Routes:

![alt text](image-451.png)

- ^Now we have no static routes, can't ping PC3, etc

Replace with summary route:

![alt text](image-452.png)

![alt text](image-453.png)

- ^should give connectivity for P1 -> PC3

Effect of Longest Prefix Match w/ overlapping routes:

![alt text](image-454.png)

![alt text](image-455.png)

- ^Going to do a summary route on R5 pointing at routes behind R1:

![alt text](image-456.png)

Try to ping 10.0.1.10 from 10.1.3.2 
- Ping uses exit interface as the ip address:

![alt text](image-457.png)

- can override that by doing an extended ping and saying we want 10.1.3.2 as source - just enter `ping`

![alt text](image-458.png)

- we have far-side connectivity b/t R5 and PC1

- Now do a trace:
    - we can see it took a direct path
![alt text](image-459.png)

![alt text](image-460.png)

Return traffic from R1 to R5 is indirect (`asynchronous traffic flow`):

![alt text](image-461.png)

![alt text](image-462.png)

Setting it up so traffic is going directly in both directions:

![alt text](image-463.png)

### Default Routes and Load Balancing Lab Demo S16V102

- Just FastEthernet3/0 on R4 hasn't been configured yet. 
    - Configure it with public ip going out to internet

![alt text](image-464.png)

1. Configure R3:

![alt text](image-465.png)

2. Configure route for internet:

![alt text](image-466.png)

- Now we configure R3 to have access to internet:

![alt text](image-467.png)

- Now we do R2 to internet:

![alt text](image-468.png)

- R5 to internet:

![alt text](image-469.png)

- R1 give it a path via R2 and R5 and the router will load balance b/t them 
    - in order to do so the route and prefix have to match perfectly

![alt text](image-470.png)

- 2 routes from R4 to get back 10.0.1.0 and 10.0.2.0 one via R3 one via R5

![alt text](image-471.png)

- Traffic from PC1 and PC2 will load balance on top and bottom paths

- Load balancing won't happen for traffic from one host to another between the same 2 ip addresses
    - i.e. PC1 to web server 50.50.50.50
    - load balancing would cause packets to arrive out of order 

#### Section 16 Lab Exercise Notes

![alt text](image-472.png)

![alt text](image-473.png)

![alt text](image-474.png)

![alt text](image-475.png)

![alt text](image-476.png)

![alt text](image-478.png)

![alt text](image-479.png)

![alt text](image-480.png)


