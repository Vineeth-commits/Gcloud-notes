#Foundation
---
* Cloud shell provides the following:
    * Temporary Compute Engine VM
    * Command-line access to the instance via a browser
    * 5 GB of persistent disk storage ($HOME dir)
    * Pre-installed Cloud SDK and other tools
    * gcloud: for working with Compute Engine and many Google Cloud services
    * gsutil: for working with Cloud Storage
    * kubectl: for working with Google Kubernetes Engine and Kubernetes
    * bq: for working with BigQuery
    * Language support for Java, Go, Python, Node.js, PHP, and Ruby
    * Web preview functionality
    * Built-in authorization for access to resources and instances
* To create a bucket
    ```bash
    gsutil mb gs://<BUCKET_NAME>
    ```
* Copying a file from the google cloud shell to a bucket
    * Use the navigation menu to select upload
    * Once uploaded in the shell, use the command
        ```bash
        gsutil cp [MY_FILE] gs://[BUCKET_NAME]
        ```
* Store all your environmental variables in a folder infraclass/config and source it.
    ```bash
    INFRACLASS_REGION=us-central1
    echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config
    source infraclass/config
    ```
    The above source command can be copied in the .profile file so it can be loaded when restarted.
* Google Cloud Marketplace lets you quickly deploy functional software packages by providing pre-defined templates with Deployment Manager.
* To change project in the gcloud shell
    ```bash
    gcloud config set project [project_id]
    ```
* A project associates objects and services with billing.The default quota for each project
is five networks but additional networks can be requested.
* In a project, networks have no ip addresses range and can be spanned in different region. Inside a network one can segregate your resources with regional subnetworks.
* There are three different networks - 
    default - Every project is provided with a default VPC network with presets subnets and firewall rules. Specifically a subnet is allocated for each region with non-overlapping sider blocks and firewall rules that allow ingress traffic from ICMP, RDP, and SSH traffic from anywhere, as well as ingress traffic from within the default network for all protocols and ports.
    auto - In an Auto Mode network, one subnets from each region is automatically created within it. The default network is actually an auto mode network. These automatically created subnets uses set of predefined IP ranges with a /20 mask that can be expanded to a /16. All of these subnets fit within the 10.128.0.0/9 cider block.  
    custom - A Custom Mode network does not automatically create subnets. This type of network provides you with complete control over its subnets and IP ranges. You decide which subnets to create in regions you choose and using IP ranges you specify within the RFC 1918 address space. These IP ranges cannot overlap between subnets of the same network.
* Every subnet has four reserved IP addresses in its primary IP range. Now, even though the two Virtual Machines in this example are in different zones, they still communicate with each other using the same subnet IP address. This means that a single firewall rule can be applied to both VM's even though they are in different zones.
* Each VM has two IP addresses - internal and external(optional)
* The external IP address is mapped to the VMs internal address transparently by VPC.
* The default firewall rules have their network rules configured to talk to all instances.
* Firewall rules allow bidirectional communication
* Inbound connections are called ingress and outbound connections are called egress
* Inbound rules are matched against ingress rules only
* Outbound rules are matched against egress rules only
* Egress - Egress firewall rules control outgoing connections originated inside your GCP network. Egress allow rules allow out bound connections that match specific protocol ports and IP addresses. Egress deny rules prevent instances from initiating connections that match non permitted port protocol and IP range combinations. For egress firewall rules, destinations to which a rule applies may be specified using IP CIDR ranges.
* Ingress - Ingress firewall rules protect against incoming connections to the instance from any source. Ingress allow rules allow specific protocol ports and IP ranges to connecting. The firewall prevents instances from receiving connections on non-permitted ports and protocols. 
* Routes tell VM instances and the VPC network how to send traffic from an instance to a destination, either inside the network or outside Google Cloud.
* Firewall rules allow you to control which packets are allowed to travel to which destinations.
* Converting an auto mode network to a custom mode network is an easy task, and it provides you with more flexibility. We recommend that you use custom mode networks in production.
* To create the privatenet network, run the following command
    ```bash
    gcloud compute networks create privatenet --subnet-mode=custom
    ```
* To create the privatesubnet-us subnet, run the following command
    ```bash
    gcloud compute networks subnets create privatesubnet-us --network=privatenet --region=us-central1 --range=172.16.0.0/24
    ```
* To create the privatesubnet-eu subnet, run the following command
    ```bash
    gcloud compute networks subnets create privatesubnet-eu --network=privatenet --region=europe-west1 --range=172.20.0.0/20
    ```
* To list the available VPC networks, run the following command
    ```bash
    gcloud compute networks list
    ```
* To list the available VPC subnets (sorted by VPC network), run the following command
    ```bash
    gcloud compute networks subnets list --sort-by=NETWORK
    ```
* Cloud NAT is Google's managed network address translation service. It lets you provision your application instances without public IP addresses, while also allowing them to access the internet in a controlled and efficient manner.
* To connect to a VM through SSH
    ```bash
    gcloud compute ssh [vm-name] --zone us-central1-c --tunnel-through-iap
    ```
* VM instances without external IP addresses are isolated from external networks. Using Cloud NAT, these instances can access the internet for updates and patches, and in some cases, for bootstrapping.
* When a VM is created the ephemeral external IP address is assigned from a pool. There is no way to predict which address will be assigned, so there is no way to write a rule that will match that VM's IP address before it is assigned. Tags allow a symbolic assignment that does not depend on order in the IP addresses. It makes for simpler, more general, and easier to maintain, firewall rules.
* Machine type, CPU platform or zone cant be changed once the VM is created.
* You can't convert a non-preemptible instance into a preemptible one. This choice must be made at VM creation. A preemptible instance can be interrupted at any time and is available at a lower cost.
* A sole-tenant node is a physical Compute Engine server that is dedicated to hosting VM instances only for your specific project. Use sole-tenant nodes to keep your instances physically separated from instances in other projects, or to group your instances together in the same host hardware. 
* Shielded VMs offer verifiable integrity of your VM instances. So you can be confident that you're instances haven't been compromised by boot or kernel level of malware or rootkits. Shielded VMs verifiable integrity is achieved through the use of secure boot, Virtual Trusted Platform Module or VTPM enabled measured boot and integrity monitoring. 
* A persistent disk is going to be attached to the VM through a network interface.
* Persistent disk can be dynamically resized even when they are running and attached to the VM.
* Snapshots are available to persistent disks only.
* VMs in Compute Engine are a collection of networked services which includes persistent disks disks that are network-attached. In some cases the GCP VM behaves unlike hardware or other kinds of virtual machines, for example, when a multi-tenant virtual CPU *bursts*, using excess capacity beyond the VM spec.
* Persistent Disks are not physical disks, they are a virtual-networked service. Each persistent disk remains encrypted either with system-defined keys or with customer-supplied keys.