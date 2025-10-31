## Section 13 - The Cisco Troubleshooting Methodology

### The Cisco Troubleshooting Methodology - S13V76
![alt text](image-231.png)

![alt text](image-232.png)

![alt text](image-233.png)

![alt text](image-234.png)

### Cisco Troubleshooting Method - Lab Example S13V77

![alt text](image-235.png)

- User on PC behind R1 router complains DNS isn't working
- DNS Server is on R3 router

1. Check the actual problem to make sure it's not a user error

![alt text](image-236.png)

![alt text](image-237.png)

- it isn't reachable

2. Do a traceroute

![alt text](image-238.png)
![alt text](image-239.png)

- problem seems to be at R2 so lets look over there now

3. Go onto R2 and try to ping R3

![alt text](image-240.png)

4. Check R3 routing table 

![alt text](image-241.png)

- no route to 10.10.30.1 

5. Add route to 10.10.30.0

![alt text](image-242.png)

6. Try to ping again, ping works

![alt text](image-243.png)

![alt text](image-244.png)

- ping & traceroute help with Layer 3 (Network) issues
- telnet helps with Layer 4 (Transport) issues

![alt text](image-245.png)

- Tells us if DNS (port 53) is running on R3
    - if it wasn't open it would mean that the service isn't running at that destination

![alt text](image-246.png)


