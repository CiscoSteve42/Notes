Introduction to Kubernetes (LFS158) Notes
=========================================

* Let's learn some K8s!

Chapter 1 
---------

* **Learning Objectives**

    * Explain what a monolith is
    * Discuss the monolith's chalenges in the cloud
    * Explain the concept of microservices
    * Discuss miscroservices advantages in the cloud
    * Describe the transformation path from a monolith to microservices

### The Modern Microservice
* Microservices can be deployed individually on separate servers provisioned with fewer resources (only what is required by each service and the host system itself, helping to lower compute resources)

* Microservices-based architecture is aligned with Event-driven Architecture and Service-Oriented Architecture (SOA) principals, where complex apps are composed of small independent processes which communicate through APIs over the network

* APIs allow access by other internal services of the same application or external, third-party services and apps

* Microservices can be scaled and updated individually, allowing for no service disruption to clients. Don't have to deal with all of Monolith's bullshit. 


### Refactoring

* A "Big-bang" approach focuses all efforts with the refactoring of the monolith, postponing the development and implementation of any new features, essentially delaying progress and possibly, in the process, even breaking the monolith

* An incremental refactoring approach guarentees that new features are developed and implemented as modern microservices which are able to communicate with the monolith through APIs, without appending the monolith's code. During this time, features are refactored out of the monlith which slowly fades away while all, or most of it's functionality is modernized into microservices, allowing a gradual transition from the monolith to microservices architecture and allows for phased migration of app features into the cloud


### Challenges

* Some apps won't 'survive' refactoring, some need to be written from the ground up in the cloud, choosing runtimes can also provided a challenge. **Application Containers** solved these issues by allowing multiple apps to be deployed on a single server, each with their own isolated runtime environments and all of the other perks of isolated, containerized environments


### Success Stories

* **AppDirect**
* **box**
* **Crowdfire**
* **GolfNow**
* **Pinterest**


Container Orchestration
-----------------------

### What Are Containers?

* **Containers** are things you put stuff in. JK lol (but not really), they're application-centric methods to deliver high-performing, scalable applications on any infrastructiure of your choice. They're best suited to deliver microservices by providing portable, isolated virtual environments for applications to run without interfaces from other running applications

* **Microservices** are lightweight apps written in various modern programming languages, with specific dependencies, libraries, and environmental requirements, apps are packaged with their dependencies so they, like, work and stuff

* Containers encapsulate Microservices and their dependencies but do not run them directly. Containers run container images


Kubernetes
----------

### What is Kubernetes?

* "K8s is an open-source system for automating deployment, scaling, and management of containerized apps."

* It comes from the Greek Word "κυβερνήτης", which means helmsman or ship pilot.

* It's written in Go and is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) and highly inspired by Google Borg.

* Google donated it to the [CNCF](https://www.cncf.io/) (the Cloud Native Computing Foundation), which is one of the largest sub-foundations of the Linux Foundation.

### From Borg to Kubernetes

* From [Google's Borg paper](https://research.google/pubs/pub43438/), published in 2015:

    * "Google's Borg system is a cluster manager that runs hundreds of thousands of jobs, from many thousands of different applications, across a number of clusters each with up to tens of thousands of machines."

* Borg runs Google's workloads, Gmap, Maps, all that jazz.

* K8s features that can be traced back to Borg include:

    * **API Servers**
    * **Pods**
    * **IP-per-Pod**
    * **Services**
    * **Labels**

K8s Features
------------

* **Automatic bin packing** Kubernetes automatically schedules containers based on resource needs and constraints, to maximize utilization without sacrificing availability.

* **Designed for extensibility** A Kubernetes cluster can be extended with new custom features without modifying the upstream source code.

* **Self-healing** Kubernetes automatically replaces and reschedules containers from failed nodes. It terminates and then restarts containers that become unresponsive to health checks, based on existing rules/policy. It also prevents traffic from being routed to unresponsive containers.

* **Horizontal scaling** Kubernetes scales applications manually or automatically based on CPU or custom metrics utilization.

* **Service discovery and load balancing** Containers receive IP addresses from Kubernetes, while it assigns a single Domain Name System (DNS) name to a set of containers to aid in load-balancing requests across the containers of the set.

* **Automated rollouts and rollbacks** Kubernetes seamlessly rolls out and rolls back application updates and configuration changes, constantly monitoring the application's health to prevent any downtime.

* **Secret and configuration management** Kubernetes manages sensitive data and configuration details for an application separately from the container image, in order to avoid a rebuild of the respective image. Secrets consist of sensitive/confidential information passed to the application without revealing the sensitive content to the stack configuration, like on GitHub.

* **Storage orchestration** Kubernetes automatically mounts software-defined storage (SDS) solutions to containers from local storage, external cloud providers, distributed storage, or network storage systems.

* **Batch execution** Kubernetes supports batch execution, long-running jobs, and replaces failed containers.

* **IPv4/IPv6 dual-stack** Kubernetes supports both IPv4 and IPv6 addresses.


K8s Architecture
----------------
* Objectives:

    * Discuss the Kubernetes architecture.
    * Explain the different components of the control plane and worker nodes.
    * Discuss cluster state management with etcd.
    * Review the Kubernetes network setup requirements.

### Control Plane Node Overview

 * Control plane provides running environment for control plane agents responsible for managing the state of a cluster.
 * Brain behind all ops inside cluster
 * CLI, Web UI, or API to send requests
 * Losing control plane introduces downtime
 * Increase fault tolerance with replicas in High-Availability (HA) mode
 * Persistence is added my saving config data in a key-value store which ONLY holds cluster staet related data

### Components 

* **API server** coordinates all adminstrative tasks
* **Scheduler** assigns new workload objects to nodes
* **Controller managers** runs controllers or operator processes to regulate the cluster state
* **Key-value data store** [etcd](https://etcd.io/) (also written in Go.)

### Worker Node Overview

* Provides a running environment for client apps

### Components

* **Container runtime** CRI-O, containerd, Docker Engine, [Mirantis Container Runtime](https://www.mirantis.com/software/container-runtime/)
* **Node agent - kubelet** kubelet is an agent running on each node, control plane, and workers. Interacts with runtime and containers in the Pod, monitors health/resources of Pods running containers
* **kubelet - CRI shims** Shims are Container Runtime Interface (CRI) implementations, interfaces, or adapters specific to each container runtime supported by K8s. Examples include cri-containerd, CRI-O, dockershim and cri-dockerd
* **Proxy - kube-proxy** network agent that runs on each node, control plane, and workers. Responsible for dynamic updates and maintenance of all networking rules on the node. Responsible for TCP, UDP, and SCTP stream forwarding or random forwarding across Pod app backends, implements user defined forwarding rules. Works in conjunction with iptables
* **Add-ons** 3rd party plugins for DNS, Dashboard, Monitoring, Logging, and Device Plugins (GPU, FPGA, NIC, etc)

### Networking Challenges

* **Container-to-Container communication inside Pods** a *namespace* is an isolated network space created by the container runtime. A network namespace can be shared across containers, or with the host OS

* **Pod-to-Pod communication across nodes** Pods are expected to be able to communicated with all others in the Cluster without NAT. K8s treats pods as VMs with their own network interface, therefore a unique IP (called **IP-per-Pod**)

    * [K8s Cluster Networking Documentation](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
    * [Container Network Interface (CNI)](https://www.cni.dev/)
    * [CNI Plugins](https://github.com/containernetworking/plugins#plugins)
    * Popular SDN plugins include Flannel, Weave, Calico, and Cilium

* **External-to-Pod communication** "K8s enables external accessibility through Services, complex encapsulations of network routing rule definitions stored in iptables on cluster nodes and implemented by kube-proxy agents."


Installing K8s
--------------

* Objectives:

    * Discuss Kubernetes configuration options.
    * Discuss infrastructure considerations before installing Kubernetes.
    * Discuss infrastructure choices for a Kubernetes cluster deployment.
    * Review Kubernetes installation tools and certified solutions.

### K8s Configuration 

* **All-in-One Single-Node Installation** control plane an worker components installed, running on single-node. Good for development and testing, bad for production.

* **Single-Control Plane and Multi-Worker Installation** single-control plane running a stacked etcd instance. Control plane can manage manage multiple worker nodes.

* **Single-Control Plane with Single-Node etcd, and Multi-Worker Installation** single control-plane node with an external etcd instance. Can also manage multiple workers.

* **Multi-Control Plane and Multi-Worker Installation** multiple control planes configured for HA in stacked etcd instance. etcd instances configured in HA etcd cluster, HA control plane can manage multiple worker nodes.

* **Multi-Control Plane with Multi-Node etcd, and Multi-Worker Installation** multiple control plane nodes configured in HA mode, with each control plane node paired with an external etcd instance. The external etcd instances are also configured in an HA etcd cluster, and multiple worker nodes can be managed by the HA control plane. This is the most advanced cluster configuration recommended for production environments. 

### Installing Local Learning Clusters 

* Minkube, [Kind](https://kind.sigs.k8s.io/), Docker Desktop, Podman Desktop, [MicroK8s](https://microk8s.io/), [K3S](https://k3s.io/)

### Installing Production Clusters with Deployment Tools

* [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)

* [**kubeadm**](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/) secure and recommended method to bootstrap a multi-node, production ready, Highly Available cluster

* [**kubespray**](https://kubespray.io/#/) lets us install Highly Available production ready clusters in the cloud or on bare metal

* [**kops**](https://kops.sigs.k8s.io/) lets us create, upgrade, and maintain clusters from the command line

### Hosted solutions

* [Alibaba Cloud Container Service for Kubernetes (ACK)](https://www.alibabacloud.com/en/product/kubernetes?_p_lc=1)
* [Amazon Elastic Kubernetes Service (EKS)](https://aws.amazon.com/eks/)
* [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/products/kubernetes-service/)
* [DigitalOcean Kubernetes (DOKS)](https://www.digitalocean.com/products/kubernetes)
* [Google Kubernetes Engine (GKE)](https://cloud.google.com/kubernetes-engine)
* [IBM Cloud Kubernetes Service](https://www.ibm.com/products/kubernetes-service)
* [Oracle Container Engine for Kubernetes (OKE)](https://www.oracle.com/cloud/cloud-native/kubernetes-engine/)
* [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift)
* [VMware Tanzu Kubernetes Grid](https://www.vmware.com/products/app-platform/tanzu-kubernetes-grid)

### K8s on Inferior OSs

* [K8s on Windows](https://kubernetes.io/docs/setup/production-environment/windows/intro-windows-in-kubernetes/).


Minikube: Installing Local K8s Clusters
---------------------------------------
* From `tldr minikube`:

```sh
  - Start the cluster:
    minikube start

  - Get the IP address of the cluster:
    minikube ip

  - Access a service named my_service exposed via a node port and get the URL:
    minikube service my_service --url

  - Open the Kubernetes dashboard in a browser:
    minikube dashboard

  - Stop the running cluster:
    minikube stop

  - Delete the cluster:
    minikube delete

  - Connect to LoadBalancer services:
    minikube tunnel
```

### What is Minikube?


