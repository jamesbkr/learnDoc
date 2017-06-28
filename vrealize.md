# VRealize
### Core Components:
The below outlines the core components of a vRealize framework.  For an enterprise deployment, use loadbalancers and cluster all servers to provide redundancy.
##### **vRealize Automation Appliance**: 
An OVF that contains the vRealize Automation Server.  This OVF is deployed in an existing virtualized infrastructure.
 * **Core Services**: 
This service is a single portal for management of the environment (cloud services, authoring, administration, and governance).
* **Identity Manager**: 
integrates with LDAP or AD and manages SSO capabilities.  Logins and authentication are performed against a local copy of AD or LDAP.  This allows for quick authentication.  It also manages tenant isolation.
* **vRealize Orchestrator**: 
Orchestrator extends the capabilities of automation so you can integrate external 3rd part tools.
* **Event Broker**: 
RabbitMQ.... Message bus that creates services based on resource lifecycle events.
* **vPostgres Database**:  
This is a default PostgreSQL appliance database used for identity and core services.

![](https://raw.githubusercontent.com/jboy42/learnDoc/master/minimalVRealize.PNG)
##### **vRealize Automation IaaS**:
IaaS enables quick modeling and provisioning of servers and desktops.  IaaS is installed on a Windows machine.  
* **IaaS Web Service**:
This provides a console to manage vRealise.
* **Model Manager**:
The model manager communicates with database, DEMs, and console.  It is used for managing the "Models".
* **Manager Service**:
Coordinates communication between the DEMs, agents, and the Database.  Requires administrative privileges to run.
* **DEM Orchestrator**:
DEM runs business logic of custom models interacting with the databases.  Each DEM either act as a worker or Orchestrator.  Workes process workflows and orchestrators monitor workers.  There is one active orchestrator at a time. The orchestrator is installed on the machine that has the model manager.
* **IaaS Database**:
IaaS uses a SQL server database.  This holds all configurations and workflows.
* **Agents**:
  proxy agent: Used to itegrate with: vSphere, Citrix Xen Server, Hyper-V, EPI, VDI, WMI.
 DEMs: used for provisioning on RHEV, SCVMM, Amazon, VMware vCloud Director, Dell, HP, Cisco.

##### Minimum install requirements:
![](https://raw.githubusercontent.com/jboy42/learnDoc/6aa5f0be6d6fc2fac16e904f05afe76ce0ccc922/minimum_installVRa.PNG)

#### vRealize Automation Multi-tenancy:
The cloud can be broken into "tenant" spaces.  This is the main separating component in a vRealize environment.  Tenant boundaries are not bound by AD domains but authentication is done through an AD server.  Users always exist to a specific tenant.  Each tenant has its own configurations: 
* Login URL
* Identity Stores
* Branding
* Notification Providers
* Buisness Policies
* Service Catalog Offerings
* Infrastrucutre Resources

Tenants can have their own administrator and the tenant space can be split into buisness units which can represent any subset of the tenant user list.
**Tenant Roles**:
* Blueprint Architect - designs and writes the blueprints for the space
* Catalog Administrator - determins what services are available and where
* Approval Administrator - defines approval policies
* Approver - Approves the policies
* Buisness Group Manager - Manages one or more buisness groups
* Support User - Supports the management of catalog items in the buisness unit
* Buisness User - a general user

#### Infrastructure Fabric:
The IaaS admin, discovers and organizes the fabric.  The fabric is a combination of private and public resources.  Placing the resources in the fabric, allows for vRealize administration.  The fabric can be broken into Fabric groups.  These fabric groups are then allocated to Buisness groups through reservations.

#### Important places to visit:
VMware solutions exchange
VMware sample Exchange
VMware Development Center


