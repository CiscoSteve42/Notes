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

* Minikube invokes the hypervisor of choice to provision the infrastructure VM(s) which will host the Kubernetes cluster node(s), or the runtime of choice to run infrastructure container(s) that host the cluster node(s).

* It invokes [kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/) to bootstrap the K8s cluster components inside of the previously provisioned node(s).

### Requirements for Running Minkube

* **VT-x/AMD-v virtualization** they may need to be enabled on the local workstation for certain hypervisors

* **kubectl** the cli client used to access and manage any K8s cluster, accessed with `minikube kubectl` command.

* **Type-2 hypervisor or container runtime** VirtualBox, KVM2, QEMU, Docker, Podman on Linux. * Minikube supports a [`--driver=none`](https://minikube.sigs.k8s.io/docs/drivers/none/) on Linux that runs K8s components on bare metal, which requires a container runtime but no hypervisor, as it uses the host's kernel natively.

* **Internet connection of first Minkube run** needed to download packages, dependencies, and updates needed to initialize cluster components.

* [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)

### Advanced Minkube Features (1)

* Examples:
```sh 
$ minikube start --kubernetes-version=v1.27.10 \
  --driver=podman --profile minipod

$ minikube start --nodes=2 --kubernetes-version=v1.28.1 \
  --driver=docker --profile doubledocker

$ minikube start --driver=virtualbox --nodes=3 --disk-size=10g \
  --cpus=2 --memory=6g --kubernetes-version=v1.27.12 --cni=calico \
  --container-runtime=cri-o -p multivbox

$ minikube start --driver=docker --cpus=6 --memory=8g \
  --kubernetes-version="1.27.12" -p largedock

$ minikube start --driver=virtualbox -n 3 --container-runtime=containerd \
  --cni=calico -p minibox
```

* Once profiles are available, output will look like this:
```sh 
$ minikube profile list

|----------|------------|---------|----------------|------|---------|---------|-------|--------|
| Profile  | VM Driver  | Runtime |       IP       | Port | Version | Status  | Nodes | Active |
|----------|------------|---------|----------------|------|---------|---------|-------|--------|
| minibox  | virtualbox | crio    | 192.168.59.101 | 8443 | v1.25.3 | Running |     3 |        |
| minikube | virtualbox | docker  | 192.168.59.100 | 8443 | v1.25.3 | Running |     1 | *      |
|----------|------------|---------|----------------|------|---------|---------|-------|--------|
```

* Target cluster can be set to minibox with `$ minikube profile minibox` and back to minikube with `$ minikube profile minikube` OR `# minikube profile default`

### Advanced Minikube Features (2)

* `minikube node list` lists nodes of a cluster
* `minikube ip` will list the control plane node's IP 


Accessing Minikube
------------------

* Objectives:

    * Compare methods to access a Kubernetes cluster.
    * Access the Minikube Kubernetes cluster with kubectl.
    * Access the Minikube Kubernetes cluster from the Dashboard.
    * Access the Minikube Kubernetes cluster via APIs.

### Accessing Minikube

* **CLI** 
* **Web UI**
* **APIs** the HTTP API directory tree of K8s can be divided into 3 group types:

    * *Core group* (`/api/v1`) includes Pods, Services, Nodes, ConfigMaps, Secrets, etc
    * *Named Group* includes objects in the (`/apis/$NAME/$VERSION`) format  with different API versions implying different levels of stability/support:

        - *Alpha level* may be dropped at any point in time (ie `/apis/batch/v2alpha1`)
        - *Beta level* well-tested, but the semantics of objects may change in incompatible ways in a subsequent beta or stable release (ie `/apis/certificates.k8s.io/b1beta1`)
        - *Stable level* appears in released software for many subsequent versions (ie `/apis/networking.k8s.io/v1`)
    * *System-wide* system-wide API endpoints (`/healthz`, `/logs`, `/metrics`, `/ui`, etc)

### kubectl

* [kubectl documentation](https://kubernetes.io/docs/reference/kubectl/)

### kubectl Configuration File 

* By default, a config file is located in `~/.kube/config` (referred to as the [kubeconfig](https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/))
```sh 
$ kubectl config view

apiVersion: v1
clusters:
- cluster:
    certificate-authority: /home/student/.minikube/ca.crt
    server: htt‌ps://192.168.99.100:8443
  name: minikube
contexts:
- context:
    cluster: minikube
    user: minikube
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: minikube
  user:
    client-certificate: /home/student/.minikube/profiles/minikube/client.crt
    client-key: /home/student/.minikube/profiles/minikube/client.key
```

* `kubectl cluster-info`

* `minikube addons enable metrics-server` 

### K8s Dashboard

* `minikube dashboard --url`

### APIs with `kubectl proxy`

* `kubectl proxy` authenticates with the API server on the control plane node and makes services available on port **8001**. We can then send `curl` requests to the API.

### APIs with Authentication 

* **Bearer token** is an access token that can be generated by the authentication server.

* `kubectl create clusterrole api-access-root --verb=get --non-resource-url='/*'`

* `kubectl create clusterrolebinding api-access-root --clusterrole api-access-root --serviceaccount=default:default`


K8s Building Blocks
-------------------

* Objectives:

    * Describe the Kubernetes object model.
    * Discuss Kubernetes building blocks, e.g. Nodes, Namespaces, Pods, ReplicaSets, Deployments, DaemonSets.
    * Discuss Labels and Selectors.

### K8s Object model

* Entities described in object model:

    * What containerized applications we are running.
    * The nodes where the containerized applications are deployed.
    * Application resource consumption.
    * Policies attached to applications, like restart/upgrade policies, fault tolerance, ingress/egress, access control, etc.

* Examples of object types are Nodes, Namespaces, Pods, ReplicaSets, Deployments, and DaemonSets

* the API Server accepts object definitions in JSON, but `kubectl` can convert YAML to JSON.

### Nodes

* [**Nodes**](https://kubernetes.io/docs/concepts/architecture/nodes/) are virtual identities assigned by K8s to the systems part of the cluster.

* Minikube uses the kubeadm bootstraping tool to initialize the control plane node during the *init* phase and grow the cluster by adding additional nodes with the *join* phase.

* The control plane nodes run the control plane agents, such as the API Server, Scheduler, Controller Managers, and etcd in addition to the kubelet and kube-proxy node agents, the container runtime, and add-ons for container networking, monitoring, logging, DNS, etc.

### Namespaces

* [Namespaces Documentation](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)

* `kubectl get namespaces` lists namespaces

* 4 Namespaces created out of the box: `kube-system`, `kube-public`, `kube-node-lease`, and `default`.

* `kubectl create namespace new-namespace-name` creates a new namespace.

* [Resource quotas](https://kubernetes.io/docs/concepts/policy/resource-quotas/) help users limit the overall resources consumed within [Namespaces](https://kubernetes.io/docs/concepts/policy/limit-range/), while LimitRanges help limit the resources consumed by individual Containers and their enclosing objects in a Namespace.

### Pods

* A [Pod](https://kubernetes.io/docs/concepts/workloads/pods/) is the smallest K8s workload object. It is the logical collection of one or more containers which represent a single instance of an app. It ensures that they:

    - Are scheduled together on the same host with the Pod.
    - Share the same network namespace/IP 
    - Have access to the same common dependencies and external storage to mount to.

* Examples of controllers: Deployments, ReplicaSets, DaemonSets, Jobs 

Example of a stand-alone Pod object's definition in YAML:
```YAML
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    run: nginx-pod
spec:
  containers:
  - name: nginx-pod
    image: nginx:1.22.1
    ports:
    - containerPort: 80
```

* `kubectl create -f foo.yaml` creates a Pod from the yaml, you could also not use a yaml and get the same results with `kubectl run nginx-pod --image=nginx:1.22.1 --port=80`

* You can generate the yaml with the following command:
```sh 
kubectl run nginx-pod --image=nginx:1.22.1 --port=80 \
--dry-run=client -o yaml > nginx-pod.yaml
```

* You can also create a json by changing the type after the -o flag

* Commands to be familiar with:
```sh
$ kubectl apply -f nginx-pod.yaml
$ kubectl get pods
$ kubectl get pod nginx-pod -o yaml
$ kubectl get pod nginx-pod -o json
$ kubectl describe pod nginx-pod
$ kubectl delete pod nginx-pod
```

### Labels 

* [Labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) re key-value pairs attached to K8s objects that are used to organize and select a subset of objects, based on the requirements in place.

* Controllers use Labels to logically group together decoupled objects, rather than using objects' names or IDs.

### Label Selectors

* There are 2 types of [label selectors](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors):

    * **Equality-Based Selectors** allow filtering of objects based on Label keys and values. Matching is achieved using the `=, ==` or `!=` operators.

    * **Set-Based Selectors** allow filtering of objects based on a set of values. We can use `in, notin` operators for Label values, and `exist/does not exist` operators for Label keys.

### ReplicationControllers

* A [ReplicationController](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/) is a complex operator that ensures a specified number of replicas of a Pod are running at any given time the desired version of the app container, by constantly comparing the actual state with the desired state of the managed app.

### ReplicaSets

* A [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) is basically a next-gen ReplicationController, it implements the replication and self-healing aspects of the ReplicationController.

* They support both equality and set-based Selectors, as opposed to ReplicationControllers that only support eqality-based Selectors.

* Common commands that utilize ReplicaSets:
```sh
$ kubectl create -f redis-rs.yaml
$ kubectl apply -f redis-rs.yaml
$ kubectl get replicasets
$ kubectl get rs
$ kubectl scale rs frontend --replicas=4
$ kubectl get rs frontend -o yaml
$ kubectl get rs frontend -o json
$ kubectl describe rs frontend
$ kubectl delete rs frontend
```

### Deployments

* [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) objects provide declarative updates to Pods and ReplicaSets.

* The DeploymentController is part of the control plane node's controller manager, and as a controller it also ensures that the current state always matches the desired state of our running containerized application.

* Example of Deployment object's definition manifest in YAML:
```YAML
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
        image: nginx:1.20.2
        ports:
        - containerPort: 80
```

* Deployment commands:
```sh 
$ kubectl apply -f nginx-deploy.yaml --record
$ kubectl get deployments
$ kubectl get deploy -o wide
$ kubectl scale deploy nginx-deployment --replicas=4
$ kubectl get deploy nginx-deployment -o yaml
$ kubectl get deploy nginx-deployment -o json
$ kubectl describe deploy nginx-deployment
$ kubectl rollout status deploy nginx-deployment
$ kubectl rollout history deploy nginx-deployment
$ kubectl rollout history deploy nginx-deployment --revision=1
$ kubectl set image deploy nginx-deployment nginx=nginx:1.21.5 --record
$ kubectl rollout history deploy nginx-deployment --revision=2
$ kubectl rollout undo deploy nginx-deployment --to-revision=1
$ kubectl get all -l app=nginx -o wide
$ kubectl delete deploy nginx-deployment
$ kubectl get deploy,rs,po -l app=nginx
```

### DaemonSets

* [DaemonSets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) are operators designed to manage node agents.

* Example of DaemonSet object definition in YAML:
```YAML
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: fluentd-agent
  namespace: default
  labels:
    k8s-app: fluentd-agent
spec:
  selector:
    matchLabels:
      k8s-app: fluentd-agent
  template:
    metadata:
      labels:
        k8s-app: fluentd-agent
    spec:
      containers:
      - name: fluentd
        image: quay.io/fluentd_elasticsearch/fluentd:v4.5.2
```

* DaemonSet commands to be familiar with:
```sh 
$ kubectl create -f fluentd-ds.yaml
$ kubectl apply -f fluentd-ds.yaml --record
$ kubectl get daemonsets
$ kubectl get ds -o wide
$ kubectl get ds fluentd-agent -o yaml
$ kubectl get ds fluentd-agent -o json
$ kubectl describe ds fluentd-agent
$ kubectl rollout status ds fluentd-agent
$ kubectl rollout history ds fluentd-agent
$ kubectl rollout history ds fluentd-agent --revision=1
$ kubectl set image ds fluentd-agent fluentd=quay.io/fluentd_elasticsearch/fluentd:v4.6.2 --record
$ kubectl rollout history ds fluentd-agent --revision=2
$ kubectl rollout undo ds fluentd-agent --to-revision=1
$ kubectl get all -l k8s-app=fluentd-agent -o wide
$ kubectl delete ds fluentd-agent
$ kubectl get ds,po -l k8s-app=fluentd-agent
```

### Services

* A **Service** involves a sophisticated solution involving the kube-proxy node agent, IP tables, routing rules, and cluster DNS server, all collectively implementing a micro-load balancing mechanisim that exposes a container's port to the cluster's network, or even the outside world.


Authentication, Authorization, Admission Control 
------------------------------------------------

* Objectives:
    - Discuss the authentication, authorization, and access control stages of the Kubernetes API access.
    - Understand the different kinds of Kubernetes users.
    - Explore the different modules for authentication and authorization.

### Overview 

* **Authentication** Authenticate a user based on credentials provided as part of API requests
* **Authorization** Authorizes the API requests submitted by the authenticated user
* **Admission Control** Software modules that validate and /or modify user requests

### Authentication 

* K8s does not have a *user* object or store *usernames* or other related details in it's object store.

* K8s CAN use usernames for the [Authentication](https://kubernetes.io/docs/reference/access-authn-authz/authentication/) phase of the API access to control (also to request logging)

* **Types of Users:**

    - **Normal Users**

    - **Service Accounts**
