Work With Cloud Workload Instances
---------------------------------------
<li>In the previous sections you learned about the features such as key pairs, flavors, snapshots
and quotas to be used with the Compute service (nova) in OpenStack. This section we will explore how to launch and work with cloud instances</li>

Creating an instance or VM
--------------------------
<pre>
openstack server create --image a419afab-a64b-41ef-bb5e-8bdee1b5bdc9 --flavor m1.tiny --security-group default --key-name local-mc --nic net-id=fixed vm02
</pre>

OpenStack server command options
------------------------------------
<pre>
create -launch a new instance
reboot -reboot an instance
suspend -suspend an instance to disk
resume -resume a suspended instance
delete -power off and remove an instance
list -display existing instances
</pre>

list the running instances 
--------------------------
<pre>
$openstack server list
+-------------+----------------------+--------+------------+-------------+------------------+------------+
| ID          | Name                 | Status | Task State | Power State | Networks         | Image Name |
+-------------+----------------------+--------+------------+-------------+------------------+------------+
| 84c6e57d... | myCirrosServer       | ACTIVE | None       | Running     | private=10.0.0.3 | vm02    |
| 8a99547e... | myInstanceFromVolume | ACTIVE | None       | Running     | private=10.0.0.4 | ubuntu     |
| d7efd3e4... | newServer            | ERROR  | None       | NOSTATE     |                  | centos     |
+-------------+----------------------+--------+------------+-------------+------------------+------------+
</pre>

Reboot an instance
------------------
<li>You can soft or hard reboot a running instance. A soft reboot attempts a graceful shut down and restart of the instance. A hard reboot power cycles the instance </li>
<li>By default, when you reboot a server, it is a soft reboot</li>
<pre>
$ openstack server reboot vm02
</pre>
<li>To perform a hard reboot, pass the --hard parameter, as follows </li>
<pre>
$ openstack server reboot --hard vmo2
</pre>

Resuce an instance
-----------------------
<li>It is also possible to reboot a running instance into rescue mode</li>
<li>For example, this operation may be required, if a filesystem of an instance becomes corrupted with prolonged use</li>

<b>Note</b>
<li>Pause, suspend, and stop operations are not allowed when an instance is running in rescue mode, as triggering these actions causes the loss of the original instance state, and makes it impossible to unrescue the instance </li>

<li>Rescue mode provides a mechanism for access, even if an image renders the instance inaccessible</li>
<li>By default, it starts an instance from the initial image attaching the current boot disk as a secondary one</li>
<li>To perform an instance reboot into rescue mode, run the following command</li>
<pre>
$ openstack server rescue vm02
</pre>

<li>To restart the instance from the normal boot disk, run the following command</li>
<pre>
$ openstack server unrescue vm02
</pre>

Delete an Instance
----------------------
<li>Run the openstack server delete command to delete the instance</li>
<pre>
$ openstack server delete centos
$ openstack server list
+-------------+----------------------+--------+------------+-------------+------------------+------------+
| ID          | Name                 | Status | Task State | Power State | Networks         | Image Name |
+-------------+----------------------+--------+------------+-------------+------------------+------------+
| 84c6e57d... | myCirrosServer       | ACTIVE | None       | Running     | private=10.0.0.3 | vm02     |
| 8a99547e... | myInstanceFromVolume | ACTIVE | None       | Running     | private=10.0.0.4 | ubuntu     |
+-------------+----------------------+--------+------------+-------------+------------------+------------+
</pre>

Suspend and resume an instance
------------------------------------
<li>To initiate a hypervisor-level suspend operation, run the following command</li>
<pre>
$ openstack server suspend vm02
<pre>
<li>To resume a suspended instance, run the following command</li>
<pre>
$ openstack server resume vm02
</pre>



