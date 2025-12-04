## Section 38 - Network Automation and Programmability

### The Benefits of Network Automation and Programmability - S38V307

![](images/2025-12-03-14-55-16.png)

![](images/2025-12-03-14-56-13.png)

![](images/2025-12-03-14-57-15.png)

![](images/2025-12-03-14-58-33.png)

![](images/2025-12-03-14-59-37.png)

![](images/2025-12-03-15-00-58.png)

![](images/2025-12-03-15-01-19.png)

![](images/2025-12-03-15-01-49.png)

![](images/2025-12-03-15-03-00.png)

![](images/2025-12-03-15-03-37.png)

![](images/2025-12-03-15-03-58.png)

![](images/2025-12-03-15-04-07.png)

![](images/2025-12-03-15-04-14.png)

### Python, Git, Github and CI-CD - S38V308

![](images/2025-12-03-15-29-12.png)

![](images/2025-12-03-15-29-22.png)

![](images/2025-12-03-15-31-37.png)

![](images/2025-12-03-15-32-47.png)

### Data Serialization Formats: XML, JSON, and YAML - S38V309

![](images/2025-12-03-15-35-29.png)

![](images/2025-12-03-15-36-05.png)

![](images/2025-12-03-15-36-51.png)

***JSON is most likely to be tested on CCNA - must be able to read JSON format

![](images/2025-12-03-15-38-05.png)

![](images/2025-12-03-15-38-24.png)

![](images/2025-12-03-15-40-12.png)

![](images/2025-12-03-15-42-38.png)

![](images/2025-12-03-15-44-33.png)

![](images/2025-12-03-15-46-00.png)

![](images/2025-12-03-15-54-16.png)

![](images/2025-12-03-16-14-08.png)

![](images/2025-12-03-16-15-14.png)

![](images/2025-12-03-16-17-14.png)

### APIs - CRUD, REST, and SOAP - S38V310

![](images/2025-12-03-16-20-07.png)

![](images/2025-12-03-16-21-11.png)

![](images/2025-12-03-16-21-48.png)

![](images/2025-12-03-16-23-09.png)

![](images/2025-12-03-16-23-55.png)

![](images/2025-12-03-16-24-53.png)

- **Caching** is holding a copy of a resource that the server is responsible of serving. Caching is commonly used for highly requested resources. 
    - Cacheability refers to the server's ability to store responses and reuse them for identical future requests.

![](images/2025-12-03-16-27-07.png) 

![](images/2025-12-03-16-27-54.png)

![](images/2025-12-03-16-31-08.png)

- ^used for putting/altering some info on a AAA server - doing a dry run to check and see if it works

![](images/2025-12-03-16-33-51.png)

![](images/2025-12-03-16-35-03.png)

### Model Driven Programmability - YANG, NETCONF, RESTCONF and gRPC - S38V311

![](images/2025-12-03-16-38-09.png)

![](images/2025-12-03-16-38-55.png)

- ^ YANG: for using remote devices to interact with our network devices, to be able to pull information from them and to push information from them

- the client, which is the API, which is working with the network device, and the server, which is the network device itself, they need to have a standardized format for that data to be laid out in.

![](images/2025-12-03-16-42-12.png)

![](images/2025-12-03-16-42-24.png)

![](images/2025-12-03-16-43-33.png)

![](images/2025-12-03-16-44-47.png)

![](images/2025-12-03-16-45-05.png)

![](images/2025-12-03-17-14-52.png)

![](images/2025-12-03-17-15-45.png)

![](images/2025-12-03-17-16-42.png)

![](images/2025-12-03-17-17-17.png)

![](images/2025-12-03-17-17-48.png)

![](images/2025-12-03-17-18-59.png)

### Lab Demo - Testing APIs  with Postman - S38V312

![](images/2025-12-03-17-20-47.png)

![](images/2025-12-03-17-21-45.png)

![](images/2025-12-03-17-21-55.png)

![](images/2025-12-03-17-22-05.png)

Using IOS XE virtual router w/ IOS XE OS (supports Restful API)

#### Get information from router:

![](images/2025-12-03-17-23-53.png)

![](images/2025-12-03-17-24-47.png)

![](images/2025-12-03-17-24-55.png)

![](images/2025-12-03-17-25-28.png)

![](images/2025-12-03-17-25-56.png)

![](images/2025-12-03-17-26-36.png)

![](images/2025-12-03-17-27-47.png)

- IOS XE is using Basic Authentication

![](images/2025-12-03-17-28-31.png)

![](images/2025-12-03-17-28-53.png)

![](images/2025-12-03-17-29-34.png)

![](images/2025-12-03-17-29-53.png)

![](images/2025-12-03-17-30-26.png)

#### Put information on Router:

- We will create a new loopback interface for it

![](images/2025-12-03-17-31-41.png)

![](images/2025-12-03-17-31-52.png)

![](images/2025-12-03-17-32-10.png)

![](images/2025-12-03-17-33-41.png)

![](images/2025-12-03-17-35-14.png)

![](images/2025-12-03-17-35-55.png)

- **irl next you should send a POST request to save the configuration but not in sandbox

![](images/2025-12-03-17-37-24.png)

![](images/2025-12-03-17-37-41.png)

- Postman is good for testing & help creating script but you'd want an actual script to do things irl

### Configuration Management Tools - Ansible and Terraform

![](images/2025-12-03-17-43-45.png)

![](images/2025-12-03-17-43-58.png)

![](images/2025-12-03-17-45-44.png)

![](images/2025-12-03-17-46-23.png)

![](images/2025-12-03-17-49-15.png)

![](images/2025-12-03-17-49-31.png)

![](images/2025-12-03-17-51-31.png)

![](images/2025-12-03-17-52-00.png)

![](images/2025-12-03-17-53-47.png)

![](images/2025-12-03-17-54-33.png)

![](images/2025-12-03-17-55-15.png)

![](images/2025-12-03-17-57-10.png)

- ^Know that for the exam

![](images/2025-12-03-17-57-48.png)

### Ansible Lab Demo - Network Automation with Ansible - S38V314

![](images/2025-12-03-17-59-47.png)

- We will add new loopback interface to each router and Configure them w/ their NTP server
& enable logging synchronous on SSH VTY lines

![](images/2025-12-03-18-01-22.png)

![](images/2025-12-03-18-01-37.png)

![](images/2025-12-03-18-03-13.png)

![](images/2025-12-03-18-03-38.png)

Check that Routers on hosts file on this linux machine:

![](images/2025-12-03-18-04-36.png)

Check Ansible Inventory:

![](images/2025-12-03-18-04-55.png)

See what files are in Ansible home directory:

![](images/2025-12-03-18-08-06.png)

Check host vars and see what's written inside:

![](images/2025-12-03-18-09-03.png)

![](images/2025-12-03-18-10-22.png)

- ^have the specified loopback address on the variables now

ping all routers to check if we can SSH:

![](images/2025-12-03-18-12-45.png)

![](images/2025-12-03-18-13-03.png)

Look at different Ansible Modules:

![](images/2025-12-03-18-14-08.png)

Look @ them in program:

![](images/2025-12-03-18-15-18.png)

![](images/2025-12-03-18-15-36.png)

- ^Can see the pre-built scripts

Now we're push the configurations to the routers w/ our playbook:

Look @ playbook:

![](images/2025-12-03-18-17-39.png)

![](images/2025-12-03-18-18-49.png)

Check Documentation for correct module:

![](images/2025-12-03-18-19-42.png)

![](images/2025-12-03-18-20-03.png)

![](images/2025-12-03-18-21-26.png)

![](images/2025-12-03-18-21-41.png)

Run the playbook:

![](images/2025-12-03-18-22-10.png)

![](images/2025-12-03-18-22-20.png)

![](images/2025-12-03-18-22-29.png)

Check this now:

![](images/2025-12-03-18-23-20.png)

![](images/2025-12-03-18-23-33.png)

![](images/2025-12-03-18-23-39.png)

![](images/2025-12-03-18-23-58.png)

- **Ansible won't make any changes if it's already been done

### SDN Software Defined Networking - S38V315

![](images/2025-12-03-18-29-19.png)

![](images/2025-12-03-18-29-55.png)

![](images/2025-12-03-18-31-03.png)

![](images/2025-12-03-18-38-58.png)

![](images/2025-12-03-18-39-16.png)

**Important for CCNA**:

![](images/2025-12-03-18-42-52.png)

AWS example:

This is @ the Application Layer:

![](images/2025-12-03-18-43-29.png)

- ^front end user sees this, this communicates w/ Controller using Northbound REST API, etc

![](images/2025-12-03-18-44-49.png)

![](images/2025-12-03-18-45-44.png)

### Software Defined Architecture - Catalyst Center (formerly DNA center) 

![](images/2025-12-03-18-49-17.png)

![](images/2025-12-03-18-50-47.png)

![](images/2025-12-03-18-50-57.png)

![](images/2025-12-03-18-51-57.png)

![](images/2025-12-03-18-52-46.png)

![](images/2025-12-03-18-53-10.png)

![](images/2025-12-03-18-54-18.png)

![](images/2025-12-03-18-55-56.png)

![](images/2025-12-03-18-58-59.png)

![](images/2025-12-03-18-59-17.png)

![](images/2025-12-03-19-00-13.png)

![](images/2025-12-03-19-01-54.png)

![](images/2025-12-03-19-03-14.png)

![](images/2025-12-03-19-04-02.png)











