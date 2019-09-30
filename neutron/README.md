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
tux@OpenStack:~$ openstack network create --description "gaming 1738 nwtwork" gaming1738-net
+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Field                     | Value                                                                                                                                                                                       |
+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| admin_state_up            | UP                                                                                                                                                                                          |
| availability_zone_hints   |                                                                                                                                                                                             |
| availability_zones        |                                                                                                                                                                                             |
| created_at                | 2019-09-30T08:33:51Z                                                                                                                                                                        |
| description               | gaming 1738 nwtwork                                                                                                                                                                         |
| dns_domain                | None                                                                                                                                                                                        |
| id                        | d542eccc-069c-4550-b2c0-987e8f42fe94                                                                                                                                                        |
| ipv4_address_scope        | None                                                                                                                                                                                        |
| ipv6_address_scope        | None                                                                                                                                                                                        |
| is_default                | False                                                                                                                                                                                       |
| is_vlan_transparent       | None                                                                                                                                                                                        |
| location                  | Munch({'project': Munch({'domain_id': 'default', 'id': u'5a3a3f4958ad460f8afd065bb37f8a94', 'name': 'admin', 'domain_name': None}), 'cloud': '', 'region_name': 'RegionOne', 'zone': None}) |
| mtu                       | 1450                                                                                                                                                                                        |
| name                      | gaming1738-net                                                                                                                                                                              |
| port_security_enabled     | True                                                                                                                                                                                        |
| project_id                | 5a3a3f4958ad460f8afd065bb37f8a94                                                                                                                                                            |
| provider:network_type     | vxlan                                                                                                                                                                                       |
| provider:physical_network | None                                                                                                                                                                                        |
| provider:segmentation_id  | 31                                                                                                                                                                                          |
| qos_policy_id             | None                                                                                                                                                                                        |
| revision_number           | 1                                                                                                                                                                                           |
| router:external           | Internal                                                                                                                                                                                    |
| segments                  | None                                                                                                                                                                                        |
| shared                    | False                                                                                                                                                                                       |
| status                    | ACTIVE                                                                                                                                                                                      |
| subnets                   |                                                                                                                                                                                             |
| tags                      |                                                                                                                                                                                             |
| updated_at                | 2019-09-30T08:33:51Z                                                                                                                                                                        |
+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
</pre>


