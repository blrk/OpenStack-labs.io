Define Flavors
---------------------
<b>Perform Using GUI</b>
<li>Admin > Compute > Flavours </li>
<li>Create Falore </li>

<b>Perform Using CLI</b>
<pre>
openstack flavor create \
-- id 6 \
--ram 512 \
--disk 5 \
--vcpus 1 \
--public \
m1.smaller
</pre>

<li>display the current list of flavors</li>
<pre>
openstack flavor list
</pre>

Create flavour for your project
----------------------------------
<pre>
openstack flavor create \
--id 7 \
--ram 512 \
--disk 5 \
--vcpus 1 \
--private \
gaming-1738.smaller
</pre>

<pre>
openstack flavor set \
--project gaming1738 \
gaming-1738.smaller
</pre>

<li>display all the flavours</li>
<pre>
openstack flavour list --all
</pre>

