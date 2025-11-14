## Section 24 - HSRP - Hot Standby Router Protocol

### Network Redundancy - S24V171

![](images/2025-11-13-16-50-04.png)

- ^SP is service provider, red line is network edge

![](images/2025-11-13-16-52-11.png)

![](images/2025-11-13-16-53-18.png)

![](images/2025-11-13-16-54-31.png)

![](images/2025-11-13-16-55-41.png)

![](images/2025-11-13-17-01-35.png)

- ^How to configure connectivity from WAN edge routers going upstream and downstream to the PCs
    - on backup route put admin distance of 5 to make it backup

- Backup route to inside via R2 if link to CD1 goes down is a **connected route** to R2
    - don't need to put an AD b/c ad on connected route is zero (always preferred)

### FHRP - First Hop Redundancy Protocols - S24V172

![](images/2025-11-13-17-09-11.png)

![](images/2025-11-13-17-11-30.png)

![](images/2025-11-13-17-21-25.png)

- **HSRP is what's covered in CCNA**

### HSRP Hot Standby Router Protocol - S24V173

![](images/2025-11-13-17-24-27.png)

![](images/2025-11-14-10-50-42.png)

![](images/2025-11-14-10-54-40.png)

![](images/2025-11-14-10-54-54.png)

![](images/2025-11-14-10-57-44.png)

##### Lab:

![](images/2025-11-14-11-13-32.png)

- Already done the rest of the upstream configuration

Configure R1:

![](images/2025-11-14-11-24-11.png)

Configure R2:

![](images/2025-11-14-11-33-09.png)

![](images/2025-11-14-11-33-21.png)

See it on a PC:

![](images/2025-11-14-11-37-22.png)

### HSRP Advanced Topics - S24V174

![](images/2025-11-14-11-44-28.png)

![](images/2025-11-14-11-46-25.png)

![](images/2025-11-14-11-47-52.png)

![](images/2025-11-14-11-48-12.png)

![](images/2025-11-14-11-48-21.png)

To make it load balance:

Configure 2 different HSRP Groups for the same ip subnet:
![](images/2025-11-14-11-50-19.png)

Configure multiple subnets going through the same pair of routers, then have one subnet going through one router and the other going through the other:
![](images/2025-11-14-11-53-01.png)

- ***HSRP group number is configured under the interface 