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
tux@OpenStack:~$ openstack image list
+--------------------------------------+--------------------------+--------+
| ID                                   | Name                     | Status |
+--------------------------------------+--------------------------+--------+
| dc552613-d985-479f-840b-fc7bbfe5d715 | centos                   | active |
| d659883d-5c2d-44f3-b26f-9fe512aeec95 | cirros-0.4.0-x86_64-disk | active |
+--------------------------------------+--------------------------+--------+
</pre>

<li>import the cloud image into Glance</li>
<pre>
openstack image create \
--public \
--container-format bare \
--disk-format qcow2 \
--min-disk 2 \
--min-ram 512 \
--file PATH image-name
<br>
openstack image create --public --container-format bare --disk-format qcow2 --min-disk 2 --min-ram 512 --file /tmp/SLES12SP1-cloudimage.qcow2 sles12
<br>
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field            | Value                                                                                                                                                                                      |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| checksum         | fcdeb8b10730ac96bccc9a121ee030f4                                                                                                                                                           |
| container_format | bare                                                                                                                                                                                       |
| created_at       | 2019-09-16T06:55:32Z                                                                                                                                                                       |
| disk_format      | qcow2                                                                                                                                                                                      |
| file             | /v2/images/8535008e-74f7-4607-a657-3a04c7557997/file                                                                                                                                       |
| id               | 8535008e-74f7-4607-a657-3a04c7557997                                                                                                                                                       |
| min_disk         | 2                                                                                                                                                                                          |
| min_ram          | 512                                                                                                                                                                                        |
| name             | sles12                                                                                                                                                                                     |
| owner            | 5a3a3f4958ad460f8afd065bb37f8a94                                                                                                                                                           |
| properties       | os_hash_algo='sha512', os_hash_value='1d8eb3390e9544316da91be59db65033606449fa1c097a8dbcd720682807db32023e2ca7a8b0a0d0bb76a4e0d976bb96a94a27a5f9a6f3e16eee39215076bd59', os_hidden='False' |
| protected        | False                                                                                                                                                                                      |
| schema           | /v2/schemas/image                                                                                                                                                                          |
| size             | 362847744                                                                                                                                                                                  |
| status           | active                                                                                                                                                                                     |
| tags             |                                                                                                                                                                                            |
| updated_at       | 2019-09-16T06:55:35Z                                                                                                                                                                       |
| virtual_size     | None                                                                                                                                                                                       |
| visibility       | public                                                                                                                                                                                     |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>
<li>display more information about the image</li>
<pre>
  openstack image show SLES12SP1_IMAGE_ID
  <br>
  tux@OpenStack:~$ openstack image list
  <br>
+--------------------------------------+--------------------------+--------+
| ID                                   | Name                     | Status |
+--------------------------------------+--------------------------+--------+
| dc552613-d985-479f-840b-fc7bbfe5d715 | centos                   | active |
| d659883d-5c2d-44f3-b26f-9fe512aeec95 | cirros-0.4.0-x86_64-disk | active |
| 8535008e-74f7-4607-a657-3a04c7557997 | sles12                   | active |
+--------------------------------------+--------------------------+--------+
<br>
tux@OpenStack:~$ openstack image show sles12
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field            | Value                                                                                                                                                                                      |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| checksum         | fcdeb8b10730ac96bccc9a121ee030f4                                                                                                                                                           |
| container_format | bare                                                                                                                                                                                       |
| created_at       | 2019-09-16T06:55:32Z                                                                                                                                                                       |
| disk_format      | qcow2                                                                                                                                                                                      |
| file             | /v2/images/8535008e-74f7-4607-a657-3a04c7557997/file                                                                                                                                       |
| id               | 8535008e-74f7-4607-a657-3a04c7557997                                                                                                                                                       |
| min_disk         | 2                                                                                                                                                                                          |
| min_ram          | 512                                                                                                                                                                                        |
| name             | sles12                                                                                                                                                                                     |
| owner            | 5a3a3f4958ad460f8afd065bb37f8a94                                                                                                                                                           |
| properties       | os_hash_algo='sha512', os_hash_value='1d8eb3390e9544316da91be59db65033606449fa1c097a8dbcd720682807db32023e2ca7a8b0a0d0bb76a4e0d976bb96a94a27a5f9a6f3e16eee39215076bd59', os_hidden='False' |
| protected        | False                                                                                                                                                                                      |
| schema           | /v2/schemas/image                                                                                                                                                                          |
| size             | 362847744                                                                                                                                                                                  |
| status           | active                                                                                                                                                                                     |
| tags             |                                                                                                                                                                                            |
| updated_at       | 2019-09-16T06:55:35Z                                                                                                                                                                       |
| virtual_size     | None                                                                                                                                                                                       |
| visibility       | public                                                                                                                                                                                     |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>

<li>Add Additional Properties to an Image in Glance</li>
<pre>
openstack image set \
--name SLES12-SP1 \
--architecture x86_64 \
--os-distro sles \
--os-version 12.1 \
SLES12SP1_IMAGE_ID
<br>
tux@OpenStack:~$ openstack image set --name SLES12-SP1 --architecture x86_64 --os-distro suse --os-version 12.1 sles12
<br>
tux@OpenStack:~$ openstack image show SLES12-SP1
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field            | Value                                                                                                                                                                                                                                                  |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| checksum         | fcdeb8b10730ac96bccc9a121ee030f4                                                                                                                                                                                                                       |
| container_format | bare                                                                                                                                                                                                                                                   |
| created_at       | 2019-09-16T06:55:32Z                                                                                                                                                                                                                                   |
| disk_format      | qcow2                                                                                                                                                                                                                                                  |
| file             | /v2/images/8535008e-74f7-4607-a657-3a04c7557997/file                                                                                                                                                                                                   |
| id               | 8535008e-74f7-4607-a657-3a04c7557997                                                                                                                                                                                                                   |
| min_disk         | 2                                                                                                                                                                                                                                                      |
| min_ram          | 512                                                                                                                                                                                                                                                    |
| name             | SLES12-SP1                                                                                                                                                                                                                                             |
| owner            | 5a3a3f4958ad460f8afd065bb37f8a94                                                                                                                                                                                                                       |
| properties       | architecture='x86_64', os_distro='suse', os_hash_algo='sha512', os_hash_value='1d8eb3390e9544316da91be59db65033606449fa1c097a8dbcd720682807db32023e2ca7a8b0a0d0bb76a4e0d976bb96a94a27a5f9a6f3e16eee39215076bd59', os_hidden='False', os_version='12.1' |
| protected        | False                                                                                                                                                                                                                                                  |
| schema           | /v2/schemas/image                                                                                                                                                                                                                                      |
| size             | 362847744                                                                                                                                                                                                                                              |
| status           | active                                                                                                                                                                                                                                                 |
| tags             |                                                                                                                                                                                                                                                        |
| updated_at       | 2019-09-16T07:02:52Z                                                                                                                                                                                                                                   |
| virtual_size     | None                                                                                                                                                                                                                                                   |
| visibility       | public                                                                                                                                                                                                                                                 |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>
Delete an image 
-----------------
<pre>
tux@OpenStack:~$ openstack image delete SLES12-SP1
<br>
tux@OpenStack:~$ openstack image list
+--------------------------------------+--------------------------+--------+
| ID                                   | Name                     | Status |
+--------------------------------------+--------------------------+--------+
| dc552613-d985-479f-840b-fc7bbfe5d715 | centos                   | active |
| d659883d-5c2d-44f3-b26f-9fe512aeec95 | cirros-0.4.0-x86_64-disk | active |
+--------------------------------------+--------------------------+--------+
</pre>
<div align="right">
<a href="https://docs.openstack.org/python-openstackclient/pike/cli/command-objects/image.html">Need to learn more about openstack image commands click here...</a>
</div>
<li>perform the tasks in OpenStack Dashboard</li>
<li>Admin > System > Images</li>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/glance/img/Screenshot_2019-09-16_12-50-49.png">
<br>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/glance/img/Screenshot_2019-09-16_12-56-51.png">

Glance Troubleshooting
--------------------------
<li><b>api.log</b> -API service log file (handles all requests for the Glance service such as any request for access or modify an existing image or to create a new image)</li>
<li><b>manage.log</b> -glance-manage utility log file(manages the registry or catalog of available images and mappings between the entries in the database that correspond to the image files stored in the image storage back end)</li>
<li><b>registry.log</b> -glance-registry utility log file(used to configure the Glance installation, particularly to set up the database)</li>
<li><b>scrubber.log</b> -glance-scrubber utility log file(used to clean up images that have been deleted)</li>
