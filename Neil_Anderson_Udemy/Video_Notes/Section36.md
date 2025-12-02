## Section 36 - Cloud Computing 

### Traditional IT Deployment Methods - S36V288

![](images/2025-12-01-13-44-49.png)

![](images/2025-12-01-13-45-19.png)

![](images/2025-12-01-13-47-46.png)

![](images/2025-12-01-13-48-30.png)

![](images/2025-12-01-13-49-20.png)

![](images/2025-12-01-13-50-26.png)

### Defining CLoud COmputing - S36V289

![](images/2025-12-01-13-53-11.png)

![](images/2025-12-01-13-53-58.png)

![](images/2025-12-01-13-55-04.png)

- Doesn't require individuals from IT team to put together - normally uses a GUI or web tool

![](images/2025-12-01-13-56-35.png)

- can provision the amount of resources you need very quickly (and scale back or out as needed)

![](images/2025-12-01-13-57-21.png)

- Can be accessed from anywhere from company's offices, or anywhere on internet, and a variety of different clients

![](images/2025-12-01-13-58-32.png)

- ^No one customer owns their own hardware - saves on costs (will usually be virtualized)

![](images/2025-12-01-14-00-58.png)

- ^like a monthly operational fee

### Cloud Computing Case Study - S36V290

![](images/2025-12-01-14-06-42.png)

- We will use AWS (Amazon Web Services) IASS (Infrastructure as a service)
    - their solution is EC2 (Elastic Cloud Compute)

![](images/2025-12-01-14-14-10.png)

- We are using EC2  b/c we will be provisioning servers in the Amazon Cloud and want to have firewalls & load balancers

For servers we will use AWS virtual machines for the servers. Configure this: 

![](images/2025-12-01-15-10-16.png)

- ^Launch instance then configure web servers first:

![](images/2025-12-01-15-11-19.png)

Next Specify the CPU and amount of memory in those servers:

![](images/2025-12-01-15-12-48.png)

Configure Instance Details (how many instances you want - we'll do 4 for the middleware - db will be separate)

- Asks if you want to configure an auto scaling group - depending on how busy servers are (# of connections or how busy the CPU is ) and they'll automatically add more servers:

![](images/2025-12-01-15-15-38.png)

![](images/2025-12-01-15-17-16.png)

- ^configure this w/ network settings

How much storage for the different servers (local disc?, external SAN?, performance guarantees)

![](images/2025-12-01-15-19-26.png)

- Then configure tags to organize a large group of servers

Then, Configure security group, aka firewall rules (type of traffic you want going into those servers):

![](images/2025-12-01-15-21-11.png)

#### Summary of Characteristics (Cloud)

![](images/2025-12-01-15-22-33.png)

Traditional Approach (all automated w/ Cloud Computing):

1. Server Teams: install OS, patches, applications

2. Networking Team: Configure VLANs, configure routing info, firewalls, load balancers

3. Storage Team: Provisions the storage
    - large datacenter will probably have external storage

### Server Virtualization - S36V291

![](images/2025-12-01-15-28-08.png)

![](images/2025-12-01-15-28-54.png)

![](images/2025-12-01-15-30-01.png)

![](images/2025-12-01-15-31-11.png)

![](images/2025-12-01-15-31-21.png)

![](images/2025-12-01-15-31-29.png)

![](images/2025-12-01-15-31-43.png)

![](images/2025-12-01-15-31-51.png)

![](images/2025-12-01-15-33-08.png)

![](images/2025-12-01-15-34-53.png)

![](images/2025-12-01-15-36-18.png)

![](images/2025-12-01-15-37-03.png)

![](images/2025-12-01-15-38-20.png)

![](images/2025-12-01-15-38-40.png)

![](images/2025-12-01-15-39-33.png)

![](images/2025-12-01-15-41-13.png)

![](images/2025-12-01-15-42-35.png)

![](images/2025-12-01-15-46-03.png)

### Virtualizing Network Devices - S36V292

![](images/2025-12-01-16-20-17.png)

Bare metal is when the OS is running directly on the hardware, no hypervisor

![](images/2025-12-01-16-22-02.png)

![](images/2025-12-01-16-23-03.png)

![](images/2025-12-01-16-24-27.png)

![](images/2025-12-01-16-25-17.png)

![](images/2025-12-01-16-26-10.png)

- ^This is fine if it's running in your *own* data center

- **In a cloud environment SP can take care of routing
    - if you wanna do it yourself though:

![](images/2025-12-01-16-27-08.png)

![](images/2025-12-01-16-34-04.png)

- ^Can only really do this on ISP routers (really high level ones)
- Customers can configure

Instead for Normal Enterprise Routers:

![](images/2025-12-01-16-36-11.png)

- ^Customer's couldn't configure this

![](images/2025-12-01-16-38-23.png)

![](images/2025-12-01-16-38-55.png)

![](images/2025-12-01-16-39-08.png)

![](images/2025-12-01-16-39-46.png)

![](images/2025-12-01-16-40-38.png)

### Cloud Service Models - S36V293

![](images/2025-12-01-16-43-55.png)

![](images/2025-12-01-16-44-46.png)

![](images/2025-12-01-16-45-51.png)

![](images/2025-12-01-16-46-20.png)

- ^Provider provides incoming network connections, client has their own network infrastructure equipment (firewalls, etc)

![](images/2025-12-01-16-48-33.png)

![](images/2025-12-01-16-49-35.png)

Example w/ AWS (cont from last lecture):

![](images/2025-12-01-16-50-35.png)

![](images/2025-12-01-16-50-53.png)

![](images/2025-12-01-16-51-05.png)

![](images/2025-12-01-16-51-24.png)

![](images/2025-12-01-16-52-39.png)

![](images/2025-12-01-16-52-48.png)

- ^Typically used for developing software (what custom environment is used for)

Example (IBM):

![](images/2025-12-01-16-53-51.png)

![](images/2025-12-01-16-54-04.png)

![](images/2025-12-01-16-55-06.png)

- SaaS Example: Microsoft Office 365 for web, software (access directly from a web portal)

### Cloud Deployment Models - S36V294

![](images/2025-12-01-16-58-14.png)

![](images/2025-12-01-16-58-38.png)

![](images/2025-12-01-16-59-23.png)

![](images/2025-12-01-16-59-34.png)

![](images/2025-12-01-17-00-31.png)

![](images/2025-12-01-17-01-19.png)

![](images/2025-12-01-17-02-11.png)

- SDN: Software Defined Networking

![](images/2025-12-01-17-04-58.png)

![](images/2025-12-01-17-06-55.png)

![](images/2025-12-01-17-07-19.png)

![](images/2025-12-01-17-07-59.png)

![](images/2025-12-01-17-08-53.png)

![](images/2025-12-01-17-09-30.png)

### Cloud Computing Advantages - S36V295

![](images/2025-12-01-17-11-28.png)

![](images/2025-12-01-17-13-52.png)

![](images/2025-12-01-17-14-18.png)

![](images/2025-12-01-17-15-20.png)

![](images/2025-12-01-17-15-52.png)

![](images/2025-12-01-17-16-20.png)

![](images/2025-12-01-17-18-07.png)

![](images/2025-12-01-17-18-49.png)












