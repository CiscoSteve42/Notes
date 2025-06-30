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

**blah blah blah, more of the same cloud service bs, lets move on to OpenStack because its actually pretty cool**
--------------------------------------------------------

* **OpenStack** lets you build cloud computing platforms

    * It began as a joint project betwenn NASA (nasasucks.gov) and Rackspace in 2010 (the year I graduated! (barely lol))

    * it's an open source software platform released under the Apache 2.0 License, also part of the OpenOpera...OtepIntern...OprahInfared??? ...OpenInfra Foundation. Yeah, that one.

* **Components and Features (Strap in Buckaroos)**

    * **Nova** a compute service that implements scalable and on-demand access to compute resources, including bare metal, virtual machines, and containers (yes, I started copypasta'ing instead of handwriting EVERYTHING, it's a 50 hour course I'm not worried about typing speed (I'm also not handwriting because I'm left handed and I drag my hand like a mf'er), fight me.)

    * **Ironic** a bare metal provisioning service part of hardware lifecycle services (and the reason that I use the word "yeet" as a 33 year old that has never played Fortnite a second in their life)

    * **Cyborg** *DC Reference* is a lifecycle management service for GPU and ASIC-based devices, part of Hardware lifecycle services.

    * **Swift** (I'm torn between making a TayTay or iOS joke here) is the object store part of Storage services that provides a highly available, distributed, eventually consistent object/blob store.

    * **Cinder** the block storage part of Storage services that provides an abstraction layer over the management of block storage devices through a self-service API.

* Skipping the rest of these to move onto the PaaS Chapter.

Platform as a Service (PaaS)
----------------------------

### Cloud Foundry Overview

* **Cloud Foundry (CF)** is an open source Platform as a Service (PaaS) framework aimed at developers in large organizations, that is portable to any cloud, highly interoperable, has an architecture supporting any programming language, and integrates easily with various cloud and on-premises tools. In addition to supporting any type of application, it provides means for these applications to access external resources through application services gateway.

* While CF can be deployed on-premises, it is recommended to install it on one of the supported [IaaS](https://www.cloudfoundry.org/the-foundry/#providers), such as Amazon AWS, Microsoft Azure, Google Cloud Platform (GCP), IBM Cloud, OpenStack, or VMware vSphere. Stable Cloud Foundry releases are also available through several certified commercial [distributions](https://www.cloudfoundry.org/#cert-distros) as well, such as Atos Cloud Foundry, Cloud.gov, SAP Cloud Platform, VMware Tanzu (formerly known as Pivotal Cloud Foundry), or others.

* CF aims to address challenges faced by developers in large organizations through a collection of customized technologies. Popular core components such as the Cloud Foundry API, CF CLI, Korifi, Garden, Diego, Eirini, Paketo Buildpacks, Stratos UI, together with BOSH, Quarks, and a set of extensions such as the Open Service Broker API make up the Cloud Foundry platform.

### Features

* Application portability
* Application auto-scaling
* Application isolation
* Centralized platform management
* Centralized logging
* Dynamic routing
* Application health management
* Role-based application deployment
* Horizontal and vertical scaling
* Security
* Support for different IaaS platforms.

### Cloud Foundry BOSH

**Cloud Foundry BOSH** is an open source tool for release engineering, deployment, lifecycle management, and monitoring of complex distributed systems, enabling developers to easily version, package and deploy software in a reproducible manner.

* BOSH aims to ease the process of building and administering consistently similar environments from development to staging and production. BOSH was designed to be the one tool to solve versioning, packaging, and reproducible software deployments as a whole, a collection of activities otherwise performed by tools such as Chef, Puppet, and Docker in various non-standard approaches. 

* BOSH follows the four principles of release management:

    * *identifiability* of all components making up a release,
    * *reproducibility* of integration that guarantees operational stability,
    * *consistency* through a stable framework for development, deployment, audit and software components accountability, and
    * *agility* for software release automation according to software engineering best practices for Continuous Integration and Continuous Delivery.

* BOSH can be installed on-premises on supported OSes such as several Linux distributions, macOS, and Windows. A popular on-premises hypervisor, VirtualBox is also supported. BOSH can be installed on supported IaaS providers as well, such as AWS, Microsoft Azure, GCP, IBM Cloud, OpenStack, VMware.

### Running Apps with `cf push`

* A powerful feature of the Cloud Foundry platform is its command line interface (CLI) that allows users to interact with various components of the platform to manage infrastructure and application deployments. 

* Applications can be pushed to Cloud Foundry through the cf push command, one of the many commands part of the cf CLI. This command is highly customizable, however, it can be easily run with default settings even by novice users of the Cloud Foundry platform. It supports popular programming languages such as Java, Node.js, Python, PHP, Go, Ruby, and .Net, but it can be extended to support additional languages and developer frameworks through community-developed buildpacks.

### Korifi: Cloud Native Cloud Foundry

* Current trends require applications to become lighter, faster, easier to share, secure, maintain, and manage. And most often these applications are designed to run in the cloud, whether on-premises, public, or hybrid, named cloud native applications. These application characteristics also reshape the application build models and tools that need to become cloud native themselves. While containers and container orchestration concepts and tools will be discussed in later chapters, complex platforms such as Cloud Foundry can become cloud native as well. Converting CF into a cloud native tool is not an effortless process, however, the result is a CF project named Korifi. It is a CF offering redesigned from the ground up for another platform, Kubernetes, a popular container orchestrator.

* The [Korifi](https://www.cloudfoundry.org/technology/korifi/) project aims to abstract CF components and dependency configuration, enabling the developer to focus on building applications. This further helps to widen the environment options where CF can be deployed, as containers and container orchestrators are platforms supported by a large array of cloud services, IaaS, and certified solution providers.

### Benefits of Using Cloud Foundry

* It is an open source platform, but there are also many commercial Cloud Foundry providers.
* It offers centralized platform management.
* It enables horizontal and vertical scaling.
* It provides infrastructure security.
* It provides multi-tenant compute efficiency.
* It offers support for multiple IaaS providers.
* It supports the full application lifecycle: development, testing, and deployment, thus enabling a continuous delivery strategy. It also provides integration with CI/CD tools.
* It allows for application virtualization using containers for application isolation.
* It leverages Kubernetes' workload management capabilities to optimize application deployments in containers.
* It is a flexible solution, supported by an extensive community of developers.
* It reduces the chance of human errors.
* It is cost-effective, reducing the overhead for Ops teams.

### Red Hat OpenShift Overview

* [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) is an open source PaaS solution provided by Red Hat. It is built on top of the container technology orchestrated by [Kubernetes](https://kubernetes.io/). OpenShift can be deployed in the cloud as a managed service or as a self-managed deployment on a public or private cloud optimized to run containers and Kubernetes.

* **OpenShift Products**

    * **Red Hat OpenShift - Managed** Hosted OpenShift deployments on public cloud platforms managed by Red Hat. This model includes the Red Hat OpenShift Service on AWS, Red Hat OpenShift on IBM Cloud, and Microsoft Azure Red Hat OpenShift.

    * **Red Hat OpeShift Platform Plus - Self-Managed** Creat your own private, secure K8s multi-cluster PaaS.

    * **Red Hat OpenShift Container Platform** Create your own self-managed consistent hybrid cloud PaaS to build and scale containerized applications.

    * **Red Hat OpenShift Kubernetes Engine - Self-Managed** An entry-level solution promoting the advantages of OpenShift over other Kubernetes solutions, supported by Red Hat.

### Benefits of Using Red Hat OpenShift

* It is an open source PaaS solution.

* It can scale applications easily and quickly.

* It uses Kubernetes for workload management.

* It provides integration with CI/CD tools.

* It is a simple and flexible solution, supported by an active community of developers.

* It enables developers to be more efficient and productive, allowing them to quickly develop, host, and scale applications in the cloud in a streamlined and standardized manner.

* It enables application portability, meaning that any application created on Red Hat OpenShift can run on any platform that supports Kubernetes.

* Red Hat OpenShift users have the choice to deploy their applications on top of physical or virtual infrastructures, as well as on public, private or hybrid clouds.

* With Red Hat OpenShift, applications are easily built with integrated service discovery and persistent storage.

* The web console and the CLI can be used to build and monitor applications.

* Red Hat OpenShift integrates Quay registry, automatic edge load balancing, cluster logging, and integrated metrics.

### Heroku Platform

* [Heroku](http://www.heroku.com/) is a fully-managed container-based cloud platform with integrated data services and a strong ecosystem. Heroku is used to deploy and run enterprise level modern applications, and it is a [Salesforce](https://www.salesforce.com/) company.

* Heroku offers multiple products; however, its core remains the Heroku Platform, a PaaS solution used to deploy large scale applications. The [Heroku Platform](https://www.heroku.com/platform) supports the following popular languages and frameworks:

    * Node.js
    * Ruby
    * Python
    * Go
    * PHP
    * Clojure
    * Scala
    * Java

* However, it can be easily extended to other languages and frameworks through custom [buildpacks](https://elements.heroku.com/buildpacks).

### Heroku Core Concepts

* Applications should contain the source code, its dependency information and the list of named commands to be executed when deployed, in a file called Procfile.

* For each supported language, it has a pre-built image which contains a compiler for that language. This pre-built image is referred to as a buildpack. Multiple buildpacks can be used together. We can also create a custom buildpack.

* While deploying, we need to send the application's content to Heroku, either via Git, GitHub, or via an API. Once the application is received by Heroku, a buildpack is selected based on the language of preference.

* To create the runtime which is ready for execution, we compile the application after fetching its dependency and configuration variables on the selected buildpack. This runtime is often referred to as a slug.

* We can also use third-party add-ons to enable access to value-added services like logging, caching, monitoring, etc.

* A combination of slug, configuration variables, and add-ons is referred to as a release, on which we can perform upgrade or rollback.

* Depending on the process-type declaration in the Procfile, a virtualized UNIX container is created to serve the process in an isolated environment, which can be scaled up or down, based on the requirements. Each virtualized UNIX container is referred to as a dyno. Each dyno gets its own ephemeral storage.

* Dyno Manager manages dynos across all applications running on Heroku.

### Features

* The Heroku Platform allows users to deploy, run, and manage applications written in multiple programming languages or frameworks, from source code that may also include dependencies.

* By encapsulating the application in a dyno, which is a lightweight and secure container, the application can be scaled based on demand.

* Application configuration can be decoupled from the application source code, allowing for application customization based on the environment where the application is deployed. Configuration customization is achieved through config vars, which combined with the application slug, produce a release.

* It is a very rich ecosystem, and it allows us to extend the functionality of an application with add-ons available in the Elements Marketplace. Add-ons allow us to easily integrate our applications with other fully-managed cloud services such as storage, database, monitoring, logging, pipelines, email, message queue, security, and networking.

* Applications deployed on the Heroku Platform can be easily integrated with Salesforce.


Containers
----------

* [Wikipedia Article on OS-level Virtualization](https://en.wikipedia.org/wiki/Operating-system-level_virtualization)

* [The Docker Blog Link, because this is Obviously a Container Chapter](https://www.docker.com/blog/)

### The Container Technology: Building Blocks

* **Namespaces**

* A namespace wraps a particular global system resource like network and process IDs in an abstraction, that makes it appear to the processes within the namespace that they have their own isolated instance of the global resource. The following global resources are namespaced:

    * **pid** provides each namespace to have the same PIDs. Each container has its own PID 1.
    * **net** allows each namespace to have its network stack. Each container has its own IP address.
    * **mnt** allows each namespace to have its own view of the filesystem hierarchy.
    * **ipc** allows each namespace to have its own interprocess communication.
    * **uts** allows each namespace to have its own hostname and domain name.
    * **user** allows each namespace to have its own user and group ID number spaces. A root user inside a container is not the root user of the host on which the container is running.

* **cgroups** *Control groups* are used to organize processes hierarchically and distribute system resources along the hierarchy in a controlled and configurable manner. The following cgroups are available for Linux:

    * **blkio**
    * **cpu**
    * **cpuacct**
    * **cpuset**
    * **devices**
    * **freezer**
    * **memory**

* **Union Filesystem** The Union filesystem allows files and directories of separate filesystems, known as layers, to be transparently overlaid on top of each other, to create a new virtual filesystem. At runtime, a container is made of multiple layers merged to create a read-only filesystem. On top of a read-only filesystem, a container gets a read-write layer, which is an ephemeral layer and it is local to the container.

### Container Runtimes

* Namespaces and cgroups have existed in the Linux kernel for quite some time, but consuming them to create containers was not easy. Although the first steps towards containerization can be traced back to 1979 with the process isolation achieved through *chroot*, followed by Linux Containers (LXC) released in 2008, it was the launch of Docker in 2013 that allowed containers to become more popular. Docker was able to hide all the complexities in the background and came up with a simple workflow to share and manage both images and containers. Docker achieved this level of simplicity through a collection of tools that interact with a container runtime on behalf of the user. The container runtime ensures the containers' portability, offering a consistent environment for containers to run, regardless of the infrastructure. 

* Once containers have become popular and container orchestration was emerging as a concept with Kubernetes becoming its primary implementation, in 2014 we saw a new container runtime being born - rkt, implementing a newly introduced set of standards, the App Container (appc) specification defining the Application Container Image (ACI) format. Shortly after, a new standard has been introduced in 2015, the Open Container Initiative (OCI), setting the stage for several new projects such as Skopeo, Buildah, and Podman, all providing sets of open source tools to allow users a quicker, more secure, daemonless, and less resource-intensive containerization experience. Kaniko has also been introduced, a project aiming to integrate the Dockerfile-based container image build process with Kubernetes, or any other environment that cannot run a Docker daemon. While the containers landscape was evolving, a new container runtime has been introduced, CRI-O - a lightweight runtime implementing Kubernetes' Container Runtime Interface (CRI) standard to allow OCI-compliant containers to be run and managed by the container orchestrator.

* **Container Runtimes**

    * **runC** Over the past few years, we have seen rapid growth in the interest and adoption of container technologies. Most of the cloud providers and IT vendors offer support for containers. To make sure there is no vendor locking and no inclination towards a particular company or project, IT companies came together and formed an open governance structure, called The [Open Container Initiative](https://opencontainers.org/) (OCI), under the auspices of the Linux Foundation. The governance body came up with both [runtime](https://github.com/opencontainers/runtime-spec) and [image](https://github.com/opencontainers/image-spec) specifications to create standards on the Operating System process and application containers. [runC](https://github.com/opencontainers/runc/) is the CLI tool for spawning and running containers according to these specifications, also categorized as a low-level runtime. runc is a Go language-based tool that creates and starts container processes. An OCI container runtime is expected to fork off the first process in the container, but Go does not have good support for the fork/exec model of computing. Go follows a threading model that expects programs to fork a second process and then to exec immediately.

    * **crun** [crun](https://github.com/containers/crun) is a much faster and low-memory footprint OCI-conformant runtime written in C. crun is lighter than runc because its C source code allows its compiled size to be 50x smaller and to run about 2x faster. C is not multi-threaded, but it follows the fork/exec model, meeting the OCI runtime expectation (Whaaaa, C is faster than Go??!? whaaat /s)

    * **containerd** [containerd](https://containerd.io/) is an OCI-compliant container runtime with an emphasis on simplicity, robustness, and portability. As a high-level runtime, it runs as a daemon and manages the entire lifecycle of containers. It is available on Linux and Windows operating systems. Docker, also run as a daemon, is a containerization platform that uses containerd as a runtime to manage runC containers.

    * **CRI-O** [CRI-O](https://cri-o.io/) is an OCI-compatible runtime, which is an implementation of the Kubernetes [Container Runtime Interface](https://kubernetes.io/blog/2016/12/container-runtime-interface-cri-in-kubernetes/) (CRI). It is a lightweight high-level alternative to using Docker as the runtime for Kubernetes.

### Docker

* **Docker Personal** is free for individual developers, education, and small businesses, and it becomes a paid subscription for medium to larger-sized organizations. Docker Personal includes essential Docker tools, such as Docker CLI, Docker Compose, Docker Build/BuildKit, Docker Engine, Docker Desktop, low image pull limits from Docker Hub, and Docker Official Images.

* **Docker Pro** [Docker Pro](https://docker.com/products/pro) subscription is aimed at professional developers by providing increased image pull limits from Docker Hub, private repositories, vulnerability scans, improved volume management, concurrent automated builds, and integrations with CI/CD tools.

* **Docker Team** [Docker Team](https://docker.com/products/team) subscription improves the developer experience with collaboration, security, and management tools.

* **Docker Business** [Docker Business](https://docker.com/products/business) subscription extends the developer experience with features such as image access controls, unified control plane, secure supply chain, and IP allow listing.

### Basic Docker Operations

* List images available in the local cache: `$ docker image ls`

* Pulling an alpine image from the registry into the local cache: `$ docker image pull alpine`

* Run a container from an image (if the image is not found in the local cache, it will be pulled from the registry). The run command is equivalent of docker container create followed by docker container <id> start: `$ docker container run -it alpine sh`

* Run a container in the background (-d option) from an nginx image: `$ docker container run -d nginx`

* List only running containers: `$ docker container ls`

* List all containers: `$ docker container ls -a`

* Inject a process inside a running container. This will start a bash shell in interactive (-i option) terminal (-t option) mode inside the container: `$ docker container exec -it <container_id/name> bash`

* Stop a running container: `$ docker container stop <container id/name>`

* Delete a stopped container: `$ docker container rm <container id/name>`

### Podman

* [Podman](https://podman.io/), or Pod Manager, is an open source, daemonless tool designed to simplify the searching, running, building, sharing, and deploying of applications using Open Containers Initiative (OCI) containers and container images. Podman provides a command line interface (CLI) that is very similar to the Docker CLI. It comes with a GUI that allows developers to interact with images and containers in a visual fashion - the Podman Desktop for Linux, macOS, and Windows. Podman also relies on an OCI-compliant Container Runtime such as runc to create the running containers, making it a great alternative containerization tool to Docker. Another Podman advantage is its capability to run containers in rootless mode by default, while rooted mode is also supported if desired. Docker on the other hand only recently has introduced rootless mode, while rooted container mode has been its default mode. Podman's image building process may use a Containerfile, similar in format to the popular Dockerfile.

* Red Hat, the developers of Podman, created two additional open source tools designed to operate within the container images landscape. [Buildah](https://buildah.io/) supports container image builds one step at a time by taking an interactive approach to processing Dockerfile instructions, while [Skopeo](https://github.com/containers/skopeo) is a tool designed to work with container images in both local and remote repositories.

### Basic Podman Operations

* List images available in the local cache: `$ podman image ls`
* Pulling an alpine image from the Docker Hub registry into the local cache: `$ podman image pull docker.io/library/alpine`
* Run a container from an image (if the image is not found in the local cache, it will be pulled from registry). The run command is equivalent of podman container create followed by podman container <id> start: `$ podman container run -it alpine sh`
* Run a container in the background (-d option) from an nginx image from the Docker Hub registry: `$ podman container run -d docker.io/library/nginx`
* List only running containers: `$ podman container ls`
* List all containers: `$ podman container ls -a`
* Inject a process inside a running container. This will start a bash shell in interactive (-i option) terminal (-t option) mode inside the container: `$ podman container exec -it <container_id/name> bash`
* Stop a running container: `$ podman container stop <container id/name>`
* Delete a stopped container: `$ podman container rm <container id/name>`

### Additional CLI Tools

* The containerd runtime came paired with the [ctr](https://github.com/projectatomic/containerd/tree/master/ctr) client, which was no match for Docker and Podman clients. While the ctr project is no longer maintained, a newer client, [nerdctl](https://github.com/containerd/nerdctl), advertised as a Docker-compatible client for containerd aims to make containerd more user friendly. Eventually, another client, [crictl](https://github.com/kubernetes-sigs/cri-tools/blob/master/docs/crictl.md), was created to support CRI-O. However, crictl can be configured for containerd and Docker as well.

### Basic nerdctl and crictl Operations

* List images available in the local cache: `$ nerdctl images`
* Pulling an alpine image from the Docker Hub registry into the local cache: `$ nerdctl pull docker.io/library/alpine`
* Run a container from an image (if the image is not found in the local cache it will be pulled from the registry): `$ nerdctl run -it alpine sh`
* Run a container in the background (-d option) from an nginx image from the Docker Hub registry: `$ nerdctl run -d docker.io/library/nginx`
* List images available in the local cache: `$ crictl images`
* Pulling an alpine image from the Docker Hub registry into the local cache: `$ crictl pull alpine`
* Run a container from an image (if the image is not found in the local cache it will be pulled from the registry): `$ crictl run -it alpine sh`
* List running containers: `$ crictl ps`

### Benefits of Using Containers

Key benefits of using containers are:

* They have a very light footprint.
* They can be deployed very fast (within milliseconds).
* They are a flexible solution, as they can run on any computer, infrastructure, or cloud environment.
* They can be scaled up or down with ease.
* There is a very rich ecosystem built around them.
* Problem containers can be easily and quickly isolated when troubleshooting and solving problems.
* Containers use less memory and CPU than VMs running similar workloads.
* Increased productivity with reduced overhead.
* They offer portability and consistency.

### Project Moby

* Moby is particularly useful for engineers who want to build their container-based system, to customize and patch an existing Docker build, or just to experiment with the latest container technologies. It uses a Lego-like approach to assemble various open source toolkits, such as:

    * **LinuxKit** to build minimal Linux distributions for containers.
    * **InfraKit** to manage infrastructure in a declarative manner.
    * **SwarmKit** to orchestrate distributed systems at scale.
    * **containerd** as container runtime.
    * **runc** to spawn and run OCI-compliant containers.
    * **Notary** for trusted data sets.
    * **LibNetwork** for networking.


Containers: Micro OSes for Containers
-------------------------------------

* Popular examples include: 

    * Alpine Linux
    * Busybox
    * Fedora CoreOS
    * Flatcar Container Linux
    * k3OS
    * Ubuntu Core
    * VMware Photon OS.

### Alpine Linux Overview

* [Alpine Linux](https://www.alpinelinux.org/about/) is an independent, non-commercial, Linux distribution designed for security, simplicity and resource efficiency. Built on top of the capabilities of BusyBox, Alpine Linux combines the security features of a Linux-based Operating System with a collection of small footprint, yet fully functional utilities.

* Although small between 5 MB and 8 MB per container, or 130 MB as a minimal standalone OS install, it is more resource-efficient than typical distributions. Users can control what binary packages to install, thus ensuring a small yet efficient system.

* Alpine Linux uses its own package manager called apk, the OpenRC init system, and set-up scripts. Users can add packages as needed such as PVR, iSCSI storage controllers, a mail server container, or an embedded switch.

* Alpine Linux was designed with security in mind, with embedded proactive security features that prevent the exploitation of entire classes of zero-day and other vulnerabilities.

### Features

* Upon installation completion, Alpine Linux makes available tools for the initial configuration of the system. Once prepared for reboot, it can be configured to boot in one of the three available runtime modes:

    * **diskless mode** The default mode, where the entire system runs from RAM.
    * **data mode** Mostly runs from RAM, but mounts /var as a writable data partition.
    * **sys mode** The typical hard disk install that mounts /boot, swap and /.

* Alpine Linux is available in many flavors:

    * **Standard** It requires a network connection.
    * **Extended** Includes the most used packages, and runs from RAM.
    * **Netboot** Includes kernel, initramfs and modloop.
    * **Mini root filesystem** Minimal for containers and chroots.
    * **Virtual** Lighter kernel than Standard.
    * **Xen** Supports the Xen hypervisor.
    * **Raspberry Pi** Includes the Raspberry Pi kernel.
    * **Generic ARM** Includes the default ARM kernel with the uboot bootloader.

* Alpine be smol

### Benefits of Using Alpine Linux

* It is a minimal OS designed to run containerized applications as well.
* It is designed for security, simplicity, and resource efficiency.
* It requires between 5 MB and 8 MB as a container.
* It requires 130 MB as a standalone minimal OS installation.
* It provides increased security by compiling user binaries as Position Independent Executables (PIE) with stack smashing protection.
* It can be installed as a container, on bare metal, as well as VMs.
* It offers flavors optimized to support Xen and Raspberry Pi.

### BusyBox Overview

* [BusyBox](https://busybox.net/), the Swiss Army Knife of Embedded Linux, combines very small versions of several popular UNIX utilities into a single compact executable. While these utilities incorporate fewer options, they still support the expected functionality and behavior. Written with size-optimization and limited resources in mind, with a container image between 1 MB to 5 MB, BusyBox is able to pack a complete environment making it an ideal fit for small or embedded systems. In addition, its modular nature makes it very easy to customize. 

* Although not an Operating System in itself, BusyBox was designed to run on Linux and to enhance a lightweight OS with tools needed to help developers troubleshoot and debug their containerized applications.

* BusyBox is licensed under the [GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)

### Benefits of Using BusyBox

* It is an open source package of tools specifically designed to run in small, containerized, or embedded systems.
* It is designed for simplicity and resource efficiency.
* It is modular and highly customizable.
* It requires between 1 MB to 5 MB as a container.
* While its code is Linux-specific, it can be easily ported to FreeBSD, Solaris, and macOS.
* It is available in Fedora, CentOS, and Red Hat Enterprise Linux editions.
* Can be built on various architectures: ARM, CRIS, H8/300, x86, ia64, x86_64, m68k, MIPS, PowerPC, S390, SH3/4/5, Sparc, v850e, and x86_64.
* Can be found running in products by Cisco, ASUS, Synology, Western Digital, Sharp, Linksys, Dell, NetGear, Belkin, Siemens, Trendnet, and others.

### Fedora CoreOS Overview

* Fedora CoreOS (FCOS) is an open source project partnered with the Fedora Project. It was formerly known as Red Hat CoreOS and CoreOS Container Linux prior to that. It combines the best of both CoreOS Container Linux and Fedora Atomic Host (FAH) while aiming to provide the best container host to run containerized workloads securely and at scale.

* Fedora CoreOS is a minimal operating system for running containerized workloads, that updates automatically and is available on multiple platforms. Although a container-focused operating system, by design, CoreOS is operable in both clusters and standalone instances. In addition, it is optimized to work with Kubernetes, but it also works very well without the containerized workload orchestrator.

### Components of Fedora CoreOS

* **Ignition from CoreOS Container Linux** A provisioning utility designed specifically for CoreOS Container Linux, which allows users to manipulate disks during early boot, such as partitioning disks, formatting partitions, writing files, and configuring users. Ignition runs early in the boot process (in the initramfs) and runs its configuration before the userspace boot, which provides advanced features to administrators.

* **rpm-ostree from FAH** One cannot manage individual packages on Atomic Host, as there is no *rpm* or other related commands. To get any required service, you would have to start a respective container. Atomic Host has two bootable, immutable, and versioned filesystems; one is used to boot the system and the other is used to fetch updates from upstream. *rpm-ostree* is the tool to manage these two versioned filesystems.

* **SELinux hardening from FAH** Containers secured with SELinux provide close-to-VM isolation, security, increased flexibility, and efficiency.

* **Installation Methods Include:**

    * **Cloud launchable** To launch directly on Amazon's AWS platform.

    * **Bare metal and virtualized** For bare-metal installs from ISO, PXE (Preboot Execution Environment) or Raw, and virtual installs on OpenStack, QEMU, Raspberry Pi 4, VirtualBox, or VMware.

    * **For cloud operators** Optimized for the following cloud services providers: Alibaba Cloud, AWS, Azure, DigitalOcean, Exoscale, GCP, IBM Cloud, OpenStack, and Vultr
.

### Benefits of Using Fedora CoreOS

* It is an OS designed to run containerized applications, in both clustered environments or as stand-alone.
* It enables us to perform quick updates and rollbacks.
* It provides increased security through SELinux.
* It can be installed on bare metal, virtual environments, and the cloud.
* It combines features of both Fedora Atomic Host and CoreOS Container Linux.
* It works well with Kubernetes.
* It uses Ignition as a provisioning tool for early boot disk partitioning, formatting, and other administrative configuration tasks.

### Flatcar Container Linux Overview

* [Flatcar Container Linux](https://www.flatcar-linux.org/) is a container-optimized OS, with a minimal image size including only the tools needed to run containers. Its name, "Flatcar", represents a flat and open railcar that is used in containers transportation. Flatcar's greatest strengths are its immutable filesystem and automated atomic updates. 

* Flatcar Container Linux is a drop-in replacement for Red Hat CoreOS Container Linux, being directly derived from CoreOS and enabling a seamless in-place migration. Users of CoreOS can effortlessly migrate to Flatcar Container Linux either by modifying a deployment to install Flatcar Container Linux, or by updating directly from Red Hat CoreOS Container Linux. 

* Flatcar Container Linux became increasingly popular once Red Hat announced the end-of-life of the CoreOS Container Linux. 

### Benefits of Using Flatcar Container Linux

* It is a container-optimized Linux OS distribution.
    An immutable/read-only filesystem makes it less vulnerable.
* A minimal OS implies a minimized attack surface.
* It receives automated security updates and patches.
* As a CoreOS successor, it supports two easy migration methods from Red Hat CoreOS Container Linux to Flatcar Container Linux.
* It runs on bare-metal and virtualization platforms such as QEMU, libVirt, VirtualBox, and Vagrant.
* It runs on public clouds such as Amazon EC2, GCE, Azure, Equinix, VMware, and DigitalOcean.
* Its first time boot is supported by the [Ignition](https://coreos.github.io/ignition/) provisioning utility.
* Supports containerd and Docker container runtimes for Kubernetes clusters.

### k3OS Overview

* [k3OS](https://k3os.io/) (the Kubernetes Operating System) is a Linux distribution that aims to minimize the OS maintenance tasks in a Kubernetes cluster. It was designed to work with Rancher's K3s lightweight Kubernetes distribution. k3OS installs fast, boots fast, requires no package manager, and is managed through Kubernetes, being optimized to run in a low-resource computing environment by running only necessary services.

* k3OS speeds up the K3s cluster boot time. At boot time, the k3OS image becomes available to K3s and the cluster takes full control over all the nodes' maintenance, eliminating the need to log in to each individual node for upgrades or other maintenance activities.

### Benefits of Using k3OS

* It is a minimalist OS that eliminates unnecessary libraries and services.
* It decreases complexity and boot time.
* It is highly secure due to a small code base and a decreased attack surface.
* It was designed to integrate with Rancher's K3s Kubernetes distribution.
* Updates and other OS maintenance tasks are performed directly from within the K3s Kubernetes cluster.
* OS configuration is simplified though `cloud-init`

### Ubuntu Core Overview

* [Ubuntu Core](https://ubuntu.com/core) is a lightweight version of Ubuntu, predominantly designed for IoT embedded devices, but also found in large container deployments. In comparison with other container OSes, its size of around 260MB places Ubuntu Core behind much lighter container OSes, such as Alpine Linux, but ahead of much larger OSes like CoreOS, sized around 800MB. Similar to Ubuntu Server and Ubuntu Desktop, Ubuntu Core works with software packages called [snaps](https://www.youtube.com/watch?v=JPXLpLwEQ_E&pp=ygUPbHVrZSBzbWl0aCBzbmFw).

* Security is a top concern for the designers of Ubuntu Core, implemented by features such as:

    * Hardened security with immutable packages and persistent digital signatures.
    * Strict application isolation.
    * Reduced attack surface by keeping a small OS, stripped down to bare essentials.
    * Automatic vulnerability scanning of packages.

* In addition, Ubuntu Core was designed with extreme reliability, implemented by:

    * Transactional updates that increase OS and data resiliency by allowing automated rollbacks when errors are encountered.
    * Automated restore points to allow returns to the last working boot in the case of an unsuccessful kernel update.
    * Consistent application data snapshots.

* Ubuntu Core was built for the enterprise by including secure app store management and license compliance. Developers using Core as their platform enjoy cross-platform portability of snaps from Desktop and Server to Core, together with CI/CD pipeline support.

### Components of Ubuntu Core

* Ubuntu Core is designed to run on bare-metal, on hypervisors such as KVM, or a wide range of hardware, including Raspberry Pi and Qualcomm Snapdragon 410c. Its top features are:

    * Immutable image for simple and consistent installation and deployment.
    * Isolated applications run with explicit permissions, such as read-only access to the filesystem.
    * Transactional updates for signed, autonomous, atomic, and flexible updates.
    * Security implemented at snap level, from build and distribution to deployment.

* Application security and isolation is implemented through:

    * AppArmor
    * Seccomp.

* Snaps are secure, isolated, dependency-free, portable, software packages for Linux. They even include their own filesystems. Snaps benefits include:

    * Automatic updates.
    * Automated recovery in the case of failed updates.
    * Critical update provision for unscheduled updates.
    * Flexible hardware and network conditions support for unpredictable systems, including redundancy for roll-backs, and autonomous bootstrapping.

* The snap packaging environment includes the following:

    * snap
    * The application package format and the command line interface (CLI)
    * snapd
    * The background service managing and maintaining snaps
    * snapcraft
    * The framework including the command to build custom snaps
    * Snap Store
    * The repository to store and share snaps.

* There are several types of snap included in Ubuntu Core:

    * **kernel** defines the Linux kernel
    * **gadget** defines specific system properties
    * **core** the execution environment for application snaps
    * **app** including applications, daemons such as snapd, and various tools.

### Benefits of Using Ubuntu Core

* It has a mid-sized footprint among the Micro OSes available.
* It supports automated updates and rollbacks.
* It is highly resilient.
* It boots the containers within seconds.
* It is highly secure and extremely reliable.
* It provides application isolation through AppArmor and Seccomp.
* It integrates with CI/CD pipelines.

### VMware Photon OS Overview

* [Photon OS™](https://vmware.github.io/photon/) is a minimal Linux container host provided by [VMware](https://vmware.com/), optimized for cloud-native applications. It is designed with a small footprint in order to boot extremely quickly on VMware vSphere deployments and on cloud computing platforms. Photon OS can be deployed on Amazon EC2, GCE, and Microsoft Azure instances, while supporting a variety of container formats as a container host or as a Kubernetes node.

* Photon OS is available in two versions, a minimal and a full version:

    * The minimal version is a lightweight container host runtime environment including a minimum of packaging and functionality to manage containers while still remaining a fast runtime environment.
    * The full version also includes packages of tools for the development, testing, and deployment of containerized applications.

### Features and availability

* Photon OS™ is optimized for VMware products and cloud platforms. It relies on an open source, yum-compatible package manager called Tiny DNF ([tdnf](https://github.com/vmware/tdnf)), and it manages services with systemd.

* Photon OS™ is a security-hardened Linux. The kernel and other aspects of the Photon OS™ are built with an emphasis on security recommendations provided by the [Kernel Self-Protection Project](https://kspp.github.io/) (KSPP). Also, if anybody that maintains this course is reading, the redirect works but it would probably be better to update the link altogether like I did in this.

* It can be easily managed, patched, and updated. It also provides support for persistent volumes to store the data of cloud-native applications on VMware vSAN™.

* Although promoted as an enterprise grade appliance operating system, Photon OS can be installed on Raspberry Pi, ARM64, and x86 as well.

### Benefits of Using VMware Photon OS 

* It is an open source technology with a small footprint.
* It supports various container runtimes as a standalone container host, or as a Kubernetes cluster node.
* We can use Kubernetes in the full version, to allow for container cluster management, but it also supports Apache Mesos.
* It boots extremely quickly on VMware platforms.
* It provides an efficient lifecycle management with a yum-compatible package manager.
* Its kernel is tuned for higher performance when it is running on VMware platforms.
* It is a security-enhanced Linux as its kernel and other aspects of the operating system are configured according to the security parameter recommendations given by the Kernel Self-Protection Project.


Container Orchestration
-----------------------

### K8s Overview

* [Kubernetes](https://kubernetes.io/) is an Apache 2.0-licensed open source project for automating deployment, operations, and scaling of containerized applications. It was started by Google in 2014, but many other companies like Docker, Red Hat, and VMware contributed to its success.

* In July 2015, [Cloud Native Computing Foundation](https://cncf.io/) (CNCF), the nonprofit organization dedicated to advancing the development of cloud-native applications and services and driving alignment among container technologies, accepted Kubernetes as its first hosted project. Intellectual Property (IP) was transferred to CNCF from Google.

* As the Kubernetes project matures, the list of supported container [runtimes](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) may change, however, currently containerd, CRI-O, Docker Engine, and Mirantis Container Runtime are supported to run containers.

### The Kubernetes Architecture: Key Components

* **Key Components:**

    * **Cluster** a collection of systems (bare-metal or virtual) and other infrastructure resources used by Kubernetes to run containerized applications.
    * **Control-Plane Node** The control-plane node is a system that takes containerized workload scheduling decisions, manages the worker nodes, enforces access control policies, and reconciles changes in the state of the cluster. Its main components are the kube-apiserver, etcd, kube-scheduler, and kube-controller-manager responsible for coordinating tasks around container workload scheduling, deployment, scaling, self-healing, state persistence, state reconciliation, and delegation of container management tasks to worker node agents. Multiple control-plane nodes may be found in clusters as a solution for High Availability.
    * **Worker Node** A system where containers are scheduled to run in workload management units called Pods. The node runs a daemon called kubelet responsible for intercepting container deployment and lifecycle management related instructions from the kube-apiserver, delegating such tasks to the container runtime found on the node, implementing container health checks, enforcing resource utilization limits, and reporting node status information back to the kube-apiserver. kube-proxy, a network proxy, enables applications running in the cluster to be accessible by external requests. Both node agents - kubelet and kube-proxy, together with a container runtime are found on worker nodes and on control-plane nodes as well.
    * **Namespace** The namespace allows us to logically partition the cluster into virtual sub-clusters by segregating the cluster's resources, addressing the multi-tenancy requirements of enterprises requiring ab isolation method for their projects, applications, users, and teams.

* **Key API Resources:**

    * **Pod** The pod is a logical workload management unit, enabling the co-location of a group of containers with shared dependencies such as storage Volumes. However, a pod is often managing a single container and its dependencies such as Secrets or ConfigMaps. The pod is the smallest deployment unit in Kubernetes. A pod can be created independently, but it is lacking the self-healing, scaling, and seamless update capabilities which Kubernetes is know for. In order to overcome the pod's shortcomings, controller programs, or operators, such as the ReplicaSet, Deployment, DaemonSet, or the StatefulSet are recommended to be used to manage pods, even if only a single application pod replica is desired.
    ```
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx-pod
      labels:
        run: nginx-pod
    spec:
      containers:
      - name: nginx
        image: nginx:1.17.9
        ports:
        - containerPort: 80
    ```

    * **ReplicaSet** The ReplicaSet is a mid-level controller, or operator, that manages the lifecycle of pods. It rolls out a desired amount of pod replicas, uses state reconciliation to ensures that the desired number of application pod replicas is running at all times, and to self-heal the application if a pod replica is unexpectedly lost due to a crash or lack of computing resources.

    * **Deployment** The Deployment is a top-level controller that allows us to provide declarative updates for pods and ReplicaSets. We can define Deployments to create new resources, or replace existing ones with new ones. The Deployment controller, or operator, represents the default stateless application rollout mechanism. Typical Deployment use cases and a sample deployment are provided below:

        * Create a Deployment to roll out a desired amount of pods with a ReplicaSet.
        * Check the status of a Deployment to see if the rollout succeeded or not.
        * Later, update that Deployment to recreate the pods (for example, to use a new image) - through the Rolling Update mechanism.
        * Roll back to an earlier Deployment revision if the current Deployment isn’t stable.
        * Scale, pause and resume a Deployment. Below we provide a sample deployment: 
    ```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: nginx-deployment
      labels:
        app: nginx-deployment
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: nginx-deployment
    template:
      metadata:
        labels:
          app: nginx-deployment
    spec:
      containers:
      - name: nginx
        image: nginx:1.17.9
        ports:
        - containerPort: 8
    ```

    * **DaemonSet** The DaemonSet is a controller, or operator, that manages the lifecycle of node agent pods. It rolls out a desired amount of pod replicas while ensuring that each cluster node will run exactly one application pod replica. It also uses state reconciliation to ensures that the desired number of application pod replicas is running at all times, and to self-heal the application if a pod replica is unexpectedly lost due to a crash or lack of computing resources.

    * **Service** The Service is a traffic routing unit implemented by the kube-proxy providing a load-balancing access interface to a logical grouping of pods, typically managed by the same operator. The Service enables applications with DNS name registration, name resolution to a private/cluster internal static IP. It can reference a single pod or a set of pods managed by ReplicaSets, Deployments, DaemonSets, or StatefulSets.
    ```
    apiVersion: v1
    kind: Service
    metadata:
      name: frontend
      labels:
        app: nginx-deployment
        tier: frontend
    spec:
      type: NodePort
      ports:
      - port: 8080
        targetPort: 80
    selector:
        app: nginx-deployment
        tier: frontend
    ```
    * **Label** The Label is an arbitrary key-value pair that is attached to resources like a pod or a ReplicaSet. In the code examples we provided, we defined labels with keys such as `run`, `app`, and `tier`. Labels are typically used to tag resources of a particular application, such as the Pods of a Deployment, to logically group them for management purposes - for updates, scaling, or traffic routing.

    * **Selector** Selectors allow controllers, or operators, to search for resources or groups of resources described by a desired set of key-value pair Labels. In the examples provided, the frontend Service will only forward traffic to Pods described simultaneously by both labels app: `nginx-deployment` and `tier: frontend`
    
    * **Volume** The Volume is an abstraction layer implemented through Kubernetes plugins and third-party drivers aimed to provide a simplified and flexible method of container storage management with Kubernetes. Through Kubernetes Volumes, containers are able to mount local host storage, network storage, distributed storage clusters, and even cloud storage services, in a seamless fashion. 

### Features

* It automatically distributes containers on cluster nodes based on containers' resource requirements, cluster topology, and other custom constraints.
* It supports horizontal scaling through the CLI or a UI. In addition, it can auto-scale based on resource utilization.
* It supports rolling updates and rollbacks.
* It supports several volume drivers from public cloud providers such as AWS, Azure, GCP, and VMware, together with network and distributed storage plugins like NFS, iSCSI, and the CephFS driver to orchestrate storage volumes for containers running in pods.
* It automatically self-heals by restarting failed containers, rescheduling containers from failed nodes, and supports custom health checks to ensure containers are continuously ready to serve.
* It manages sensitive and configuration data for an application without rebuilding the image.
* It supports batch execution.
* It supports High Availability of the control-plane node to add control plane resiliency.
* It eliminates infrastructure lock-in by providing core capabilities for containers without imposing restrictions.
* It supports application deployments and updates at scale.
* It supports cluster topology aware routing of traffic to service endpoints.

### Benefits of Using K8s

* It is an open source system that packages all the necessary features: orchestration, service discovery, and load balancing.
* It manages multiple containers at scale.
* It automates deployment, scaling, and operations of application containers.
* It is portable, extensible and self-healing.
* It provides consistency across development, testing, and production environments, on-premise and across clouds.
* It is highly efficient with resource utilization.

### K8s Hosted Solutions and platforms

* **Hosted Solutions** 

    * [Amazon EKS (Aamazon Elastic K8s Service)](https://aws.amazon.com/eks/)

    * [AKS (Azure K8s Service)](https://azure.microsoft.com/en-us/services/kubernetes-service/)

    * [GKE (Google K8s Engine)](https://cloud.google.com/kubernetes-engine/)

    * [IBM Cloud K8s Service](https://www.ibm.com/cloud/container-service/)

    * [NetApp Project Astra](https://cloud.netapp.com/project-astra)

    * [OKE (Oracle Container Engine for K8s)](https://www.oracle.com/cloud/compute/container-engine-kubernetes.html)

    * [Red Hat OpenShift](https://www.openshift.com/products)

    * [VKE (Vultr K8s Engine)](https://www.vultr.com/kubernetes/)

    * [TKG (VMware Tanzu K8s Grid)](https://tanzu.vmware.com/kubernetes-grid)

* **Platform Solutions**

    * [Managed K8s](https://ubuntu.com/kubernetes/managed)

    * [D2iQ Enterprise K8s Platform](https://d2iq.com/kubernetes-platform)

    * [Kubermatic K8s Platform](https://www.kubermatic.com/products/kubermatic/)

    * [PMK (Platform9 Managed K8s)](https://platform9.com/managed-kubernetes/)

    * [MPK (Rackspace Managed Platform for K8s)](https://www.rackspace.com/cloud/kubernetes)

    * [RKE (Rancher K8s Engine)](https://www.rancher.com/products/rke)


### Docker Swarm Overview

* **Swarm Manager Nodes** Accept commands on behalf of the cluster and make scheduling decisions. They also maintain the cluster state and store it using the *Internal Distributed State Store*, which uses the [Raft](https://raft.github.io/raft.pdf) consensus algorithm. One or more nodes can be configured as managers for fault-tolerance. When multiple managers are present, they are configured in active/passive modes.

* **Swarm Worker Nodes** Run the Docker Engine and the sole purpose of the worker nodes is to run the container workload given by the manaer node(s).

### Features

* It is compatible with Docker tools and API, so that the existing workflow does not change much.
* It provides native support to Docker networking and volumes.
* It can scale up to large numbers of nodes.
* It supports failover and High Availability for the cluster manager for fail-tolerance.
* It uses a declarative approach to define the desired state of the various services of the application stack.
* For each service, you can declare the number of tasks you want to run. When you scale up or down, the Swarm manager automatically adapts by adding or removing tasks to maintain the desired state.
* The Docker Swarm manager node constantly monitors the cluster state and reconciles any differences between the actual state and your expressed desired state.
* The communication between the nodes of Docker Swarm is enforced with Transport Layer Security (TLS), which makes it secure by default.
* It supports rolling updates to control a delay between service deployment to different sets of nodes. If a task rollout is unsuccessful, you can roll back a task to a previous version of the service.

### Docker Swarm Solutions

* [yes.](https://docs.docker.com/engine/swarm/)

### Benefits of Using Docker Swarm

* Native clustering for Docker

* Well integrated with the existing Docker tools and workflow

* Setup is easy, straightforward, and flexible

* Manages containerized workload in a cluster of Docker Entines that are treated as a single entity

* Provides scalability and supports High Availability

* Efficiently and productivity are incread by reducing deployment and management time, as well as duplication of efforts 

### Amazon ECS Overview

* [The Docs](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/launch_types.html)

### Amazon ECS Components

* **Cluster** a logical grouping of tasks or services. With the EC2 launch type, a cluster is also a grouping of container instances.

* **Container Instance** only applicable if we use the EC2 launch type. We define the Amazon EC2 instance to become part of the ECS cluster and to run the container workload.

* **Container Agent** only applicable if we use the Fargate launch type. It allows container instances to connect to your cluster.

* **Task Definition** specifies the blueprint of an application, which consists of one or more containers.

* **Scheduler** places tasks on the cluster.

* **Service** allows one or more instances of tasks to run, depending on the task definition. 

* **Task** a running container instance from the task definition.

* **Container** created from the task definition.

### Amazon ECS Features

* It is compatible with Docker containers and Windows containers as well.

* It provides a managed cluster so that users do not have to worry about managing and scaling the cluster.

* The task definition allows the user to define the applications through a JSON file. Shared data volumes, as well as resource constraints for memory and CPU, can also be defined in the same file.
* It provides APIs to manage clusters, tasks, etc.

* It allows easy updates of containers to new versions.

* The monitoring feature is available through AWS CloudWatch.

* The logging facility is available through AWS CloudTrail.

* It supports third party hosted Docker registries, the public Docker Hub, or the [Amazon Elastic Container Registry](https://aws.amazon.com/ecr/) (ECR).

* AWS Fargate allows you to run and manage containers without having to provision or manage servers.
It allows you to build all types of containers. You can build a long-running service or a batch service in a container and run it on ECS.

* You can apply your Amazon Virtual Private Cloud (VPC), security groups and AWS Identity and Access Management (IAM) roles to the containers, which helps maintain a secure environment.

* You can run containers across multiple availability zones within regions to maintain High Availability.

* It can be integrated with AWS services like Elastic Load Balancing (ELB), Virtual Private Cloud (VPC), Identity and Access Management (IAM), Amazon ECR, AWS Batch, Amazon CloudWatch, AWS CloudFormation, AWS CodeStar, AWS CloudTrail, and more.

### Benefits of Using Amazon ECS

* It provides a managed cluster on public, private, or hybrid cloud.
* It is built on top of Amazon Elastic Compute Cloud (EC2).
* It is highly available and scalable.
* It leverages other AWS services, such as CloudWatch Metrics.
* We can manage it using CLI, Dashboard or APIs.

### Azure Container Instances (ACI) Overview

* [The docs.](https://azure.microsoft.com/en-us/services/container-instances/)

### ACI Features

* They expose containers directly to the internet through IP addresses and *fully qualified domain names* (FQDN).
* Allow user interaction with the environment of a running container by executing commands in the container through a shell.
* Offer VM-like application isolation in the container. 
* Allow for resource specification, such as CPU and memory. 
* They allow containers to mount directly Azure File shares to persist their state.
* They support the running of both Linux and Windows containers.
* They support the scheduling of single- and multi-container groups, thus allowing patterns like the sidecar pattern.

Unikernels
----------

* "Unikernels are specialized, single-address-space machine images constructed by using library operating systems". ~ [unikernels website](http://unikernel.org/)

### Specialized VM Images

* The Unikernel creates specialized VM images with just:

    * The Application Code
    * The config files of the app
    * The user-space libraries needed by the app
    * The application runtime (such as JVM)
    * The system libs of the unikernel, which allow back and forth communication with the hypervisor

* According to the [x86 protection ring docs](https://en.wikipedia.org/wiki/Protection_ring), the kernel runs on **ring0**, and the application runs on **ring3**.

* [Comparison of a Traditional OS Stack and a MirageOS Unikernel](https://en.wikipedia.org/wiki/Unikernel#/media/File:Unikernel_mirage_example.png)

### Benefits of Unikernels

* A minimalistic VM image to run an application, which allows us to have more applications per host.
* A faster boot time.
* Efficient resource utilization.
* A simplified development and management model.
* A more secured application than the traditional VM, as the attack surface is reduced.
* An easily-reproducible VM environment, which can be managed through a source control system like Git.


### Unikernel Implementations

* **Specialized and purpose-built unikernels** Utilize all the modern features of software and hardware, while disregarding backward compatibility. **NOT** POSIX-compliant, examples include [HaLVM], [MirageOS](https://mirage.io/), and [Clive](http://lsub.org/ls/clive.html)

* **Generalized 'fat' unikernels** run unmodified applications, which make them *fat*, examples include [OS](http://osv.io/) and [Drawbridge](https://www.microsoft.com/en-us/research/project/drawbridge/)

Microservices
-------------

* So far a bunch of stuff I learned in my [Intro to DevOps and SRE Course](https://github.com/CiscoSteve42/Notes/blob/main/Linux/Linux%20Foundation/IntrotoDevOps.md)

* Yeah, that was it.

SDN and Networking for Containers
---------------------------------

* **Software-defined networking (SDN)** decouples the network control layer from the traffic forwarding layer, allowing SDN to program the control layer and to create custom rules in order to meet these new networking requirements.

### SDN Architecture

* **Data Plane** also known as the *Forwarding Plane*, is responsible for handling data packets and apply actions to them based on rules which we program into lookup-tables.

* **Control plane** tasked with calculating and programming the actions for the Data Plane. This is where the forwarding decisions are made and where services such as QoS and VLANs are implemented.

* **Management Plane** place where we can configure, monitor, and manage the network devices.

### Activities Performed by a Network Device

* **Ingress and egress packets** These are performed at the lowest layer, which decides what to do with ingress packets and which packets to forward, based on forwarding tables. These activities are mapped as Data Plane activities. All routers, switches, modem, etc., are part of this plane.

* **Collect, process, and manage the network information** By collecting, processing, and managing the network information, the network device makes the forwarding decisions, which the Data Plane follows. These activities are mapped by the Control Plane activities. Some of the protocols which run on the Control Plane are routing and adjacent device discovery.

* **Monitor and manage the network** Using the tools available in the Management Plane, we can interact with the network device to configure it and monitor it with tools like SNMP (Simple Network Management Protocol).

### Container Networking standards

* **Container Network Model (CNM)** Implemented using [libnetwork](https://github.com/moby/libnetwork#libnetwork---networking-for-containers), which standardizes the container network creation process through three main build components: a network sandbox, one or multiple endpoints, and one or multiple networks. Libnetwork is used in one of the following modes:

    * **Null** NOOP implementation of the driver, used when no networking is required.
    * **Bridge** provides a Linux-specific bridging implementation based on Linux Bridge.
    * **Overlay/Swarm** provides [multi-host communication](https://github.com/docker/libnetwork/blob/master/docs/overlay.md) over VXLAN.
    * **Remote** does not provide a driver, instead provides a means of supporting drivers over a remote transport, by which we cant write third-party drivers.

* **Container Networking Interface (CNI)** a Cloud Native Computing Foundation (CNCF) project which consists of specifications and libraries for writing plugins to configure network interfaces in Linux containers, along with a number of supported plugins. It is limited to providing network connectivity of containers and removing allocated resources when the container is deleted. As such, it has a wide range of support. It is used by projects like Kubernetes, OpenShift, and Cloud Foundry.

### Service Discovery

* **Service discovery** is a mechanism that enables processes and services to find each other automatically and talk to  each other. In relation to containers, it maps the container name with it's IP, so we can access the container by name instead of my it's IP, which will change if it's not static.

* Service discovery is achieved in 2 steps:

    * **Registration** When a container starts, the container scheduler registers the container name to the container IP mapping in a key-value store such as etcd or Consul. And, if the container restarts or stops the scheduler updates the mapping accordingly.

    * **Lookup** Services and applications use *Lookup* to retrieve the IP address of a container, so that they can connect to it. Generally, this is supported by DNS (Domain Name Server), which is local to the environment. The DNS used resolves the requests by looking at the entries in the key-value store, which is used for *Registration*. Consul, CoreDNS, SkyDNS and Mesos-DNS are examples of such DNS services.

### Multi-Host Networking

* [**Docker Overlay Drivers**](https://docs.docker.com/network/overlay/)

* [**Macvlan Driver](https://docs.docker.com/network/macvlan/)

### Third-Party Network Plugins

* [**Kuryr Network Plugin**](https://github.com/openstack/kuryr)

* [**Weave Net**](https://www.weave.works/docs/net/latest/install/plugin/plugin-how-it-works/)

### Podman Network Drivers

* [Podman network](https://docs.podman.io/en/latest/markdown/podman-network.1.html) operations allow us to list networks, create custom networks, inspect them, attach containers to them, and finally remove them when no longer needed. Podman supports the creation of CNI-compliant container networks. To create container networks, Podman supports drivers for various network types. Default is the bridge driver, usable in both rootless and rooted modes. However, in rooted mode, two additional drivers can be used, the macvlan and ipvlan drivers, with options such as parent to designate a host device and the mode to be set on the interface. The macvlan and ipvlan drivers are only available in rooted mode because they require access to the host network interfaces, otherwise the rootless networking needs a separate network namespace. 

* A mix of rootless (*$*) and rooted (*#*) network operations are provided below:

```bash
$ podman network ls

$ podman network create --subnet 192.168.20.0/24 --gateway 192.168.20.3 bridgenet

$ podman network inspect bridgenet

# podman network create -d macvlan -o parent=eth0 macvnet

# podman network inspect macvnet
```

### K8s Networking

* Requirements that need to be implemented by K8s networking drivers , as specified in the Container Network Interface (CNI):

    * All pods on a node can communicate with all pods on all nodes without NAT 

    * Agents on a Node (eg system daemonds, kubelet) can communicate with all Pods on that Node

    * The Pods in the host network of a Node can communicate with all Pods on all Nodes without NAT (for Linux or other platforms supporting Pods running in the host network)

### Multi-Node Networking with K8s

* `kubectl -n demos get po,svc,ep -l demo=demo3 -owide`

* `kubectl -n demos exec client-app-7d9bb6c977 fslxq -- sh -c 'curl -s 192.168.142.153' WEBSERVER`

* `kubectl -n demos exec client-app-7d9bb6c977-fslxq -- sh -c 'curl -s 10.98.67.45' WEBSERVER`

* `kubectl -n demos exec client-app-7d9bb6c977-fslxq -- sh -c 'curl -s web-app-svc' WEBSERVER`

### Cloud Foundry: Container-to-Container Networking

* By default, [Gorouter](https://docs.cloudfoundry.org/concepts/cf-routing-architecture.html) (which, you may have guessed, is [written in Go.](https://github.com/cloudfoundry/gorouter)), routes external and internal traffic to different Cloud Foundry components. 

* The [container-to-container networking](https://docs.cloudfoundry.org/concepts/understand-cf-networking.html) feature of CF enables app instances to communicate with each other directly, *HOWEVER*, when the container-tocontainer networking feature is disabled, all application-to-application traffic must go through the Gorouter.

* Components of the CF architecture that make container-to-container networking possible: 

    * **Network Policy Server** A management node hosting a database of app traffic policies.

    * **Garden External Networker** Sets up networking for each app through the CNI plugin, exposing apps to the outside, by allowing incoming traffic from Gorouter, TCP Router, and SSH Proxy.

    * **Silk CNI Plugin** For IP management through a shared VXLAN overlay network that assigns each container a unique IP address. The overlay network is not externally routable and it prevents the container-to-container traffic from escaping the overlay.

    * **VXLAN Policy Agent** Enforces network policies between apps. When creating routing rules for network policies, we should include the source app, destination app, protocol, and ports, without going through the Gorouter, a load balancer, or a firewall.


Software-Defined Storage and Storage Management for Containers
------

* **SDS (Software-defined Storage)** represents storage virtualization aimed to separate the underlying storage hardware from the software that manages and provisions it. Physical hardware from various sources can be combined and managed with software, as a single storage pool. Examples include [TrueNAS](https://www.truenas.com/) and [VMware vSAN](https://www.vmware.com/products/vsan.html).

### Ceph Overview

* **Ceph** is an open source distributed storage system that supports applications with different storage interface needs, as it provides *object*, *block*, and *filesystem* storage in a single unified storage cluster, making it flexible, highly reliable, and easy to manage.

* Ceph uses the **Controlled Replication Under Scalable Hashing (CRUSH)** algorithm to deterministically find, write, and read the location of objects.

* **[Ceph Documentation by Red Hat](https://docs.ceph.com/en/latest/architecture/)

### Ceph Architecture

* **Reliable Autonomic Distributed Object Store (RADOS)** *is the object store which stores the objects* (I swear that I almost got a stroke from reading that sentence.) This layer makes sure that data is always in a consistent and reliable state. Performs operations like replication, failure detection, recovery, data migration, and rebalancing across the cluster nodes. 3 major components are:

    * **Object Storage Device (OSD)** where the actual user content is written and retrieved with read operations. One OSD daemon is typically tied to one physical disk in the cluster.

    * **Ceph Monitors (MON)** resonsible for monitoring the cluster state, all cluster nodes report to Monitors. Monitors map the cluster state through the OSD, Place Groups (PG), CRUST and Monitor maps.

    * **Ceph Metadata Server (MDS)** needed only by CephFS to store the file hierarchy and metadata for files.

* **Librados** a lib that allows direct access to RADOS from langs like C, C++, Python, Java, PHP, etc. Ceph Block Device, RADOSGW, and CephFS are implemented on to of Librados.

* **Ceph Block Device (RBD)** provides the block interface for Ceph. Works as a block device and has enterprice features like thin provisioning and snapshots.

* **RADOS Gateway (RADOSGW)** provides a REST API interface for Ceph, which is compatible with Amazon S3 and OpenStack Swift. 

* **Ceph File System (CephFS)** privdes a POSIX-compliant distributed filesystem on top of Ceph. It relies on Ceph MDS to track the file hierarchy.

### Benefites of Using Ceph

* Its an open source storage solution that supports *Object*, *Block*, and *File System* storage

* Runs on any commodity hardware, without any vendor lock-in

* Provides data safety for mission-critical apps

* Provides automatic balance of filesystems for maximu performance

* Scalable and highly available, with no single point of failure

* Reliable, flexible, and cost-effective storage solution

* Achieves higher throughput by stripping the files/data across multiple nodes

* Achies adaptive load-balancing by replicating frequently accessed objects over multiple nodes

### GlusterFS Volumes

* **FUSE** [Filesystem in Userspace](https://en.wikipedia.org/wiki/Filesystem_in_Userspace) 

* Types of Volumes Supported by GlusterFS:

    * Distributed GlusterFS volume

    * Replicated GlusterFS volume

    * Distributed replicated GlusterFS volume

    * Dispersed GlusterFS volumes

    * Distributed dispersed GlusterFS volume

* GlusterFS does not have a centralized metadata server, it uses an elastic hashing algorithm to store files on bricks (I got bricks in the Benzzz)

* GlusterFS volumes can be accessed using one of the following methods:

    * Native FUSE mount 
    * Network File System (NFS)
    * Common Internet File System (CIFS)

### Benefits of Using GlusterFS

* Scales to several petabytes

* Can be configured on commodity hardware

* Open source storage solution that supports *Object*, *Block*, and *Filesystem* storage

* Does NOT have a metadata server

* Scalable, modular, and extensible

* Provides features like replications, quotas, geo-replication, snapshots, and BitRot detection

* POSIX-compliant, providing High Availability via local and remote data replication

* Allows optimization for differnt workloads

### Docker Storage Drivers

* Docker uses the [copy-on-write](https://en.wikipedia.org/wiki/Copy-on-write) mechanism when containers are started from images.

* Docker supports the following storage drivers on Linux:

    * **BtrFS** Supports snapshots

    * **Device Mapper** For earlier CentOS and RHEL releases

    * **Fuse-Overlay** Preferred for rootless mode 

    * **Overlay2** Preferred for all supported Linux distros (Ubuntu, Debian, CentOS, Fedora, RHEL, SLES 15)

    * **VFS (Virtual File System)** For testing only, not for production

    * **ZFS** Supports snapshots (FreeBSD gang represent!)

### Managing Data in Docker

* **Volumes** are stored in the `/var/lib/docker/volumes` dir and they are directly managed by Docker. Volumes are the recommended method of storing persistent data in Docker

* **Blind Mounts** allow Docker to mount any file or directory from the *host system* into a container 

* **Tmpfs** stored in the host's memory only, but not persisted on it's filesystem, recommended for non-persistent state data 

### Docker Containers with Volumes 

* In Docker, a container with a mounted volume can be created using either the `docker container run` or `docker container create` commands:

```sh
$ docker container run -d --name web -v webvol:/webdata myapp:latest
```

* The above command would create a Docker volume inside the Docker working directory `/var/lib/docker/volumes/webvol/_data` on the host system, mounted on the container at the `/webdata` mount point. We may list the exact mount path via the `docker container inspect` command.

* A container bind mount can be created using either the `docker container run` or the `docker container create` commands:

```sh
$ docker container run -d --name web -v /mnt/webvol:/webdata myapp:latest
```

* This mounts the host's `/mnt/webvol` dir to the `/webdata` mount point on the container as it's being started.

### Docker Volume Plugins

* "We can extend the functionality of the Docker Engine with the use of plugins." *Proceeds to list like 20 plugins.*

### Podman Storage Drivers

* Podman also uses the Volume feature to store persistent data, together with Volume drivers

* Podman is also capable of using the copy-on-write mechanism when containers are ran. The container image is saved on a read-only filesystem layer while all changes performed by the container are saved on a writable filesystem of the container.

* The following storage driver choices are available for Podman:

    * **AUFS (Another Union File System)**
    * **BtrFS**
    * **Thinpool (Device Mapper)**
    * **Overlay**
    * **VFS (Virtual File System)**
    * **ZFS**

### Managing Data in Podman

* **Volumes** Volumes are stored under the `/var/lib/containers/storage/volumes` dir for root, and under the `~/.local/share/containers/storage/volumes` dir for reular users. They are directoly managed by Podman, and represent the recommended method of storing persistent data with Podman.

* **Bind** Podman can mount a named vol from the *host system* into the container.

* **Tmpfs** It is stored in the host's memory only but not persisted on it's filesystem, and the content is erased when the container is stopped (think TailsOS)

* **Image** to mount an OS image file

* **Devpts** to mount a filesystem storing pseudoterminal (telnet, ssh, xterm)

### Podman Containers with Volumes

* A container with a mounted volume can be created using either the `podman container run` or the `podman container create` commands:

```sh
$ podman container run -d --name=web -v webvol:/webdata myapp:latest 
```

* The above command would create a volume on the host system in the Podman of the current user `~/.local/share/containers/storage/volumes/webvol/_data` or `/var/lib/containers/storage/volumes/webvol/_data` if ran by root and mount it on the container at the `/webdata` mount point. We may display the mount path with the `podman container inspect` command.

* A bind mount can be achieved with either the `podman container run` or the `podman container create` commands.

### Creating a Named Volume with Podman

* A volume can be easily created with the following command. By default it uses the local driver

```sh 
$ podman volume create container-volumecontainer-volume
container-volume
```

* Once created, the volume listing displays the volume driver and the volume name 

```sh 
$ podman volume ls
DRIVER    VOLUME NAME 
local     container-volume
```

* Inspecting the volume reveals additional details, such as the mountpoint on the host system where the volume is created by the container engine.

```sh 
$ podman volume inspect container-volume
[
    {
        "Name":"container-volume",
        "Driver": "local",
        "Mountpoint": "/home/yourmom/.local/share/containers/storage/volumes/container-volume/_data",
        "CreatedAt": "2025-06-18T10:47:24.128418284-05:00",
        "Labels": {},
        "Scope": "local",
        "Options": {},
        "MountCount": 0, 
        "NeedsCopyUp": true,
        "NeedsChown": true
        "LockNumber": 0
    }
]
```

* We run an Alpine image in the data-container and attach the container volume, which opens up the container shell in interactive mode using the following command `podman container run -v container-volume:/data -it --name data-container alpine sh` and the container shell will appear as so `/# `. Navigate to the `/data` dir, create any kind of file, then `exit` the container shell. Then go to the `.local/share/containers/storage/volumes/container-volumes/_data` dir in your home directory and notice that the file that you created is there.

* Describing the container rebeals it's config details, together with the mounted volume details. These details are aligned with the ones displayed by the volume described above `podman container inspect data-container | grep Mounts -A16`

### Volume Management in K8s 

* K8s uses volumes to attach external storage to containers managed by Pods. The volume is basically a directory, backed by a storage medium, with contents determined by the volume type.

* A volume is linked to a Pod and shared among containers of that Pod. If the pod is deleted, the volume and data are lost as well.

* A volume can be shared by some containers in the same Pod.

### Volume Types

* **awsElasticBlockStore** *With the* `awsElasticBlockStore` vol type, we can mount an [AWS EBS](https://aws.amazon.com/ebs/) vol on containers of a Pod.

* **azureDisk** `azurDisk` allows us to mount an [Azure Data Disk](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/managed-disks-overview?toc=%2Fazure%2Fvirtual-machines%2Flinux%2Ftoc.json) on containers of a Pod.

* **azureFile** `azurefile` lets us mount an Azure File Volume on containers in a Pod.

* **cephfs** `cephfs` lets us mount a CephFS vol on containers of a Pod.

* **configMap** `configMap` lets us attach a decoupled storage object that encaps config data, scripts, and possibly entire filesystems, to containers of a Pod (sounds pretty dope.)

* **emptyDir** An empty vol is created for the Pod as soon as it is scheduled on a worker node. The life of the vol is tightly coupled the Pod. Pretty basic shit, if you delete it, that shit be gone.

* **gcePersistentDisk** with the `gcePersistenDisk` vol type, we can mount a [GCE](https://cloud.google.com/compute/docs/disks/) persistent disk into a Pod (Cloud integration and shit, amirite? IS THAT NOT WHY I'M TAKING THIS COURSE)

* **hostPath** the `hostPath` vol type allows us to share a dir from the host with the containers of a Pod. If the content of the vol dies, it's still available on the host.

* **nfs** allows you to mount a `nfs` share on containers in a Pod. 

* **persistentVolumeClaim** the `persistentVolumeClaim` type lets us attach a persistent vol to a Pod.

* **rdb** `rdb` lets us mount a [Radios Block Device](https://docs.ceph.com/docs/master/rbd/) vol on containers in a Pod.

* **secret** `secret` lets us attach storage objects that encapsulate encoded *sensitive* information such as pws, keys, certs, or tolkiens to containers in a Pod.

* **vshpereVolume** `vsphereVolume` lets us mount a vSphere VMDK vol to containers in a Pod.

### Persistent Volumes

* The **Persistent Volume Subsystem** in K8s provides us with APIs to manage and consume the storage. To manage a vol, it uses the [PV (PersistenVolume)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) resource type to consume it, it uses the [PersistentVolumeClaim (PVC)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) resource type

* PVs can be provisioned statically or dynamically. For [dynamic provisioning](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/), K8s uses the [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/) resource, which contains predefined provisioners and parameters for PV creation. With PVC, a user sends the reuqests for dynamic PV creation, which gets wired to the StorageClass resource.

* Some vol types that support managing storage using PVs are:

    * **AWSElasticBlockStore**
    * **AzureFile**
    * **AzureDisk**
    * **GCEPersistentDisk**
    * **NFS**
    * **iSCSI**
    * **RBD**
    * **CephFS**
    * **vsphereVolume**

### Persistent Volumes Claim

* [**PersistentVolumeClaim**](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) is a request for service by a user. Users request for PV resources based on size, access modes, and vol type. Once a suitable one is found, it is bound to the PVC. After a successful bind, the PVC can be used in a Pod, to allow the containers' access to the PV.

* Once the Pod is deleted, the PVC may be detached from the PV releasing it for possible future use. The PV can either be deleted, retrained or recycled, all based on the user-defined [reclaim policy](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy.)

### Adding Storage Volumes to K8s Pods

* The Pod definition manifest sets up an Ubuntu container with a hostPath vol. The hostPath vol plugin binds the `/tmp/data-vol` host dir with the `/data` container dir. If the host directory does not exist prior to the Pod's deployment, it will be created upon deployment.

```yaml
apiVersion: v1 
kind: Pod 
metadata:
  creationTimestamp: null 
  labels:
    run: storage-pod
  name: storage-pod 
  namespace: infra 
spec:
  containers:
  - command:
    - bash
    - -c 
    - sleep 3600
    image: ubuntu
    name: storage-pod 
    resources: {} 
    volumeMounts:
    - name: vol
      mountPath: /data
  volumes:
    - name: vol
      hostPath:
        path: /tmp/data-vol 
        type: DirectoryOrCreate
  dnsPolicy: ClusterFirst
  nodeName: wo1-admn6
  restartPolicy: Always 
status: {}
```

* The `nodeName` ensures that the Pod is scheduled on a specific nod. Prior to deploying the Pod, the targed node does not have a `/tmp/data-vol` dir. 

* For example `kubectl apply -f storage-pod.yaml` will create a storage pod, and list it with `kubectl -n infra get pod -o wide`

### Distributed Storage Management System

* K8s' best practices recommend that we should aim for decoupling as much as possible, that includes decoupling our applications from the underlying storage infrastructure. This can be achieved by introducing a new abstraction layer between the Kubernetes storage resource definitions and the storage infrastructure - storage interfaces that are not available as Kubernetes native storage plugins such as the following:

* **Rook** [Rook](https://rook.io/) is a graduated project of the [Cloud Native Computing Foundation (CNCF)](https://cncf.io/) capable of managing File, Block, and Object storage for K8s clusters. It simplifies and automates the deployment, scalability, self-healing, disaster recovery, management, and monitoring of distributed storage systems such as Ceph. Minimizes data loss through distribution and replication, and optimizes the usage of commodity hardware in favor of costly storage solutions, preventing possible vendor lock-in.

* **Longhorn**  [Longhorn](https://longhorn.io/) is an incubating project of the CNCF originally developed by [Rancher](https://rancher.com/). It implements highly available persistent storage for K8s. It is capable of managing cloud-native persistent block storage at reduced costs, unlike (absolutely) proprietary cloud storage service alts. It has built-in backups and incremental snapshot capabilties, along with cross-cluster disaster recovery, which are much desired features for today's multi-cluster K8s deployment model.

### Cloud Foundry Volume Service

* With *volume services*, the volume service broker allows Cloud Foundry apps to attach external storage.

* With the `volume bind` command, the service broker issues a vol mount instruction, which instructs the Diego schedule to schedule the app instances on cells which have the appropriate vol driver. In the backend, the vol driver gets attached to the device. Cells then mount the device into the container and start the app instance.

* **CF Volume Services**

    * **nfs-volume-release** allows for easy mounting of NFS shares for Cloud Foundry apps.

    * **smb-volume-release** same but with SMB shares.

### CSI (Container Storage Interface)

* The aim of [CSI](https://github.com/container-storage-interface/spec) is to have the same vol plugin work with container orchestrators out of the box, usually through the help of third party storage plugins.

* The role of CSI is to maintain the [specification](https://github.com/container-storage-interface/spec/blob/master/spec.md) and the [protobuf](https://github.com/container-storage-interface/spec/blob/master/csi.proto), which is a protocol buffer and platform-neutral lang that serializes structured data.


DevOps and CI/CD 
----------------

* Gonna blow through this chapter pretty fast since I've already taken a Linux Foundation course on DevOps ([my notes for the course](https://github.com/CiscoSteve42/Notes/blob/main/Linux/Linux%20Foundation/IntrotoDevOps.md)) but it should make a good review.

### Jenkins Overview 

* [Jenkins](https://jenkins.io/) is one of the most popular automation tools, and a graduated project of the [CD Foundation](https://cd.foundation/). It's written in Java and is CI/CD compliant.

* [CloudBees](https://www.cloudbees.com/) offers a variety of Jenkins-based CI/CD products.

* [Servana](https://servanamanaged.com/services/managed-jenkins/) uses CloudBees Jenkins distribution hosted in Servana's own datacenters.

* Jenkins can also be hosted on major cloud platforms.

### Jenkins Functionality

* Jenkins can build Freestyle, Apache Ant, and Apache Maven-based projects.

* Jenkins supports over 1900 plugins in different categories, such as *Source Code Management* *Administration*, *Build Management*, *User Interface*, and *Platforms*.

* Jenkins supports the build of a **Pipeline**, which is a concept representing an entire app's lifecycle. A Jenkins Pipeline is a series of plugins that collectively implement CD. Pipeline's features (according to the [Jenkins Documentation](https://jenkins.io/doc/book/pipeline/)) are:

    * **Code** Pipelines are implemented in code and typically checked into source control, giving teams the ability to edit, review, and iterate upon their delivery pipeline.

    * **Durable** Pipelins can survive both planned and unplanned restarts of your Jenkins master.

    * **Pausable** Pipelines can optionally stop and wait for human input or approval before completing the jobs for which they were built.

    * **Versatile** Pipelines support complex real-world CD requirements, including the ability to fork or join, loop, and work in parallel with each other.

    * **Extensible** The Pipeline plugin supports custom extensions to it's DSL (domain scripting lang) and multiple options for integration with other plugins.

* [Blue Ocean](https://www.jenkins.io/doc/book/blueocean/) is a UI designed to improve user experience.  

* [Pipeline: Stage View](https://plugins.jenkins.io/pipeline-stage-view/) and [Pipeline: Graph View](https://plugins.jenkins.io/pipeline-graph-view/) are visualization plugins that aim to offer the same functionality as, and eventually replace, Blue Ocean UI.

### Travis CI Overview

* [Travis CI](https://travis-ci.com/) is a hosted, distributed CI solution for projects hosted on GitHub, BitBucket, and others.

* To run a test with CI, link your GitHub account with Travis and select a repo and create a `.travis.yml` file that defines how the build should be executed.

### Executing Build with Travis CI

* The following are build options that can be defined in a `.travis.yml` file, options marked with an asterisk are optional:

    * `before_install`
    * `install`
    * `before_script`
    * `script`
    * `before_cache`*
    * `after_success` or `after_failure`
    * `before_deploy`*
    * `deploy`*
    * `after_deploy`*
    * `after_script`

### Travis CI Characteristics

* It supports various databases

* The build phase is supported by various VMs/Containers, and various OSs 

* Travis CI supports [most languages](https://docs.travis-ci.com/user/language-specific/)

* After testing, we can deploy the app on [many cloud providers](https://docs.travis-ci.com/user/deployment)

### Benefits of Using Travis CI

* its a hosted, distributed solution integrated with GitHub and BitBucket
* easily set up and configured
* has free and several paid tiers
* supports testing for different versions of the same runtime

### Concourse Overview

* [Concourse](https://concourse-ci.org/) is an open source CI/CD system started in 2014 and written in Go.

* For containerization, it uses Docker and Docker-Compose, while the series of tasks together with resources allow us to build a job or pipeline.

* Concourse is driven by the *fly* CLI, and also has a web GUI.

### Benefits of Using Concourse

* Open source
* Can be set up on-prem or in the cloud
* Very simple method of configuring and managing CI pipelines
* Good visualization web UI 
* Can be scaled across many servers
* Data to run the pipeline can be provided by resources that never affect the performance of a worker

### Cloud Native CI/CD Tools

* [**Helm**](https://helm.sh/) is a popular package manager for K8s. It packages K8s apps into Charts, with all the artifacts, objects, and dependencies an entire app needs in order to successfully be deployed in a K8s cluster.

* [**Skaffold**](https://github.com/GoogleContainerTools/skaffold) is a tool from Google that helps to build, push, pull, and deploy code to the K8s cluster. Supports Helm.

* [**Argo**](https://argoproj.github.io/) is a cloud native family of tools aimed at workflow management on K8s clusters. The [Argo Workflows](https://argoproj.github.io/workflows/) tool is responsible for orchestrating multi-step task sequences as CI/CD pipelines on K8s, while also managing clusters. [Argo CD](https://argoproj.github.io/cd/) performs GitOps, and [Argo Rollouts](https://argoproj.github.io/rollouts/) is used for advanced deployment strategies.

* [**Flux**](https://fluxcd.io/) is a set of open source tools that enable GitOps and CD on K8s. It integrates with Helm, GitHub, GitLab, Harbor, and can be extended with components from the GitOps Toolkit for source control management, K8s kustomization, Helm, notifications, and image management automation. 

* [**GitLab**](https://about.gitlab.com/) is a DevOps platform that incorporates CI, automated delivery piplines, enables GitOps and DevSecOps. Integrates with Terraform to allow for easy deployment from bare metal, VMs, or containers wo the public cloud. Built in security compliance through automated vulnerability scanes, static and dynamic application security testing and implementing supply chain security.

* [**JFrog Pipelines**](https://jfrog.com/pipelines/)

* [**CircleCI**](https://circleci.com/) is a fast, highly scalable, reliable, and extensible CI/CD tool that builds pipelines into K8s. It provides native Docker support and integrates with K8s services and tools such as GKE, Amazon EKS, AKS, Red Hat OpenShift, Kublr, Nirmata, and Helm. It uses orbs to package CircleCI configuration defining commands, executors, and jobs. Has free and paid versions.

* [**Jenkins X**](https://jenkins-x.io/) popular CI/CD tool that can be used on K8s as well. It leverages Terraform for infrastructure management, Helm for GitOps, open source or cloud secret management servies, and [Tekton](https://tekton.dev/) for cloud native pipeline orchestration. Helps deploy, simplify, and automate CI/CD pipelines. Also automates the preview of pull requests for fast feedback before changes are merged, then it automates the environment management and the promotion of the new app versions between different environments.

* [**Spinnaker**](https://spinnaker.io/) is an open source multi-cloud continuous delivery platform, originally created for Netflix (btw), for releaseing software changes with high velocity. Supports all major cloud providers and integrates with K8s natively.


Tools for Cloud Infrastructure: Configuration Management
--------------------------------------------------------

* **Infrastructure as Code** the infrastructure resources are defined in a declarative fashion in config files that ultimately can be re-used io be able to provision consistently reproducible systems across environments.

* *Configuration management* tools allow us to define the desired stae of the systems in an automated way.

### Ansible Overview

* [**Ansible**](https://www.ansible.com/) is an easy-to-use, open source configuration management (CM) tool. It is an agentless tool that works through SSH. It can automate infrastructure provisioning (on-prem or public cloud), app deployment, and orchestration.

### Deployment Workflows

* Ansible has agentless architecture, which ensures that maintenance tasks are restricted to a single management node, and not in every instance of the cluster. All updates to managed notes are pushed via SSH, to lists of nodes that are managed through inventory files. To list the nodes, we must do the following:
```
[webservers]
www1.example.com
www2.example.com

[dbservers]
db0.example.com
db1.example.com
```

* Ansible supports dynamic inventory files for cloud providers. The management node connects with either a password or SSH key.

* [Default Ansible Modules](https://github.com/ansible/ansible/tree/devel/lib/ansible/modules)

### Playbooks

* [Playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html) are Ansible's configuration, deployment, and orchestration language.

* [Ansible Galaxy](https://galaxy.ansible.com/) is a free site for finding, downloading, and sharing community-developed Ansible roles.

* [Ansible Automation Platform](https://www.ansible.com/products/controller) is an enterprise product that introduces a UI interface, access control, and central management.

### Benefits of Using Ansible

* easy-to-use open source configuration management tool
* agentless
* automates cloud provisioning, app deployment, and orchestration
* provides consistent, reliable, and secure management
* supported by a large and active community of devs
* low learning curve 
* provides role-based access control
* is available for all major OSs


### Puppet Overview

* [Puppet](https://puppet.com/) is an open source config management tool that usees the agent/server model to configure the systems. The Agent is referred to as the Puppet Agent and the server is the Puppet Server. It also supports the agentless model to manage target systems.

* [Puppet Enterprise](https://puppet.com/products/puppet-enterprise/) ...is the Enterprise version. Duh.

### Puppet Agent

* Puppet Agent needs to be installed on each system we want to manage/configure with Puppet. Each agent is responsible for:

    * Connecting securely to the Puppet Server to pull updates and a series of instructions in a file referred to as the *Catalog File*.

    * Sending back the status to the Puppet Server.

* Puppet Agent is available for Linux, Mac, and Windows (it's apparently also available for BSD systems via ports)

### Puppet Server

* Puppet Server can be installed only on Unix-based systems. But what they REALLY mean by this is that you should run it on Linux, as it CAN work in FreeBSD or MacOS, since it IS a Java program and all, but is generally not recommended from what I've read. ANYWAY, the Puppet Server is responsible for:

    * Compiling the Catalog File for hosts based on the system, configuration, manifest file, etc

    * Sending the Catalog File to Agents when they query the Server.

    * Storing Information about the entire environment, such as host information, metadata (such as authentication keys), etc.

    * Gathering reports form each Agent and then preparing the overall report.

### The Catalog File

* Puppet prepares a Catalog File based on the manifest file. A manifest file is created using the Puppet Code:
```
user { 'stuudent':
  ensure    => present,
  uid       => '1001',
  gid       => '1001',
  shell     => ''/bin/bash',
  home      => '/home/student'
}
```

* This defines and creates a user `student` with:

    * UID/GID as 1001
    * The login shell is set to `/bin/bash`
    * The ~ dir is set to `/home/student`

* A manifest file can have one or more sections of code in this format:
```
resource_type { 'resource_name'
  attribute => value 
  ...
}
```

* After processing the manifest file, the Puppet Server prepares the Catalog File based on the target platform.

* [Puppet Core Documentation](https://puppet.com/docs/puppet/latest/resource_types.html)

### Puppet Tools

* [PuppetDB](https://puppet.com/docs/puppetdb/latest/index.html) helps generate reports, search a system, etc.

* [Puppet Forge](https://forge.puppet.com/) has ready-to-use modules for manifest files from the community.

### Benefits of Using Puppet

* Open source config management tool
* Provides scalability, automation, and centralized reporting
* Available for all major OSs
* Provides role-based access control

### Chef Overview

* [Chef](https://www.chef.io/) uses the client/server model or the clientless model to perform the configuration management[.](https://www.youtube.com/watch?v=EEbQSROxkFw&pp=ygUPY2hlZiBzb3V0aCBwYXJr) The client is installed on each host which we want to manage and is referred to as [Chef Client](https://docs.chef.io/chef_client_overview/), while pulling updates from the server is referred to as [Chef Server](https://docs.chef.io/server_overview/). Additionally, there is the [Chef Workstaion](https://docs.chef.io/workstation/), which is used to[:](https://www.youtube.com/watch?v=QrGrOK8oZG8&pp=ygUOdG9vIG1hbnkgY29va3M%3D)

    * Develop [cookbooks](https://docs.chef.io/chef_overview/#cookbooks) and [recipes](https://docs.chef.io/recipes/)
    * Sync [chef-repo](https://docs.chef.io/chef_repo/) with the version control system
    * Run command line tools
    * Configure [policy](https://docs.chef.io/policy/), [roles](https://docs.chef.io/roles/), etc
    * Interact with nodes to perform a one-off configuration

### Chef Cookbook

* A Chef Cookbook is the basic unit of configuration which defines a scenario and contains everything that supports the scenario.

* A **recipe** is the most fundamental unit for configuration, which mostly contains resources, resource names, attribute-value pairs, and actions.
```
package "apache2" do 
  action :install
end

service "apache2" do 
  action [:enable, :start]
end
```

* An [**attribute**](https://docs.chef.io/attributes.html) helps us define the state of the node. After each *chef-client* run, the node's state is updated on the *Chef Server*.

* [Knife](https://docs.chef.io/knife.html) provides an interface between a local `chef-repo` and the *Chef Server*.

### Supported Platforms

* *Chef Client* supports the following platforms:

    * AIX 
    * Linux Distros 
    * FreeBSD and other Unix-based Systems
    * MacOS
    * Windows 

* *Chef Server* is supported on:

    * RHEL 
    * SUSE 
    * Ubuntu

### Benefits of Using Chef

* Open source systems integration framework
* provides automation, scalability, High Availability and consistency in deployment
* Available for all major OSs
* Provides role-based access control.
* Provides real-time visibility, audits, and compliance with [Chef Automate](https://automate.chef.io/)

### Salt Overview

* [Salt](https://saltproject.io/) is an open source configuration management system built on top of a remote execution framework.

* It can be used in a client/server or agentless model.

* The client/server model* It can be used in a client/server or agentless model.

* In the client/server model, the server pushes commands and configs to all clients in a parallel manner, which the client runs, which returns back the status.

* In agentless mode, the server connects with remote systems via SSH, but it offers limited functionality.

* Salt is developed by VMware, and [VMware Aria Automation](https://www.vmware.com/products/aria-automation.html) is a Salt-based enterprise product.

### Salt Minions and Salt Masters

* **Salt Minions** Each client is referred to as a Salt minon, receiving config commands from the Master, and reporting back results.

* **Salt Masters** A central management server is referred to as a *Salt master*. Multi-master is also supported.

* In a default setup, the Salt master and minions communicate over a high speed data bus, [ZeroMQ](https://zeromq.org/), which requires an agent to be installed on each minion.

### Other Components: Modules, Returners, Grains, Pillar Data

* Remote execution is based on [Execution Modules](https://docs.saltproject.io/en/latest/ref/modules/all/index.html) and [Returner Modules](https://docs.saltproject.io/en/latest/ref/returners/all/index.html).

* Execution Modules provide basic functionality, like installing packages, managing files, managing containers, etc. All support modules are listed in the [Salt Module Index](https://docs.saltproject.io/en/latest/py-modindex.html), but we can also write custom modules.

* Returner Modules allow for minions' responses to be saved on the master or other locations. We can use default Returners or write custom ones.

* All information collected from minions is saved on the master, and is referred to as [Grains](https://docs.saltproject.io/en/latest/topics/grains/). [Pillar Data](https://docs.saltproject.io/en/latest/topics/pillar/) includes private information such as cryptographic keys and other specific information about eac minion which the master has. Pillar Data is shared between the master and the individual minion.

* **Configuration Management** is where the master can easily set up a minion with a specific state.

* Salt has different [State Modules](https://docs.saltproject.io/en/latest/ref/states/all/index.html) to manage a state.

### Benefits of Using Salt

* Open source config management system
* Provides automation, High Availability, and event-driven infrastructure
* Provides role-based access control
* Supports agent-based and agentless deployments
* Available for all major OSs


Tools for Cloud Infrastructure: Build and Release
-------------------------------------------------

* **Chapter Objectives**: Discuss and use build and release tools: Terraform, CloudFormation, and BOSH.

### Terraform Overview

* [Terraform](https://www.terraform.io/) is a tool that allows to define the IaC. The config files can be written in [HashiCorp Configuration Language](https://github.com/hashicorp/hcl)(HCL).

### Terraform Providers

* Terraform [Providers](https://www.terraform.io/docs/providers/index.html) in different stacks:

    * **IaaS**: AWS, DigitalOcean, GCP, OpenStack, Azure, Alibab Cloud, etc.
    * **PaaS**: Heroku, Cloud Foundry, etc.
    * **SaaS**: DNSimple, etc.

### Features

* **IaC**: Infrastructure is described using a high-level configuration syntax. This allows a blueprint of your datacenter to be versioned and treated as you would any other code. Additionally, infrastructure can be shared and re-used.

* **Execution Plans**: Terraform has a "planning" step whre it generates an execution plan. The execution plan shows what Terraform will do when you call apply. This lets you avoid any suprises when Terraform manipulates infrastructure.

* **Resource Graph**: Terraform builds a graph of all your resources, and parallelizes the creation and modification of any non-dependent resources. Because of this, Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.

* **Change Automation**: Complex changesets can be applied to your infrastucture with minimal human interaction.With the previously mentioned execution plan and resource graph, you know exactly what Terraform will change and in what order, avoiding many possible human errors.

### Benefits of Using Terraform

* It allows to build, change, and version infrastructure in a safe and effiecient manner.
* I can manage existing, as well as customized service providers. Is provider agnostic.
* It can manage a single app or an entire datacenter.
* It is a flexible abstraction of resources.

### CloudFormation Overview

* [CloudFormation](https://aws.amazon.com/cloudformation/) is a tool that allows us to define our infrastructure as code on AWS. The config file can be written in either YAML or JSON, and it can be used via Web Console or the command line.

### Features

* *Extensibility*: It supports the modeling, provisioning, and management of third-party app resources through the [AWS CloudFormation Registry](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/registry.html), for monitoring, incident management, and version control.

* *Authoring with JSON or YAML* To model the infrastucture and describe resources in a text file. The CloudFormation Designer helps with vidual design when required.

* *Authoring with programming languages* Through AWS Cloud Development Kit (AWS CDK) it supports TS, Python, Java, and .Net to model cloud apps, integrated with CloudFormation for infrastructure provisioning.

* *Safety controls* It provides Rollback Triggers to safely roll back to a prior state.

* *Preview environment changes* To model the possible impact of the proposed changes to any of the existing resources.

* *Dependency management* Determines actions sequence during stack operations.

* *Cross-account and cross-region management* Allowed from a single template, called *StackSet*.

### Benefits of Using CloudFormation

* It allows us to build, change, and version all AWS infrastructure in a safe and efficient manner.

* It supports text file configuration files (YAML and JSON), multiple programming langs (TS, Python, Java, .NET), and CLI.

* It allows for safe and repeatable infrastructure management.

* It treats infrastructure as code, allowing quick edits and version control (IaC).

### BOSH Overview








