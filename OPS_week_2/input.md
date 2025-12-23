<u>1. Create a performance testing plan describing your</u> <u>remote monitoring methodology and testing approach:</u>

Firstly, ill need to be able to do the performance of the components such as CPU, RAM, and more, ill need to see their resource usage when in idle and when under load. Ill be testing the Cpu, ram, disk, network and server performance with all of them combined.

<img src="./2sef4vj2.png" style="width:6.26042in;height:3.90625in" /> - Top, is a command do display the systems resource usage shows things such as CPU, MEMORY and more this will help me monitor the performance whilst also testing.

sudo apt install htop, installing a different model of viewing resources, this installs the packes for the application.

Htop, is colour coded and you can interact with the data more compared to top so you have more options and more power .

<img src="./hpljkavo.png" style="width:6.26042in;height:3.95833in" /><img src="./rcd2dldi.png" style="width:6.26042in;height:0.89583in" />

Vmstat, reports system performance such as input output cpu, things like cache buffer, how many apps are waiting for cpu time etc, is a vital command that is very helpful for performance testing and evaluating potential bottlenecks.

<img src="./ekrz5gnn.png" style="width:6.26042in;height:3in" /> - Iostat, displays the resources used by each individual used if its a shared device, shows the read and write of the disk, this primarly is used to check the performance of the disk, hard drive, ssd or m.2

sudo apt install iftop, installs the packages for the app to be able to run

<img src="./43fiqenj.png" style="width:6.26042in;height:0.96875in" /><img src="./gyxu1x1h.png" style="width:6.26042in;height:2.83333in" /><img src="./41fsenea.png" style="width:6.26042in;height:1.54167in" /><img src="./3skiux25.png" style="width:6.26042in;height:1.45833in" />

Iftop, is supposed to show network performance, would display bandwith usage and more

Sudo apt install nmon, install the packages for the app nmon

nmon, nmon is very versatile it can be used for many thing it can monitor most of the things that all of the other commands did, its a all in one with a semi simple interface.

sudo apt install stress

<img src="./5ynwhbey.png" style="width:6.26042in;height:4.13542in" /><img src="./gmtju1xq.png" style="width:6.26042in;height:2.40625in" />

sudo apt install iperf3

Iperf3, didnt get to work properly didnt show much (dont know how to use)

Proof of remote monitoring accesability, via SSH

Command: sudo systemctl status sshd

Used this command to check if the server is running and if I will be able to connect to it.

Command used: ssh <u>vboxuser@192.168.0.170</u>,
 used to connect to the SSH server

<img src="./vhqw25cc.png" style="width:6.26042in;height:3.625in" />

This proves that the ssh server is up and running but also proof of being logged into it and being able to run commands as a administrator.

<u>Task2</u>

||
||
||
||
||
||
||

<img src="./e1e03bog.png" style="width:6.26042in;height:0.76042in" /><img src="./vfdbfyor.png" style="width:2.22917in;height:0.30208in" /><img src="./jlo5ax4x.png" style="width:1.30208in;height:0.27083in" /><img src="./qk00jsip.png" style="width:6.26042in;height:0.66667in" />

||
||
||
||

Disable root logging

sudo apt update, updates the softwatre packges.

sudo apt install openssh-server –y - sudo nano /etc/ssh/sshd_config

change port from 22 to 2222, PermitRootLogin no and PasswordAuthentication no, this is a sweare switch to using keys instead for authentication, this is safer as the keys are encrypted and will stop brutforce attacks.

Firewall, in here I've installed the firewall and configured it to deny all connections that dont specificly match the allowed one. Which will be connection from specifically

<img src="./aidrn2bk.png" style="width:6.26042in;height:4.79167in" />port:2222

<img src="./3fmk1zxw.png" style="width:6.26042in;height:3.72917in" /><img src="./kyaq4u5b.png" style="width:6.26042in;height:0.76042in" />

Network Security

Tsk3

Brute force SSH attacks

There s multiple way that people gain unauthorised access to system that they should not have access to, its important to know how they do it and what we can do to prevent it from happening.

One very common attack is Brute-Force SSH Attacks: This usually happens when repeated attempts to guess SSH password using automated bots to try and guess the password, they have algorithms with most common password to make it more efficient.

This is very big as they can get Unauthorized remote access which leads to data theft, deletion or change or change of data, making data unusable.

How to protect yourself from just attacks: * Disable password authentication

* Change default port, to reduce bots scanning for ports * Enable firewall (ufw) to limit ports allowed, and controll the network activity

* Using encrypted keys also make it much harder almost imposible for this to work anymore

This will limit the attacker as it will make it harder to find the port but also spam passwords.

Privilege Escalation

Another threat to many systems that have many users is privilege escalation, user account attempt to get unauthorised administrative access by taking advantage of the access rights that they have.

If they manage to, they will have full control of the system, and will be able to access data deleted download, might even open backdoors or install malware.

How to prevent this from happening:

By disable of the root login, also the rule of least privilege principle only allows users to access what they need, also installing apparm or to restrict application behaviour, meaning giving user the least amount of privileges that they need to have access, this makes sure that the used don't have access anything that they shouldn't.

Denial of Service DOS

This happens by attackers flooding the network with loading materials such as loading the CPU, memory, disk causing the performance to go down or even stop.

This leads to system slowdown or even complete failure due to overload, interruption of access to the system and in the worst case scenario hardware damage but unlikely.

How to stop these types of attacks:

By enabling the firewall to prevent spam of unwanted traffic / suspicious.

Using performance monitor tools to check if anything looks odd Automatic updates prevent old system being attacked from older software that has exploits to get unauthorised access

Apparmor to limit resource misuse

These steps will make the system more stable and will make it harder for Dos attacks to occur.
