Introduction to Cloud Infrastructure Technologies
=================================================

Virtualization
--------------
* **Cloud Computing** is a computing model that enables remote allocation of computing resources, owned by a third party, to be utilized by end users

* The definition according to the **NIST (National Institute of Standard and Technology)** is "a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort service provider interaction"

* Most cloud service models fall into one of the following NIST categories:

    * **IaaS (Infrastructure as a Service)**

    * **PaaS (Platform as a Service)**

    * **SaaS (Sofware as a Service)**

* Additional service models introduced to describe the needs and requirements of clients of remote computing services:

    * **Analytics as a Service (AnaaS)**

    * **API as a Service (AaaS)**

    * **Big Data as a Service (BDaaS)**

    * **Business Process as a Service (BPaaS)**

    * **Code as a Service (CaaS)**

    * **Communications Platform as a Service (CPaaS)**

    * **Desktop as a Service (DaaS)**

    * **Database as a Service (DBaaS)**

    * **Function as a Service (FaaS)**

    * **Monitoring as a Service (MaaS)**

    * **Anything as a Service (XaaS)**

    * **Deez Nuts as a Service (DNaaS)**


### Key Features of Cloud computing

* **Speed and Agility**

* **Cost**

* **Easy Access to Resources**

* **Maintenance**

* **Multi-tenancy**

* **Reliability**

* **Scalability and Elasticity**

* **Security**


### Cloud Deployment Models

* **Private Cloud** designated and operated soley for one organization, can be built using a software stack such as OpenStack

* **Public Cloud** AWS, GCP, Azure. Cloud for anybody that will pay

* **Hybrid Cloud** combination of public and private cloud, beneficial for storing sensitive information on the private cloud and meeting temporary resource needs during peak or times of high demand by cloud scaling (known as **Bursting**)

* **Community Cloud** multiple organizations sharing a common cloud Infrastructure

* **Distributed Cloud** formed by distributed systems connected to a single network

* **Multicloud** organization using multiple cloud vendors for it's workload, usually to avoid vendor lock-in

* **Poly Cloud** one organization uses multiple public cloud providers to leverage specific services from each provider


### Virtualization

* **Examples of Type-1 Hypervisors:**

    * **Proxmox** They didn't ACTUALLY put it on this list, but less people are sleeping on it everyday

    * **AWS Nitro**

    * **Microsoft Hyper-V**

    * **Nutanix AHV**

    * **Oracle VM Server for SPARC**

    * **Oracle VM Server for x86**

    * **Red Hat Virtualization**

    * **VMWare ESXi**

    * **Xen**

* **Type-2 Hypervisors:**

    * **Parallels Desktop for Mac**

    * **VirtualBox**

    * **VMware Player**

    * **VMWare Workstation**

* **Linux Kernel Modules that Fit Both Categories:**

    * KVM

    * bhyve

* **Software Emulation** occurs at both the system and user space levels, as supported by a tool such as QEMU, allows for any OS to run on any architecture, or for programs to run on originally unsupported systems. Can be used in conjunction with hypervisors such as KVM to provision VMs


### KVM Overview

* [Mental Outlaw](https://www.youtube.com/MentalOutlaw) has a great [video](https://www.youtube.com/watch?v=wxxP39cNJOs) on getting KVM set up with QEMU/virt-manager.

* **KVM** is a loadable virtualization module of the Linux kernel that converts the kernel into a hypervisor capable of managing guest VMs. Originally designed for x86, but ported to FreeBSD(umm what? this is listed but it's an OS, not a CPU architecture...maybe they know something I don't? Whatever.), S/390, PowerPC, IA-64, and ARM

### KVM Features

* **KVM** is an open-source software that provides hardware-assisted virtualization with support for various guest OSs, such as Windows, Solaris, or Linux

* Enables device abstraction of network interfaces, disk, but not the processor. Instead, it exposes /dev/kvm interface that can be used by an external user space host for emulation. 

* **Examples of User-Space Tools** for KVM VM management include **KubeVirt**, **QEMU**, and **virt-manager**

* Supports **nested guests**, which is exactly what it sounds like. Also supports hotpluggable devices such as CPUs and PCI devices 

* **Overcommitting** is possible for the allocation of additional virtualized resources that may not be available on the system


### Creating a Virtual Machine Instance on the KVM Hypervisor 

* **virt-manager** GUI/ VMM (Virtual Machine Manager) for KVM VM instances

* This is honestly pretty straightforward and similar to VirtualBox as far as setting up a VM goes, although I did have to follow the Mental Outlaw video linked above with the installation and setting up services/configs


### Benefits of Using KVM

* its FOSS

* provides efficient hardware-assisted virtualization for a crapload of OSs (Linux, BSD, Solaris, Windows, MacOS, ReactOS, Haiku)

* provides para-virtualization of Ethernet cards, disk I/O controllers, and graphical interfaces for guest OSes

* highly scalable

* employs advanced security features, utilizing SELinux. Provides **MAC (Mandatory Access Control)** between VMs, and won a bunch of military awards for being dope as shit


### VirtualBox Overview

* It's like KVM but not as good

* GPLv2 license


### Benefits of Using VirtualBox 

* Also FOSS 

* Runs on all mainstream OSs 

* choose between software or hardware-based virtualization

* easy to use 

* run virtualized apps side-by-side with normal desktop applications 

* provides **teleportation** (live migration)


### Vagrant Overview

* **Benefits of using VMs in a development environment:**

    * Reproducible environment

    * Management of multiple projects, each in it's isolated and restricted environment

    * Sharing the environment with other teammates

    * Keeping the development and deployment environments in sync

    * Running consistently the same VM on different OSes leveraging hypervisors such as VirtualBox, VMware, and KVM

* **Vagrant** is a cross-platform cli tool by HashiCorp used to build and distribute virtualized development environments, ships with limited features but has extensive plugin support, recently added Docker support allowing it to manage containers as well as VMs


### Managing VMs with Vagrant

* **Vagrantfile** describes how VMs should be configured and provisioned, Ruby syntax config file contains all the information about provisioning and configuring a set of machines. Is portable, but there should only be 1 Vagrantfile per project. The **vagrant** command reads the configuration given to the config file and does different opperations such as **up**, **ssh**, **destroy**, etc. **vagrant** also has sub-commands such as **box** to manage Box images, **rdp** to connect to VMs using RDP protocol. Link to the documentation [here](https://developer.hashicorp.com/vagrant/docs/cli). 

* **Boxes** the package format for the Vagrant environment. The Vagrantfile requires an image, which is then used to instantiate VMs. Box images can be versioned and customized to specific needs simply by updating the Vagrantfile accordingly

* **Providers** the underlying engines or hypervisors used to provision VMs or containers. Vagrant default is Virtualbox, but also supports Hyper-V, VMware, and Docker out of the box. Custom providers like AWS may be configured as well

* **Synced Folders** feature that allows us to sync a directory on the host system with a VM, helping the user manage shared files/directories easily

* **Provisioners** allow us to automatically install software and make configuration changes after the machine is booted, part of the **vagrant up** process. Types of provisioners available include File, Shell, Ansible, Puppet, Chef, Docker, Podman, Puppet, and Salt

* **Plugins** extend the functionality of Vagrant

* **Networking** Vagrant provides high-level networking options for port forwarding, network connectivity, and network creation, allowing for cross-provider portability

* **Multi-Machine** Vagrantfile can describe multiple VMs, typically intended to work together or may be linked between themselves


### Benefits of Using Vagrant

* Automates setup of 1 or more VMs

* Introduces consistency in infrastructure provisioning though Vagrantfile

* Flexible cross-platform tool

* Support for Docker containers as well as VMs provisioned with VMware, VirtualBox, and Hyper-V

* Easy to install/configure 

* Very useful in multi-dev teams


Infrastructure as a Service (IaaS)
---------------------------------

* **IaaS** is a cloud service model that provides on-demand physical and virtual computing resources, storage, network, firewall, and load balancers, utilizing hypervisors such as Xen, KVM, VMware ESXi, Hyper-V, or Nitro 

* It's the backbone of all other cloud services, providing computing resources, after provisioning of the computing resources, other services are set up on top. Enables devs to provision and destroy isolated test environments as needed, when needed, quickly, and safely. Provisioning process can be easily reproduced to add consistency to the test environment, not only by the same dev, but but the entire team if desired. Cool. Cool cool cool.   


### Amazon EC2 Overview

* **AWS** iS oNe Of ThE lEaDiNg ClOuD sErViCe Pr0v1d3rZ. Anyway, it's cloud services, whether Platform, Software, DB, Containers, Serverlezz, Machine Learning (to name a few, hurumph ho her derrr) rely heavily on it's infrastructure.

* **Amazon Elastic Compute Cloud (Amazon EC2)** is part of Amazon's infrastructure as a service (IaaS) model. It allows users and enterprises alike to build a reliable, flexible, and secure cloud infrastructure for their apps and workloads on Amazon's proprietary platform. **Console** is the web interface for AWS resources

* EC2 instances are VMs that run on Amazon's physical infrastructure (duh) and Amazon also has a [**CLI tool**](https://aws.amazon.com/cli/) that you can use.

* EC2 services run on various type-1 hypervisors, such as Xen, KVM, and **Nitro**, which is a newer KVM-based lightweight hypervisor that delivers close to bare-metal performance


### Features and Tools

* When provisioning EC2 instances, users can manage hardware profile, OS image with software package, additional storage, attached network, and firewall rules

* **Amazon Machine Images (AMI)** are preconfigured images with the information needed to launch EC2 instances, including OS and software packages. Stored in the AWS repo and used to quickly launch instances, images customizable by anybody

* **Instance Types** determine the virtualized hardware profile of the instance to be launched. Each instance is preconfigured with different compute, memory, and storage capabilities, and are categorized in instance families such as:

    * General purpose instances

    * Optimized instances for:

        - CPU-intensive applications such as ML, HPC (High-Performance Computing), batch workloads, and media transcoding

        - GPU-intensive applications such as ML and graphically, intensive, scientific engineering applications

        - RAM for in-memory databases, in-memory caches, and real-time data processing

        - Machine Learning, it gets its own category tool

        - SSD Storage for data-intensive workloads and distributed filesystems

* Additional configurable aspects of EC2 instances, related services and tools may include:

    * **Virtual Private Cloud (VPC)** for network isolation

    * **Security Groups** for VPC networks to control EC2 inbound/outbound traffic

    * **Amazon Elastic Block Store (EBS)** for persistent storage attachment

    * Dedicated hosts to provision instances on a physical machine reserved for our use

    * **Elastic IP** to remap a Static IP automatically

    * **CloudWatch** for monitoring resources and applications

    * **Auto Scaling** to dynamically resize resources


### Benefits of Using Amazon EC2

* Easy-to-use IaaS solution

* Flexble and scalable

* Provides a secure and robust functionality for computing resources

* Provides guest OS options that include *a handful* of Linux distributions, macOS, and Windows

* Enables automation

* Cost-effective (only pay for resources used)

* Designed to work in conjunction with other AWS components, while integrating with third-party automation tools

* Promises up to 99.99% uptime

* Provides specialized instances for workloads, such as HPC, ML, databases/data processing, batch workloads, media transcoding, and graphically intensive or engineering applications


### Azure Virtual Machine Overview

* **Azure Virtual Machine** service allows you to do cloud stuff through both the **Web Portal** and the **Azure Cloud Shell**, which is configurable in PowerShell or Bash


### Features and Tools

* **VM Image** defines the base OS or the app for the VM. Both Linux and Windows VMs can be launched from images available through the **Azure Marketplace** Why no MacOS bro? Oh yeah.....ha. 

* **VM Size** determines the type and capacity of the compute, memory, storage, and network resources for the VM to be launched

* VMs are grouped in **families** based on their inteded usage:

    * General purpose for development and testing environments, low traffic web servers, and small databases

    * Optimized VMs for:

        - CPU for medium traffic web servers, batch processes, and application servers 

        - GPU for heavy graphic rendering, video editing, and deep learning 

        - RAM for relational databases and in-memory analysis

        - **HPC** (High Performane Compute)

        - Storage for data warehousing and large transactional databases

* **Additional Configurable Aspects of VMs:**

    * Network security groups to manage network traffic

    * SSD or HDD for persistent storage attachment, with optional encryption

    * Dedicated hosts to provision VMs on a physical machine reserved for OUR (Communism intensifies) use

    * Accelerated networking for low latency and high throughput

    * Virtual network for network isolation

    * Monitoring resources and applications

    * Resource Manager templates for VM development

    * Seamless hybrid connections

    * Automated backups


### Benefits of Using Azure Virtual Machine

* Easy-to-use IaaS solution

* Flexible and scalable

* Provides a secure and robust functionality for your compute resources

* Provides guest OS options such as *several* Linux distros and Windows

* Enables automation

* Cost-effective, only pay for time and resources used

* Designed to work in conjunction with other Azure services


### DigitalOcean Droplet Overview

* **DigitalOcean** is a leading cloud service provider. Instances are Linux VMs launched on top of the KVM type- hypervisor (primarily with SSDs) called **droplets**


### Features and Tools

* Monitoring to collect performance metrics

* Cloud firewalls to secure network infrastructure

* Backups that can be automated, allowing for easy droplet restores or to launch new pre-configured droplets

* Snapshots to be used as restore points after a failed upgrade or config change

* Team Management for collaboration

* Block Storage for droplet storage

* Spaces for scalable and secure storage solutions aimed to store and deliver data

* Load Balancers for traffic distribution 

* Floating IPs for flexibility when assigning IPs to droplets and to release them when no longer needed 

* APIs for programmatic droplet launching

* Networking features, such as DNS IPv6, and private networking 


### Benefits of Using DigitalOcean

* Allows you to configure a cloud within 55 seconds

* Flexible and scalable

* Promises up to 99.99% uptime for select services 

* Provides a high level of security by using KVM virtualized droplets 

* Provides sever Linux distros as guest OS options

* Enables automation

* Cost-effective, blah blah cloud blah blah pay for what you use 

* Focused on providing a simple, user-friendly experience

* Uses high-performance SSDs 

* Offers a one-click installation of a multitude of applications and application stacks, including CloudBees, Jenkins, LAMP, Docker, K8s, NGINX, and WordPress 


### Google Compute Engine Overview 

* **GCP (Google Cloud Platform)** is...yeah, its GCP dawg

* **GCE (Google Compute Engine)** is part of Google's IaaS model service, services are enable by KVM type-1 hypervisor, running on Google's physical infrastructure, enabling Windows and Linux guest VMs

* **Console** is GCP's web interface


### Features and Tools

* **GCE Machine Types:** 

    * General-purpose machines 

    * Memory-optimized

    * Compute-optimized

    * Accelerator-optimized

    * Shared-core

* **Configurable Aspects of GCE VMs (and related services):**

    * Storage disks

    * Networking VPC and firewalls

    * Snapshots

    * Cloud Security Scanner

    * Health checks

    * Sole-tenant nodes

    * Network Endpoint Group


### Benefits of Using Google Compute Engine

* Flexible, allows you to scale easily

* Fast boot time 

* Very secure, encrypts all stored data

* Enables automation

* Provides *several* Linux Distros and Windows

* Cloud Cost-effective, that's the new term for it.

* Supports custom machine Types

* Supports VPC, load balancers, etc


### IBM Cloud Virtual Servers Overview

* **IBM Cloud**  is another cloud service provider (REALLY??!?!!), it's IaaS model is the **IBM Cloud Virtual Servers** service. 


### Features and Tools

* The 4 Supported Types of VMs:

    * **Public** for multi-tenants

    * **Dedicated** for single-tenants

    * **Transient** for ephemeral multi-tenants

    * **Reserved** for mult-tenants committed for a pre-specified term

* Like every cloud service so far, there are optimized profiles for specific workloads, these are:

    * **Balanced** for common cloud workloads

    * **Balanced Local Storage** for medium to large databases

    * **Compute** for compute-intensive deployments 

    * **Memory** for caching and analytics workloads

    * **Variable Compute** for workloads without constant high-CPU performance

    * **GPU** for high-performance deployments


### Benefits of Using IBM Cloud Virtual Servers

* Copypasta from every other single cloud benefits package


### Introduction to Linode Compute Instances

* **Linode** is brought to you by **Akamai Technologies**, defintiely read that one in Jack Rhysider's voice.


### Features and tools

* Linode Plan Types:

    * Shared CPU

    * Dedicated CPU

    * Premium Plans

    * High Memory Plans

    * GPU Plans


### Benefits of Using Linode Compute Instances

* Copypasta


### Oracle Cloud Compute Virtual Machines Overview

* One of **Oracle Cloud**'s most commonly used infrastructure products is **Cloud Compute**, which does all of the same old cloud stuff

* **Oracle Cloud Infrastructure Compute Virtual Machines** are offered in many shapes with **Oracle Compute Units (OCPUs)** to support a wide range of workloads and software platforms


### Features and Tools

* Different Infrastructure VM Types:

    - **Standard/General Purpose Instances** for most use cases

    - **Dense IO** high performance instances suitable for large database applications

* When provisioning cloud VMs, users are able to manage additional instance aspects and related services:

    - Flexible Image Management

    - Low latency block storage for boot volumes, for increased performance and reliability, and to facilitaet backups and restores

    - Secure and flexible network through full customizable private VCN (Virtual Cloud Networks)

    - High availability
