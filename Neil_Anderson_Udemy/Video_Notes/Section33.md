## Section 33 - Cisco Device Security 

### Line Level Security - S33V261

![](images/2025-11-28-13-25-01.png)

![](images/2025-11-28-13-25-31.png)

![](images/2025-11-28-13-29-02.png)

![](images/2025-11-28-13-30-11.png)

![](images/2025-11-28-13-31-15.png)

![](images/2025-11-28-13-32-10.png)

![](images/2025-11-28-13-33-25.png)

![](images/2025-11-28-13-34-33.png)

Configure Password for Telnet/SSH do it under the Switched Virtual Interface (SVI) on VLAN 1 (or whatever VLAN you picked):

![](images/2025-11-28-13-36-20.png)

![](images/2025-11-28-13-37-18.png)

![](images/2025-11-28-13-38-41.png)

![](images/2025-11-28-13-39-26.png)

![](images/2025-11-28-13-39-38.png)

- ^Configure the at the line level (can be separate for console and Telnet)
    - 5 minutes and 30 seconds

- `VTY Lines`: Virtual Terminal Lines

![](images/2025-11-28-13-42-37.png)

![](images/2025-11-28-13-43-31.png)

### Privileged Exec and Password Encryption - S33V262

![](images/2025-11-28-13-50-12.png)

![](images/2025-11-28-13-51-20.png)

![](images/2025-11-28-13-51-03.png)

![](images/2025-11-28-13-52-20.png)

![](images/2025-11-28-13-53-02.png)

![](images/2025-11-28-13-53-41.png)

![](images/2025-11-28-13-54-27.png)

![](images/2025-11-28-13-54-45.png)

### Line Level Security Lab Demo - S33V263

![](images/2025-11-28-14-24-26.png)

Secure Console Access for Router:

- Don't forget to put 'login' command - won't prompt for password otherwise

![](images/2025-11-28-14-28-13.png)

Go back and add login:

![](images/2025-11-28-14-28-41.png)

- ^When you put 'login' with no other keywords after, it means use the password was just configured at the line level.

![](images/2025-11-28-14-29-49.png)

- **You can't Telnet into a Cisco router unless you explicitly allow it 

Configure Telnet Security & Access:

- We have 16 lines, want to enable security & admin login on all of them:

![](images/2025-11-28-14-31-46.png)

![](images/2025-11-28-14-32-10.png)

![](images/2025-11-28-14-32-42.png)

- ^Need to enable secret along w/ access 

Configure so that PC1 has access to Router but not PC2

Set password and allow just PC1 to Telnet:

![](images/2025-11-28-14-34-42.png)

- ^Now PC1 can log in but not PC2

Now Set an Enable Password:

![](images/2025-11-28-14-36-08.png)

- too visible in startup config

Enable a Secret Instead:

![](images/2025-11-28-14-36-36.png)

![](images/2025-11-28-14-37-02.png)

Passwords on VTY lines and and console are still visible on run config, encrypt them:

![](images/2025-11-28-14-39-03.png)

![](images/2025-11-28-14-39-20.png)

### Usernames and Privilege Levels - S33V264

![](images/2025-11-28-14-40-26.png)

![](images/2025-11-28-14-41-02.png)

![](images/2025-11-28-14-42-48.png)

![](images/2025-11-28-14-43-17.png)

![](images/2025-11-28-14-44-22.png)

![](images/2025-11-28-14-45-46.png)

![](images/2025-11-28-14-46-21.png)

![](images/2025-11-28-14-46-32.png)

![](images/2025-11-28-14-47-06.png)

![](images/2025-11-28-14-47-42.png)

![](images/2025-11-28-14-48-18.png)

![](images/2025-11-28-14-48-55.png)

![](images/2025-11-28-14-49-08.png)

![](images/2025-11-28-14-49-34.png)

![](images/2025-11-28-14-49-59.png)

![](images/2025-11-28-14-50-29.png)

![](images/2025-11-28-14-51-22.png)

![](images/2025-11-28-14-51-45.png)

### SSH Secure Shell - S33V265

![](images/2025-11-28-14-52-20.png)

![](images/2025-11-28-14-53-22.png)

![](images/2025-11-28-14-54-27.png)

![](images/2025-11-28-14-56-46.png)

### SSH Secure Shell Lab Demo - S33V266

![](images/2025-11-28-14-57-54.png)

- Access R1 from PC1

![](images/2025-11-28-14-58-31.png)

- ^Telnet or SSH hasn't been configured at line-level yet

use a username a secret:

![](images/2025-11-28-14-59-20.png)

Set up Telnet Access First:

![](images/2025-11-28-14-59-51.png)

![](images/2025-11-28-15-00-17.png)

SSH still fails:

![](images/2025-11-28-15-00-38.png)

Set up SSH Access:

- **Should also set up a hostname

![](images/2025-11-28-15-01-31.png)

![](images/2025-11-28-15-02-17.png)

Disable Telnet Access:

![](images/2025-11-28-15-03-16.png)

Only accept SSH v2:

![](images/2025-11-28-15-03-31.png)

### AAA Authentication, Authorization, and Accounting - S33V267

![](images/2025-11-28-15-04-50.png)

![](images/2025-11-28-15-06-52.png)

![](images/2025-11-28-15-08-30.png)

![](images/2025-11-28-15-09-22.png)

![](images/2025-11-28-15-09-43.png)

![](images/2025-11-28-15-10-09.png)

![](images/2025-11-28-15-10-16.png)

![](images/2025-11-28-15-10-41.png)

![](images/2025-11-28-15-10-49.png)

![](images/2025-11-28-15-11-22.png)

![](images/2025-11-28-15-11-37.png)

- Cisco AAA server is more granular than Active Directory Domain Controller (AAA can control what commands are allowed)     
    - integrate both so you get the granularity of AAA and the easiness of just 1 username/psswrd on ADDC

![](images/2025-11-28-15-15-30.png)

![](images/2025-11-28-15-15-37.png)

![](images/2025-11-28-15-15-45.png)

![](images/2025-11-28-15-16-05.png)

![](images/2025-11-28-15-16-26.png)

![](images/2025-11-28-15-17-40.png)

![](images/2025-11-28-15-17-54.png)

### AAA Configuration - S33V268

![](images/2025-11-28-15-18-59.png)

-  ^line 1: if the router or switch cannot communicate with the AAA server, then it fails over to using the local usernames.

![](images/2025-11-28-15-24-25.png)

![](images/2025-11-28-15-25-29.png)

![](images/2025-11-28-15-27-48.png)

![](images/2025-11-28-15-29-29.png)

![](images/2025-11-28-15-30-33.png)

### Global Security Best Practices - S33V169

![](images/2025-11-28-15-32-28.png)

![](images/2025-11-28-15-33-09.png)

![](images/2025-11-28-15-34-30.png)

![](images/2025-11-28-15-35-15.png)

- CDP - Cisco Discovery Protocol (neighbors & ip addresses)

![](images/2025-11-28-15-37-13.png)

![](images/2025-11-28-15-39-08.png)

![](images/2025-11-28-15-39-52.png)

### Global Security Best Practices Lab Demo - S33V270

![](images/2025-11-28-15-47-21.png)

Configure the Login Banner: 

![](images/2025-11-28-15-48-30.png)

![](images/2025-11-28-15-48-47.png)

Configure NTP: 

![](images/2025-11-28-15-49-14.png)

Set Time Zone and place/ip:

![](images/2025-11-28-15-55-10.png)

![](images/2025-11-28-15-55-21.png)



***Note*** - In order for a switch to access another subnet it needs to have it's default gateway set to an edge router.

i.e. 

    SW2(config)#int vlan 1
    SW2(config-if)#no shutdown
    SW2(config-if)#exit
    SW2(config)#ip default-gateway 10.0.1.1 


