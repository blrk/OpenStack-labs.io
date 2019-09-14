Domains
--------------
<li>Domains are high-level containers for projects, users and groups. </li>
<li>can be used to centrally manage all keystone-based identity components.</li>
<li>introduction of account domains, server, storage and other resources can now be logically grouped into multiple projects (previously called tenants) which can themselves be grouped under a master account-like container.</li>
<li>multiple users can be managed within an account domain and assigned roles that vary for each project.</li>
<li>Identity V3 API supports multiple domains.</li>
<li>Users of different domains may be represented in different authentication back ends </li> and even have different attributes that must be mapped to a single set of roles and privileges, that are used in the policy definitions to access the various service resources. </li>
<a href="https://docs.openstack.org/security-guide/identity/domains.html">More Info about domains</a>

