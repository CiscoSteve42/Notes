Introduction to DevOps and Site Reliability Engineering
=======================================================

* Course that I'm taking from the Linux Foundation in preparation for my LFCA exam.


Intro to DevOps and SRE (not JRE, thank god) 
--------------------------------------------

* **DevOps** (Development + Operations) is a set of practices, principles, and cultural philosophies that aim to enchance collaberation and communication between the software devs and the operations teams with the primary goal of automating and streamlining the processes of software delivery and infrastructure changes, fostering a culture of continuos improvement and faster, more reliable releases.

    * Focuses on creating new features and improvements in the system

    * Ensures greater agility, reliability, ans security in operations

* **Site Reliability Engineering** (SRE) is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems. Developed by Google to create scalable and highly reliable software systems. 

    * Focuses on ensuring the reliability and stability of the system


### Emergence of DevOps

* **Early Influences**

    * **The Agile movement**, emerging in the 90s and formally established in 2001, emphasized iterative development and collaberation, paving the way for DevOps' focus on faster delivery and team integration

    * **Automation** The rise of automation tools throughout the SDLC (software development lifecycle) simplified manual tasks, allowing teams to focus on higher-level activities

    * **Cloud Computing** The emergence of cloud platforms provided a scalable and flexible environment for development and deployment, further facilitaing collaboration and faster delivery


* **Formative Years (2007-2009)**

    * **Patrick Debois** A Belgian consultant and project manager, that in 2007, frustrated by pre-DevOps practices, began advocating for closer collaboration. He coined the term "DevOps" in '09, which resonated with the growing desire for a more integrated approach to software development. 

    * **Agile Infrastructure** the 'Agile infrastructure' movement emerged around the same time, focusing on applying Agile principles to infrastructure management, aligning it with development practices.


* **Gaining Momentum (2010s)**

    * **CI/CD (Continuous Integration and Continuous Delivery)**  The adoption of CI/CD practices became instrumental in accelerating software deliver and improving feedback loops between development and operations.

    * **DevOps tools and platforms** A surge of specialized DevOps tools and platforms emerged, automating tasks and providing shared visibility throughout the SDLC.

    * **Increased Awareness and Adoption** DevOps became a popular topic in conferences and publications, leading to increased awareness and adoption across various industries.


* **Continuous Evolution (Present Day)**

    * As industry needs change, new DevOps practices and tools emerge, focusing on areas such as security, compliance, and automation in clound environments

    * The focus of DevOps culture expands beyond tools and processes to create a collaborative culture that fosters communication, shared responsibility, and continuous improvement. 


### Key Factors Contributing to the Emergence of DevOps

* Need for faster software delivery

* Inefficiencies of siloed teams

* Rise of automation tools 

* Cloud computing


### Key Principles of DevOps

* **Collaboration** emphasizes breaking down silos between development and operations teams, encouraging shared responsiblities and improved communication.

* **Automation** using tools to automate manual and repetitive tasks in the software development and delivery pipeline.

* **Continuous Integration (CI)** Devs integrate their code into a shared repo multiple times a day, with automated builds and tests to detect and address issues early in the development process.

* **Continuous Deployment (CD)** automatically deploying code changes to production environments after passing automated tests, ensuring rapid and reliable releases.

* **Infrastructure as Code (IaC)** managing and provisioning infrastructure through code, enabling consistent and repeatable infrastructure deployments.

* **Monitoring and Feedback** ehphasizing continuous monitoring of applications and infrastructure, providing real-time feedback to identify and address issues promptly. 


### Benefits of DevOps

* **Speed**s stuff up with automation and collaboration

* **Rapid Delivery** Continuous integration, delivery, and deployment

* **Reliability** Automated testing with a focus on quality assurance and reliability, reducing risks of downtime

* **Scalability** Automating processes and containerization platforms allow for increased scalabilty

* **Improved Collaboration** between the Devs and the Ops team

* **Security** incorporation of security testing and compliance checks into the development and deployment process, helping identify and address security vulnerabilities early in the development cycle

* **Improved Customer Satisfaction** delivers software quickly and efficiently, good stuff, happy customer, happy Grug

* **Cost Savings** Optimizing resources for reduced development and deployment costs


### DevOps Tools 

* **Version Control**

    * **Git** is widely used for version control, and helps track changes in source code during development.

    * **Subversion (SVN)** is a centralized version control system. It allows users to keep track of all changes made to files and directories in a repo. SVN is known for it's simplicity and is often used in projects where a centralized, linear workflow is preferred.

    * **Bitbucket** is a cloud-based platform offering Git-based version control, code review, and CI/CD tools. It offers features such as code hosting, issue tracking, and pull requests.

    * **GitHub** (what's that?) is a popular cloud-based platform for version control, social coding, and project management.

* **CI/CD**

    * **Jenkins** is an open source automation server that facilitates building, testing, and deploying code changes.

    * **Travis CI** is a CI/CD service that integrates with GitHub repos for automated testing and deployment.

    * **CircleCI** is a cloud-based CI/CD platform supporting automation and parallel testing.


* **Configuration Management**

    * **Ansible** is an open source automation tool that simplifies config management, app deployment, and task automation.

    * **Chef** enables infrastructure automation and configuration management using reusable scripts known as *reciples*

    * **Puppet** is a configuration management tool used for automating the provisioning and management of infrastructure.


* **Containerization and Orchestration**

    * **Docker** is a *very* popular  platform for developing, shipping, and running apps in containers. 

    * **Podman** is an open source container engine that offers a Docker-compatible cli and runtime. It features image creation, management, and deployment, but lacks some advanced features like built-in orchestration

    * **LXC (Linux Containers)** lightweight containerization technology built into the Linux kernel, offering efficient resource utilzation and isolation. Simplicity and portability, but lacks advanced features of other Tools

    * **Kubernetes** an open source container orchestration platform for automating the deployment, scaling, and management of containerized applications. The *Big Daddy* of container orchestration platforms. 

    * **OpenShift** a container platform developed by Red Hat. Extends Kubernetes and provides additional features for enterprise applications, including source-to-image builds and developer-focused tools.  

    * **Apache Mesos** an open source cluster management and orchestration platform designed to simplify the management of distributed applications and resources in data centers of cloud environments


* **IaC**

    * **Terraform** a tool for building, changing, and versioning infrastructure efficiently and safely

    * **AWS CloudFormation** Amazon's IaC services for provisioning and managing AWS resources using templates

    * **OpenTofu** a fork of Terraform. *Open source, community-driven, and managed by the Linux Foundation*


* **Continuous Monitoring**

    * **Prometheus** an open source monitoring and alerting toolkit designed for reliability and scalabilty

    * **Zabbix** a *comprehensive* monitoring solution for servers, networks, applications, and other IT infrastructure. Offers monitoring capabilities, alerting, and reporting features. Supports various monitoring protocols and provides extensive customization options 

    * **Nagios** Popular open source monitoring tool with a focus on server and network monitoring. Offers flexible plugin system for extending it's monitoring capabilties and features robust alerting and notification options.

    * **OpenNMS** open source network management system with built-in monitoring capabilities. Provies comprehensive network discovery, mapping, and monitoring features, and offers a web-based interface for managing and visualizing networking performance.

    * **Grafana** a visualization platform that integrates with various data sources, including Prometheus, for creating interactive and shareable dashboards


* **Collaboration and Communication**

    * **Slack** team colab tool

    * **Microsoft Teams** communication and collaboration platform, integrates with other MS tools


* **Logging**

    * **ELK Stack (Elasticsearch, Logstash, Kibana)** a set of tools for log management, enabling search, analysis, and visualization of log data

    * **Fluentd** lightweight and high-performance log collector and forwarder. Offers flexible configuration and supports various input plugins for collecting logs from different sources. Integrates seamlessly with other logging tools and platforms

    * **Splunk** a comprehensive logging platform offering log collection, indexing, search, analysis, and visualization. It provides powerful rea-time analytics and AI-driven insights for troubleshooting and security.

    * **Datadog** a comprehensive monitoring platform offering log management, metrics collection, and app performance monitoring functionalities


* **Source Code Management (SCM)**

    * **Bitbucket**

    * **GitLab**

    * **GitHub**

### The Future of DevOps

* **AI-Powered Automation** AI-powered tools will automate tedious tasks, predict failures, and optimize software delivery processes

* **Security-first approach** Security will need to be integrated seamlessly into the entire SDLC (software development life cycle), from code development to deploying and monitoring

* **Shift towards self-service platforms** teams will rely more on self-service platforms to access the tools and resources that they need without relying on central IT teams, allowing for more independent and autonomous work

* **Rise of Low-code/no-code tools** allows non-technical users to participate in the software development process, making it more accessible

* **Focus on observability and monitoring** continuous monitoring and observability is and will be crucial in dynamic cloud environments

* **Collaboration across the entire value chain** DevOps will extend past the Dev and the Ops, assimilating everything from marketing and sales to customer support. *We are DevOps, Resistance is Futile.*

* **Embracing the "everything as code" (EaC) approach** This philosophy will become increasingly prevalent, where infrastructure, configuration, and other aspects of the tech stack are managed as code, providing for greater consistency, flexibility, and automation

* **Continuous learning and upskilling** Tech evolves and you need to as well to stay relevant and adaptable. *It's a cold world out there kid.*


Introduction to Cloud
---------------------
By the end of this chapter, you should be able to:

* Discuss the meaning and importance of cloud and its major services

* Explain different cloud deployment models

* Familiarize yourself with the characteristics and procedures necessary for deploying widely-used services across popular cloud platforms


### What is *the Cloud*

* It's somebody else's server that you're paying to use, but all romanticized and sh!t.


### Why Should You Bother?

* "*When you're too poor to buy, the most popular option is to rent*" ~ me, just now.

* **Scaling Success with Flexibility**

    * **Flexibility** Dynamic scaling of resources based on demand. The systam can automatically allocate additional server power to handle increased loads, ensuring that apps remain responsive and available.

    
* **Rapid Prototyping and Innovation**

    * Cloud has like, a bunch of tools and allows devs to leverage IaC and stuff. More in the numerous cloud courses that I'm going to be taking after this one =/


### A *Brief* History of Cloud

* **Back in the Day...(1950s-90s)** 

    * Something, something something...Salesforce and AWS...

    * #fill in with the history of cloud when you have a connection [doit](https://www.techtarget.com/whatis/feature/The-history-of-cloud-computing-explained)

 
* **The Birth of *Virtualization* (Early 2000s)**

   * VMs laid the foundation for the scalable infrastructure that we associate with the cloud. 


* **The Rise of Public Cloud Providers (Mid 2000s)**

    * **AWS**: *Elastic Compute Cloud (EC2)* was launched in 2006 and, was considerd the first major public cloud service. In 2007, AWS introduced *Simple Storage Service (S3)* and launched additional services throughout the years

    * **GCP**: *Google App Engine* was announced in 2008, then *Google Cloud Platform* was launched in 2012, which offered services such as Compute Engine, CLoud Storage, and BigQuery

    * **Azure**: In 2008, Microsoft announced *Project Red Dog*, which was later known as Azure...so red...blue...what? *Anyway*, Azure was launched in 2012 as *Windows Azure*, but got renamed to *Microsoft Azure* in 2014

    
    * *AWS* is the GOAT, so that's why I'm learning it regardless of how I feel about Mr Yacht-ception Man (the other choices aren't exactly peachy either. I'm just gonna shut up and learn cloud ksrythx)

    * Cloud existed before this in various forms although the term wasn't popularized and used until this era, the *definition* of cloud computing was still evolving in this era


* **The Era of PaaS and SaaS (Late 2000s-Early 2010s)**

    * **Paas** (Platform as a Service) platforms like Google App Engine, Cloud Foundry, AWS Beanstalk, etc provided devs with tools to deploy and build apps with out managing underlying infrastructure

    * **SaaS** (Software as a Service) platforms like Dropbox and Salesforce were dope for delivering software through the cloud


* **Hybrid Cloud and Multi-Cloud Strategies (Present)**

   * **Hybrid Cloud** allows a combination of on-prem infrastructure with cloud services. Blah blah flexibility compliance

   * **Multi-Cloud Strategies** uses services from multiple Cloud providers to optimize costs and meet company needs


* **Innovations and Future Horizons**

    * Serverless Computing, Edge Computing, and AI continue to evolve the cloud


### Types of Clouds 

I will always hear all of these in Professor Messer's voice

* **IaaS (Infrastructure as a Service)**

    * Devs get basic tools, such as servers, storage, and networking to create and manage their own apps (building your house but renting the land and utilities)

* **PaaS (Platform as a Service)**

    * Lets devs focus on building and improving apps (hire a company to build the house)

* **SaaS (Software as a Service)**

    * Fully developed apps available for users on the fly (like moving into a fully furnished house)

* **FaaS (Function as a Service)**

    * Allows devs to deploy apps without managing the servers, with the cloud provider dynanamically managing the allocation of resources, allowing the devs to focus on functionality and scaling while only paying for what they need (House MD...I just wanted to say it)


### Cloud Deployment models

* **Public Cloud** computing resources are provided by a third-party cloud provider and are made accessible to the general public over the internet. Examples include the main cloud providers (Azure, AWS, GCP) 

* **Private Cloud** exclusive environment utilized by a single organization, can be hosted on prem or by a third party. Tools used include OpenStack, Hyper-V, XenServer, and vSphere by VMware, which allow orgranizations to esatblish a private cloud in their own datacenters

* **Hybrid Cloud** utilizes features of both public and private clouds, allowing the sharing of data and apps between the 2, allowing for more flexibility and diverse deployment options. Examples include Azure Hybrid Cloud, VMware Cloud Foundation, and CloudHesive 

* **Community Cloud** shared among multiple organizations with shared concerns, such as regulatory compliance. This allows organizations to collaborate within the cloud to complete objectives

* **Multi-Cloud** leveraging multiple cloud providers to avoid vendor lock-in, enhance redundancy, and optimize costs. 


### Major Cloud services

* **Compute Services** "Engine" or "virtual brains" of software. VMs are versitile computing environments, and containers, such as those managed by Google Kubernetes Engine (GKE), Azure Kubernetes Service (AKS), or Rancher offerce lightweight and scalable ways to package and deploy apps

* **Storage Services** "Cloud memory". *Object storage*, like Amazon S3, Azure Blob Storage, or wasabi "vast digital warehouse" where you can store your data. *Block storage*, such as Google Cloud Persistent Disks, offers more traditional storage options, while file storage services such as AWS Elastic File System (EFS) or Azure File Storage organize date in a file structure designed for easier access

* **Database Services** "Brain's memory banks" stores and manages structured data. Services like AWS RDS, Azure SQL Database, or DigitalOcean Managed Databases provide scalable and efficient solutions for relational databases. NoSQL databases such as MongoDB Atlas or Google Cloud Firestore offer flexibility when working with unstructured or semi-structured data

* **Networking Services** "Connectors of the cloud" enables communication between various components. Virtual networks such as AWS VPC, Azure Virtual Network, Oracle Cloud Infrastructure (OCI)'s Virtual Cloud Network (VCN), or DigitalOcean's Virtual Private Cloud (VPC) act as the digital infrastructure for applications. CDNs (Content Delivery Networks) like Cloudflare or Akamai speed up content delivery by caching it closer to users

* **Security and Identity Services** "Guardians of the Cloud, out this Fall. Rated PG-13." IAM (Identity and Access Management) services such as AWS IAM or Azure Active Directory manage who has access to what. Encryption services, such as AWS KMS or Azure Key Vault add an extra layer of security by safeguarding sensitive information

* **Machine Learning and AI Servies** Platforms such as Google AI Platform or Azure Machine Learning provide tools and frameworks, NLP (Natural Language Processing) services such as AWS Comprehend or Google Cloud Natural Language API make it easy to analyze and understand human language. 

* **Serverless Computing** akin to "outsourcing mundane tasks", allowing devs to focus purely on writing code. FaaS services such as AWS Lambda or Azure Functions allow you to run code in response to events without worrying about managing servers

* **IoT Services** "Conductors of a digital orchestra" Platforms such as AWS IoT or Azure IoT Hub help you connect, monitor, and manage IoT devices seamlessly. For edge computing, where processing happens closer to the data source, services like Google Cloud IoT Edge or Azure IoT Edge provide a distributed solution

* **DevOps and CI/CD Services** Continuous Integration tools such as Jenkins or GitLab CI automate testing and integration of code changes. Container orchestration tools such as Kubernetes and Docker Swarm help manage and deploy containerized apps, ensuring consistency across different environments

* **Analytics and Big Data Services** Platforms like AWS EMR and Azure HDInsight make it easy to process and analyze large datasets. For data warehousing, where you need to store and query massive amounts of data quickly, services like Google BigQuery or Snowflake provide scalable solutions

* Jesus Christ the GCP UI is a laggy trash fire


Introduction to Containers and Kubernetes
-----------------------------------------

### The Difference Between Containers and VMs

* **Virtual Machines: Isolated and Versatile** fully isolated virtual environment, complete with OS and all necessary dependencies, physical hardware is abstracted

    * **Strong isolation** operates as an independent entity with it's own dedicated resources, making them highly secure

    * **Compatibility** different OSs on same hardware, allows running legacy apps or different OS versions in parallel

    * **Complete Abstraction** VMs operate as if running on dedicated physical machines, giving them full control of the virtual environment

    * **Resource Overhead** Uses more resources than containers due to needing a whole OS instance for each VM, resulting in higher infrastructure costs and slower startup times than containers


* **Containers: Lightweight and Efficient** run packages and dependencies isolated from host system, lightweight and highly efficient VM alternative

    * **Resource Efficiency** share the host OS's kernel, elliminating the need for multiple OS instances, making them more resource efficient than VMs

    * **Rapid Startup and Scalability** rapid startup makes containers highly scalable and allows for horizontal scaling (spinning up multiple instances of an app to handle increased workload)

    * **Isolation and Security** containers are isolated from host OS and each other, which provides strong isolation but vulnerable if host OS has a kernel vulnerability

    * **Ease of Management** easy to deploy update and roll back due to their lightweight nature, making them ideal for apps that require frequent updates and CI/CD workflows 

* **Which One to Choose**

    * **Development and Testing** Containers are widely used in development and testing due to agility and easy of management

    * **Microservices Architecture** Containers allow for easy scaling and deployment of individual services

    * **Legacy Applications** VMs are preferred for legacy apps that may not be compatible in modern environments, can run apps without significant modifications to the infrastructure

    * **High Isolation Environments** VMs more secure than containers, better fror when data privacy is paramount


### Brief History of Containers 

* **Chroot (1970s)** allows a process to have it's own isolated view of the filesystem by changing the root directory to a specified filepath

* **FreeBSD Jails (2000)** lightweight virtualization by isolating processes, filesystems, and networking. Early form of containerization

* **Solaris Containers (2004)** allowed multiple Solaris instances to be ran isolated on a single host

* **cgroups and Namespaces (2007)** the Linux kernel introduced control groups (cgroups), which enabled resource isolation, and namespaces, which enabled process isolation

* **LXC (Linux Containers) (2008)** used cgroups and namespaces to provide process and resource isolation

* **Docker (2013)** revolutionized container technology, friedly cli and standardized images

* **Container Orchestration (2014+)** tools such as Kubernetes, Docker Swarm, Apache Mesos, or Hashicorp's Nomad automate deployment, scaling, and management of containerized apps

* **OCI (Open Container Initiative) (2015)** specifications define the Open Container Format (OCF) for container images and the Open Container Runtime (OCR) for container runtimes

* **Containerd (2017)** Docker donated containerd (it's container runtime) to the CNCF (Cloud Native Computing Foundation) and it is now a core component of many container platforms and orchestration tools

* **Rise of Alternatives (2020s)** tools like Podman provide flexibility and address some concerns associated with Docker


### Docker: What's Under the Hood

* **Docker Engine**

    * **Containerd** Industry standard core container runtime, provides basic functionality for container execution and management. Handles low-level container operations such as container creation, execution, and deletion

    * **runC** at the core of containerd is runC, the industry standard container runtime. Responsible for spawning and running containers based on OCI (Open Container Initiative) specs. Handles container lifecycle, including creating and running containers from images 

    * **libcontainer** original Docker container execution library, eventually it's functionality was incorporated into containerd

* **Docker Client** CLI tool that allows users to interact with the Docker Daemon/Engine, such as building, running, and managing containers

* **Docker Images** lightweight, standalone, executable packages that include the app and all of it's dependencies. Images are built from instructions defined in the Dockerfile. Stored in a registry such as Docker Hub so that they can be easily shared and distributed

* **Docker Registry** place to store docker images, can be public or private

* **Docker Compose** tool for defining and running multi-container Docker apps. Allows users to describe services, networks, and volumes in a docker-compose.yml file (Compose ftw!)

* **Docker Swarm** Docker's native clustering and orchestration solution. Users can create and manage a swarm of Docker nodes, turning them into a single virtual Docker host. Enables deployment and scaling of services across multiple containers

* **Networking and Storage Drivers** Networking and storage drivers containers can be configured on requirements, such as communicating with each other or the outside network


### Podman: An Alternative to Docker

* **What makes Podman different from other container engines (Docker)**

    * **Daemonless Architecture** Each command runs in the Podman process, reducing attack surface and allowing non-root (or non-docker group) users to run containers

    * **Root and Rootless Modes**
        
        * **Root Mode** similar to traditional Docker, provides root access to the system

        * **Rootless Mode** One of Podman's biggest features, reduces risk of priv escalation

    * **Use of Fork/Exec Model** when a container is started with Podman, it forks itself then execs the runtime (like runc or crun). Each container is it's process or set of processes on the host, managed directly by the kernel and not by a long-running daemon process

    * **Compatibility with Docker** compatible with Docker in CLI syntax, making transition easy. Easy to alias for most commands 

    * **Pods Management** Similar to Kubernetes, groups of containers that share the same network, IPC, and PID namespaces are called pods. Allows Podman to align well with Kubernetes environments

    * **Image Management** uses same images format as Docker, including Docker Compose files!

    * **Networking** supports multiple network modes, including host, bridge, and container networking. Modes are handled per container and can be set up to mimic Docker's networking configurations

    * **Security** daemonless and rootless mode reduce security risks, native integration with SELinux, seccomp, and other security features provided by the Linux kernel


### The Need for Container Orchestration

* **Automating Container Management**

    * **Deployment** orchestrators can automatically deploy containers to different nodes in a cluster, ensuring that apps are available and running smoothly

    * **Scaling** containerized apps can automatically scale up or down based on demand, ensuring optimal resource utilization

    * **Health Monitoring** orchestrators can monitor the health of containers and automatically restart them if they fail, ensuring app uptime

    * **Networking** networks for containerized apps can be configured and managed, ensuring communication with each other and external resources

* **Streamlining Complex Workflows** orchestration platforms can help simplify and streamline complex workflows, such as CI/CD pipelines. They can automate the build, test, and deployment of containerized apps, allowing devs to do other dev stuff

* **Improving Resource Utilization** make sure containers are only running when needed, saving on costs

* **Enforcing Consistency and Control** enforces consistency and control over containerized apps, helping ensure that they're deployed in a consistent manner and meet security/compliance requirements 

* **Enabling Multi-Cloud Deployments** apps can be deployed across multiple cloud vendors, providing greater flexibility and resilience

* **Popular Orchestration Platforms** 

    * **Kubernetes** 

    * **Docker Swarm**  

    * **Apache Mesos**

    * **Nomad**


### Kubernetes: The Orchestrator of Containerized Applications

* **The Breakdown**

    * **Deployment** automated deployment across a cluster of nodes

    * **Scaling** automatic scaling based on demand

    * **Load Balancing** even traffic distribution across different instances, ensuring high availability and responsiveness

    * **Service Discovery** enables apps to discover and communicate with each other, regardless of their location in the cluster

    * **Health Monitory** monitors health of apps and automatically restarts them if they fail

    * **Security** robust security framework for managing access control and protecting apps

    * **Self-healing** restarts, replaces, and kills containers that don't respond to the user-defined health check, doesn't advertise them to clients until they're ready to serve

    * **Horizontal Scaling** scale up or down with a command, in the UI, or automatically based on CPU usage

* **The History**

    * **2014** originates from Google's internal container management system, Borg (We are Google, Resistance is Futile)

    * **2015** K8s open sourced under the Apache 2.0 license

    * **2017** K8s 1.0 released

    * **2023** shizz is used everywhere

* **Why it's the GOAT**

    * **Open Source**

    * **Scalable**

    * **Flexible**

    * **Community-driven**

    * **Collaboration**

    
### Key Components of Kubernetes

* **Control Plane Node** control plane nodes in K8s play a critical roll in managing the cluster's state and configuration. Responsible for making global cluster decisions such as scheduling, detecting, and responding to cluster events, such as starting up a new pod when a deployment's *replicas* field is unsatisfied. Key components include: **API Server** front end for the K8s control plane. Responsible for handling and validating requests, and updasting corresponding objects in the cluster, exposes the K8s API 
    * **Cluster Data Store - etcd** only stateful part of the cluster which persists the entire cluster config (aka desired state) and the current state of the cluster

    * **Controller Manager** controllers are responsible for maintaining the desired state and handling tasks such as node manaement, replication, and endpoints

    * **Scheduler** ensures the the workload is evenly distributed across the cluster, assigns pods to nodes based on resource availability, constraints, and other policies

* **Worker Node (Minion)** the machines (physical or virtual) where your containers run. Managed by the control plane and perform requested, necessary workloads. Each node has the necessary component to orchestrate and run apps. Key components include:

    * **Kubelet** an agent running on each node that communicates with the control plane node's API server. Ensures that containers are running in a pod and reports back to the control plane about the node's status

    * **Container Runtime** responsible for managing the entire container lifecycle on the node. Containerd is a prime example

    * **Kube Proxy** K8s agent installed on every node in the cluster. Implements local IPTABLES or IPVS rules to handle routing and load-balancing of traffic on the Pod network. Monitors changes that happen to Services objects and their endpoints, and translates them into actual network rules inside the node. Installed as an add-on during installation, usally created as a DaemonSet 

* **Pod** smallest deployable unit, encapsulates one or more containers and shares network and storage resources

* **ReplicaSet** manages the lifecycle of pods and ensures that a specified number of replicas for a pod are running at all times, can scale the amount of pods up or down based on defined configs

* **Deployment** provides declaritive updates to applications. Users define the desired staet and the dployment controller changes the actual state to match the desired one, facilitating updates and rollbacks

* **Service** defines a set of pods and a policy to access them. Allows communication between different sets of pods in the cluster, abstracting the underlying network details

* **Volume** manages storage, provides data persistence for containers. Volumes can be attached to pods, allowing data to persist across pod restarts

* **Namespace** provides a way to divide cluster resources into multible virtual clusters, useful for organizing and isolating resources within a cluster

* **ConfigMap and Secret** used to manage config data and sensitive information (ie passwords, API keys) separately from the application code

* **Kubernetes Dashboard** web-based UI for visually managing and monitoring the cluster. 


### What Kubernetes is **Not**

* Kubernetes is **NOT** a...

    * **Traditional Virtualization Platform** operates at the container orchestration level, not at the VM level. Does not provide virtualization, manages and orchestrates containerized applications

    * **Containerization Platform** K8s relies on container runtimes such as containerd or Docker to manage and run containers, Kubernetes focuses or orchestrating and automating deployment, scaling, and management

    * **Replacement for Docker** it is not a containerization platform

    * **PaaS** more granular control than traditional PaaS offerings. Infrastructure details are defined and manged by the user rather than abstracted away from them

    * **Config Management Tool** focuses on declaring the desired state of apps and managing their lifecycle, but does not handle general-purpose config management tasks like Ansible or Puppet

    * **Inherently Secure** robust framework, not perfect. Still implement best practices, configure network policies, and regularly update clusters

    * **Just for Microservices** can manage and orchestrate a wide range of application types, including monolithic apps and those following other architectural patterns

    * **One-Size-Fits-All Solution** designed primarily for complex, distributed systems that require scalability, resilience, and flexibility


### Developing Container Technologies

* **Containerd** core container runtime, originally part of Docker but now a standalone project and a key component for various container platforms

* **Podman** provides daemonless, rootless container experience

* **BuildKit** toolkit for building container images, provides a more modular and efficient way to build container images, often interated into container build systems. Originally part of the Moby project, the open source project rto advance the software containerization movement
 
* **Kata Containers** an open source project that combines lightweight VMs with the speed and manageability of containers, aims to provide the security benefits of VMs with the performance advantages of containers

* **CRI-O* Lightweight container runtime specifically designed for K8s, implements with the CRI (Kubernetes Container Runtime Interface) to enable the launching of containers straight from K8s with the need for a platform like Docker (Minikube uses CRI-O as it's container runtime!)

* **KubeVirt** extends K8s to support running and managing VMs alongside container workloads, giving them a unified platform

* **Firecracker** lightweight open source virtualization technology designed for serverless computing, created by AWS. Combines security of VMs with speed and efficiency of containers

* **OCI Specifications** the Open Container Initiave continues to play a crucial role in standardizing container formats and runtimes

* **Kpack** a Kubernetes-native platform for building and updating container images that automates the image-building process, making it easier for devs to create and maintain container images directly within the Kubernetes environment

* **Gvisor** a user-space kernel developed by Google that provides an additional layer of isolation to container, giving them VM-like security with the performance overhead


Infrastructure As Code (IaC)
----------------------------

* involves describing and provisioning infrastructure elements through machine-readable script files, treating infrastructure in a manner similar to software code 

* Allows devs to define infrastructure configurations using high-level programming language

* Key advantages include the ability to version control the infrastructure code, ensuring traceability, reproducibility, and easy collaboration across dev teams

* Not only simplifies initial deployments but also facilitates scaling, updates and teardowns


### Why Would You Bother?

* **Software Engineers**

    * **Efficiency and Consistency** configs can be scripted, ensuring consistency across different environments

    * **Collaboration and Version Control** enables engineers to use tools like Git to manage changes, track history, and collaborate seamlessly, like is done with application code

    * **Automation and DevOps Practices** CI/CD pipelines can trigger automated infrastructure updates, streamlining the development process

* **Developers**

    * **Scalability and Flexibility** applications can be easily scaled by modifying resource allocation in code 

    * **Reduced Downtime and Rollbacks** devs can easily revert to a previous version if needed

    * **Cross-Platform Compatibility** scripts can be adapted for different platforms

* **Product Managers**

    * **Cost Optimization** resources are provisioned as necessary

    * **Rapid Prototyping and Experimentation** environments can quickly be set up and torn down

    * **Risk Mitigation and Compliance** helps enforce standardized configurations, reducing the risk of non-compliance

* **Short-term and Long-term Business Impact**

    * **Agility and Innovation** accelerates development ctcles, allowing for fostering innovation, keeping products competitive, and quick adaptation to market changes

    * **Reliability and Stability** promotes stability by minimizing configuration drifts and automating error-prone manual processes, leading to a better end-user experience

    * **Resource Optimization and Cost Savings** resource usage optimized


### Categories of Infrastructure as Code Tools

* **Declaritive IaC Tools** users specify the desired staet of the infrastructure, and the tool ensures that the system reaches that state

    * **Terraform** allows users to define infrastructure using a declarative configuration languate. Supports various providers, enabling multi-cloud and hybrid cloud scenarios

    * **Pulumi** provides IaC in multiple languages, including Python, TS, and Go, allows integration with various cloud providers and offers flexibility

    * **SaltStack** open source platform using .yaml config files for IaC, focuses on automation and offers centralized infrastructure management

* **Configuration Management Tools**

    * **Ansible** uses declarative yaml scripts do define the state of a system. Excels at config management, automating repetitive tasks, and can be used for provisioning infrastructure

    * **Chef** uses a Ruby-based DSL (Domain Specific Language) for writing system configs. Supports declarative, but execution of Chef recipes can be seen as imperitive because the code specifies how to achieve the desired state. Powerful for managing complex environments but has a steep learning curve

    * **Puppet** config management tool that can also be used for IaC using a declarative language called Puppet DSL to define the desired infrastructure state. Good for highly scentralized and controlled infrastructure management  

* **Container Orchestration Tools**

    * **Kubernetes** tools like Helm provide a way to define and version infrastructure configurations in K8s

    * **Nomad** excels in managing heterogeneous environments, handling bare metal, VMs, and cloud platforms with equal ease

    * **CloudHedge** offers container-based VMs and serverless functions alongside container orchestration, suitable for organizations wanting a unified platform for infrastructure and application management

* **Cloud Native IaC Tools**

    * **Azure Resource Manager (ARM)** templates are JSONs that define the resources needed for an Azure solution. Tailored for Azure services, provides a way to automate the deployment and configuration of Azure resources

    * **AWS CloudFormation** templates are JSON or YAML and specify the resources needed and their configurations. Follows a procedural approach to create, update, or delete resources

* **Considerations for Choosing IaC Tools**

    * **Compatibility**

    * **Community Support**

    * **Scalability**

    * **Ease of Learning**

    * **Security**


### Five Fundamental Features of an IaC Tool

* **Declarative Configuration** allows users to specify the desired state of their infrastructure without detailing the steps to reach that state

* **Idempotent Operations**

* **Version Control Integration**

* **Dependency Management**

* **Parallel Execution**
