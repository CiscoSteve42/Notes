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

* **Idempotent Operations** ensures that applying the same config multiple times produces the same result, regardless of the intial or intermediate states

* **Version Control Integration** Git but for your infrastructure

* **Dependency Management** ensures that components are provisioned in the correct order based on their dependencies

* **Parallel Execution** allows the tool to perform multiple operations simultaneously


### Introduction to Terraform

* Terraform is a powerful open source IaC tool that lets you define your infrastructure in human-readable config files, the code becomes the blueprint for your infrastructure, allowing you to:

    * Provision and manage infrastructure across multipple cloud providers like AWS, Azure, GCP, and even on-prem datacenters

    * Automate infrastructure changes in a safe and reliable way

    * Version control your infrastructure like any other code, making collaboration and rollbacks a breeze

    * Re-use infrastructure components as modular "Terraform modules," promoting consistency and efficiency 

* By leveraging the power of Terraform, you can:

    * **Ship Code Faster** 

    * **Focus on What Matters**

    * **Collaborate Better**

    * **Achieve Consistency**

    * **Embrace Reusability**


### Introduction to Open OpenTofu

* OpenTofu is an open source IaC tool forked from Terraform version 1.5 with familiar syntax and functionality but also introduces many key enhancements and features that cater to the needs of the open source community and address the limitations of the BSL 

* **Advantages of OpenTofu**

    * **Open Source and Community-driven** according to the [OpenTofu FAQ page](https://opentofu.org/faq/), this is under the MPL (Mozilla Public License)

    * **Flexibility and Control** but according to this next paragraph, its under the BSL (MariaDB's Business Source License), which is ACKSHUALLY the license that Terraform adopted, and the last MPL-licensed version of Terraform was forked as the first version OpenTofu and they appear to not have deviated from this licensing. The more you know. 

    * **Future-proof** open sourcing ensures that Terraform-like IaC tools will remain available and accessible to everyone, regardless of HashiCorp's future decisions involving Terraform

    * **Continuous Development and Improvement** open source is the sh!t, but we already knew this

    * **Familiarity for Terraform Users** easy to transition from one to the other

* **How OpenTofu Helps Devs and DevOps Engineers**

    * **Increased Agility and Productivity** 

    * **Improved Collaboration and Communication**

    * **Enhanced Security and Compliance**

    * **Reduced Vendor Lock-in**

    * **Cost-effectiveness**


### Introduction to AWS CloudFormation

* Allows you to define, provision, and manage your cloud infrastructure in a declarative way. Templates are either json or yaml and contain a set of instructions for AWS to create and configure the needed resources. Benefits of this approach include:

    * **Improved Consistency and Reliability** eliminates need for manual configuration, ensuring consistency through reduction of the risk of human error

    * **Increased Agility and Speed** infrastructure can be quickly provisioned and scaled based on needs, ability to create new or update existing stacks with minimal effort

    * **Reduced Costs** automation = lower costs

    * **Enhanced Traceability and Auditability** tracks all changes made along with the who and when, valuable for troubleshooting and audits

* **Key Concepts of AWS CloudFormation**

    * **Templates** written in json or taml and define the resources to be created or configured

    * **Stacks** collection of AWS resources that are created and managed together using a CloudFormation template

    * **Resources** building blocks of your cloud infrastructure, such as AWS EC2 instances, S3 bucks, and Lambda functions

    * **Parameters** allow you to pass values into your CloudFormation templates at the time of stack creation or update

    * **Outputs** allows you to retrieve information about the resources created in your CloudFormation stacks

* **Benefits for Devs and DevOps Engineers**

    * **Improved Code Resusability**

    * **Simplified Infrastructure Management**

    * **Enhanced Collaboration**

    * **Reduced Risk of COnfiguration Errors**

    * **Faster Infrastructure Deployment**

* **Comparison with OpenTofu**

    * **Open Source** CloudFormation is AWS. ABSOLUTELY PROPRIETARY

    * **Vendor Lock-in** ties you in with the AWS ecosystem

    * **Community** relies on AWS for support and development

    * **Features** not as many features as OpenTofu

    * **Cost** charges for each CloudFormation operation

    * **Learning Curve** CloudFormation has it's own syntax, therefore separate learning curve


Continuous Integration/Continuous Delivery (CI/CD)
--------------------------------------------------

* **CI/CD Overview**

    * **Continuous Delivery** a software development practice that aims to automate the process of releasing software changes to production environments in a frequent and reliable manner. Builds upon the concept of Continuous Integration (CI) by extending the automated pipeline to include deployment and release processes. In CD, the goal is to have software in a state where it can be released to production at any time

    * **CI/CD** development approach that automates the process of building images, running tests, and deploying software updates. Minimizes manual errors, provides dev feedback, and enables rapid product iterations


### Why Should You Bother?

* **The Need for Speed and Efficiency** CI/CD automates and streamlines the entire development pipeline, from code integration to deployment, ensuring a swift and efficient release process

* **Early Detection of Bugs and Issues** by integrating code changes frequently, devs can identify and rectify issues at an early stage, reducing the chances of buts accumulating and causing major problems later in the development process, saves time and enhances stability of software

* **Consistent and Reliable Builds** every code commit triggers an automated build process, leading to consistent and reliable builds, minmizing "it works on my machine" and fostering more collaboration and production

* **Automated Testing for Code Quality** validates correctness, and provides documentation for future development

* **Faster Deployment with Continuous Delivery** improves customer experience and allows a faster response to customer feedback and market changes

* **Increased Collaboration and Communication** automation and visibility allow more time and insight to contribute to the project or focus on other aspects of work

* **Cost-Efficiency and Resource Optimization** less human errors = less money spent fixing human errors


### What is *Continuous Integration*?

* At it's core, CI involves the regular merging of code changes from multiple contributors into a shared repo, serving as a proactive measure to identify and rectify integration issues at an early stage

* frequent integration, automated build processes (including code compilation, automated testing, and the creation of executable artifacts)  ensure that the codebase is consistently and reliably built

* Devs leverage various types of automated tests, including unit and integration tests, to validate the code

* immediate feedback loop allows for quick identification and resolution of issues due to prompt notifications

* early bug detection, better collaboration and understanding of project's state, more confidence in code and changes

* improved collaboration, increased efficiency, streamlined deployment processes

* more than a practice, it's a *mindset*


### What is Continuous **Delivery**?

* practice that extends the principles of CI to ensure that the codebase is always in a deployable state

* primary objective is to make software releases available, predictable, and sustainable

* automated testing and deployment processes are integral components in a CD pipeline

* **Key Characteristics**

    * **Automated Testing** like CI, strong emphasis on automated testing (including unit and integration tests)

    * **Deployment Automation** automation of the process leading up to deployment allows for the creation of a consistent and repeatable method of releasing software. 

    * **Deployment to Staging or Pre-Production** software typically deployed to a staging or pre-production environment where additional testing, user acceptance testing, or other validation processes can take place, ensuring that the software is ready for production release 

    * **Manual Intervention for Production Release** CD stops short of automatically deploying changes to production, ultimate decision requires the user to deploy, providing an additional layer of control and oversight

* **CD Benefits Include:**

    * **Reliable Releases** reliable and consistent releaes reduce the risk of introducting errors into the production environment

    * **Reduced Time to Market** automation minimizes the time required to move from development to a deployable state, allowing faster and more frequent releases


### What is Continuous **Deployment** (also CD...)

* CD takes the principals of CD a step further by actually automating the deployment to production after the changes pass automated testing. Goals is to go fast. And efficient, but ASAFP for sure

* **Key Characteristics**

    * **Automated Production Deployment** hallmark of CD is the automatic deployment of code changes to the production environment once they pass testing, minimizing the need for manual intervention

    * **High Level of Automation** heavy reliance on automation throughout the entire dev pipeline, automated testing and deployment scripts play a crucial role in this process

    * **Immediate User Access** new features or fixes immediately become accessible to end-users, allowing for quick responses to user feedback or market changes

* **Benefits Include:**

    * **Faster Time to Market** user get shiny new features faster

    * **Continuous Feedback Loop** Grugs address issues faster

    * **Efficient Resource Utilization** automation let Grugs focus on other Grug tasks


### Continuous Integration (CI) Principles and Practices

* **CI Principals**

    * **Frequent Code Integration** devs integrate code changes into a shared repo frequently, ensuring that the codebase is continuously evolving in a collaborative manner (push it, git push it gud...oohhhhhh yeahhhhh)

    * **Automated Builds** every integration triggers an automated build process, including compiling the code, running tests, and creatin executable artifacts. Automation ensures consistency and reliability

    * **Automated Testing** a comprehensive suite of automated tests is run with each integration to detect and address issues early in the development process

    * **Immediate Feedback** devs immediately know if their code integration was a success or failure, allowing for prompt issue resolution which reduces the risk of defects accumulating

* **CI Practices**

    * **Version Control** using Git or other version control system to manage code changes

    * **Automated Builds** automated builds triggered by commits that compile, run tests, and produce deployable artifacts

    * **Automated Testing** suite of automated tests including unit, integration, and possibly end-to-end tests

    * **CI Server** (examples include Jenkins and Travis CI) server monitors the version control system and triggers builds and tests upon code changes


### CDelivery and CDeployment Principles and Practices

* **Principles**

    * **Consistent Deployment Process** ensure that a deployment process is consistent and repeatable , reducing the risk of errors and ensuring that each release is reliable

    * **Automated Deployment** creates a streamlined and efficient method for releasing software (including deploying to staging for extra testing)

    * **Environment Parity** strive for parity between different environments, such as development, staging, and production, to minimize issues related to environment-specific differences

* **Practices**

    * **Continuous Delivery** software is always deployable, but deployment itself requires human intervention

    * **Continuous Deployment** includes the deployment process in automation

    * **Feature Toggles** use feature toggles or flags to enable/disable specific features in production, allowing for the decoupling of deployment and release, which enables the gradual rollout of features

    * **Rollback Mechanisms** allows rapid response to problems without causing extended downtime

    * **Monitoring and Logging** robust monitoring and logging to track the performance and behavior of the app in real-time, facilitating rapid identification and resolution of issues in production


### Understanding Release Strategies

* **Rolling Release** new features and updates are continuously and incrementally realeased as soon as they are ready

    * **Characteristics:**

        * **Continuous Updates**

        * **No Version Numbers**

        * **Incremental Improvements**

    * **Use Cases:**

        * Web applications and services that can be updated seamlessly without user disruption

        * Software where continuous evolution and rapid delivery of features are critical

        * Telling people that you use Arch Linux (btw)

* **Feature Toggles (Feature Flags)** involves wrapping new features in conditional statements that can be controlled externally, allowing devs to enable or disable features without modifying code, providing flexibility in managing future releases

    * **Characteristics:**

        * **Selective Activation**

        * **Gradual Rollout**

        * **Rapid Experimentation**

    * **Use Cases:**

        * testing new features with a subset of users

        * safely releasing features that might be turned off if issues arise

* **Blue-Green Deployment:** two environments are maintained, one is production (blue) while the other is for deploying/testing new releases (green) the switch between environments determines the active production version

    * **Characteristics:**

        * **Zero Downtime**

        * **Quick Rollback**

    * **Use Cases:**

        * web apps where downtime is not acceptable

        * ensuring seamless transition between releases in critical systems

* **Canary Release:** involves deploying a new version of the software to a small subset of users before a full release, allowing real world testing and monitoring

    * **Characteristics:**

        * **Gradual Rollout**

        * **Real-time Monitoring**

        * **Risk Mitigation**

        * **Morbid Naming**

    * **Use Cases:**

        * web and mobile apps where real-world user feedback is valuable

        * minimizing the impact of potential issues on a small user subset

* **Phased (Staged) Rollout** the new version is released to a limited subset of users initially then to a progressively proader audience over time. Each phase allows for monitoring and addressing issues before expanding to the next group

    * **Characteristics:**

        * **Controlled Progression**

        * **Feedback and Monitoring**

        * **Risk Mitigation**

    * **Use Cases:**

        * Large-scall apps with diverse user bases

        * ensuring stabilty and performance in a controlled manner


### GitOps as a Deployment Tool

* **Key Principles of GitOps:**

    * **Declarative Configuration** the desired state of the infrastructure and application is declared in Git repos as YAML manifests, Helm charts, or other declarative formats

    * **Single Source of Truth** Git repo is the only source of truth for the desired state of the system, ensuring consistency and traceability

    * **Pull-based Reconciliation** a GitOps controller continuously monitors the repo for changes and automatically applies them to the target environment, ensuring the desired state is achieved

* **Benefits of Using GitOps for Deployment:**

    * **Simplified Deployment Process** provides a straightforward and automated deployment process

    * **Increased Consistency and Reliability** consistent and reliable deployments across different environments

    * **Improved Collaboration** shared platform for managing infrastucture encourages collaboration between devs and ops teams

    * **Enhanced Auditability and Traceability** complete audit trail of changes made, facilitating troubleshooting and compliance audits

* **Popular GitOps Tools:**

    * **Argo CD** open source GitOps CD tool that supports multiple platforms and environments

    * **Flux CD** open source GitOps CD tool specifically designed for Kubernetes deployments

    * **Tekton CD** open source GitOps CD platform built on Kubernetes

    * **Jenkins X** open source platform that combines GitOps principles with Jenkins for CD

* **GitOps Adoption Considerations:**

    * **IaC Adoption**

    * **Tool Selection**

    * **Security Considerations**


Introduction to Observability
-----------------------------

* Observability is the ability to understand the internal state of a system based on it's external outputs. Being able to infer what is happening inside the system based on available information such as logs, metrics, and traces


### The Three Pillars of Observability

* **Logs** they're better than bad, they're good! Logs are digital records of events that have occurred within a system, which are often sequential and timestamped.  

* Types of logs include:

    * **Application Logs** record events happening within the application layer, such as user actions, system errors, or transactions

    * **System Logs** documents events at the OS level, including system calls, scheduled tasks, and messages from the kernel

    * **Audit Logs** focuses on security-related events, tracking user activities and changes to the system configuration

* **Metrics** numerical values that represent the characteristics of a system at a given point in time, ranging from simple measurements such as CPU utilization and memory usage, to more complex ones, such as request rates, error counts, or transaction durations. Quantifiable, high-level view of the system crucial for setting benchmarks, identifying trends, and triggering alerts when predefined thresholds are exceeded 

    * **System Metrics** provides insights into the health and performance of the underlying infrastucture, such as CPU load, memory consumption, disk I/O, and network bandwidth

    * **Application Metrics** tracks app performance, including request latency, throughput, error rates, and transaction volumes

    * **Business Metrics** daily active users, conversion rates, revinue metrics, etc. Metrics that impact business outcomes

* **Traces** capturing the path of the journey of a single request or transaction across a distributed system and measuring it's latency across various services

    * **Components of Traces**

        * **Span** a single operation or component interactio within a trace, often including start and end times for measurement

        * **Trace Context** carries the trace's identity across process, network, and service boundaries, ensuring that all spans belonging to a single trace are correctly associated 

        * **Annotations and Metadata** additional info attached to spans, such as IDs, error messages, or other contextual data

    * **Types of Traces**

        * **Distributed Tracing** tracks the journey of requests through microservices or distributed architectures, highlighting the interactions and latency between services

        * **Real User Monitoring (RUM)** captures traces of actual user interactions within a system, providing insights into user experience and performance issues

        * **Synthetic Monitoring** uses simulated requests to monitor system performance and availability in a controlled manner, complementing real user data with consistent, baseline measurements


### Why is Observability Needed?

* **Complexity of Modern Systems** with the rise of microservices architecture, cloud computing, and distributed systems, apps have become more complex

* **Faster Incident Resolution** Observability tools enable quicker detection and resolution of issues

* **Improved User Experience** proactive monitoring and analytics of system behavior lead to a better user experience as performance issues can be identified and addressed more quickly

* **Improved Troubleshooting** identify and diagnose problems quickly with analysis to pinpoint the root issue

* **Enhanced Performance** can identify bottlenecks and resource constraints

* **Reduced Costs** makes sense


### Components of an Observability Stack

* **Data Collection**

    * **Instrumentation** involves adding code to your applications and infrastucture to collect telemetry data, including metrics, logs, and traces. Popula technologies include OpenTelemetry, Prometheus, and ELK Stack (Elasticsearch, Logstash, Kibana)

    * **Agents** lightweight programs that run on your systems and collect data from various sources, such as apps, containers, and OSs. Popular examples include Datadog Agent, Fluentd, and Telegraf

* **Data Storage and Management**

    * **Metric Stores** store and manage time-series metric data, examples include Prometheus, InfluxDB, and TimescaleDB

    * **Log Aggregators** collect, centralize, and store log data from various sources, examples include Elasticsearch, Logstash, and Graylog

    * **Trace Storage** traces require specialized storage solutions due to their high volume and complex structure, options include Jaeger, Zipkin, and Honeycomb

* **Data Analysis and Visualization**

    * **Dashboards and Graphs** help visualize data in a way that's easy to understand and analyze, tools include Grafana, Kibana, and Datadog dashboards

    * **Alerting and Notification** help you stay informed about critical events and incidents by sending alerts when predefined thresholds are breached, choices include Prometheus Alertmanager, PaerDuty, and Slack integrations

    * **Analytics and Troubleshooting Tools** help analyze data in depth to identify the root cause of problems and find solutions, choices include Honeycomb, Datadog APM, and New Relic APM

* **Additional Components**

    * **Service Mesh** provides additional observability features like distributed tracing and traffic management, popular service meshes include Istio and Linkerd

    * **Chaos Engineering** practice that involves intentionally injecting faults into your system to see how it reacts, helping to identify and mitigate potential weaknesses, popular choices include Chaos Monkey and Gremlin

* **Building Your Observability Stack**

    * **Open Source Solutions** offers flexibility and cost-effectiveness but requires more effort and expertise

    * **Managed Services** Cloud providers and other vendors offer managed observability solutions that are easy to set up and use but can be more expensive

    * **Hybrid Approach** combination of both for specific needs and budget

* **Examples of Tools**

    * **Monitoring Tools** systems for collecting and aggregating data, such as Prometheus, Grafana, or Datadog

    * **Logging Systems** platforms for collecting and analyzing logs, such as Splunk or ELK Stack (Elasticsearch, Logstash, Kibana)

    * **Tracing Systems** Distributed tracing tools for tracking requests as they move through a distributed system, such as Jaegar, Zipkin, or OpenTelemetry


### Observability in DevOps and SRE

* **Observability in DevOps**

    * **Continuous Monitoring**

        * **Objective** DevOps emphasizes CI/CD and continuous monitoring, the latter of which observability is very much a part of

        * **Role** DevOps use observability tools to do DevOps stuff

    * **Feedback Loops** 

        * **Objective** Observability helps shortening feedback loops by providing actionable insights into the impact of changes on the system

        * **Role** Devs receive feedback about how code changes system behavior, helping them make informed decisions and improvements

    * **Collaboration Across Teams**

        * **Objective** Observability tools provide a common language and platform for better collaboration

        * **Role** fosters a culture of shared responsibility where Devs and Ops teams work together to solve problems

    * **IaC**

        * **Objective** Observability integrated into IaC to monitor changes

        * **Role** helps assess the performance and reliability of infrastructure changes, ensuring that they meet operational requirements

* **Observability in SRE** is not just about monitoring, but understanding the entire system's behavior, from application code to infrastructure, and leveraging that understanding to ensure reliability, efficiency, and continuous improvement. Understanding Service Level Agreement (SLA), Service Level Objective (SLO), and Service Level Indicator (SLI) is crucial in the field of cloud native technologies and observability


### Challenges in Observability 

* **Data Volume and Overhead**

    * **Challenge** modern systems generate vast amounts of data, including logs, metrics, and traces. Managing and analyzing this volume of data can be overwhelming, leading to challenges in storage, processing, and the associated costs

    * **Solution** implementing intelligent data sampling and aggregation techniques can help reduce the dasta volume without sacrificing essential insights

* **Integration Complexity**

    * **Challenge** integrating various observability tools and platforms can be complex. Different tools may use different formats and standards, leading to integration challenges

    * **Solution** adopting standard formats, such as OpenTelemetry for tracing, and using observability platforms that offer easy integration with common monitoring and logging tools can streamline the process

* **Lack of Standardization**

    * **Challenge** lack of standardized practices and formats can make it challenging to implement a consistent approach

    * **Solution** adopting formats such as OpenTelemetry

* **Complex Distributed Systems**

    * **Challenge** in microservices architectures and distributed systems, understanding the relationship and dependencies between different components can be complex. Tracing requests across various services and components can be a b!tch

    * **Solution** implementing distributed tracing tools and practices, combined with well-defined service meshes, can help visualize and understand the flow of requests through a system

* **Security and Privacy Concerns**

    * **Challenge** collecting and storing observability data may raise security and privacy concerns

    * **Solution** implementing proper access controls, encyption, and anonymization of sensitive data

* **Alert Fatigue**

    * **Challenge** too many false positives or irrelevant alerts can lead to alert fatigue

    * **Solution** fine-tuning alerting thresholds, implementing intelligent alerting strategies, and usuing anomaly detection techniques

* **Tool Proliferation**

    * **Challenge** adopting too many tools can lead to tool sprawl, making it challenging to manage and maintain

    * **Solution** carefully evaluate and select observability tools based on specific use cases. Aim for tools that provide comprehensive coverage without unnecessary duplication

* **Cultural Resistance**

    * **Challenge** lack of understanding, cultural barriers, concerns about change

    * **Solution** fostering a culture of collaboration and emphasizing the benefits of observability in terms of faster issue resolution, improved system reliability, and better user experience


### Popular Observability Tools

* **Monitoring and Metrics**

    * **Prometheus** open source monitoring and alerting toolkit designed for reliability and scalability. Collects metrics from configured targets, stores them, and makes them available for querying

    * **Grafana** popular open source platform for visualizing and analyzing metrics. Integrates with various data sources, such as Prometheus, InfluxDB, and Elasticsearch

    * **InfluxDB** high-performance, distributed, and scalable time-series database commonly used for storing and querying metrics data

    * **Datadog** cloud-based observability platform that integrates monitoring, logging and APM (application performance monitoring) capabilties, supports wide range of integrations

* **Logging**

    * **ELK Stack** Elasticsearch is a distributed search and analytics engine, Logstash is a log pipeline tool, and Kibana is a visualization platform

    * **Splunk** widely used platform for searching, monitoring, and analyzing machine-generated data, including logs

* **Tracing**

    * **Jaeger** open source, end-to-end distributed tracing system that helps in monitoring and troubleshooting the latency of requests in complex, microservices-based architectures

    * **Zipkin** another open source distributed tracing system that allows users to trace requests as they travel through various services in a distributed system

* **Application Performance Monitoring (APM)**

    * **New Relic** (Frontalot, with the bad speller. Yo keep it logged in) a cloud-based APM tool that provides detailed insights into application performance. Offers features like transaction tracing, error tracking, and infrastructure monitoring

    * **AppDynamics** a comprehensive AP solution that provides real-time monitoring of applications, user experience, and infrastructure, helps identify performance bottlenecks

* **Infrastructure Monitoring**

    * **Nagios** widely-used open source infrastructure monitoring solution, can monitor and provide alerts for hosts, services, and networking devices

    * **Zabbix** open source monitoring solution that offers features for monitoring servers, networks, applications, and services, supports range of data visualization options

* **Cloud Native Observability**

    * **AWS CloudWatch** monitoring and observability service for AWS resources

    * **Azure Monitor** MS Observability service for Azure


Site Reliability Engineering (SRE)
---------------------------------

* Final Chapter!

* SRE is an approach to running large-scale, reliable services, with Google being widely credited for formalizing and popularizing the term. Primary focus is to improve the reliability of services, measured through SLIs, SLOs, and SLAs 


### SRE versus DevOps

* **Characteristics of SRE**

    * **Focus on Reliability** SREs are specifically tasked with maintaining a high level of service reliability and meeting SLOs

    * **Error Budgets** quantifies the allowable amount of downtime or errors within a specific timeframe, allowing for a balance between reliability and innovation as long as the error budget isn't exhausted

    * **Measurable Objectives** uses SLOs and SLIs to quantify the performance and reliability of systems to guide decision-making and help prioritize efforts

    * **Blame-Free Post-Mortems** conducted to understand the root causes of issues and to implement preventative measures for the future

    * **Automation** a core principle of SRE, leveraged to handle routine operational tasks, enabling them to focus on strategic improvements and proactive measures

* **Characteristics of DevOps**

    * **Cultural Approach** emphasizes collaboration and communication between dev and ops teams

    * **CI/CD** aims for streamlined and automated software delivery pipeline, facilitating frequent and reliable releases

    * **IaC** enables the automation of infrastruction provisioning and configuration, resulting in consistent and reproducible environments

    * **Cross-Functional Teams** collaboration through the development process to deliver more resilient and scalable systems

* **SRE vs DevOps: Relationship and Overlap**

    * **Collaboration** both emphasize collaboration, but SRE is a specific role with a narrower focus on reliability, while DevOps is more of a cultural approach that spans the entire development cycle

    * **Automation** both seek to improve efficiency and reduce manual errors

    * **Shared Goals** both seek to improve system reliability, reduce downtime, and accelerate the delivery of software


### Measuring Reliability with SLIs

