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
view the list of users in a domain
---------------------------------------
<pre>
tux@OpenStack:~$ openstack user list --domain Faculty

<li>nothing will be printed (no users created yet)</li>
</pre>
Domain user creation 
-----------------------
<pre>
tux@OpenStack:~$ openstack user create --domain Faculty --description "Domain admin" --password-prompt blrk
User Password:
Repeat User Password:
+---------------------+----------------------------------+
| Field               | Value                            |
+---------------------+----------------------------------+
| description         | Domain admin                     |
| domain_id           | 1390944379d146fab75d7505359049c8 |
| enabled             | True                             |
| id                  | 62389dcd21b94148be82eb1432616cb0 |
| name                | blrk                             |
| options             | {}                               |
| password_expires_at | None                             |
+---------------------+----------------------------------+
</pre>
add role to the domain user (admin)
---------------------------------------
<pre>
tux@OpenStack:~$ openstack role add  --domain Faculty --user blrk admin

Note(nothing will be printed)
</pre>
login using the credential created
---------------------------------------
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-14_17-31-09.png'>
<li> After login you will the the domain admin dashboard</li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-14_17-38-57.png'>
<li> Look at project link is missing in the left pane</li>
create a project
-----------------
<pre>
tux@OpenStack:~$ openstack project create --domain Faculty --description "Blockchain development" blockchain
+-------------+----------------------------------+
| Field       | Value                            |
+-------------+----------------------------------+
| description | Blockchain development           |
| domain_id   | 1390944379d146fab75d7505359049c8 |
| enabled     | True                             |
| id          | ed0b2560f1a74667b94abf67c5e9a512 |
| is_domain   | False                            |
| name        | blockchain                       |
| parent_id   | 1390944379d146fab75d7505359049c8 |
| tags        | []                               |
+-------------+----------------------------------+
</pre>
add project access to the domain admin
---------------------------------------
<li> do it using the dashboard</li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-14_17-56-48.png'>
<li> logout and login again you will get the project tab back and able to access apis<li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-14_18-06-16.png'>
