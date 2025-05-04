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


### The Legacy Monolith * So basically, a bunch of apps were built without foresight and now maintaining them just kinda sucks. Mainly due to hardware requirements being very specific, they can't be moved to the cloud like a normal ass app. It's old and shitty and needs to be re-written in Rust. ### The Modern Microservice
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


### What is Container Orchestration?

* Wrong Answers only:
    
    * A symphony written for a group of boxes

    * Not whatever the fuck was happening at the Suez Canal

* Ummm sure, anywaayyyys....

Kubernetes
----------

### What is Kubernetes?

* "K8s is an open-source system for automating deployment, scaling, and management of containerized apps."

* It comes from the Greek Word "κυβερνήτης", which means helmsman or ship pilot.

* It's written in Go and is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0) and highly inspired by Google Borg.

* Google donated it to the [CNCF](https://www.cncf.io/) (the Cloud Native Computing Foundation), which is one of the largest sub-foundations of the Linux Foundation.

### From Borg to Kubernetes


