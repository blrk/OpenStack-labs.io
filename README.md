# OpenStack-labs.io
What are Key Pairs?
-----------------------------------------------
<li>Combination of SSH Public/Private keys </li>
<li>Public key can be injected into instances when instantiated (must be stored in OpenStack Environment) </li>

It allows root SSH access to instances as root (Note : root password is usually disabled)
key pairs can be generated in OpenStack
available existing keys can be uploaded 

Key Pair Managment Commands
-----------------------------------------
Syntax: openstack keypair MODE OPTIONS

create -generate a new keypair
create --pubkey PUBKEY -import an existing public key
delete -delete a new keypair
list -display existing keypairs
show KEYPAIR -display details about a keypair

Generate a Key Pair with the Dashboard
