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

* **Docker Client**

* **Docker Images**

* **Docker Registry**

* **Docker Compose**

* **Docker Swarm**

* **Networking and Storage Drivers**
