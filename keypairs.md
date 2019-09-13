What are Key Pairs?
-----------------------------------------------
<li>Combination of SSH Public/Private keys </li>
<li>Public key can be injected into instances when instantiated (must be stored in OpenStack Environment) </li>
<li>It allows root SSH access to instances as root (Note : root password is usually disabled) </li>
<li>key pairs can be generated in OpenStack</li>
<li>available existing keys can be uploaded </li>

Key Pair Managment Commands
-----------------------------------------
Syntax: openstack keypair MODE OPTIONS

<li>create -generate a new keypair </li>
<li>create --pubkey PUBKEY -import an existing public key</li>
<li>delete -delete a new keypair </li>
<li>list -display existing keypairs </li>
<li>show KEYPAIR -display details about a keypair </li>

Generate a Key Pair with the Dashboard
-----------------------------------------------
<li> Select --> Project --> click on Keypairs and Press the button --> Create key pair</li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot%20from%202019-09-13%2009-36-09.png'>
<li>Then the Folowing window appreas provide necessary values as shown </li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-13_09-54-47.png'>
<li> After providing the necessary values click the +Create Key Pair button </li>
<li>Then a key will be downloaded automatically save the key and keep it safe </li>
<li> if the key generation is sucessfull you will be able see it on the dashboard </li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-13_10-03-13.png'>
