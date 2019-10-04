Software Defined Networks in OpenStack
--------------------------------------------
<div align="right">
  <a href="https://en.wikipedia.org/wiki/Software-defined_networking">What is Software defined network? click here</a><br>
  <a href="https://www.openvswitch.org/">Need to know Open vSwitch click here ...</a>
 </div>
<li>provides the software defined networking functionality</li>
<li>Nova project - basic way of networking (nova-network)</li>
<li>neutron -- plug-in based architecture to allow it to be extensible</li>
<li>provides layer 2 and layer 3 networking for an OpenStack cloud</li>
<div align="right">
  <a href="https://docs.openstack.org/neutron/pike/configuration/">Various neutron configuration options click here...</a><br>
  <a href="https://www.geeksforgeeks.org/tunneling/">What is tunneling? visit here... </a><br>
  <a href="https://www.imperva.com/blog/what-is-gre-tunnel/">GRE tunnel? open this link...</a><br>
  <a href="https://www.geeksforgeeks.org/virtual-lan-vlan/">VLANs? click here ...</a> <br>
  <a href="https://medium.com/@NTTICT/vxlan-explained-930cc825a51">VXLANs? visit here....<a> <br>
  <a href="https://www.geeksforgeeks.org/network-address-translation-nat/">SNAT and DNAT? click here ...</a><br>
  <a href="https://wiki.openstack.org/wiki/Neutron#Plugins"> Neutron third party plugin options open this link ...</a>
</div>

OpenStack Security Groups
---------------------------
<li>firewall rules</li>
<li>allow ingress or egress traffic</li>
<li>applied to projects</li>
<li>quota - resrict the creation of more number of rules</li>
<li>Following image Shows how ingress egress associated with VMs</li>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/neutron/img/ingress-egress.png" height="400" width="500"/>
<div align="center">
  <a href="https://medium.com/google-cloud/why-ingress-traffic-to-the-cloud-is-free-79dc217b916">Reference --ingress & egress</a>
</div>

Neutron Configuration Commands
-----------------------------------
<li>View the existing private networks</li>
<pre>
tux@OpenStack:~$ openstack network list
+--------------------------------------+---------+----------------------------------------------------------------------------+
| ID                                   | Name    | Subnets                                                                    |
+--------------------------------------+---------+----------------------------------------------------------------------------+
| 2924b13a-923f-4def-a2a5-00359389926f | shared  | 2f9465b1-b844-4945-aca9-9d143994ff34                                       |
| 4d38b744-bdbc-4d4d-a526-963007fb4f0a | private | 2ab02cbc-d360-474c-813c-d70a4cb48f78, 7dd8ff73-feaa-4554-a96f-a34312488169 |
| d1e7fac7-018e-4079-960e-de9b6016c108 | public  | 2982866b-ef6d-4c54-9c75-db976c0d011f, b676dc5c-0515-4ac2-b12b-384341381cff |
+--------------------------------------+---------+----------------------------------------------------------------------------+
</pre>
<li>Create a private network</li>
<pre>
tux@OpenStack:~$ openstack network create --description "gaming nwtwork 1738" --project gaming1738 gnet-1738
+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field                     | Value                                                                                                                                                                               |
+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| admin_state_up            | UP                                                                                                                                                                                  |
| availability_zone_hints   |                                                                                                                                                                                     |
| availability_zones        |                                                                                                                                                                                     |
| created_at                | 2019-09-30T08:38:50Z                                                                                                                                                                |
| description               | gaming nwtwork 1738                                                                                                                                                                 |
| dns_domain                | None                                                                                                                                                                                |
| id                        | 8627faf8-1087-451d-b69a-f104a57b0787                                                                                                                                                |
| ipv4_address_scope        | None                                                                                                                                                                                |
| ipv6_address_scope        | None                                                                                                                                                                                |
| is_default                | False                                                                                                                                                                               |
| is_vlan_transparent       | None                                                                                                                                                                                |
| location                  | Munch({'project': Munch({'domain_id': None, 'id': u'ecfc023743d04dd2bd89efdf08deea19', 'name': None, 'domain_name': None}), 'cloud': '', 'region_name': 'RegionOne', 'zone': None}) |
| mtu                       | 1450                                                                                                                                                                                |
| name                      | gnet-1738                                                                                                                                                                           |
| port_security_enabled     | True                                                                                                                                                                                |
| project_id                | ecfc023743d04dd2bd89efdf08deea19                                                                                                                                                    |
| provider:network_type     | vxlan                                                                                                                                                                               |
| provider:physical_network | None                                                                                                                                                                                |
| provider:segmentation_id  | 68                                                                                                                                                                                  |
| qos_policy_id             | None                                                                                                                                                                                |
| revision_number           | 1                                                                                                                                                                                   |
| router:external           | Internal                                                                                                                                                                            |
| segments                  | None                                                                                                                                                                                |
| shared                    | False                                                                                                                                                                               |
| status                    | ACTIVE                                                                                                                                                                              |
| subnets                   |                                                                                                                                                                                     |
| tags                      |                                                                                                                                                                                     |
| updated_at                | 2019-09-30T08:38:50Z                                                                                                                                                                |
+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>
<li> delete a private network</li>
<pre>
tux@OpenStack:~$ openstack network delete d542eccc-069c-4550-b2c0-987e8f42fe94
tux@OpenStack:~$ openstack network list
+--------------------------------------+---------+----------------------------------------------------------------------------+
| ID                                   | Name    | Subnets                                                                    |
+--------------------------------------+---------+----------------------------------------------------------------------------+
| 2924b13a-923f-4def-a2a5-00359389926f | shared  | 2f9465b1-b844-4945-aca9-9d143994ff34                                       |
| 4d38b744-bdbc-4d4d-a526-963007fb4f0a | private | 2ab02cbc-d360-474c-813c-d70a4cb48f78, 7dd8ff73-feaa-4554-a96f-a34312488169 |
| d1e7fac7-018e-4079-960e-de9b6016c108 | public  | 2982866b-ef6d-4c54-9c75-db976c0d011f, b676dc5c-0515-4ac2-b12b-384341381cff |
+--------------------------------------+---------+----------------------------------------------------------------------------+
</pre>
<li> list out subnets which are ipv4</li>
<pre>
tux@OpenStack:~$ openstack subnet list --ip-version 4
+--------------------------------------+----------------+--------------------------------------+------------------+
| ID                                   | Name           | Network                              | Subnet           |
+--------------------------------------+----------------+--------------------------------------+------------------+
| 2ab02cbc-d360-474c-813c-d70a4cb48f78 | private-subnet | 4d38b744-bdbc-4d4d-a526-963007fb4f0a | 10.0.0.0/26      |
| 2f9465b1-b844-4945-aca9-9d143994ff34 | shared-subnet  | 2924b13a-923f-4def-a2a5-00359389926f | 192.168.233.0/24 |
| b676dc5c-0515-4ac2-b12b-384341381cff | public-subnet  | d1e7fac7-018e-4079-960e-de9b6016c108 | 172.24.4.0/24    |
+--------------------------------------+----------------+--------------------------------------+------------------+
</pre>
<li>create a subnet </li>
<li> Note: subnets are part of a network with some ip series </li>
<pre>
tux@OpenStack:~$ openstack subnet create --description "gaming developer network" --network  gnet-1738 --allocation-pool start=10.0.0.10,end=10.0.0.100 --gateway 10.0.0.1 --dhcp --dns-nameserver 8.8.8.8 --subnet-range 10.0.0.0/24 gnet-1738-dev 
+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field             | Value                                                                                                                                                                                       |
+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| allocation_pools  | 10.0.0.10-10.0.0.100                                                                                                                                                                        |
| cidr              | 10.0.0.0/24                                                                                                                                                                                 |
| created_at        | 2019-10-04T04:24:44Z                                                                                                                                                                        |
| description       | gaming developer network                                                                                                                                                                    |
| dns_nameservers   | 8.8.8.8                                                                                                                                                                                     |
| enable_dhcp       | True                                                                                                                                                                                        |
| gateway_ip        | 10.0.0.1                                                                                                                                                                                    |
| host_routes       |                                                                                                                                                                                             |
| id                | 41fb8411-b44e-4b6d-9b3a-0af5fefc3b4f                                                                                                                                                        |
| ip_version        | 4                                                                                                                                                                                           |
| ipv6_address_mode | None                                                                                                                                                                                        |
| ipv6_ra_mode      | None                                                                                                                                                                                        |
| location          | Munch({'project': Munch({'domain_id': 'default', 'id': u'5a3a3f4958ad460f8afd065bb37f8a94', 'name': 'admin', 'domain_name': None}), 'cloud': '', 'region_name': 'RegionOne', 'zone': None}) |
| name              | gnet-1738-dev                                                                                                                                                                               |
| network_id        | 5e77f038-1eea-4f10-9601-0e82859d60dc                                                                                                                                                        |
| prefix_length     | None                                                                                                                                                                                        |
| project_id        | 5a3a3f4958ad460f8afd065bb37f8a94                                                                                                                                                            |
| revision_number   | 0                                                                                                                                                                                           |
| segment_id        | None                                                                                                                                                                                        |
| service_types     |                                                                                                                                                                                             |
| subnetpool_id     | None                                                                                                                                                                                        |
| tags              |                                                                                                                                                                                             |
| updated_at        | 2019-10-04T04:24:44Z                                                                                                                                                                        |
+-------------------+-----------------------------------------
</pre>
<li>list the created subnet</li>
<pre>
tux@OpenStack:~$ openstack subnet list --ip-version 4
+--------------------------------------+----------------+--------------------------------------+------------------+
| ID                                   | Name           | Network                              | Subnet           |
+--------------------------------------+----------------+--------------------------------------+------------------+
| 2ab02cbc-d360-474c-813c-d70a4cb48f78 | private-subnet | 4d38b744-bdbc-4d4d-a526-963007fb4f0a | 10.0.0.0/26      |
| 2f9465b1-b844-4945-aca9-9d143994ff34 | shared-subnet  | 2924b13a-923f-4def-a2a5-00359389926f | 192.168.233.0/24 |
| 41fb8411-b44e-4b6d-9b3a-0af5fefc3b4f | gnet-1738-dev  | 5e77f038-1eea-4f10-9601-0e82859d60dc | 10.0.0.0/24      |
| b676dc5c-0515-4ac2-b12b-384341381cff | public-subnet  | d1e7fac7-018e-4079-960e-de9b6016c108 | 172.24.4.0/24    |
+--------------------------------------+----------------+--------------------------------------+------------------+
</pre>

<li>Delete a subnet</li>
<pre>
tux@OpenStack:~$ openstack subnet delete gnet-1738-dev
tux@OpenStack:~$ openstack subnet list --ip-version 4
+--------------------------------------+----------------+--------------------------------------+------------------+
| ID                                   | Name           | Network                              | Subnet           |
+--------------------------------------+----------------+--------------------------------------+------------------+
| 2ab02cbc-d360-474c-813c-d70a4cb48f78 | private-subnet | 4d38b744-bdbc-4d4d-a526-963007fb4f0a | 10.0.0.0/26      |
| 2f9465b1-b844-4945-aca9-9d143994ff34 | shared-subnet  | 2924b13a-923f-4def-a2a5-00359389926f | 192.168.233.0/24 |
| b676dc5c-0515-4ac2-b12b-384341381cff | public-subnet  | d1e7fac7-018e-4079-960e-de9b6016c108 | 172.24.4.0/24    |
+--------------------------------------+----------------+--------------------------------------+------------------+
</pre>

Creating a Virtual Router
----------------------------
<li><b>Note:</b> Creating a virtual router has a dependency</li>
<li><b>Dependency > </b> network and subnet must be created before creating a project</li>

<li>list the router</li>
<pre>
tux@OpenStack:~$ openstack router list --project gaming1738
Note: Nothing will be listed beacuse no router has been create for the project gaming1738
</pre>

<li>create a router</li>
<pre>
tux@OpenStack:~$ openstack router create --description "gaming 1738 developer router" --project gaming1738 rgaming1738-dev
+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field                   | Value                                                                                                                                                                               |
+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| admin_state_up          | UP                                                                                                                                                                                  |
| availability_zone_hints |                                                                                                                                                                                     |
| availability_zones      |                                                                                                                                                                                     |
| created_at              | 2019-10-04T05:50:41Z                                                                                                                                                                |
| description             | gaming 1738 developer router                                                                                                                                                        |
| distributed             | False                                                                                                                                                                               |
| external_gateway_info   | None                                                                                                                                                                                |
| flavor_id               | None                                                                                                                                                                                |
| ha                      | False                                                                                                                                                                               |
| id                      | 1a1f56d1-b308-4bf4-924f-5660434f2daa                                                                                                                                                |
| location                | Munch({'project': Munch({'domain_id': None, 'id': u'ecfc023743d04dd2bd89efdf08deea19', 'name': None, 'domain_name': None}), 'cloud': '', 'region_name': 'RegionOne', 'zone': None}) |
| name                    | rgaming1738-dev                                                                                                                                                                     |
| project_id              | ecfc023743d04dd2bd89efdf08deea19                                                                                                                                                    |
| revision_number         | 1                                                                                                                                                                                   |
| routes                  |                                                                                                                                                                                     |
| status                  | ACTIVE                                                                                                                                                                              |
| tags                    |                                                                                                                                                                                     |
| updated_at              | 2019-10-04T05:50:41Z                                                                                                                                                                |
+-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>

<li> list the router </li>
<pre>
tux@OpenStack:~$ openstack router list --project gaming1738
+--------------------------------------+-----------------+--------+-------+----------------------------------+-------------+-------+
| ID                                   | Name            | Status | State | Project                          | Distributed | HA    |
+--------------------------------------+-----------------+--------+-------+----------------------------------+-------------+-------+
| 1a1f56d1-b308-4bf4-924f-5660434f2daa | rgaming1738-dev | ACTIVE | UP    | ecfc023743d04dd2bd89efdf08deea19 | False       | False |
+--------------------------------------+-----------------+--------+-------+----------------------------------+-------------+-------+
</pre

<li> show the external gateway interface of the created router <li>
<pre>
tux@OpenStack:~$ openstack router show rgaming1738-dev | grep external
| external_gateway_info   | None    |
</pre>

<li> connecting router to an external gateway</li>
<pre>
tux@OpenStack:~$ openstack router set --external-gateway public rgaming1738-dev

tux@OpenStack:~$ openstack router show rgaming1738-dev | grep external
| external_gateway_info   | {"network_id": "d1e7fac7-018e-4079-960e-de9b6016c108", "enable_snat": true, "external_fixed_ips": [{"subnet_id": "b676dc5c-0515-4ac2-b12b-384341381cff", "ip_address": "172.24.4.52"}, {"subnet_id": "2982866b-ef6d-4c54-9c75-db976c0d011f", "ip_address": "2001:db8::13d"}]} |
</pre>

<li> After creating the router and assigning a external gateway your project network look like this</li>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/neutron/img/router-and-net.png"/>
