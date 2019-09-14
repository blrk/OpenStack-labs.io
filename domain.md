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
tux@OpenStack:~$ openstack domain create faculty
+-------------+----------------------------------+
| Field       | Value                            |
+-------------+----------------------------------+
| description |                                  |
| enabled     | True                             |
| id          | 340bc5053c8c4de3a71df9e54b3c0a77 |
| name        | faculty                          |
| tags        | []                               |
+-------------+----------------------------------+
</pre>

