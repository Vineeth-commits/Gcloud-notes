#Core Infrasturcture
---
* Benefits of cloud computing
    * Computing resources are available on demond and self service
    * Access to resources over the net from anywhere
    * Measured service
    * Resources are elastic
* A zone is a deployment area for Google Cloud Platform Resources. A multi-region zone can be deployed to provide better fault tolerance. The locations are separated by atleast 160km.
* Quotas are designed to prevent the over-consumption of resources whether because of error or malicious attacks.
* Billing exports lets you store detailed expenditure in places such as BigQuery dataset or a Cloud storage bucket.
* Infrastructure as a Service or IaaS offering provide raw compute, storage and network organized in ways that are familiar from data centers. Here you pay what you allocate.
* Product as a Service or PaaS bind application code you write to libraries that give access to the infrastructure your application needs. Here you pay for what you use.
* Identity and Access Management, also called as IM or IAM is used to provide certain privilages to an indiviual based on their work. This adds an additional layer of security by providing restricting access to sensitive data or operations.
* GCP hierarchy resource 
    (Higher) organization node => folders => projects => resources (Lower)
* Each GCP project can have a different owners and users - they are build separately and managed separately.
* Project IDs are permanent, unique and unchangeable identifier(given by the user). A unique project number is also assigned by the GCP.
* Project names can be assigned for convenience.
* Projects can be assigned to different folders to organise it. To use folders, an organization node should be used at the top of the hierarchy.
* Organization node is the root node for google cloud resources.
* A policy is set on a resource. Each policy contains a set of roles and role members.
* A policy set at the organization level is inherited by all levels below it.
* A less restrictive policy overrides a more restrictive policy
* An IAM policy has a *"who"* part,a *"can do what"* part, and an *"on which resource"* part.
* The *"who"* part names the user or users you're talking about. The *"who"* part of an IAM policy can be defined either by a Google account, a Google group, a Service account, an entire G Suite, or a Cloud Identity domain.
* The *"can do what"* part is defined by an IAM role. An IAM role is a collection of permissions. Most of the time, to do any meaningful operations, you need more than one permission.
* There are three kinds of primitive roles in GCP - 
    * owner - can do everything an editor can do and also manage roles and permissions on the resources.
    * editor - can do everything a viewer and also change the state.
    * viewer - can only view it but can not change the state.
* IAM has predefined roles which offer a fine grained permission on particular services.
* IAM customs roles allow to precisely define the permissions. These roles can only be used at a project or organization level not at the folder level.
* A service account can be used to give permissions to a VM instance. These use cryptographic keys instead of passwords to access it. IAM predefined or custom roles can be assigned to a service account.
* IAM roles from broadest to finest: primitve roles => predefined roles => custom roles
* An IAM policy implemented higher in the resource can't take away access that is granted by lower-level policies. 
* There are four ways to interact with GCP -
    * Console
    * SDK and cloud shell
    * Mobile app
    * APIs
* Google cloud SDK (Software Development Kit) allows to manage your resources and your applications on GCP
* The services that make up GCP offer application programming interfaces so that the code you write can control them. These APIs are what's called RESTful. In other words they follow the representational state transfer paradigm.
* To get started with GCP with minimal effort, one can use google cloud launcher.
* Use an incognito or a private window to open GDC to avoid signing up with your Google account.
* In terms of security, Google takes care of the lower parts of the stack, and customers are responsible for the higher parts.
* Primitive roles affect all resources in a GCP project. Predefined roles apply to a particular service in a project.
* The VPC or Virtual Private Cloud Network have global scope. They can have subnets in any GCP region worldwide and subnets can span the zones that make up a region. This architecture makes it easy for you to define your own network layout with global scope. 
* In Google Cloud VPCs, subnets have regional scope. VPC subnets can span the zones that make up a region. This is beneficial because your solutions can incorporate fault tolerance without complicating your network topology.
* If you increase the size of a subnet in a custom VPC network, the IP addresses of virtual machines already on that subnet will not be affected. You can dynamically increase the size of a subnet in a custom network by expanding the range of IP addresses allocated to it. Doing that doesn’t affect already configured VMs.
* A preemptible is different from the ordinary VMs. A preemptible is given a termination permission if its resources are needed elsewhere.
* Use shared VPC to share a network or indiviual subnets, with other GCP projects.
* Use VPC peering to interconnect networks in GCP projects.
* VPCs routing tables are built-in hence one need not provision or manage a router. VPCs gives global distributed firewall.
* Cloud Load Balancing
    * Application presents a single front-end to the world making users get a single, global anycast IP address.
    * Backends are selected based on the loads.
* VPC load-balancing options-
    * Global HTTP(S) - Layer 7 load balancing based on load. Can route different URLs to different backends
    * Global SSL proxy - Layer 4 load balancing of non-HTTPS SSL traffic based on load. Supported on specific port numbers.
    * Global TCP proxy - Layer 4 load balancing of non SSL TCP traffic. Supported on specific port numbers.
    * Regional - Load balancing of any traffic(TCP, UDP). Supported on any port number.
    * Regional internal - Load balancing of traffic inside a VPC. Use of internal tiers of multiple tier application.
* GCP offers many interconnect options
    * VPN - Secure multi-gbps connections over tunnels
    * Direct Peering - private connection between you and google for your hybrid cloud workloads.
    * Carrier Peering - Connection through the largest partner network of service providers.
    * Dedicated interconnect - Connect N x 10G transport circuits for private cloud traffic to google cloud at google POP's
* To display a list of all the zones in the region to which Qwiklabs assigned you, enter this partial command gcloud compute zones list | grep followed by the region that Qwiklabs or your instructor assigned you to.
    ```bash
    gcloud compute zones list | grep us-central1
    ```
* To set your default zone to the one you just chose, enter this partial command gcloud config set compute/zone followed by the zone you chose.
    ```bash
    gcloud config set compute/zone us-central1-b
    ```
* To create a VM instance called my-vm-2 in that zone, execute this command:
    ```bash
    gcloud compute instances create "my-vm-2" \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-v20190213" \
    --subnet "default"
    ```
* **Object Storage** - object storage means you save to your storage here, you keep this arbitrary bunch of bytes I give you and the storage lets you address it with a unique key. Often these unique keys are in the form of URLs which means object storage interacts nicely with Web technologies.
* Cloud Storage is not a file system because each of your objects in Cloud Storage has a URL. 
* Cloud storage is immutable binary objects.
* Cloud Storage is comprised of buckets you create and configure and use to hold your storage objects. The storage objects are immutable, which means that you do not edit them in place but instead you create new versions. 
* Roles are inherited from project to bucket to object.
* Cloud Storage lets you choose among four different types of storage classes: Regional,Multi-regional, Nearline, and Coldline.
* Multi-regional and Regional are high-performance object storage, whereas Nearline and Coldline are backup and archival storage.
* Multi-regional storage is appropriate for storing frequently accessed data.
* Coldline storage is a very low cost, highly durable service for data archiving, online backup, and disaster recovery. Coldline storage is the best choice for data that you plan to access -at most - once a year. 
* Cloud Bigtable is a NoSQL, wide-column database service for terabyte applications. Structured objects, with lookups based on a single key
* In NoSQL schema, not all rows might need to have the same columns.
* Cloud BigTable is often called persistent hashtables. Each item in the database can be sparsely populated, and is looked up with a single key.
* Cloud SQL is a managed RDBMS offering mySQL and PostGreSQL as a service.
* Cloud Spanner is a relational database with SQL queries and horizontal scalable RDBMS. Consider using Cloud Spanner if you have outgrown any relational database, or sharding your databases for throughput high performance, need transactional consistency, global data and strong consistency, or just want to consolidate your database. 
* Cloud Datastore is a horizontally scalable NoSQL DB. One of its main use cases is to store structured data from App Engine apps. You can also build solutions that span App Engine and Compute Engine with Cloud Datastore as the integration point. 
* Cloud Datastore actually stores structured objects, with transactions and SQL-like queries.
* Cloud Datastore is the best for semi-structured application data that is used in app engines' applications. 
* Bigtable is best for analytical data with heavy read/write events like AdTech, Financial or IoT data. 
* Cloud Storage is best for structured and unstructured, binary or object data like images, large media files and backups.
* SQL is best for web frameworks and in existing applications like storing user credentials and customer orders.
* Cloud Spanner is best for large scale database applications that are larger than two terabytes; for example, for financial trading and e-commerce use cases. 
* The name of the bucket should be globally unique and for that one can use their project ID as the name.
* In Cloud Shell, the DEVSHELL_PROJECT_ID environment variable contains your project ID.
* Enter this command to make a bucket named after your project ID:
    ```bash
    gsutil mb -l $LOCATION gs://$DEVSHELL_PROJECT_ID
    ```
* IaaS lets you share computer resources with others by virtualizing the hardware.
* In a PaaS like app engine, one gets access to a family of services that application needs. As demand for your application increases, the platform scales your applications seamlessly and independently by workload and infrastructure. This scales rapidly, but you give up control of the underlying server architecture.
* In containers, it give you the independent scalability of workloads like you get in a PaaS environment, and an abstraction layer of the operating system and hardware, like you get in an Infrastructure as a Service environment. Containers start up as an instance of a running program compared to booting up a new instance of an OS.
* Kubernetes orchestrate many containers on many hosts which can roll to new versions or the old versions if something goes wrong.
* Containers start much faster than virtual machines and use fewer resources, because each container does not have its own instance of the operating system.
* Kubernetes is an open-source orchestrator for containers so you can better manage and scale your applications.
* Kubernetes lets you deploy containers on a set of nodes called a cluster. Cluster is a set of master components that control the system as a whole and a set of nodes that run containers.
* Whenever Kubernetes deploys a container or a set of related containers, it does so inside an abstraction called a pod(collection of containers). 
* A pod is the smallest deployable unit in Kubernetes. Think of a pod as if it were a running process on your cluster.
* A deployment represents a group of replicas of the same pod. It keeps your pods running even if a node on which some of them run on fails.
* Kubernetes then creates a service with a fixed IP address for your pods when you connect a load balancer. In GKE, this kind of load balancer is created as a network load balancer.
* A service groups a set of pods together and provides a stable endpoint for them.
* A configuration file can be provided to kubernetes to run a desired state.
* One way to run a container in a pod in Kubernetes is to use the command
    ```bash
    kubectl run
    ```
* To see the running nginx pods, run the command 
    ```bash
    kubectl get pods
    ```
* To make the pods in your deployment publicly available, you can connect a load balancer to it by running the command
    ```bash
    kubectl expose
    ```
* To show you your service's public IP address
    ```bash
    kubectl get services command
    ```
* To view your replicas and see their updated state
    ```bash
    kubectl get replicasets
    ```
* Command to watch the pods come online.
    ```bash
    kubectl get pods
    ```
* To check the deployments
    ```bash
    kubectl get deployments
    ```
* Anthos is a hybrid and multi-cloud systems and service management
* A Kubernetes cluster is a group of machines where Kubernetes can schedule containers in pods. The machines in the cluster are called “nodes.”
* The resources used to build Kubernetes Engine clusters come from Compute Engine, Kubernetes Engine gets to take advantage of Compute Engine’s and Google VPC’s capabilities.
* Google keeps Kubernetes Engine refreshed with successive versions of Kubernetes.
* To create a cluster the following APIs must be enabled -
    * Kubernetes Engine API
    * Container Registry API
* To create a kubernetes cluster
    ```bash
    export MY_ZONE=us-central1-a
    gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2
    ```
* To check the version of kubernetes
    ```bash
    kubectl version
    ```
* Expose the nginx container to the Internet
    ```bash
    kubectl expose deployment nginx --port 80 --type LoadBalancer
    ```
    Kubernetes created a service and an external load balancer with a public IP address attached to it. The IP address remains the same for the life of the service. Any network traffic to that public IP address is routed to pods behind the service: in this case, the nginx pod.
* View a new service
    ```bash
    kubectl get services
    ```
* Scale up the number of pods running on your service
    ```bash
    kubectl scale deployment nginx --replicas 3
    ```
* App engine makes deployment, maintenance and scalability easy so one can focus on innovations.
* App Engine will scale your application automatically in response to the amount of traffic it receives. That’s why App Engine is especially suited for applications where the workload is highly variable, like a web application.
* If one wants to code in another language, Standard Environment is not right. You'll want to consider the Flexible Environment.
* App engine standard environment uses sandbox to run. The limitations to this are-
    * No writing to the local file or the system files.
    * No installation of arbitrary third party softwares
    * All requests time out at 60s
* In app engine flexible environment, docker containers on compute engine VMs are used.
* Application Programming Interface or API is other pieces of software that presents a clean, well-defined interface that abstracts away needless details and then they document that interface.
* Cloud Endpoints help to log and monitor the APIs.
* Apigee Edge is also a platform for developing and managing API proxies. It has a different orientation though. It has a focus on business problems like rate limiting, quotas, and analytics.
* To initialize your App Engine app with your project
    ```bash
    gcloud app create --project=$DEVSHELL_PROJECT_ID
    ```
* To deploy an app engine
    ```bash
    gcloud app deploy
    ```
* To view the application deployed on web browser
    ```bash
    gcloud app browse
    ```
* **Cloud source repositories** - Fully featured git repositories hosted on google cloud platform
* **Cloud functions** - create single-purpose functions that responds to events without a server or runtime.
* **Deployment manager** - It provides repeatable deployments. One can create a .yaml file or python file describing your environment.
* Stackdriver is GCP's tool for monitoring, logging and diagnostics.
* Build a deployment from the template
    ```bash
    gcloud deployment-manager deployments create my-first-depl --config mydeploy.yaml
    ```
* Deployment Manager is an infrastructure management system for GCP resources.
* GCP customer chooses to use Cloud Source Repositories as they don't want to host their own git instance, and they want to integrate with IAM permissions.
* Google big data solutions is a serverless platform where you don't have to worry about provisioning Compute Instances to run your jobs.
* Apache Hadoop is an open source framework for big data. It is based on the MapReduce programming model which Google invented and published.
* Cloud Dataproc is a fast, easy, managed way to run Hadoop, Spark, Hive, and Pig on Google Cloud Platform. All you have to do is request a Hadoop cluster.
* Cloud dataflow is both a unified programming model and a managed service and it lets you develop and execute a big range of data processing patterns: extract, transform, and load batch computation and continuous computation. Data flows are used to build pipelines - the Source, processes it in a variety of ways, the Transforms, and writes its output to a cloud storage, the Sink.
* BigQuery is a fully-managed, petabyte-scale, low-cost analytics data warehouse. 
* Cloud Pub/Sub (Pub for publishers and sub for subscribers) is a scalable, reliable messaging service.
* The Cloud Vision API enables developers to understand the content of an image.
* The Cloud Speech API enables developers to convert audio to text.
* The Cloud Natural Language API analysis text to reveal its structure and meaning.
* Cloud Translation API provides a simple, programmatic interface for translating an arbitrary string into a supported language.
* The Cloud Video Intelligence API lets you annotate videos in a variety of formats. 
* **Tensorflow** - An open source software library that is used for building machine learning applications