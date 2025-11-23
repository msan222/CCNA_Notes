## Section 29 - NAT - Network Address Translation 

### IPv4 Address Exhaustion and NAT - S29V221

Overview of IPv4 Address Exhaustion and Network Address Translation (NAT)

Review

![](images/2025-11-22-13-15-09.png)

![](images/2025-11-22-13-15-52.png)

![](images/2025-11-22-13-16-44.png)

![](images/2025-11-22-13-17-36.png)

![](images/2025-11-22-13-18-38.png)

![](images/2025-11-22-13-19-26.png)

![](images/2025-11-22-13-20-17.png)

![](images/2025-11-22-13-20-25.png)

![](images/2025-11-22-13-21-48.png)

### Static NAT - S9V222

![](images/2025-11-22-13-23-54.png)

![](images/2025-11-22-13-25-00.png)

![](images/2025-11-22-13-26-29.png)

![](images/2025-11-22-13-27-33.png)

- **Static NAT rules are bi-directional so we don't need to configure a separate NAT rule for the Int-S1 server 10.0.1.10 to send traffic back out to the internet

![](images/2025-11-22-13-55-31.png)

- ^now whenever traffic is coming in on interface Fa1/0 and is going to the outside via Fa0/0, the router will change the source ip address on the outbound traffic from 10.0.1.10 to 203.0.113.3
    - For incoming traffic whenever it comes in w/ the destination address 203.0.113.3 coming along in on interface Fa0/0 on the outside, the router will change the destination address to 10.0.1.10 and send it through interface Fa1/0

Verify:

- send traffic then do this:

![](images/2025-11-22-13-59-52.png)

### NAT Translations - Inside Local, Inside Global, Outside Local, Outside Global - S29V223

- **Understand output on 'sh ip nat translation' 

**CONFUSING, STUDY EXTRA** 

![](images/2025-11-22-14-02-14.png)

![](images/2025-11-22-14-04-44.png)

When Outside Local and Outside Global Will be different: (not important for CCNA)

*Common for a merger b/t 2 companies

![](images/2025-11-22-14-06-06.png)

![](images/2025-11-22-14-07-52.png)

- Need to translation destination address too b/c it wouldn't be able to actually reach end host

![](images/2025-11-22-14-09-31.png)

### Static NAT Lab Demo - S29V224

![](images/2025-11-22-14-14-09.png)

Configure NAT interfaces:

![](images/2025-11-22-14-17-11.png)

![](images/2025-11-22-14-18-23.png)

Configure translation:

![](images/2025-11-22-14-19-27.png)

Verify: 

![](images/2025-11-22-14-20-27.png)

- difference b/t 'sh' command and 'debug' is that debug does updates in real time

Ping from internal:

![](images/2025-11-22-14-21-33.png)

View from external: 

![](images/2025-11-22-14-22-10.png)

Check inbound web traffic:

![](images/2025-11-22-14-25-35.png)

Check Translation Table on R1:

![](images/2025-11-22-14-26-31.png)

- ^ICMP entry has already timed out already (common irl)

Redo ping from outside and now the table is fully updated:

![](images/2025-11-22-14-28-15.png)

- R1 is not doing any translation for outside

### Dynamic NAT - S29V225

![](images/2025-11-22-14-30-37.png)

![](images/2025-11-22-14-32-34.png)

![](images/2025-11-22-14-33-06.png)

![](images/2025-11-22-14-33-45.png)

![](images/2025-11-22-14-34-39.png)

***Standard Dynamic NAT is not normally used IRL

![](images/2025-11-22-14-35-54.png)

![](images/2025-11-22-14-39-15.png)

![](images/2025-11-22-14-40-22.png)

![](images/2025-11-22-14-41-01.png)

How many addresses have been translated:

![](images/2025-11-22-14-42-01.png)

### Dynamic NAT Lab Demo - S29V226

![](images/2025-11-22-14-44-11.png)

- Already have F0/0 and F1/0 configured:

![](images/2025-11-22-14-45-49.png)

- We need to configure F2/0 as inside too

![](images/2025-11-22-14-47-01.png)

Configure Public ip address pool:

![](images/2025-11-22-14-47-46.png)

Configure Access list for range of private ip address on the inside that are going to get mapped:

(standard access list)

![](images/2025-11-22-14-49-07.png)

Now tie the pool and ACL together:

![](images/2025-11-22-14-49-27.png)

### PAT Port Address Translation - S29V227

![](images/2025-11-22-14-53-58.png)

![](images/2025-11-22-14-54-27.png)

![](images/2025-11-22-14-54-49.png)

![](images/2025-11-22-14-57-12.png)

![](images/2025-11-22-14-57-22.png)

Where it changes from Standard: 

![](images/2025-11-22-14-58-01.png)

![](images/2025-11-22-14-58-41.png)

![](images/2025-11-22-15-02-13.png)

![](images/2025-11-22-15-00-28.png)

![](images/2025-11-22-15-01-21.png)

![](images/2025-11-22-15-01-37.png)

![](images/2025-11-22-15-02-52.png)

![](images/2025-11-22-15-03-11.png)

![](images/2025-11-22-15-03-43.png)

- 3rd host gets translated to last ip address in the pool

![](images/2025-11-22-15-04-02.png)

![](images/2025-11-22-15-04-55.png)

- ^already used up all NAT pool addresses so b/c of Dynamic NAT w/ overload will reuse last address in pool w/ different source port 

![](images/2025-11-22-15-07-58.png)

- **Very common irl

![](images/2025-11-22-15-08-48.png)

- since w/ DHCP the public ip addresses might change, can't configure a pool to use

But:

![](images/2025-11-22-15-10-23.png)

![](images/2025-11-22-15-10-46.png)

![](images/2025-11-22-15-12-21.png)

- ^can see all port numbers

### PAT Port Address Translation Lab Demo - S29V228

![](images/2025-11-22-15-13-41.png)

- No NAT Configs to start

- no public ips, getting them from DHCP on F0/0 and they could change at any time

Check Interface ip Addresses on R1:

![](images/2025-11-22-15-16-05.png)

- 203.0.113.3 might change at any time

Configure NAT interfaces:

![](images/2025-11-22-15-16-37.png)

Configure access list for inside hosts:

![](images/2025-11-22-15-16-56.png)

Create NAT Rule: 

- Map access list to interface (with overload to enable PAT)

![](images/2025-11-22-15-17-44.png)

Verify:

![](images/2025-11-22-15-19-10.png)

![](images/2025-11-22-15-19-42.png)

- **Arrows mean translation happened**

![](images/2025-11-22-15-20-37.png)








