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

Metadata Definitions
------------------------
<li>Glance hosts a metadefs catalog</li>
<li>provides a way to programmatically determine various metadata key names and valid values that can be applied to OpenStack resources</li>

Image Service Overview
-------------------------
<li>A number of periodic processes run on the OpenStack Image service to support caching</li>
<li>Replication services ensure consistency and availability through the cluster</li>
<li>Other periodic processes include auditors, updaters, and reapers</li>

<b>OpenStack Image service includes the following components</b>
<li><b>glance-api:</b>Accepts Image API calls for image discovery, retrieval, and storage</li>
<li><b>glance-registry:</b>Stores, processes, and retrieves metadata about images. Metadata includes items such as size and type</li>
<li><b>Database:</b>Stores image metadata and you can choose your database depending on your preference. Most deployments use MySQL or SQLite</li>
<li><b>Storage repository for image files:</b>Various repository types are supported</li>
  <ul>
    <li>normal file systems (or any filesystem mounted on the glance-api controller node)</li>
    <li>Object Storage, RADOS block devices, VMware datastore, and HTTP</li>
    <li>Note that some repositories will only support read-only usage</li>
  </ul>
<li><b>Metadata definition service:</b>A common API for vendors, admins, services, and users to meaningfully define their own custom metadata</li> 
  <ul>
    <li>This metadata can be used on different types of resources like images, artifacts, volumes, flavors, and aggregates</li>
    <li>A definition includes the new property’s key, description, constraints, and the resource types which it can be associated with</li>
  </ul>
  
Design Principles
-----------------
<b>all OpenStack projects, is written with the following design guidelines in mind</b>
<li>Component based architecture: Quickly add new behaviors</li>
<li>Highly available: Scale to very serious workloads</li>
<li>Fault tolerant: Isolated processes avoid cascading failures</li>
<li>Recoverable: Failures should be easy to diagnose, debug, and rectify</li>
<li>Open standards: Be a reference implementation for a community-driven api</li>
<div align="right">
<a href="https://docs.openstack.org/glance/latest/">For more info visit here (About Glance)</a><br>
<a href="https://docs.openstack.org/newton/install-guide-rdo/common/get-started-image-service.html">For more info Visit here (Image service overview) </a>
</div>

How to use Glance
---------------------
<li>list the images currently in the Glance server registry</li>
<pre>
openstack image list
</pre>

<li>import the cloud image into Glance</li>
<pre>
openstack image create \
--public \
--container-format bare \
--disk-format qcow2 \
--min-disk 2 \
--min-ram 512 \
--file PATH
</pre>
<li>display more information about the</li>
<pre>
  openstack image show SLES12SP1_IMAGE_ID
</pre>

<li>Add Additional Properties to an Image in Glance<li>
<pre>
openstack image set \
--name SLES12-SP1 \
--architecture x86_64 \
--os-distro sles \
--os-version 12.1 \
SLES12SP1_IMAGE_ID
</pre>

<li>perform the tasks in OpenStack Dashboard</li>
<li>Admin > System > Images</li>

Glance Troubleshooting
--------------------------
<li>api.log -API service log file (handles all requests for the Glance service such as any request for access or modify an
existing image or to create a new image)</li>
<li>manage.log -glance-manage utility log file(manages the registry or catalog of available images and mappings between the entries in the database that correspond to the image files stored in the image storage back end)</li>
<li>registry.log -glance-registry utility log file(used to configure the Glance installation, particularly to set up the database)</li>
<li>scrubber.log -glance-scrubber utility log file(used to clean up images that have been deleted)</li>
