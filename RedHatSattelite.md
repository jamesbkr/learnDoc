# Satellite
##### Why Satellite
Standardizes operating environment.  Satellite is used for automation, standardization, and streamlined management.  Satellite allows for automated software distribution.  lifecycle management.  mold satallite server to the environment.  It allows for drift remediation.  Content management is simplified.  Satellite can Federate out using capsule server to scale horizontally.  Satellite is localized in many languages.  It allows for provisioning in bare metal along with private and public cloud.
### Satellite 6 software compotnents
- Puppet - configuration management
- Foreman - provisioning
- Pulp - Repository manangement
- Katello - Content/lifecycle managemnt
- Candlespin - Subscription management

### provisioning
Satellite provisions to bare metal, private, and public clouds.  Federates content delivery, Discover non provisioned hosts.

### configuration
Define desired state of system.  Enforce Compliance to configuration standards.  Audit and report when changes are made.

### software management
Define and manage standard operating environments.  Responds quickly to secure vulnerabilities.  Deploy scalable and secure patching policy.  Manage releases centrally.

### subscription management
Centrally manage subscriptions.  Accurate inventory and utalization information.  Reporting on what is in use and where.

## Physical components
### Sattelite server
- Multi-tenant
- on-premance repository management
- user and group role based access (RBAC)
- Powerful user interfaces (GUI, API, & CLI)
- Advanced subscription management
- pulls content from redHat, Git, Puppet

### Satellite Capsule Server
- Federated services
- Automated provisioning
- discovery of new physical and virtual machines

### Smart Management
- Required for each subscription managed via satallite.

## Main Components in Satellite
##### Foreman
Foreman is an upstream component that does a lot of work.  used for provisioning and life cycle management of physical and virtual systems.  Satellite also includes components, configuraiton, and funcaiotnality to prvovision and configure operating systems other that RHEL.
##### Katello
This is the content and subscription user interface.  Katello must be interacted with through satellite.  there is no direct interaction with Katello.  
##### Candlepin
susbcription managemnt subsystem.  Only supported use through satellite 6 UI, CLI, or API.  Interacting directly with candlepin can break Satellite
##### Pulp
Content management subsystem.  Cannot interact directly with pulp.  Can break satellite if you interact directly with it.  Must use satellite interface.
##### Hammer
CLI tool for interacting with Satellite
##### REST API service
API for custom scripting and integrations
##### Capsul server
Provides federated services to discover, provision, and configure hosts ooutside of primary satellite server.  Pulp server/content node features, including repository synchronization and content delivery.  Capsule servers also provide Satellite Provisioning Smart Proxy Features:  DHCP, DNS, TFTP, Puppet Master servers from 0.24, Puppet CA, and Baseboard managemetn controller (BMC).  
##### Puppet
Puppet is the backbone of the Configuration management strategy of Satellite.  Through the use of Foreman, Satellite 6 leverages Puppet and Puppet modules to ensure that the desired system end-state is met.  Puppet is an open sourced congfiguratoin management system that typically run in a client server fashion.  Puppet has its own DSL. Puppet runs on a schedule and determes what manefest needs to be run.  The agent applies the manifest every time the agent is run.  This is done for drift correction. So basically drift is managemd every time Puppet Fires.  Puppet masters can be installed with the satellite or capsul server.
- facts:  Puppet uses Facter.  which is a piece of software that understands many things about the operating system on which it is working.  it can use these various facts to make decisions on what to do in the manifest.  
- Main components in a manifest are: file, package, service - these resources are actual definitions about the file, package, or service that is run on the system.  
### Logical breakdown of users and things in satellite
- orgainization: logical group of hosts based on ownership, purpose, content, security level, ect...
- location: meant to represent a physical location where hosts live for breakdowns.  
- manifests: Manifests are signed ZIP files which provide SKU-level mapping of products including sla and expiration date.  They contain information in JSON format and are fairly cryptic.  Extracted and parsed. 

### Host Registration
- Activation Keys: define which life-cycle environment the host should be placed in.  Which host collectoin the host should be assigned to.  Which organization the host should be a part of.  Whether to use a system template for the host. the subscritpoin usage limit for the host.  the specific subscription assigned to the host.
- Host Group: sets variables for hosts in that group.  Hosts can belong to one host group but host groups can be nested in other host groups for layers of hosts. 


