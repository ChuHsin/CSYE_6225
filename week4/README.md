# Virtualization (虚拟化)
 
## Benefits of Virtualization
* Effective way to reduce IT expenses while boosting efficiency and agility for all size businesses
* Reduce capital and operating costs
* Minimize or eliminate downtime
* Increase IT productivity, efficiency, agility and responsiveness.
* Provision applications and resources faster.
* Enable business continuity and disaster recovery.
* Simplify data center management
* Build a true Software-Defined Data Center.

## How virtualization Works
* Virtualization uses software to simulate the existence of hardware and create a virtual computer system.
* Doning this allows businesses to run more than one virtual system and multiple operating systems and applciations on a single server.
* This can provide economies of scale and greater efficiency.

## The Virtual Machine
* A virtual computer system
A tightly isolated software container with an operating system and application inside.
* Each self-contained VM is completely independent.
* Putting multiple VMs on a single computer enables several os and apps to run on just one physical server, or "host".

### Hypervisor
A thin layer of software called a **Hypervisor** decouples the VMs from the host and dynamically allocates computing resources to each VM as needed.

Hypervisor is what you install on the server to let you run vms.

## Key Properties of VMs
* Partitioning
  * run multiple os on one physical machine
  * divedde system resources betweeen virtual machines
* isolation
  * provide fault and security isolation at the harware level
  * preserve performance with advanced resource controls
* Encapsulation
  * Save the entire state of a virtual machine to files
  * Move and copy vms as easily as movign and copying files
* Hardware Independence
  * Provision or migrate any virtual machine to any physical server.

## Server Consolidation
Using server virtualization, a company can maixize the use of its server reources and reduce the number of servers required. The result is server consolidation, which improves efficiency and cuts costs.
合并服务器

## V is not cloud computing
* Cloud computing is not the same thing as virtualization, it's something you can do using virtualization.
* Cloud computing describes the delivery of shared computing resources on demand through the Internet.
* you can start by virtualizing your your servers and then move to cloud computing for even more agility and increased self-service.

# Amazon Elastic Computer Cloud (Amazon EC2)
* A web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.
* Reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.
* pay only for capacity that you actually use.
* Provides developers the tools to build failure resilient applications and isolate them from common failure scenarios.
* **Amazon EC2 is a virtual machine in the cloud.**

## EC2 Instance Types
* EC2 provides a wide selection of intance types optimized to fit different use cases.
* Different combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications.
* Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload.

## Instance Type Categories
* General Purpose
* Compute Optimized
* Memory Optimized
* Accelerated Computing (GPU)
* Storage Optimized
 
Google Cloud can customize your 

## EC2 Pricing
* On-Demand
  pay for compute capacity byt he hour with no long-term commitments or upfront payments.
  recommended for: low cost and flexibility with out any up-front payment or long-term commitment.

* Spot Instances
  allow you to bid on spare EC2 computing capacity for up to 90% off the On-Demand price.
  for: applications that have flexible start and end times.
  are only feasible at very low compute prices
  Users with urgent computing needs for large amounts of additional capacity.

* Reserved Instances
  capacity reservation.
  for applications that have steady state or predictable usage.
  Applications with steady state usage
  applications that may require reserved capacity
  1 or 3 year term to reduce their total computing costs.

* Dedicated Hosts
  A physical EC2 server dedicated for your use
  help you reduce costs by allowing you to use your existing server-dound software licenses, also help you meet compliance requirements.
* Dedicated Instances

## EC2 Features
* Secure login using key pairs
* Temporary and Permanent Storage Volumes
* Security Groups (firewalss)
* Static IPv4 address (Elastic IP address)
* Metadata, known as tags
* Subnets (virtual networks)

## Amazon Machine Image (AMI) & Instances
* A template that contains a software configuration (an os, an application server, and applications)
* From an AMI, you launch an instance, which is a copy of the AMI running as a virtual server in the cloud.
* You can launch multiple instances of an AMI
* Your instances keep running until you stop or terminate them, or until they fail.
* If an instance fails, you can launch a new one from the AMI

## Root Device Volume
When  you launch an instance, the root device volume contains the image used to boot the instance.
Instance can be launched with either
* AMIs backed by Amazon EC2 instance store
* AMIs backed by Amazon EBS

### AMIs backed by Amazon EC2 instance store
Instances that use instance stores for the root device automatically have one or more isntance store volumes available, with one volume serving as the root device volume.
When an instance is launched, the image taht is used to boot the isntance is copied to the root volume.
* Any data on the instance store volumes persists as long as the instance is running, but this data is deleted when the instance is termninated (instance store-backed instances do not support the Stop action) or if it fails()
* Your storage is local to the software that's running your virtual machine.

**If you need Persistant Storage**
### EBS-backed Instances
Instances that use EBS for the root device automatically have an Amazon EBS volume attached.
* When you launch an Amazon EBS-backed instance, an Amazon EBS volume is created for each Amazon EBS snapshot referenced by the AMI used.
* **EBS-backed instance can be stopped and later restarted without affecting data stored in teh attached volumes.**

### Amazon Elastic Block Store (Amaozn EBS)
* Provides block level storage volumes for use with EC2 instances.
* Your VM and your EBS volume has to be in the same availability zone.
* storages volumes taht persist independently from the life of the instance.
* EBS is recommended when data must be quickly accessible and requires long-term persistence.

### IOPS - Input/Output Opeartions Per Second
* A unit of measure representing input/output operations per second. measured in KiB, and the underlying drive technology determines the maximum amount of data that a volume type counts as a single I/O
* for SSD, 256 KiB is an I/O, for HDD is 1024 KiB, becuase SSD volumes handle small or random I/O much more efficiently than HDD volumes.
* IOPS count

### Security Group
### Instance Metadata and User Data
* Instance metadata is data about your instance that you can use to configure or manage the running instance.
* You can also use instance metadata to access user data that you specified when lauching your instance.
* For example, you can specify parameters for configuring your instance, or attach a simple script.

### Creating Your Own AMI
You can launch an instance from an existing AMI, customize the instance, and then save this updated configuration as a custome AMI.
Instances launched from this new custom AMI include the customizations that you made when you craeted the AMI.

## HashiCorp Packer
An open source tool for creating identical machine images for multiple platforms from a single source configuration.

### AMI Use Cases
* Golden Images
* Environment Parity
* Auto-scaling Acceleration


# Infrastructure as Code
## Why ?
* Virtualization, cloud, containers, server automation, and software-defined networking should simplify IT operation work.
* It should take less time and effort to provision, configure, update, and maintain services.
* Problems should be quickly detected and resolved, and systems should all be consistently configured and up to date.
* IT staff should spend less time on routine drudgery, having time to rapidly make chagnes and improvements to help their organizaitons meet the ever-changing needs of the modern world.
* Adopting cloud and automation tools immediately lowers barriers for making changes to infrastructure,
* Managing changes in a way that improves consistency and reliability doesn't come out of the box with the software. It takes people to think through how they will use the tools and put in place the systems, processes, and habits to use them effectively,

## What is Infra as Code?
* Infrastructure as code is an approach to infrastructure automation based on practices from software development.
* It emphasizesconsistent, reppeatable routines for provisioning and changing systems and their configuration.
* Changes are made to definitions and then rolled out to systems through unattended processes that include thorough validation.


* Modern Tooling can treat infrastructure as if it were software and data.
* Apply software development tools such as version control systems, automated testing libraries, and deployment orchestration to manage infrastructure.
* It also opens the door to exploit development practices such as test-driven development, continuous integration, and continuous delivery.

 ## Goals of Infrastructure as Code
 * IT infrastructure supports and enables change, rather than being an obstacle or a constraint.
 * Changes to the system are routine, without drama or stress for users or IT staff.
 * IT staff spends their time on valuable thing sthat engage their abilities, not on routine, repetitive tasks.
 * Users are able to definem provision, and manage the resources they need, without needing IT staff to do it for them.
 * Teams are abel to easily and quickly recover from failures, rather than assuming failure can be completely prevented.
 * Improvements are made continuously, rather than done through expensive and risky projects.
 * Solutions to problems are proven through implementing, testing, and measuring them, rather than by discussing them in meetings and documents.

## Practicing

## Infrastructure as Code with Terraform
### Terraform Files
in the HashiCorp Configuration Language (HCL)

### Provider
to configure the provider(s) you want to use. "aws"

### Initialize Working Directory
When you're first starting to use Terraform, you need to run terraform init to tell Terraform to scan the code, figure out which providers you're using, and download the code for them.
You need to run init any time you start with new Terraform code.

### Create an Execution Plan
Terraform plan command.
Try run, check whether the execution plan for a set of changes matches your expectations without making any changes to real resources or to the state.