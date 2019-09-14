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

Openstack Keypair commands
---------------------------------
<pre>
  keypair create
  keypair delete
  keypair list
  keypair show
</pre>

How to list the keypairs
-------------------------------
<pre>
tux@OpenStack:~$ openstack keypair list
+------------+-------------------------------------------------+
| Name       | Fingerprint                                     |
+------------+-------------------------------------------------+
| gaming1738 | b4:d6:5a:59:3c:66:d2:57:47:1e:da:f9:21:24:4d:d3 |
+------------+-------------------------------------------------+
</pre>

Create 2 keys (RSA and DSA) in the terminal
<pre>
tux@OpenStack:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/tux/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/tux/.ssh/id_rsa.
Your public key has been saved in /home/tux/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:IBmMPLPHW3VmaLGoDFdhEImWqpl6vbLl7GWnX4PfTPk tux@OpenStack
The key's randomart image is:
+---[RSA 2048]----+
| . =+++..o       |
|  O o= .+.+      |
| o.=+ oo.+       |
|. .+oo..         |
|.o .oo  S        |
|+   .    .   .   |
|.  .. o o o o    |
|. o+.o o o = .   |
| ..+=.... . o E  |
+----[SHA256]-----+
tux@OpenStack:~$ ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/home/tux/.ssh/id_dsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/tux/.ssh/id_dsa.
Your public key has been saved in /home/tux/.ssh/id_dsa.pub.
The key fingerprint is:
SHA256:Hdq8WvMpeyBMmKyI1rX+1e2Om3uuLUcG5/PevLY28qU tux@OpenStack
The key's randomart image is:
+---[DSA 1024]----+
|                 |
|                 |
|     . o  .      |
|     .+ .= o .   |
| ......oS + +    |
|......  o o..=   |
|.   .    o+oo.o .|
|     .  .o.+*= Bo|
|      ... .X%=E=*|
+----[SHA256]-----+
tux@OpenStack:~$ ls .ssh/
id_dsa  id_dsa.pub  id_rsa  id_rsa.pub  known_hosts
</pre>

import keypair 
------------------
<li>In the OPenStack dashboard select Project --> Compute --> Keypairs then clic on the +Import Public Key button</li>
Run the following command in the terminal to get the keypair
------------------------------------------------------------
<pre>
  tux@OpenStack:~$ cat .ssh/id_rsa.pub
</pre>
<li> copy the key (select the output --> right click and copy) </li>
<img src='https://github.com/blrk/OpenStack-labs.io/blob/master/Screenshot_2019-09-14_16-02-28.png'>
<li> After pasting the key click the button Import public key</li>
