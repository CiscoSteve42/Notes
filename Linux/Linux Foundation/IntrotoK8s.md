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


### The Legacy Monolith

* So basically, a bunch of apps were built without foresight and now maintaining them just kinda sucks. Mainly due to hardware requirements being very specific, they can't be moved to the cloud like a normal ass app. It's old and shitty and needs to be re-written in Rust.


### The Modern Microservice

* Microservices can be deployed individually on separate servers provisioned with fewer resources (only what is required by each service and the host system itself, helping to lower compute resources)

* Microservices-based architecture is aligned with Event-driven Architecture and Service-Oriented Architecture (SOA) principals, where complex apps are composed of small independent processes which communicate through APIs over the network

* APIs allow access by other internal services of the same application or external, third-party services and apps

* Microservices can be scaled and updated individually, allowing for no service disruption to clients. Don't have to deal with all of Monolith's bullshit. 


### Refactoring

* A "Big-bang" approach focuses all efforts with the refactoring of the monolith, postponing the development and implementation of any new features, essentially delaying progress and possibly, in the process, even breaking the monolith

* An incremental refactoring approach guarentees that new features are developed and implemented as modern microservices which are able to communicate with the monolith through APIs, without appending the monolith's code. During this time, features are refactored out of the monlith which slowly fades away while all, or most of it's functionality is modernized into microservices, allowing a gradual transition from the monolith to to 
