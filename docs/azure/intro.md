## Cloud Computing Advantages
- Scalability (scale up/down, scale in/out)
- High Availability
- Elasticity (auto scaling based on conditions)
- Agility
- Geo-distribution
- Disaster Recovery

## Cloud Service Models
- IaaS (Networking, Storage, Servers, Virtualization)
- PaaS (OS, Middleware, Runtime)
- SaaS (Data Storage, Applications)

## Deployment Models
- Public
- Private
- Hybrid

## Azure Services
### Compute
- VM
- VM Scale Sets (To deploy  manage a set of identical VMs)
- Azure Kubernetes Services
- Azure Container Instances
- Azure Service Fabric
- Azure Batch (Enables large-scale parallel  high-performance computing (HPC) batch jobs  the ability  scale  tens/hundreds/thousands of VMs)
- Azure Functions (Server )
  - Durable Functions ( Execute stateful workflows)
  - Azure Logic Apps ( Execute stateless workflows)
- Windows Virtual Desktop (full desktop for users)

### Network
- Azure Virtual Network (Enables communicate  azure resources,  users on the internet,   your on-premises client computers)
- Azure Load Balancer (Balances the load b/w VMs -  on resource availability)
- Azure Application Gateway (load balances, SSL termination, Auto scaling, Session Affinity, Web Application Firewall - WAF)
- Azure VPN Gateway (Connecting on-premises to azure datacenter through internet Ex: Site-to-site VPN, Point-to-site VPN)
- Azure DNS
- Azure CDN (distributed network servers, cached data, point-of- [several servers compared  datacenters, also partnership  akamai, verizon], Dynamic Site Acceleration - for dynamic content )
- Azure DDoS Protection
- Azure Traffic Manager
- Azure Express Route (Private ethernet connection b/w on-premises  -located Microsoft cloud datacenter)
- Azure Network Watcher
- Azure Firewall
- Azure Virtual WAN
- Network Security Group (Control inbound/outbound communication  VMs)

### Storage
- Disk storage (For Virtual Machines) (page blob)
- Azure Blob Storage (Object Storage - massive amounts of data) (unstructured) (Block blob, Append Blob, Page Blob)
- Azure File Storage (File Share) (unstructured) (supports SMB protocol - makes it to be attached to VMs as a network drive)
- Azure Queue Storage
- Azure Table Storage (Semi Structured Data storage)
- Axure Data Box / Azure Data Box Heavy
- Azure archive storage (subset of blob storage)

### Database
- Azure Cosmos DB (globally distributed, multi-model database service) (semi-structured) (Document DB - SQL API, Mongo DB | Key-Value DB - Azure Table Storage| Graph DB - Gremlin | Column Family DB - Cassandra)
- Azure SQL Database (PaaS -  It handles most of the database management functions, such as upgrading, patching, backups, and monitoring, without user involvement) (structured)
- SQL Server on Virtual Machines / Azure SQL Managed Instance (PaaS -  as on premises, east  migrate) (structured)
- Azure Database for MySQL (semi-structured)
- Azure Database for PostgreSQL (semi-structured)
- Azure Database for MariaDB
- Azure Synapse Analytics
- Azure Database Migration Service
- Azure Cache for Redis

### Web
- Azure App Service (Enables you  build  host web apps, background jobs, mobile back-ends,  RESTful APIs)
- Azure Notification Hubs
- Azure API Management
- Azure Cognitive Search
- Web Apps Feature for Azure App Service
- Azure SignalR Service

### IOT
- IoT Central (customized IOT solution with IoT hub, event hub/ service bus, storage, portal etc..)
- Azure IoT Hub (2way communication b/w cloud and device - d2c/c2d)
  - Azure event grid (designed to process events not data - can have logics)
- IoT Edge (deployment of models in IOT devices) (run logic on device) (can still send data)

### Big Data
- Azure Synapse Analytics
- Azure HD Insight
- Azure Databricks

### AI (Azure Machine Learning Service/ Studio)
- Azure Machine Learning
- Azure Cognitive Services
- Azure Bot Service

### DevOps
- Azure DevOps (Kanban, Pipeline, Repos, Test Plan, Artifacts, DevTest Labs)
- Azure DevTest Labs

## Monitoring
- Azure Advisor (Evaluates your Azure resources  makes recommendations  help improve reliability, security,  performance, achieve operational excellence,  reduce cost)
- Azure Monitor (A platform for collecting, analyzing, visualizing,  potentially taking action  on the metric  logging data from your entire Azure  on-premises environment)
- Azure Service Health ( view of the health of the Azure services, regions,  resources you rely on.  ex: status.azure.com)

## Features
### Security
- Azure Security  (A monitoring service that provides visibility of your security posture across all of your services, both on Azure  on-premises. The term security posture refers  cybersecurity policies  controls, as well as how well you can predict, prevent,  respond  security threats)
- Azure Sentinel
- Azure Key Vault
### Network Security
- Azure Firewall (protects access to virtual networks)
- Azure DDoS Protection
- User Defined Routes (allow us to override azure's default system routes) (inspect traffic using virtual appliance)
- Network Security Group (inbound/outbound - can be attached to subnets and network cards) (can be linked to multiple resources as long as the region matches)
  - Application Security Group (used in NSGs) 
### Secure Access
- Azure AD
- Multifactor / Conditional Access
### Governance
- Cloud Governance Strategy
- Azure Role  Access Control (RBAC) (general - administrator, contributor, reader)
- Resource Locks
- Azure Policy (a rule that can be applied to a resource/group/subscription)
- Azure Initiative (Group of policies that can be applied as above)
- Azure  Blueprints (blueprint to create ARM templates, Role based access controls and policies) (versioned and applied on the deployed resources)
- Microsoft Privacy Statement, the Online Services Terms,  the Data Protection Addendum, Azure Trust 
### Costing
- Azure TCO Calculator (Total Cost of Ownership) (for migration cost analysis)
- Azure Pricing Calculator (for each individual resource)
### SLA
- Individual Resource SLA, Composite SLA
### Application Integration Services
- Azure notification hub
- Azure event hub (1way communication, takes in data)
- Azure Logic Apps
- Azure Service Bus
- Azure API Apps
- Azure API Management
- Azure Queue Storage
### Rest
- Azure SignalR service
- Azure Resource Manager (Infrastructure as Code - IAC)
