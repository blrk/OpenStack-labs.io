How to acess CSE-KITS OpenStack Cloud
---------------------------------
<b>There are two ways to acess http://cloud.csekits.edu/</b>
<li>Access using GUI(Dahboard-Horizon)</li>
<li>Access using command line interface(CLI)</li>
<li style="color: #008000">Note: Don't use the url that is not registered in the KITS dns server</li>

Access using GUI(Dahboard-Horizon)
-----------------------------------
<li>Open the browser and type the URL > http://192.168.83.191 > press enter</li>
<li>You will see the following login screen</li>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/cloud.csekits.edu/img/Screenshot_2019-09-18_09-33-55.png"></img>
<li>Enter the domain name as > Faculty, user name (employee id) > ex 1738, password > type your password, then click sign in</li>
<img src="https://github.com/blrk/OpenStack-labs.io/blob/master/cloud.csekits.edu/img/Screenshot_2019-09-18_09-34-44.png"></img>
<li>After succcessful login the dahboard will be loaded</li>

Access using command line interface(CLI)
------------------------------------------
<li><b>For windows Users</b></li>
<li>Download putty from this link</li> 
<div align="right">
<a href="http://ctc.karunya.edu/node/3">Download Putty here</a>
</div>
<li>Log into code.karunya.edu > provide your credentials to login</li>
<li>After login use the following commands</li>
<pre>
[1738@code ~]$ ssh 1738@192.168.83.191
The authenticity of host '192.168.83.191 (192.168.83.191)' can't be established.
ECDSA key fingerprint is ba:8a:90:41:6e:4a:d0:dc:c0:67:e8:af:97:38:d0:80.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.83.191' (ECDSA) to the list of known hosts.
1738@192.168.83.191's password: 
1738@OpenStack:~$ 
</pre>

<li><b>For Linux Users</b></li>
<pre>
blrk@rk-lpc:~> ssh 1738@code.karunya.edu
                               code.karunya.edu

************************************NOTICE**************************************

This is a private computer system which is restricted to the students, faculty 
and staff of Karunya University. Actual or attempted unauthorized use of this 
computer system will result in criminal and/or civil prosecution.

We reserve the right to view, monitor and record activity on the system without
notice or permission. Any information obtained by monitoring, reviewing or 
recording is subject to review by law enforcement organizations in connection 
with the investigation or prosecution of possible criminal activity on this 
system.

Anyone using this system consents to the terms, morals, ethics and the laws of 
the Country and Karunya University.

If you wish to continue, please login.

************************************NOTICE**************************************

INFO: This server's console is also available over HTTP. 
Please visit http://code.karunya.edu/ from the latest Google Chrome Browser.

DON'T FORGET TO LOGOUT AFTER YOUR WORK.

Seraph Password: 
Last login: Fri Sep 20 10:44:03 2019 from 192.168.83.193
[1738@code ~]$ ssh tux@192.168.83.191
tux@192.168.83.191's password: 
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-62-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

59 packages can be updated.
36 updates are security updates.

New release '18.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Fri Sep 20 01:16:26 2019 from 192.168.2.88
tux@OpenStack:~$ 
</pre>

<li>Enjoy using OpenStack!!!!!</li><br><br>

<i>Managed by <br>
Novell Center of Excellecne for Cloud Computing, CSE III Floor, KITS</i>

