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

