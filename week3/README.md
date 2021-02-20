
# Fundamentals of Computer Networking

LAN: local area network
WAN: wide area network

LAN is usuallly confined to local geographic area whereas WAN is spread across a larger geographic area. WAN is usually made of multiple LANs.
Systems are not onnected directly to each other, instead they are indiretly connected to each other via a switch or router.

### Communication Link 
* coaxial, copper or fiber cable or radio waves.
* transmit data at different rates.
* bits/second
* 8 bits/second = 1 byte/second -- b / B

Bandwidth: maximum rate of data transfer across a given path.

### Network Protocols
Define the format and order of messages exchanged between two or more communicating entities as well as the actions taken on transmission and /or receipt of a message or other event.

***Protocols defines the structure of the message that's being sent and received.***

## Network Protocol Stack & OSI Reference Model
Five-layer Internet protocol stack:
```
Application
Transport
Network
Link
Physical
```

Seven-layer ISO OSI reference model
OSI: Open Systems Interconnection
```
Application
Presentation
Session
Transport
Network
Link
Physical
```
### Application Layer
Network applications, application-layer protocols (HTTP, FTP, etc.) 
Layer 5 and Layer 6 are mainly used by the application layer.

### Transport Layer
The transport layer transports application layer messages between client and server side of the application.
Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) are examples of some popular transport layer protocols.

### Network Layer
Responsible for moving transport layer protocols from one host to another.
defines the fields in data packet(datagram) as well as how the end systems and routers act on this field.
If the data packet is too large, network layer might split it into multiple packets which will be combined into one at the receiving node.
Most popular network layer protocol is the Internet Protocol (IP)

### Link Layer
moving packet from one node to another

### Physical Layer
move the individual bits

Presentation & Session Layer

### Transmission Control Protocol TCP
Reliable Data Tranfer -- ensures that data is delivered from sending process to receiving process **correctly** and **in order**
* connection based - Sender will keep connection with receiver open until it is done successfully sending all the data packets.
* **error checking** and **erroneous** packets will be retransmitted from source to destination.
* has congestion control. It will not send next chunk of data until it has received OK(ACK) fromt he receiver.
* Common application-layer protocol that use TCP/IP are HTTP, FTP, SMTP, etc.

### User Datagram Protocol (UDP)
* UDP is designed to do as little work as possible to send data.
* has no congestion control. Data is transmitted as soon as it can.
* no reliability guarantee, don't have any acknowledgment back to the sender. It doesn't care if the message was successfully received.
* has not overhead of connection establishment. 没有提前建立的网络连接，像 TCP 会先连通网络，然后交替传输
* no connection state is maintained as we are not tracking successful delivery of data or the order in which data is sent. --> always used for DNS queries, video streaming, dynamic host configuration protocol

### Internet Protocol (IP)
* principal communications protocol in the internet protoco lsuite for relaying datagrams across network boundaries.
* best-effort delivery service, makes no guarantee about delivering correct data, the order in which it is delivered or avoidance of delivering duplicate data pretty much like UDP. Both layer 3, TCP like layer 4.
* First major version - IPv4, successor IPv6

### IPv4
* uses 32 bit addressing system
* address space is approximately 4 billion IP addresses.
* each system on network must have globally unique IP address.

32 bits binary -> 4 * 8 == 4 bytes == 4 dotted-decimal notation
172.16.254.1

### Subnet
* a subnet is isolated network
address of a network/bit-length of the prefix.
if mask bits == 8
hosts = 2^(32 - 8) - 2

mask bits define the size of your network.

for every subnet that you create, one of the IP address is reserved for the gateway, the last is reserved for Multicast

the not zero position is the prefix for every IPs under this subnet

you won't create a network with slash 32

### IPv4 Address Exhaustion
have been exhausted since 2011

### Network Address Translation (NAT)
* NAT allows sharing of one Internet-routable IP address of a NAT gateway for an entire private network.
* think of your router as a NAT gateway
* NAT allows ISPs to support mroe systems with the limited availability of public IPs
* IoT has significantly increased number of systems connected to internet.

From A to B :
From A to B - C -> From C to B;
B to C - C -> From B to A;


### IPv6
Most recent version of Internet Protocol
uses 128 bit addressing ysstem
does not support NAT

eight groups of four hexadecimal digits with the groups being separated by colons (:)

# Virtual Private Cloud 
## VPC
* allows you to lauch resources into a virtual network you have defined.
* a virtual network that belongs to you and is logically isolated from virtual networks that belong to other users.
* default VPC on both AWS and GCP will include an internent gateway.
* An internet gateway enables your instances to connect to the internet.

### Route Tables
* A route table contains a set of rule, called routes, that are used to determine where network traffic is directed.
* each subnet in your VPC must be associated with a route table;
* the table controls the routing for the subnet.
* A subnet can only be associated with one route table at a time, but you can associate multiple subnets with thte same route table.

### Internet Gateways
* An Internet gateway is a horizontally scaled, redubdant, and highly available VPC component that allows communication between instances in your VPC and the Internet.
* It imposes no availability risks or bandwidth constraints on your network traffic.
* An Internet gateway serves two purposes:
  * to provide a target in your VPC route tables for Internet-routable traffic
  * to perform network address translation(NAT) for instances that have been assigned public IPv4 addresses.
* An Internet gateway supports IPv4 and IPv6 traffic.

### Elastic IP addresses
* is a static, public IPv4 address designed for dynamic cloud computing.
* we can stop and start our instance at any time, and they still have the same IP address.

### Security Groups
* acts as a virtual firewall for your instance to control inbound and outbound traffic.
* rules that control the inbound traffic and outbound traffic to instances.
* act as instance level



# Cloud Computing
### On-Premise 前提假设
Servers are acquired, operating systems are installed, other hardware may be invovled, but all of that lives within your four walls, or the walls of your datacenter.

### Scaling
Scaling represents the ability of the resource to handle increased or decreased usage demands. The following are types of scaling:
* Horizontal Scaling - scaling out and scling in
* Vertical Scaling - scaling up and scaling down
#### Horizental
out --> adding servers, in --> remove servers; doesn't have down time.
#### Vertical
when you vertical scaling, you are adding more capacity to your resource. Have to re-configure, always have down time.

## Business Drivers
### Capacity Planning
the process of determining and fulfilling future demands of an organization's IT resources, products and services.
discrepancy between the capacity of an IT resource and its demand. Over-provisioning, under-provisioning.

* Lead Strtegy
* Lag Strategy
* Match Strategy
requires estimating usage load fluctuations.
average server utilization levels are often under 20%. more pronounced the variation, the more the waste.

### Cost Reduction 
* Cost of acquiring new infrastructure
* Cost of its ongoing ownership

capital expenses to operating exprenses
Absense of up-front CapEx allows capital to be redirected to core business investment.



### Organizational Agility
ability to adapt and evolve to successfully face change caused by internal and external factors.

is the measure of an organizatio's responsiveness to change.
Up-front investments and infrastructure ownership costs that are required to enable new or expanded business solutions may themselves be prohibitive.(高昂的)

## Cloud Computing
*"a style of computing in which scalable and elastic IT-enabled capabilities are delivered as a service to external customers using Internet technologies."*

**5 essential characteristics
3 service models
4 deployment models**

### Cloud Characteristics
For an IT environment to be considered cloud.
1. #### On-demand self service
   consumer can unilaterally access cloud-based IT resources.
   giving the cloud consumer the freedom to self-provision these IT resources.
   once configured, usage of the self-provisioned IT resources can be automated, no further involvement is required.

2. #### Broad Network Access
   widely accessible
   ubiquitous, support for a range of devices, transport protocols, interfaces, and security technologies.
3. #### Resource Pooling (multitenancy)
   an instance of the program to serve different consumers (tenants) and each is isolated from the other.
   rely on the user of virtualization technologies.
   can be dynamically assigned and reassigned, according to cloud service consumer demands.
4. #### Elasticity
   automated ability of a cloud to transparently scale IT resources, predetermined.
   a core justification for the adoption of the cloud computing, it is closely associated with reduced investment and proportional cost benefit.
5. #### Measrued Usaege
   the ability of cloud platform to keep track of the usage of its IT resoureces,  primarily by cloud consumers.
   can charge a cloud consumer only for the IT resources actually used, or timeframe (subscription)

### Cloud Delivery Models
Applications -> Data -> Runtime -> Middleware -> O/S -> Virtualization -> Servers -> Storage -> Networking

1. ### IaaS Infrastructure as a Service
   provides Hardware, networking, connectivity, OS, and other Raw IT resources;
   provides consumer high level of contorl and responsibility over its configuration and utilization
   offer customized physical hardware for servers, load balancers, Gateways, firewalls, Instrusion Detection System and Intrusion Prevention Systems
   consumer is responsible for securing the "raw" IT resources
   AWS, GCP, MS Azure, IBM SoftLayer, Rackspace
2. ### Paas Platform as a Service
   "ready to use" environment to deploy applications
   consumers do not have control over or manage the underlying cloud infrastructure;
   Heroku, IBM BlueMix and Google App Engine.
3. ### SaaS Software as a Service
   product, generic utility
   Gmail, GitHub, Google Drive

### Cloud Depolyment Models
1. #### Public Cloud
   is provisioned for open use by the general public
   provider is responsible for the creation of on-going maintenance of public cloud and its IT resources
2. #### Community Cloud
   public cloud that access is limited to a specific community of cloud consumers
   AWS GovCloud
3. #### Private Cloud
   enable an organization to use cloud computing techonology as a means of centralizing access to IT resources by defferent parts, locations, or departments of the organization.
   mitigate some of the risks of public cloud, since organizatio nhas much higher level of control


# AWS
Console home page

## IAM
### IAM Features
Shared access to your AWS account
Granular permissions
Secure access to AWS resources for applications that run on Amazon EC2

IAM is secure by default, users have no access to AWS resources until permissions are explicitly granted.

Flexible security credential management
password, key pairs, X.509 certificates, MFA

Leverage external identity systems
support federation from corporate systems from other companies.

