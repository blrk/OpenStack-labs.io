Domains
--------------
<li>Domains are high-level containers for projects, users and groups. </li>
<li>can be used to centrally manage all keystone-based identity components.</li>
<li>introduction of account domains, server, storage and other resources can now be logically grouped into multiple projects (previously called tenants) which can themselves be grouped under a master account-like container.</li>
<li>multiple users can be managed within an account domain and assigned roles that vary for each project.</li>
<li>Identity V3 API supports multiple domains.</li>
<li>Users of different domains may be represented in different authentication back ends </li> and even have different attributes that must be mapped to a single set of roles and privileges, that are used in the policy definitions to access the various service resources. </li>
<li><a href="https://docs.openstack.org/security-guide/identity/domains.html">More Info about domains</a></li>

domain commands
---------------
<pre> 
tux@OpenStack:~$ openstack domain
openstack: 'domain' is not an openstack command. See 'openstack --help'.
Did you mean one of these?
  domain create
  domain delete
  domain list
  domain set
  domain show
</pre>
<li><a href="https://docs.openstack.org/python-openstackclient/pike/cli/command-objects/domain.html#domain-create">Domain command reference</a></li>

domain create
<pre>
tux@OpenStack:~$ openstack domain create --description "Domain of CSE Faculty" Faculty
+-------------+----------------------------------+
| Field       | Value                            |
+-------------+----------------------------------+
| description | Domain of CSE Faculty            |
| enabled     | True                             |
| id          | 1390944379d146fab75d7505359049c8 |
| name        | Faculty                          |
| tags        | []                               |
+-------------+----------------------------------+
</pre>
view information about the domain
-----------------------------------
<pre>
tux@OpenStack:~$ openstack domain list | grep Faculty
| 1390944379d146fab75d7505359049c8 | Faculty   | True    | Domain of CSE Faculty |
</pre>
details about the domain
------------------------
<pre>
tux@OpenStack:~$ openstack domain show Faculty
+-------------+----------------------------------+
| Field       | Value                            |
+-------------+----------------------------------+
| description | Domain of CSE Faculty            |
| enabled     | True                             |
| id          | 1390944379d146fab75d7505359049c8 |
| name        | Faculty                          |
| tags        | []                               |
+-------------+----------------------------------+
</pre>
delete a domain 
-----------------
<pre>
tux@OpenStack:~$ openstack domain delete test
Failed to delete domain with name or ID 'test': Cannot delete a domain that is enabled, please disable it first. (HTTP 403) (Request-ID: req-7966c148-ee7b-44ee-a026-2abcea318469)
1 of 1 domains failed to delete.
</pre>
Set domain properties
---------------------
<li> diable a domain</li>
<pre>
tux@OpenStack:~$ openstack domain set --disable test
<li>Delete a domian </li>
tux@OpenStack:~$ openstack domain delete test
tux@OpenStack:~$ openstack domain list | grep test
nothing will be printed
</pre>




