## Section 34 - Network Device Management

### Syslog - S34V273

![](images/2025-11-28-17-08-25.png)

![](images/2025-11-28-17-08-41.png)

![](images/2025-11-28-17-09-12.png)

![](images/2025-11-28-17-09-21.png)

![](images/2025-11-28-17-09-39.png)

![](images/2025-11-28-17-10-04.png)

![](images/2025-11-28-17-10-27.png)

- ^what happened

![](images/2025-11-28-17-10-40.png)

![](images/2025-11-28-17-10-57.png)

- ^3 and up is when something bad is happening

![](images/2025-11-28-17-12-57.png)

![](images/2025-11-28-17-14-39.png)

![](images/2025-11-28-17-15-33.png)

![](images/2025-11-28-17-16-24.png)

![](images/2025-11-28-17-17-36.png)

![](images/2025-11-28-17-18-01.png)

![](images/2025-11-28-17-19-00.png)

![](images/2025-11-28-17-19-45.png)

![](images/2025-11-28-17-20-38.png)

![](images/2025-11-28-17-21-25.png)

### Terminal Monitor and Logging Synchronous - S34V274

Configuring Syslog - NMS (Network Monitoring System)

![](images/2025-11-28-17-37-53.png)

![](images/2025-11-28-17-38-40.png)

Telnet into the router using puTTY:

![](images/2025-11-28-17-39-10.png)

Large window is Console Session, Small window is puTTY session:

![](images/2025-11-28-17-40-05.png)

Debug the pings that are coming in on puTTY:

![](images/2025-11-28-17-40-57.png)

- ^we still need to enable it on Telnet

Turn it on in Telnet/SSH:

![](images/2025-11-28-17-42-36.png)

Turn off all debugging: `undebug all` or `u all` for short

![](images/2025-11-28-17-43-40.png)

![](images/2025-11-28-17-45-26.png)

Enable Logging Synchronous to fix it on all lines:

![](images/2025-11-28-17-45-52.png)

Fixed:

![](images/2025-11-28-17-46-07.png)

### Syslog Lab Demo - S34V275

![](images/2025-11-28-17-47-32.png)

![](images/2025-11-28-17-48-38.png)

Default logging Level is debugging:

![](images/2025-11-28-17-48-56.png)

![](images/2025-11-28-17-49-19.png)

![](images/2025-11-28-17-50-49.png)

Turn off logging to console:

![](images/2025-11-28-17-51-36.png)

Enable logging to Telnet session, level 5 and up:

![](images/2025-11-28-17-52-21.png)

![](images/2025-11-28-17-54-02.png)

Configure Logging to the buffer:

![](images/2025-11-28-17-54-27.png)

![](images/2025-11-28-17-54-48.png)

#### External Logging - Kiwi Syslog Server

![](images/2025-11-28-17-56-17.png)

Set it up on the Router: 

![](images/2025-11-28-17-57-02.png)

![](images/2025-11-28-17-57-19.png)

### SNMP Simple Network Management Protocol - S34V276

![](images/2025-11-28-17-58-45.png)

![](images/2025-11-28-17-59-33.png)

![](images/2025-11-28-18-00-24.png)

![](images/2025-11-28-18-01-19.png)

![](images/2025-11-28-18-02-13.png)

![](images/2025-11-28-18-04-26.png)

***For CCNA you don't need to know how to set up Syslog server or SNMP server

How to configure the configuration on a Router:

![](images/2025-11-28-18-05-29.png)

![](images/2025-11-28-18-07-47.png)

### SNMP Lab Demo - S34V277

![](images/2025-11-28-18-17-06.png)

Configure SNMP on R1:
(everything is on default)

![](images/2025-11-28-18-18-11.png)

Set Community Strings:

![](images/2025-11-28-18-18-50.png)

Set up where the SNMP Server is:

![](images/2025-11-28-18-19-24.png)

Specify what traps to send to that server:

![](images/2025-11-28-18-19-52.png)

Trap for when someone invokes configuration mode on the router:

![](images/2025-11-28-18-20-31.png)

![](images/2025-11-28-18-21-22.png)

### SNMP v3 Configuration - S34V278

![](images/2025-11-28-18-38-16.png)

![](images/2025-11-28-18-39-05.png)

![](images/2025-11-28-18-41-15.png)

![](images/2025-11-28-18-43-25.png)

![](images/2025-11-28-18-58-29.png)

![](images/2025-11-28-18-59-33.png)

![](images/2025-11-28-19-00-58.png)

- ^NMS server in this group will have full read-only access to the device

![](images/2025-11-28-19-01-48.png)

![](images/2025-11-28-19-02-32.png)

![](images/2025-11-28-19-03-27.png)

![](images/2025-11-28-19-03-50.png)

- Then you'd configure a matching user on the NMS server too and *then* the NMS server would be able to access the device and pull information from it. 

### SNMPv3 Lab Demo - S34V279

![](images/2025-11-29-14-17-14.png)

- Using PRTG Network Monitor (SNMP software)

- Haven't configured SNMP settings, including username, on the router yet

Create Group, set version and security level:

![](images/2025-11-29-14-21-02.png)

COnfigure User (security, version, password, encryption, password):

![](images/2025-11-29-14-22-16.png)

Now configure matching settings on SNMP manager (server):

![](images/2025-11-29-14-24-04.png)

![](images/2025-11-29-14-24-26.png)

![](images/2025-11-29-14-25-25.png)

![](images/2025-11-29-14-25-56.png)

![](images/2025-11-29-14-26-07.png)

### Syslog vs SNMP - S34V280

![](images/2025-11-29-14-26-55.png)

![](images/2025-11-29-14-28-47.png)

![](images/2025-11-29-14-29-35.png)

![](images/2025-11-29-14-30-38.png)

![](images/2025-11-29-14-31-19.png)



