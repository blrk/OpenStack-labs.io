Glance
--------------
<li>provides a service where users can upload and discover data assets that are meant to be used with other services</li>
<li>currently includes images and metadata definitions</li>

Images
-------------
<li>Glance image services include discovering, registering, and retrieving virtual machine (VM) images</li>
<li>Glance has a RESTful API that allows querying of VM image metadata as well as retrieval of the actual image</li>
<b>Possible places to store VM images</b>
<li>simple filesystems</li>
<li>object-storage systems like the OpenStack Swift project</li>

Image Service Overview
-------------------------
<li>A number of periodic processes run on the OpenStack Image service to support caching</li>
<li>Replication services ensure consistency and availability through the cluster</li>
<li>Other periodic processes include auditors, updaters, and reapers</li>
Metadata Definitions
------------------------
<li>Glance hosts a metadefs catalog</li>
<li>provides a way to programmatically determine various metadata key names and valid values that can be applied to OpenStack resources</li>

Design Principles
-----------------
<b>all OpenStack projects, is written with the following design guidelines in mind</b>
<li>Component based architecture: Quickly add new behaviors</li>
<li>Highly available: Scale to very serious workloads</li>
<li>Fault tolerant: Isolated processes avoid cascading failures</li>
<li>Recoverable: Failures should be easy to diagnose, debug, and rectify</li>
<li>Open standards: Be a reference implementation for a community-driven api</li>
<div align="right">
<a href="https://docs.openstack.org/glance/latest/">For more info visit here</a>
</div>

