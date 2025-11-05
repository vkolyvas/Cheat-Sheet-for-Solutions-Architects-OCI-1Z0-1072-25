# Cheat-Sheet-for-Solutions-Architects-OCI-1Z0-1072-25
This Repository has enough information for you passing the OCI Solution Architect 1z0-1072-25 exam at ease. <br />
Key Topics of 1Z0-1072-25.<br />
Things you MUST study before going to the exam like a Last-Minute Study Sheet.<br />
Quick Exam OCI-1Z0-1072-25 Recall<br />
Exam OCI-1Z0-1072-25 Strategy Tip <br />

Key Topics of 1Z0-1072-25<br />
•	IAM & Policies: Use compartments, groups, policies. Policies grant access (no explicit deny). Principle of least privilege. Resources belong to one compartment; policies need to reference correct compartment. Resource movement affects effective policies.
•	Networking: VCN, subnets, route tables, security lists, NSGs. Gateways (Internet, NAT, Service, Local/Remote Peering). Steering policies (Geolocation, ASN, IP‐prefix, Proximity) for DNS traffic. DRG, peering, connectivity (VPN, FastConnect). Network Visualiser/NPA tools for topology/analysis.
•	Compute: VM shapes, bare metal, dedicated hosts, capacity types (on-demand, preemptible, dedicated). Instance configurations, instance pools. Shielded instances for firmware/boot security.
•	Storage: Block volumes (performance tiers, backups, clone/expand/restore), Object Storage (tiers: Standard, Infrequent, Archive; retention rules; pre-authenticated requests), File Storage (mount targets, exports, snapshots, metered bytes), and service gateways for secure access between compute and services.
•	Other Key Topics: Databases (managed DB, Autonomous DB), Architecting best practices (regions, ADs, FDs, compartments, isolation), Terminology (region, availability domain, compartment, tenancy), Security (Vault, encryption at rest/in-use, Confidential Computing), Tools & Automation (Terraform, Resource Manager, OS Management Hub for patching).
________________________________________

Cheat Sheet for Solutions Architects – OCI 1Z0-1072-25
IAM / Access
•	Tenancy = root compartment; compartments can be nested up to 6 levels. 
•	Policy syntax: Allow <subject> to <verb> <resource-type> in <location> [where <conditions>].
•	Verbs: inspect, read, use, manage.
•	Principle of least privilege → grant only required permissions.
•	Resources have exactly one compartment at a time; moving a resource to new compartment means new compartment’s policies apply immediately.
•	Administrator roles (for identity domains) can simplify user access by reducing custom policy count.
•	Tag‐based access control: use where target.resource.compartment.tag.<key> = '<value>'.
Networking
•	VCN: your private network in OCI. Subnets live in VCNs.
•	Gateways:
  Internet Gateway for internet traffic.
  NAT Gateway for outbound internet from private subnets.
  Service Gateway for private access to OCI public services without internet.
•	Peering and DRG: VCNs in same/different regions can connect via local or remote peering using DRG.
•	Traffic Management Steering policies: Geolocation Steering = route based on user’s geographic location.
•	Security Lists apply at subnet level; NSGs apply at VNIC level.
•	Use Network Visualiser for topology view; use Network Path Analyzer for connectivity issues.
Compute
•	Choose shape based on workload (standard, denseIO, GPU, flexible).
•	Capacity types: on‐demand, preemptible (interruptible), dedicated host (single-tenant, for node licensing).
•	Instance pools + instance configurations: reuse template to scale.
•	Shielded instances provide enhanced firmware/boot security.
•	Use OS Management Hub for patching and update management across instances.
Storage
•	Block Volume: persistent block storage, can expand, backup, clone. Cannot attach across availability domains.
•	Object Storage:
  Tiers: Standard (frequent access), Infrequent Access (less frequent), Archive (lowest cost, retrieval delay).
  Retention rules prevent deletion/modification until duration expires.
  Pre-authenticated requests allow sharing objects securely.
•	File Storage: NFS‐style file system, mount targets. MeteredBytes = data + snapshots + overhead.
•	Use service gateways to allow compute in private subnet to access Object Storage without internet exposure.
Architecting Best Practices
•	Multi-region or multi-AD deployment for high availability & fault tolerance.
•	Use compartments to isolate projects, teams, environments (Dev, Test, Prod).
•	Set quotas and tag defaults at compartments for governance.
•	Secure by design: least privilege, encryption in transit and at rest, use vaults for keys.
•	Automate with Terraform/Resource Manager; enable monitoring/alerts; consider cost optimization (e.g., smaller shapes, preemptible, proper tiering).
•	For connectivity: use redundant circuits, diverse on-prem terminations, backup VPN/FC.
Terminology Quick Reference
•	Region: geographic area (e.g., us-ashburn-1)
•	Availability Domain (AD): isolated data-center within region
•	Fault Domain (FD): group of hardware within AD (for anti-affinity)
•	Compartment: logical container for resources and policies
•	Tenancy: your entire OCI account (root compartment)
•	OCID: unique identifier for each resource
•	Dynamic group: group of instances (compute) that can act as principals

Things you MUST study before going to the exam like a Last-Minute Study Sheet

🧩 Identity & Access Management (IAM)
Compartment Access Control: Policies at the root don’t automatically grant access to nested compartments.
Admin Roles: Simplify access control by reducing complex IAM policy creation.
Resource Movement Impact: Moving a resource to another compartment removes prior access unless new policies cover it.
Least Privilege Principle: Always grant only the minimum permissions necessary.
NetworkAdmins Policy: Use full compartment path (A:B:C) when defining tenancy-level policies.
Invalid Policy Syntax: You can’t assign tenancy-wide visibility to “any-user.”
Tag-Based Access Control: IAM condition tags let you dynamically grant access based on group attributes.
Instance Principals: No need for tokens; instances authenticate via dynamic groups and IAM policies.
Auth Tokens: Use auth tokens when third-party APIs can’t use OCI’s signature method.
Policy Optimization: Eliminate redundant child-compartment policies; inherit from parent.
________________________________________
🌐 Networking
DNS Steering: Geolocation steering routes users based on location.
Site-to-Site VPN: Provides redundant tunnels and supports BGP or static routing.
Invalid Block Volume Action: Block volumes can’t attach across availability domains.
Service Gateway: Enables secure, private access to Object Storage without public internet.
Network Path Analyzer: Detects misconfigurations causing connectivity issues.
Remote Peering Setup: Requires DRG + RPC per VCN with non-overlapping CIDRs.
Hybrid Redundancy: Use FastConnect with VPN or dual FastConnect for resilience.
Private CIDRs: Use only RFC-1918 ranges (10.x, 172.16-31.x, 192.168.x).
Private IPs: One primary private IP per VNIC; can attach a public IP in public subnets.
SSH Connectivity Issues: Check NSG or security list ingress for port 22.
Network Visualizer: Displays VCN topology across tenancy for easy management.
Outbound Data Costs: OCI egress pricing is far lower than competitors.
Capture Filters: Use flow log and packet capture filters for monitoring.
________________________________________
💻 Compute
Dedicated Hosts: Use for isolated hardware and node-based licensing compliance.
Shielded Instances: Protect from firmware and rootkit attacks with secure boot.
Instance Configurations: Delete only if not part of a pool; reusable across pools.
Performance Autotune: Detached block volumes auto-adjust to lowest cost tier.
Burstable Instances: Cheaper compute for low-usage workloads with burst credits.
Preemptible Instances: Ideal for short-term, cost-sensitive workloads.
Maintenance Events: OCI automatically reboots instances if not manually migrated.
________________________________________
🗄️ Storage
Backup Tier: Infrequent Access tier minimizes cost with instant retrieval.
File System Replication: Replicate within or across OCI regions for resilience.
File System Snapshot: Only counts changed data once in metered size.
Retention Rules: Duration applies from last modification date of each object.
Restore from Backup: Can restore to a larger block volume size.
File Overwrite Metering: Overwriting data increases total metered storage.
File Storage Encryption: Oracle keys by default; customer Vault keys optional.
Pre-Authenticated Requests: Can’t edit PARs; delete to revoke access.
Replica Activation: Must promote replica before using as a new volume.
Multipart Uploads: Upload in 50 GiB parts, up to 10,000 parts total.
Object Replication: Cross-region replication ensures durability.
File Access Blocked: Fix by updating VCN or NSG rules blocking mount target.
Block Volume Attachment: Volumes stay within their availability domain.
Snapshot Storage: Snapshots only count changed data once.
________________________________________
🔐 Security, Governance & Monitoring
OS Patching: Use OS Management Hub to centrally patch Linux kernels.
Confidential Computing: Encrypts and isolates in-use data to prevent host access.
Least Privilege IAM: Limit access scope strictly to what’s required.
Web Application Acceleration: Uses caching and compression to speed Layer-7 traffic.
DNS Service: Manage zones and records, not IAM or WAF rules.
Inter-Region Latency Dashboard: View latency trends for up to 30 days.
Network Visualizer: Visualizes connections between all VCNs for clarity.
Network Capture Filters: Combine flow logs and packet captures for deep analysis.
Outbound Data Costs: OCI egress fees are very low compared to competitors.
Private IP Behavior: One private IP per VNIC; can assign a public IP in public subnet.
________________________________________
✅ Quick Exam Recall
IAM: Policies are compartment-based; use dynamic groups + tags.
Networking: Remember gateway types (IGW, SGW, NAT, DRG, LPG).
Compute: Match instance type (burstable, preemptible, dedicated) to workload.
Storage: Tier smartly (Standard, IA, Archive) and know replication rules.
Security: Encryption, least privilege, and redundancy are always the right answers.
________________________________________
✅ Exam Strategy Tip
Focus on how OCI enforces compartmentalization, encryption, and automation — nearly every correct answer aligns with security, cost-efficiency, or fault tolerance.



