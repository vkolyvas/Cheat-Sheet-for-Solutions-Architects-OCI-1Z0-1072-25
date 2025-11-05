# Cheat-Sheet-for-Solutions-Architects-OCI-1Z0-1072-25
________________________________________
This Repository has enough information for you passing the OCI Solution Architect 1z0-1072-25 exam at ease. <br />
Key Topics of 1Z0-1072-25.<br />
Things you MUST study before going to the exam like a Last-Minute Study Sheet.<br />
Quick Exam OCI-1Z0-1072-25 Recall<br />
Exam OCI-1Z0-1072-25 Strategy Tip <br />
________________________________________

Key Topics of 1Z0-1072-25<br />
•	IAM & Policies: Use compartments, groups, policies. Policies grant access (no explicit deny). Principle of least privilege. Resources belong to one compartment; policies need to reference correct compartment. Resource movement affects effective policies.<br />
•	Networking: VCN, subnets, route tables, security lists, NSGs. Gateways (Internet, NAT, Service, Local/Remote Peering). Steering policies (Geolocation, ASN, IP‐prefix, Proximity) for DNS traffic. DRG, peering, connectivity (VPN, FastConnect). Network Visualiser/NPA tools for topology/analysis.<br />
•	Compute: VM shapes, bare metal, dedicated hosts, capacity types (on-demand, preemptible, dedicated). Instance configurations, instance pools. Shielded instances for firmware/boot security.<br />
•	Storage: Block volumes (performance tiers, backups, clone/expand/restore), Object Storage (tiers: Standard, Infrequent, Archive; retention rules; pre-authenticated requests), File Storage (mount targets, exports, snapshots, metered bytes), and service gateways for secure access between compute and services.<br />
•	Other Key Topics: Databases (managed DB, Autonomous DB), Architecting best practices (regions, ADs, FDs, compartments, isolation), Terminology (region, availability domain, compartment, tenancy), Security (Vault, encryption at rest/in-use, Confidential Computing), Tools & Automation (Terraform, Resource Manager, OS Management Hub for patching).<br />
________________________________________

Cheat Sheet for Solutions Architects – OCI 1Z0-1072-25<br />
IAM / Access<br />
•	Tenancy = root compartment; compartments can be nested up to 6 levels. <br />
•	Policy syntax: Allow <subject> to <verb> <resource-type> in <location> [where <conditions>].<br />
•	Verbs: inspect, read, use, manage.<br />
•	Principle of least privilege → grant only required permissions.<br />
•	Resources have exactly one compartment at a time; moving a resource to new compartment means new compartment’s policies apply immediately.<br />
•	Administrator roles (for identity domains) can simplify user access by reducing custom policy count.<br />
•	Tag‐based access control: use where target.resource.compartment.tag.<key> = '<value>'.<br />

Networking<br />
•	VCN: your private network in OCI. Subnets live in VCNs.<br />
•	Gateways:<br />
  Internet Gateway for internet traffic.<br />
  NAT Gateway for outbound internet from private subnets.<br />
  Service Gateway for private access to OCI public services without internet.<br />
•	Peering and DRG: VCNs in same/different regions can connect via local or remote peering using DRG.<br />
•	Traffic Management Steering policies: Geolocation Steering = route based on user’s geographic location.<br />
•	Security Lists apply at subnet level; NSGs apply at VNIC level.<br />
•	Use Network Visualiser for topology view; use Network Path Analyzer for connectivity issues.<br />

Compute<br />
•	Choose shape based on workload (standard, denseIO, GPU, flexible).<br />
•	Capacity types: on‐demand, preemptible (interruptible), dedicated host (single-tenant, for node licensing).<br />
•	Instance pools + instance configurations: reuse template to scale.<br />
•	Shielded instances provide enhanced firmware/boot security.<br />
•	Use OS Management Hub for patching and update management across instances.<br />

Storage<br />
•	Block Volume: persistent block storage, can expand, backup, clone. Cannot attach across availability domains.<br />
•	Object Storage:<br />
  Tiers: Standard (frequent access), Infrequent Access (less frequent), Archive (lowest cost, retrieval delay).<br />
  Retention rules prevent deletion/modification until duration expires.<br />
  Pre-authenticated requests allow sharing objects securely.<br />
•	File Storage: NFS‐style file system, mount targets. MeteredBytes = data + snapshots + overhead.<br />
•	Use service gateways to allow compute in private subnet to access Object Storage without internet exposure.<br />

Architecting Best Practices<br />
•	Multi-region or multi-AD deployment for high availability & fault tolerance.<br />
•	Use compartments to isolate projects, teams, environments (Dev, Test, Prod).<br />
•	Set quotas and tag defaults at compartments for governance.<br />
•	Secure by design: least privilege, encryption in transit and at rest, use vaults for keys.<br />
•	Automate with Terraform/Resource Manager; enable monitoring/alerts; consider cost optimization (e.g., smaller shapes, preemptible, proper tiering).<br />
•	For connectivity: use redundant circuits, diverse on-prem terminations, backup VPN/FC.<br />

Terminology Quick Reference<br />
•	Region: geographic area (e.g., us-ashburn-1)<br />
•	Availability Domain (AD): isolated data-center within region<br />
•	Fault Domain (FD): group of hardware within AD (for anti-affinity)<br />
•	Compartment: logical container for resources and policies<br />
•	Tenancy: your entire OCI account (root compartment)<br />
•	OCID: unique identifier for each resource<br />
•	Dynamic group: group of instances (compute) that can act as principals<br />

Things you MUST study before going to the exam like a Last-Minute Study Sheet<br />

🧩 Identity & Access Management (IAM)<br />
Compartment Access Control: Policies at the root don’t automatically grant access to nested compartments.<br />
Admin Roles: Simplify access control by reducing complex IAM policy creation.<br />
Resource Movement Impact: Moving a resource to another compartment removes prior access unless new policies cover it.<br />
Least Privilege Principle: Always grant only the minimum permissions necessary.<br />
NetworkAdmins Policy: Use full compartment path (A:B:C) when defining tenancy-level policies.<br />
Invalid Policy Syntax: You can’t assign tenancy-wide visibility to “any-user.”<br />
Tag-Based Access Control: IAM condition tags let you dynamically grant access based on group attributes.<br />
Instance Principals: No need for tokens; instances authenticate via dynamic groups and IAM policies.<br />
Auth Tokens: Use auth tokens when third-party APIs can’t use OCI’s signature method.<br />
Policy Optimization: Eliminate redundant child-compartment policies; inherit from parent.<br />
________________________________________
🌐 Networking<br />
DNS Steering: Geolocation steering routes users based on location.<br />
Site-to-Site VPN: Provides redundant tunnels and supports BGP or static routing.<br />
Invalid Block Volume Action: Block volumes can’t attach across availability domains.<br />
Service Gateway: Enables secure, private access to Object Storage without public internet.<br />
Network Path Analyzer: Detects misconfigurations causing connectivity issues.<br />
Remote Peering Setup: Requires DRG + RPC per VCN with non-overlapping CIDRs.<br />
Hybrid Redundancy: Use FastConnect with VPN or dual FastConnect for resilience.<br />
Private CIDRs: Use only RFC-1918 ranges (10.x, 172.16-31.x, 192.168.x).<br />
Private IPs: One primary private IP per VNIC; can attach a public IP in public subnets.<br />
SSH Connectivity Issues: Check NSG or security list ingress for port 22.<br />
Network Visualizer: Displays VCN topology across tenancy for easy management.<br />
Outbound Data Costs: OCI egress pricing is far lower than competitors.<br />
Capture Filters: Use flow log and packet capture filters for monitoring.<br />
________________________________________
💻 Compute<br />
Dedicated Hosts: Use for isolated hardware and node-based licensing compliance.<br />
Shielded Instances: Protect from firmware and rootkit attacks with secure boot.<br />
Instance Configurations: Delete only if not part of a pool; reusable across pools.<br />
Performance Autotune: Detached block volumes auto-adjust to lowest cost tier.<br />
Burstable Instances: Cheaper compute for low-usage workloads with burst credits.<br />
Preemptible Instances: Ideal for short-term, cost-sensitive workloads.<br />
Maintenance Events: OCI automatically reboots instances if not manually migrated.<br />
________________________________________
🗄️ Storage<br />
Backup Tier: Infrequent Access tier minimizes cost with instant retrieval.<br />
File System Replication: Replicate within or across OCI regions for resilience.<br />
File System Snapshot: Only counts changed data once in metered size.<br />
Retention Rules: Duration applies from last modification date of each object.<br />
Restore from Backup: Can restore to a larger block volume size.<br />
File Overwrite Metering: Overwriting data increases total metered storage.<br />
File Storage Encryption: Oracle keys by default; customer Vault keys optional.<br />
Pre-Authenticated Requests: Can’t edit PARs; delete to revoke access.<br />
Replica Activation: Must promote replica before using as a new volume.<br />
Multipart Uploads: Upload in 50 GiB parts, up to 10,000 parts total.<br />
Object Replication: Cross-region replication ensures durability.<br />
File Access Blocked: Fix by updating VCN or NSG rules blocking mount target.<br />
Block Volume Attachment: Volumes stay within their availability domain.<br />
Snapshot Storage: Snapshots only count changed data once.<br />
________________________________________
🔐 Security, Governance & Monitoring<br />
OS Patching: Use OS Management Hub to centrally patch Linux kernels.<br />
Confidential Computing: Encrypts and isolates in-use data to prevent host access.<br />
Least Privilege IAM: Limit access scope strictly to what’s required.<br />
Web Application Acceleration: Uses caching and compression to speed Layer-7 traffic.<br />
DNS Service: Manage zones and records, not IAM or WAF rules.<br />
Inter-Region Latency Dashboard: View latency trends for up to 30 days.<br />
Network Visualizer: Visualizes connections between all VCNs for clarity.<br />
Network Capture Filters: Combine flow logs and packet captures for deep analysis.<br />
Outbound Data Costs: OCI egress fees are very low compared to competitors.<br />
Private IP Behavior: One private IP per VNIC; can assign a public IP in public subnet.<br />
________________________________________
✅ Quick Exam Recall<br />
IAM: Policies are compartment-based; use dynamic groups + tags.<br />
Networking: Remember gateway types (IGW, SGW, NAT, DRG, LPG).<br />
Compute: Match instance type (burstable, preemptible, dedicated) to workload.<br />
Storage: Tier smartly (Standard, IA, Archive) and know replication rules.<br />
Security: Encryption, least privilege, and redundancy are always the right answers.<br />
________________________________________
✅ Exam Strategy Tip<br />
Focus on how OCI enforces compartmentalization, encryption, and automation — nearly every correct answer aligns with security, cost-efficiency, or fault tolerance.



