## Section 32 - The Security Threat Landscape 

### The Security Threat Landscape - S32V251

![](images/2025-11-26-13-23-59.png)

![](images/2025-11-26-13-25-42.png)

![](images/2025-11-26-13-30-07.png)

![](images/2025-11-26-13-32-22.png)

![](images/2025-11-26-13-34-53.png)

![](images/2025-11-26-13-35-45.png)

### Common Attacks - S32V252

![](images/2025-11-26-13-45-03.png)

![](images/2025-11-26-13-47-43.png)

![](images/2025-11-26-13-49-00.png)

![](images/2025-11-26-13-50-21.png)

![](images/2025-11-26-13-51-43.png)

![](images/2025-11-26-13-52-16.png)

![](images/2025-11-26-13-53-18.png)

![](images/2025-11-26-13-54-24.png)

![](images/2025-11-26-13-58-47.png)

![](images/2025-11-26-14-00-46.png)

![](images/2025-11-26-14-01-19.png)

![](images/2025-11-26-14-02-19.png)

![](images/2025-11-26-14-02-50.png)

![](images/2025-11-26-14-04-45.png)

![](images/2025-11-26-14-05-20.png)

### Firewall and IDS/IPS - S32V253

![](images/2025-11-26-14-07-18.png)

![](images/2025-11-26-14-10-55.png)

![](images/2025-11-26-14-15-25.png)

- Two different options b/c IPS can sometimes bottleneck/slow traffic 

![](images/2025-11-26-14-16-28.png)

![](images/2025-11-26-14-17-27.png)

![](images/2025-11-26-14-17-49.png)

![](images/2025-11-26-14-18-48.png)

- Clustered Devices can help w/ scalability and higher throughput 
    - put multiple hardware devices in and send traffic through all of them - if the devices support clustering then they can all act as one single solution for management
    - now have higher throughput and redundancy

![](images/2025-11-26-14-22-03.png)

![](images/2025-11-26-14-23-00.png)

![](images/2025-11-26-14-24-35.png)

### Firewalls vs Packet Filters - S32V254

![](images/2025-11-26-14-27-18.png)

![](images/2025-11-26-14-28-24.png)

![](images/2025-11-26-14-29-47.png)

![](images/2025-11-26-14-29-47.png)

![](images/2025-11-26-14-30-42.png)

![](images/2025-11-26-14-30-58.png)

- source port is 49160, destination port is HTTP or port 80

![](images/2025-11-26-14-33-29.png)

![](images/2025-11-26-14-34-02.png)

![](images/2025-11-26-14-35-41.png)

![](images/2025-11-26-14-39-23.png)

- ACLs don't keep track of the states so they don't recognize the incoming traffic, the traffic coming back as valid return traffic.

![](images/2025-11-26-14-40-57.png)

![](images/2025-11-26-14-41-59.png)

![](images/2025-11-26-14-42-37.png)

![](images/2025-11-26-14-42-47.png)

- b/c neither options are good, you always want a statewall firewall connected to the internet to track connections for security

![](images/2025-11-26-14-44-01.png)

![](images/2025-11-26-14-45-12.png)

- ^Looks like it's making the ACL stateful & tracking but it isn't 

![](images/2025-11-26-14-45-41.png)

![](images/2025-11-26-14-46-11.png)

![](images/2025-11-26-14-46-39.png)

![](images/2025-11-26-14-47-48.png)

- Dept A and B aren't supposed to communicate with each other - but traffic going b/t them wouldn't go by the firewall - how do we keep it separate?
    - use and ACL to prevent them from sending traffic to each other

### Cryptography - S32V255

![](images/2025-11-26-14-56-01.png)

![](images/2025-11-26-14-56-26.png)

![](images/2025-11-26-14-57-15.png)

![](images/2025-11-26-14-58-57.png)

![](images/2025-11-26-14-59-38.png)

![](images/2025-11-26-15-00-13.png)

![](images/2025-11-26-15-02-07.png)

![](images/2025-11-26-15-02-18.png)

![](images/2025-11-26-15-06-50.png)

![](images/2025-11-26-15-21-07.png)

- ^Ask a host to encrypt with the correct key to verify it

![](images/2025-11-26-15-21-32.png)

![](images/2025-11-26-15-21-42.png)

![](images/2025-11-26-15-23-27.png)

![](images/2025-11-26-15-24-13.png)

![](images/2025-11-26-15-24-50.png)

![](images/2025-11-26-15-25-45.png)

### TLS Transport Layer Security - S32V256

![](images/2025-11-26-15-26-45.png)

![](images/2025-11-26-15-27-53.png)

![](images/2025-11-26-15-29-17.png)

![](images/2025-11-26-15-29-24.png)

- ^private key never leaves Amazon, even Certificate Authority doesn't see it. 

![](images/2025-11-26-15-30-46.png)

![](images/2025-11-26-15-31-16.png)

- ^doesn't include Verisign's private key but Cert is signed by it

![](images/2025-11-26-15-32-01.png)

![](images/2025-11-26-15-32-16.png)

- PKI - Public Key Infrastructure

![](images/2025-11-26-15-35-24.png)

![](images/2025-11-26-15-35-31.png)

![](images/2025-11-26-15-35-39.png)

![](images/2025-11-26-15-36-20.png)

![](images/2025-11-26-15-47-29.png)

![](images/2025-11-26-15-48-08.png)

- ^asks to encrypt with private key from Amazon's cert

![](images/2025-11-26-15-50-01.png)

![](images/2025-11-26-15-50-17.png)
    
![](images/2025-11-26-15-50-54.png)

![](images/2025-11-26-15-51-01.png)

![](images/2025-11-26-15-52-02.png)

![](images/2025-11-26-16-00-57.png)

![](images/2025-11-26-16-02-24.png)

![](images/2025-11-26-16-03-11.png)

![](images/2025-11-26-16-03-56.png)

![](images/2025-11-26-16-06-25.png)

### Site-to-site VPN Virtual Private Networks - S32V257

![](images/2025-11-26-16-25-05.png)

- ^Traffic through VPN tunnel will be encrypted 

![](images/2025-11-26-16-25-59.png)

![](images/2025-11-26-16-26-40.png)

- ^each of your tunnels should have a different key but pre-shared keys are more common irl

![](images/2025-11-26-16-27-14.png)

![](images/2025-11-26-16-33-18.png)

![](images/2025-11-26-16-35-09.png)

![](images/2025-11-26-16-35-35.png)

![](images/2025-11-26-16-35-57.png)

- You'll mostly use ESP not AH, and Tunnel/Transport mode will often already be selected when setting up a tunnel 

![](images/2025-11-26-16-37-31.png)

![](images/2025-11-26-16-39-46.png)

- ^Use an `ACL` to specify the `interesting traffic`

![](images/2025-11-26-16-44-51.png)

![](images/2025-11-26-16-45-32.png)

- **Don't need to know how to configure for CCNA

![](images/2025-11-26-16-48-43.png)

- ^Config of R2 will be mirror image of R1

![](images/2025-11-26-16-58-02.png)

- ^Encryption and has specified in Phase 1 is for the initial authentication or the setup. Need to specify what algorithms using for actual traffic in Phase 2.

- `Diffie Hellman` Groups - In terms of VPN, used in **IKE or Phase1** part of setting up tunnel. They are used to determine the strength of the key used in the key exchange process

![](images/2025-11-26-17-06-21.png)

![](images/2025-11-26-17-07-51.png)

![](images/2025-11-26-17-10-56.png)

![](images/2025-11-26-17-12-19.png)

![](images/2025-11-26-17-14-33.png)

![](images/2025-11-26-17-18-21.png)

![](images/2025-11-26-17-17-08.png)

### Remote Access VPN Virtual Private Networks - S32V258

![](images/2025-11-26-17-19-34.png)

- ^uses TLS, **not** IPsec

- TLS will be called SSL in a lot of other places (i.e. SSL cert for website actually uses TLS)

![](images/2025-11-26-17-21-12.png)

![](images/2025-11-26-17-22-44.png)

![](images/2025-11-26-17-23-23.png)

### Threat Defense Solutions - S32V259

![](images/2025-11-26-17-25-50.png)

- anti-malware
    - signatures: looks for characteristics of known viruses and if found will block them from running
    - Heuristics: looks for characteristics on a file which are common across other different viruses (not known characteristics)

![](images/2025-11-26-17-30-29.png)

![](images/2025-11-26-17-31-21.png)

![](images/2025-11-26-17-32-01.png)

![](images/2025-11-26-17-32-59.png)

![](images/2025-11-26-17-33-56.png)

![](images/2025-11-26-17-35-56.png)

![](images/2025-11-26-17-37-06.png)

![](images/2025-11-26-17-37-34.png)

![](images/2025-11-26-17-38-10.png)

![](images/2025-11-26-17-38-47.png)

![](images/2025-11-26-17-39-37.png)

![](images/2025-11-26-17-40-20.png)

![](images/2025-11-26-17-41-46.png)

![](images/2025-11-26-17-42-22.png)

![](images/2025-11-26-17-43-38.png)

![](images/2025-11-26-17-44-10.png)

![](images/2025-11-26-17-44-32.png)

![](images/2025-11-26-17-44-56.png)



