#Scaling and Automation
---
* Cloud VPN securely connects your on-premise network to your GCP VPN network.
* Dedicated Interconnect provides direct physical connections between your On-premise network and Google's network. This enables you to transfer a large amount of data between networks which can't be more cost-effective than purchasing additional bandwidth over the public Internet.
* Partner Interconnect provides connectivity between your on-premise network andyour VPC network through a supported service provider. This is useful if your data center is in the physical location that cannot reach a Dedicated Interconnect co-location facility or if your data needs don't warrant a Dedicated Interconnect.
* Interconnect services provide direct access to RFC1918 IP addresses in your VPC with an SLA. Peering services like Dedicated interconnect, partner interconnect and Cloud VPN.
* Peering services offer access to Google public IP addresses only without an SLA like Direct Peering and Carrier Peering.
* Shared VPC allows an organization to connect resources from multiple projects to a common VPC network. This allows the resources to communicate with each other securely, and efficiently using internal IPs from that network.
* VPC Network Peering in contrast, allows private RFC 1918 connectivity across two VPC networks, regardless of whether they belong to the same project, or the same organization. Now, remember that each VPC network will have firewall rules that define what traffic is allowed or denied between the networks.
* VPNs use IPSec tunnels to provide an encapsulated and encrypted path through a hostile or untrusted environment.
* Dedicated Interconnect requires a connection in a GCP colocation facility and provides 10 Gbps per link.
* Shared VPC is a centralized approach to multi-project networking, because security and network policy occurs in a single designated VPC network.
* One uses a global load balancer when your users and instances are globally distributed. 
* The regional load balancers are the internal and network load balancers and they distribute traffic to instances that are in a single GCP region.
* A managed instance group is a collection of identical virtual machine instances that you control as a single entity using an instance template.
* HTTP requests are load balanced on port 80 or 8080, and HTTPS requests are load balanced on port 443.
* An HTTP(s) load balancer uses a target HTTPS proxy instead of a target HTTP proxy. 
* An HTTPS load balancer requires at least one signed SSL certificate installed on the target HTTPS proxy for the load balancer.
* QUIC is a transport layer protocol that allows faster client connection initiation, eliminates head of line blocking in multiplexed streams, and supports connection migration when a client's IP address changes.
* The HTTP load balancer should forward traffic to the region that is closest to you.
* SSL proxy is a global load balancing service for encrypted, non-HTTP traffic.
* TCP proxy is a global load balancing service for unencrypted non-HTTP traffic.
* Network load balancing is a regional non proxied load balancing service. In other words, all traffic is passed through the load balancer instead of being proxied and traffic can only be balanced between virtual machine instances that are in the same region unlike a global load balancer. 
* A target pool resource defines a group of instances that receive incoming traffic from forwarding rules. 
* Internal load balancing is a regional, private load balancing service for TCP and UDP based traffic. In other words, this load balancer enables you to run and scale your services behind a private load balancing IP address.
* The foundational process at the base of Google's Site Reliability Engineering (SRE) is monitoring
* Stackdriver Trace provides latency sampling and reporting for Google App Engine, Google HTTP(S) load balancers, and applications instrumented with the Stackdriver Trace SDKs. Reporting includes per-URL statistics and latency distributions.
* Stackdriver integration streamlines and unifies these traditionally independent services, making it much easier to establish procedures around them and to use them in continuous ways.