## Section 28 - ACLs - Access Control Lists

Segmentation:
`Layer 2 - VLANS
Layer 3 - Subnets`

### Access Control Lists Overview - S28V213

![](images/2025-11-20-18-06-39.png)

![](images/2025-11-20-18-07-20.png)

![](images/2025-11-20-18-07-47.png)

![](images/2025-11-20-18-08-18.png)

![](images/2025-11-20-18-08-34.png)

![](images/2025-11-20-18-09-46.png)

- ^gt is greater than, destination is port 23

### Standard, Extended, and Named ACLs - S28V214

![](images/2025-11-20-18-15-20.png)

![](images/2025-11-20-18-15-36.png)

![](images/2025-11-20-18-15-47.png)

![](images/2025-11-20-18-16-57.png)

![](images/2025-11-20-18-17-55.png)

- ^deny 1 host on the network but allow the rest

![](images/2025-11-20-18-18-37.png)

![](images/2025-11-20-18-19-59.png)

![](images/2025-11-20-18-24-08.png)

![](images/2025-11-20-18-24-52.png)

![](images/2025-11-20-18-25-26.png)

![](images/2025-11-20-18-29-14.png)

### ACL Syntax - S28V215

![](images/2025-11-21-12-30-44.png)

![](images/2025-11-21-12-36-50.png)

![](images/2025-11-21-12-41-12.png)

- ^When specifying a protocol use TCP or UDP if you want the access control entry to traffic b/t a particular source and destination 

![](images/2025-11-21-12-42-36.png)

![](images/2025-11-21-12-44-14.png)

![](images/2025-11-21-12-45-40.png)

- ^not a particular application 

![](images/2025-11-21-12-46-34.png)

![](images/2025-11-21-12-46-53.png)

![](images/2025-11-21-12-48-55.png)

![](images/2025-11-21-12-49-28.png)

![](images/2025-11-21-12-50-00.png)

![](images/2025-11-21-12-50-10.png)

![](images/2025-11-21-12-51-09.png)

- ^Here, we specified the destination port and we said log as well.

![](images/2025-11-21-12-51-51.png)

- ^matches are really helpful for troubleshooting

![](images/2025-11-21-13-05-26.png)

### ACL Operations - S28V216
***Important Lecture***

![](images/2025-11-21-13-06-45.png)

- Have to actually apply the ACLs after creating them & their entries

- 'be the router'- imagine your arms are the interfaces - traffic comes in on one interface (inbound) and you can apply the ACL then, and goes out another interface (outbound) and you can apply it at that point

![](images/2025-11-21-13-14-47.png)

Check to see what access groups are applied to what interfaces:

![](images/2025-11-21-13-15-38.png)

![](images/2025-11-21-13-16-44.png)

![](images/2025-11-21-13-16-54.png)

- ^As soon as a match for the traffic is found it only reads that first one

![](images/2025-11-21-13-19-12.png)

![](images/2025-11-21-13-21-51.png)

![](images/2025-11-21-13-24-04.png)

![](images/2025-11-21-13-24-46.png)

![](images/2025-11-21-13-25-11.png)

![](images/2025-11-21-13-26-03.png)

- ^if we go on the command line on R1 we **will** be able to Telnet onto the command line to R2

### Numbered ACLs Lab Demo - S28V217

#### Numbered Standard ACL

![](images/2025-11-21-13-35-15.png)

- Routing has been configured, PC1 can ping PC2, PC2 can ping PC3

![](images/2025-11-21-13-36-13.png)

Routes we have on R1 right now:

![](images/2025-11-21-13-36-54.png)

First thing: PCs on 10.0.2.0/24 shouldn't be able to access R2 at 10.0.0.2 *but* PCs in 10.0.1.0/24 should. The PCs should all have connectivity to each other.
    - Have to configure all this on R1 using a **Standard** ACL

- **B/C with a standard ACL you can only specify **Source Address**, we'll have to configure the ACL on the outbound interface F0/0

Create Standard ACL and add an entry:

![](images/2025-11-21-13-42-42.png)

Allow traffic from 10.0.1.0/24: 

![](images/2025-11-21-13-43-11.png)

Apply that ACL outbound on F0/0:

![](images/2025-11-21-13-47-33.png)

PC3 now can't ping R2:

![](images/2025-11-21-13-48-26.png)

But can ping the rest of the network:

![](images/2025-11-21-13-48-43.png)

#### Numbered Extended ACL

Scenario: Permit **only** PC1 to Telnet to R2. (Remotely get onto R2's command line)

Go onto R1:

Allow Telnet traffic from 10.0.1.10 to 10.0.0.2 but deny Telnet from everywhere else and allow all other kinds of traffic from 10.0.1.0/24 

Allow PC1:

![](images/2025-11-21-13-52-42.png)

Deny Every other Telnet Traffic to R2:

![](images/2025-11-21-13-53-14.png)

***Important to put the permit before the deny so it actually allows PC1 Telnet through

Allow all other types of traffic:

![](images/2025-11-21-13-54-36.png)

Apply at interface closest to source:

Apply on F1/0 on R1:

![](images/2025-11-21-13-56-25.png)

- **Could have done it on F0/0 but we already put our standard ACL and you can only have one ACL per interface per direction

![](images/2025-11-21-13-57-54.png)

Test it, Telnet from PC1 to R2:

![](images/2025-11-21-13-58-12.png)

- ^Good

Make sure PC2 can't telnet to R2:

![](images/2025-11-21-13-58-37.png)

- ^it can still ping though

### Named ACLs Lab Demo - S28V218

![](images/2025-11-21-14-01-30.png)

- ACLs from previous lab are still there

Scenario (Configuring from R1): 
    - PC1 needs to be able to Telnet to R2 but no one else should have it. 
    - PC2 needs to be able to ping R2 but no one else should be able to 

Remove ACL from F1/0 on R1 (leftover from last lab):

![](images/2025-11-21-14-04-47.png)

- *The ACL is removed but it still exists in the running config

Create a named Access List:

- specifying host, destination, and port number so it needs to be extended ACL

![](images/2025-11-21-14-08-03.png)

- ^named F1/0_in

Now we're in the ACL subcommands:

![](images/2025-11-21-14-09-02.png)

Permit Telnet from PC1 to R2:

![](images/2025-11-21-14-09-55.png)

Deny the rest of Telnet traffic from the subnet and any others:

![](images/2025-11-21-14-11-49.png)

Now permit & Deny traffic:

Permit PC2 ping to R2:

![](images/2025-11-21-14-13-01.png)

Deny from everyone else:

![](images/2025-11-21-14-13-24.png)

Permit all other types of traffic:

![](images/2025-11-21-14-14-09.png)

Apply the ACL to the interface (inbound):

![](images/2025-11-21-14-15-13.png)

Check PC1 can Telnet to R2 but not ping it:

![](images/2025-11-21-14-15-52.png)

Check PC2 can ping R2 but not Telnet to it:

![](images/2025-11-21-14-16-21.png)

Make sure you can still ping all others:

![](images/2025-11-21-14-16-57.png)

See all your ACLs and how many hits they're getting:

![](images/2025-11-21-14-17-18.png)


















