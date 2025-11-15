## Section 25: STP - Spanning Tree Protocol **Core CCNA Topic**

### Layer 3 Path Selection and Loop Prevention Review - S25V176

- Spanning Tree - Layer 2 technology that prevents loops across layer 2 switch network

Review:
![](images/2025-11-14-14-50-12.png)

- ^switches CD1, CD2, Acc3, Acc,4 are all layer 2 
    - The rest is Layer 3

![](images/2025-11-14-14-54-28.png)

![](images/2025-11-14-14-57-30.png)

- when configuring a backup route it needs to be pointing to the same subnet as the original route

![](images/2025-11-14-14-59-44.png)

![](images/2025-11-14-15-00-34.png)

PCs POV:

- Pcs have 2 gateways available on 10.10.10.0/24 network

![](images/2025-11-14-15-01-57.png)

- Configure HSRP on R1 & R2 so PCs will only need to use 1 gateway

##### How Routing Loops Can Happen

![](images/2025-11-14-15-05-39.png)

![](images/2025-11-14-15-05-47.png)

- will only loop for length of TTL

![](images/2025-11-14-15-07-34.png)

### Why we have the Spanning Tree Protocol - S25V178

Review Ethernet Path Selection:

![](images/2025-11-14-15-10-47.png)

![](images/2025-11-14-15-18-40.png)

![](images/2025-11-14-15-21-49.png)

![](images/2025-11-14-15-22-38.png)

![](images/2025-11-14-15-23-06.png)

![](images/2025-11-14-15-24-02.png)

![](images/2025-11-14-15-24-11.png)

![](images/2025-11-14-15-31-20.png)

![](images/2025-11-14-15-32-21.png)

![](images/2025-11-14-15-32-57.png)

![](images/2025-11-14-15-33-21.png)

![](images/2025-11-14-15-35-06.png)

![](images/2025-11-14-15-35-57.png)

![](images/2025-11-14-15-36-24.png)

![](images/2025-11-14-15-36-54.png)

- ^Layer 2 traffic will loop forever 

![](images/2025-11-14-15-37-15.png)

![](images/2025-11-14-15-39-11.png)

- BUT before the ports were blocked, we were able to send traffic up to *both* CD1 and CD2 via F0/24 and F0/21 
    - with the ports blocked we're only able to use half the physically available connected uplink bandwidth

![](images/2025-11-14-15-41-54.png)

![](images/2025-11-14-15-42-40.png)

### Spanning Tree Terminology - The Bridge - S25V179

![](images/2025-11-14-15-51-48.png)

![](images/2025-11-14-15-52-53.png)

![](images/2025-11-14-15-54-11.png)


### How Spanning Tree Works - S25V180

![](images/2025-11-14-16-15-53.png)

![](images/2025-11-14-16-21-02.png)

![](images/2025-11-14-16-22-03.png)

![](images/2025-11-14-16-22-25.png)

![](images/2025-11-14-16-24-34.png)

![](images/2025-11-14-16-25-06.png)

![](images/2025-11-14-16-25-32.png)

![](images/2025-11-14-16-30-17.png)

![](images/2025-11-14-16-31-24.png)

![](images/2025-11-14-16-36-52.png)

![](images/2025-11-14-16-38-40.png)

- ^BUT if the direct link b/t SW4 and Root went down, **Spanning Tree is redundant** and the link from SW4 to SW3 would open up so SW4 had a path to the Root

![](images/2025-11-14-16-40-29.png)

- ^you'd have to change the cost on both sides of the link

![](images/2025-11-14-16-42-15.png)

![](images/2025-11-14-16-43-43.png)

![](images/2025-11-14-16-44-38.png)

![](images/2025-11-14-16-45-37.png)

![](images/2025-11-14-16-47-10.png)

20:15



