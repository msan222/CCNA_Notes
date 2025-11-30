## Section 35 - QoS Quality of Service

### QoS Overview - S35V283

![](images/2025-11-29-15-29-33.png)

![](images/2025-11-29-15-33-11.png)

![](images/2025-11-29-15-33-50.png)

![](images/2025-11-29-15-35-58.png)

![](images/2025-11-29-15-37-01.png)

![](images/2025-11-29-15-40-21.png)

![](images/2025-11-29-15-42-08.png)

![](images/2025-11-29-15-43-51.png)

![](images/2025-11-29-15-45-17.png)

![](images/2025-11-29-15-46-32.png)

![](images/2025-11-29-15-48-05.png)

![](images/2025-11-29-15-48-54.png)

![](images/2025-11-29-15-49-07.png)

![](images/2025-11-29-15-49-49.png)

![](images/2025-11-29-15-51-21.png)

### Classification and Marking - S35V284

![](images/2025-11-29-15-53-30.png)

![](images/2025-11-29-15-54-14.png)

![](images/2025-11-29-15-55-52.png)

- ^Call signalling is setting up/shutting down a call
    - payload (actual call) is the voice - Max latency of 150 milliseconds 

![](images/2025-11-29-15-59-30.png)

- In an IP header, there is a single byte called TOS, the Type of Service byte (8 bits). 
    - The DSCP value is carried in there: 
        - DSCP uses the first 6 bits in that byte.
        - 6 bits gives us 64 four possible values.

![](images/2025-11-29-16-03-35.png)

- ip phone is generating & marking its own packets
    - ip phone can put both a CoS and a DSCP value on a packet
- *BUT* you don't want to trust any markings from the PC from behind the phone

- Voice uses UDP for voice (RP based off UDP) since there's less overhead 

Process:

1. As the phone is making the packet, it will then encapsulate that with the Layer 3 header which has got the source and the destination IP address
    - it also puts the DSCP value in that IP header. 
        - It's voice payload so it marks it as EF. 

2. The phone, on that same packet encapsulates it in the Layer 2 header.
    - The Layer 2 header has got the source and the destination MAC addresses 
    - it will mark the traffic at Layer 2 as CoS 5.

![](images/2025-11-29-16-10-13.png)

![](images/2025-11-29-16-10-39.png)

![](images/2025-11-29-16-11-55.png)

- `NBAR`: Network Based Application Recognition 

![](images/2025-11-29-16-12-59.png)

![](images/2025-11-29-16-14-59.png)

### Congestion Management - S35V285

How to configure Queueing on Cisco Devices

![](images/2025-11-29-16-25-18.png)

Congestion Management: Manipulating the queue so you give better service to the traffic that requires it

![](images/2025-11-29-16-27-22.png)

![](images/2025-11-29-16-28-33.png)

![](images/2025-11-29-16-35-29.png)

![](images/2025-11-29-16-40-42.png)

![](images/2025-11-29-16-42-54.png)

- `**DON'T` need to know this exact configuration for the CCNA exam, just the theory

### Policing and Shaping - S35V286

![](images/2025-11-29-16-45-15.png)

![](images/2025-11-29-16-47-28.png)

![](images/2025-11-29-16-49-14.png)

- ^worm is a type of virus

- Remember: Bandwidth doesn't actually affect physical bandwidth, just software policy. 
    - You *Can* change physical bandwidth with a `Shaping Policy`

![](images/2025-11-29-16-53-46.png)

- ^just configure policy map and apply to interface because it's applying to all traffic 

![](images/2025-11-29-16-54-40.png)

Also need to add LLQ policy:

![](images/2025-11-29-16-57-36.png)

![](images/2025-11-29-16-58-03.png)

- ^Configurations not necessary for CCNA










