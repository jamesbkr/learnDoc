# Openstack
## Nova - Compute:
Nova is the compute component of Openstack.  Nova was one of the firs components released and has a wide range of capabilities.  It can integrate with KVM, qemu, Xen, VMware, Hyper-V and Docker.  
#### core daemons in the Nova service
* Nova-compute: accepts actions from the queue in order to perform common actions on an instance.
* Nova-conductor: this is the interface with the database for Nova.  Without it, Nova can create irregular data in the database.
* Nova-scheduler: Controls interactions with the messaging queue.  It picks up messages and forwards them to the compute instances.
* Nova-api: the API service for Nova.
* Nova-api-metadata: for getting metadata information about specific Nova instances.

#### Key notes:
* Nova-compute should not be run on the same node as the conductor or the database.
* other useful daemons:  nova-consoleauth, nova-novncproxy, nova-spicehtml5proxym, nova-xvpvncproxy.

## Keystone - Identity:
Keystone is the identity management service for Openstack.  Keystone can authenticate with username/password and API key authentication.  Keystone uses a Project, Domain, Role model for allowing user and group access.  Keystone uses WSGI.  Apache with mod_wsgi is used to deploy the service.

## Neutron - Networking:
Neutron is the networking component of Openstack.  By default, Neutron will setup a private network that instances live on and an internet routable network that instances will need to be connected on to inable internet access.  Neutron has two types of core componenets:
* neutron-server: daemon that brokers requests through the various Neutron plugins
* plugins and agents: plugins are virtual representations of ports, brides, address handlers, and more vendor specific types for virtual and physical switches.

**Neutron is flexable**

## Glance - Image Management:
Glance is used for managing and images inside Openstack.  Images are usually qcow2, ISO or img files.  There are 2 main components of Glance:
* Glance-api: API used to interact with Glance.
* Glance-registry: internal Glance registry that maintaines meta-data about the images loaded.

**there is also storage needed to hold the images and metadata**
## Cinder - Block Storage:
Openstacks block storage solution.  Cinder can provide persistent storage to instances or expandable disk space for instances.  
Components:
* cinder-api:  API that accepts requests from the other pieces of Openstack.  It then sends them to the volume daemon for usage.
* cinder-backup: service for backing up volumes to a storage provider.
* cinder-scheduler: selects the storage node to store something.
* cinder-volume: this is the daemon that actually interacts with the storage providors.

## Swift - Object Storage:
Swift is Openstacks object storage service.  Object storage is highly scalable and available.  These objects are then accessable via REST.  
Components: 
* periodic processes: these are housekeeping processes that are run by swift.  replication, updaters, audits, and more.
* swift-account-server: Account manager
* swift-container-server: handles management of container folders
* swift-object-server: handles management of the objects in the storage nodes
* swift-proxy-server: a server that receives requests via API in order to change data.

Swift can use something other than Keystone to authenticate.

## Ceilometer - Telemetry: 
this a metering and usage monitor for Openstack.  It polls data about metering, collects it, and publishes it to data storage or messaging queues.  Ceilometer is not lightweight and allows for more functionality than most 3rd party providors.
components:
* ceilometer-agent-central: horizontally scalable polling component for statistics.
* ceilomeeter-agent-compute: compute node service for polling statistics on compute nodes
* ceilometer-agent-notification: a service that consumes messaging data from the queue to build events and metering data.
* ceilometer-api:  The API that is hit to conduct polls.
* ceilometer-collector: this is the data distributor that puts data where it needs to go after it is polled.

## Ironic - bare metal:
This is the service that is used for provisioning of bare metal servers.  It supports PXE and IPMI.  
componenets:
* ironic-api: processes requests and sends them to the conductor.
* ironic-conductor: this is the service that actually does the actions for ironic.
* ironic-python-agent:
* Python service that runs in a temporary ram disk to provide ironic services with remote access and in-band hardware control.


## Heat - Orchestration:
Heat uses text based templates for orchestrating and deploying resources.  the sets of resources are called "stacks".  This may include instances, network components, security rules, ect... The format for these files: either use HOT or CFN.
components:
* heat-api: Restful API that is used for interacting with Heat.
* heat-api-cfn: Used for CFN templates
* heat-engine: provides orchestration.

HOT template guide: http://docs.openstack.org/developer/heat/template_guide/

## Magnum - Containers:
Magnum is used for orchestrating and managing containers.  Docker swarm and Kubernetes are the two main Container orchestrators that it takes advantage of.


