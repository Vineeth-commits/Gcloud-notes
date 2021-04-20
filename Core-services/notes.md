#Core Services
---
* In the gcloud IAM hierarchy, organization node is the root node. Projects are children of folders and the resources are the children of the project.
* Organization roles:
    * **Organization admin**: Control over all cloud resources; useful for auditing
    * **Project creator**: Controls project creation; control over who can create projects
* There are three types of IAM roles:
    * **Basic** - These are broad and they affect all resources in the projects. It has owner, editor and viewer roles.
    * **Pre-defined roles** - These roles apply to a particular GCP service in a project.
    Compute engine IAM roles-
        1. **Compute admin** - Full control of all compute engine resources.
        2. **Network admin** - Permissions to create, modify and delete networking resources, except for firewall rules and SSL certificates.
        3. **Storage admin** - Permissions to create, modify and delete disks, images and snapshots
    * **Custom roles** - These give a finer grain of choice where permissions can be set precising
* There are five different members -
    * Google account
    * Service account
    * Google group
    * G suite
    * Cloud identity domain
* A service account is an account that belongs to your application instead of to an individual end-user. This provides an identity for carrying out server-to-server interactions in a project without supplying user credentials.
* Access scopes are actually the legacy method of specifying permissions for your VM. 
* Use the principle of least privilege when granting roles. 
* Storage and database services
    * Object - cloud Storage
    * Relational - Cloud SQL and Spanner
    * Non-relational - Cloud Firestore and Bigtable
    * Warehouse - BigQuery
* Cloud Storage is a object storage service used to store website content, storing data for archiving and disaster management, distributing large data objects to users via direct download.
* Cloud storage is not a file system but instead a collection of buckets that place objects into.
* Cloud storage has four storage classes-
    * Standard 
    * Nearline 
    * Coldline
    * Archive
* The data stored in the buckets are objects
* An ACL(Access Control Lists) is a mechanisms used to define who has access to your buckets and objects, as well as what the level of access to have. The maximum number of ACL entries you can create for a bucket or object is 100. 
* Object life cycle management policies specify actions to be performed on objects that meet certain rules.
* Transfer appliance: Rack, capture and then ship your data to google cloud.
* Storage transfer service: import online data
* Offline media import: Third party provider uploads the data from physical media
* Cloud SQL is a fully managed database service
* Cloud spanner combines the benefits of relational database structure with non-relational horizontal scale
* Cloud firestore is a no SQL document database
* Cloud Spanner provides ACID (Atomicity, Consistency, Isolation, Durability) properties that enable transactional reads and writes on the database. It can also scale globally.
* BigQuery is a data warehousing service that allows the storage of huge data sets while making them immediately processable without having to extract or run the processing in a separate service.
* Resource manager lets you hierarchically manage resources.
* Child policies cant restrict access granted at the parent level
* Resources are organized into global, regional and zonal - Images, snapshots, and networks, are global resources, external IP addresses are regional resources, and instances and disks are zonal resources.
* Labels are utilty for organizing GCP resources
* Quotas are established at reasonable defaults for common cloud usage and proof of concept activities. If you are planning to scale up a production cloud solution you may need to request that the quotas be raised. This is a reasonable checkpoint to verify that actions that might result in a large consumption of resources are reviewed.
* Stackdriver is Google Cloud's operations suite
* Workspace is the root entity that holds monitoring and configuration information
* Monitoring is at the base of site reliability which incorporates aspects of software engineering and applies that to operations whose goals are to create ultra-scalable and highly reliable software systems.
* The foundational process at the base of Google's Site Reliability Engineering (SRE) is monitoring
* Stackdriver Trace provides latency sampling and reporting for Google App Engine, Google HTTP(S) load balancers, and applications instrumented with the Stackdriver Trace SDKs. Reporting includes per-URL statistics and latency distributions.
* Stackdriver integration streamlines and unifies these traditionally independent services, making it much easier to establish procedures around them and to use them in continuous ways.