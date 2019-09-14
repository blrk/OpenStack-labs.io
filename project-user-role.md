Manage projects, users, and roles
--------------------------------------
<li>As an administrator, you manage projects, users, and roles. </li>
<li>Projects are organizational units in the cloud to which you can assign users.</li>
<li>Projects are also known as projects or accounts. 
<li>Users can be members of one or more projects.</li>
<li>Roles define which actions users can perform.</li>
<li>You assign roles to user-project pairs.</li>

<li>You can define actions for OpenStack service roles in the /etc/PROJECT/policy.json files.</li>
<li>For example, define actions for Compute service roles in the /etc/nova/policy.json file.</li>

<li>You can manage projects, users, and roles independently from each other.</li>

<li>During cloud set up, the operator defines at least one project, user, and role.</li>
<ul>
<b>What you can do?</b>
<li>You can add, update, and delete projects and users</li> 
<li>assign users to one or more projects</li>
<li>and change or remove the assignment.</li>
<li>enable or temporarily disable a project or user, update that project or user.</li>
<li>You can also change quotas at the project level.</li>
</ul>
<ul>
<b>Want to delete an user account</b>
  <li>Before you can delete a user account, you must remove the user account from its primary project.</li>
</uL>
<a href="https://docs.openstack.org/keystone/pike/admin/cli-manage-projects-users-and-roles.html">More about project visit this link</a>

Working with Projects
--------------------------
List projects
-------------
<pre>
openstack project list
</pre>
Create a project
-------------------
<pre>
openstack project create --description 'application development' --domain Faculty app-development
</pre>
Update a project
----------------
<b>Diable a project</b>
<pre>
openstack project set PROJECT_ID --disable
</pre>
<b>Enable a Project</b>
<pre>
openstack project set PROJECT_ID --enable
</pre>
<b>update the name of a project</b>
<pre>
openstack project set PROJECT_ID --name project-new
</pre>
<b>View project details</b>
<pre>
openstack project show PROJECT_ID
</pre>
<b>Delete a project</b>
<pre>
openstack project delete PROJECT_ID
</pre>
Users Management
-------------------------
<b>List users</b>
<pre>
openstack user list
</pre>

<b>Create a user</b>
<pre>
openstack user create \
--email app-admin@karunya.edu \
--password-prompt \
--project app-development \
--domain Faculty \
app-admin
</pre>
