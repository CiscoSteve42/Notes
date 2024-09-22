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






