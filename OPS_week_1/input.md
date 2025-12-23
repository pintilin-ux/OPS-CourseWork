> Task 1:
>
> 1. Create a System Architecture Diagram showing both systems and network
> connections
>
> The system architecture consists of two different virtual machines and
> also a host on Windows 11, using Oracle VirtualBox. An Ubuntu Server
> virtual machine is deployed as a server, while a separate workstation
> system is used for administration.
>
> <img src="./oqgrsql4.png" style="width:6.5in;height:5.82292in" />
>
> Network connectivity is provided through VirtualBox networking, with NAT
> enabled and a host-only network to help with secure SSH-based management
> between systems.
>
> Task 2 and 3:
>
> As my main distribution for the virtual machine, I have chosen Ubuntu.
>
> Ubuntu is very stable and is supported constantly with updates. Ubuntu
> provides 5 years of security and maintenance updates, which reduces the
> overall risk of the system being penetrated, as it is more secure and
> easier to maintain.
>
> Ubuntu also has a strong amount of packages which offer various features
> that help with the user experience, as they help track system
> performance but also enhance security. Some of these are: OpenSSH Server,
> UFW, Fail2Ban, sysstat, iperf3, fio.
>
> Ubuntu security: Ubuntu has packages such as AppArmor, which includes
> mandatory access control, and also has features like unattended upgrades
> for automatic security patches, to prevent old software being attacked.
>
> As my second VM instance, I chose Linux Mint.
>
> Linux Mint is robust and user friendly, quite simple to use and not too
> complex for beginners. The GUI is a massive advantage, making it easier
> to navigate. It also maintains stability and has features like Cinnamon
> that make the client system more efficient by minimizing time spent on
> configuring.
>
> Overall, it is very good, as it is user friendly, stable, and reliable to
> use as the second instance.
>
> Ubuntu Server was chosen as the primary system due to its long-term
> support model that helps guarantee five years of stability and security
> updates, making the operational risks smaller during the working time.
> It uses the command line for all server administration and performance
> testing. In contrast, Linux Mint was selected for the workstation VM as
> it is efficient, user friendly, and has a GUI. This stability and ease
> of use simplify the client-side administrative tasks and documentation,
> while maintaining a reliable environment for accessing the server for
> essential command-line tools.
>
> ||
> ||
> ||
>

Advantages 

Ubuntu -Long-term stability , extensive community support, simple package management . 

Linux Mint -Very user-friendly desktop environment , easy to install, stable Debian/Ubuntu base. 


Disadvantages 

Ubuntu -Slightly larger install .

Linux Mint -Very user-friendly desktop environment , easy to install, stable Debian/Ubuntu base. 

Not a server focused distribution. 


> ||
> ||
> ||
>
> Ubuntu is highly known for beginners as it has a friendly interface and
> is stable. It makes it easy to install through the terminal, it is very
> secure, and it is constantly being supported with updates. Being a
> monolithic kernel, it is high in performance as everything runs directly
> in the kernel.
>
> I chose Ubuntu over others like Linux Mint, as it has more support in
> updates, stronger community resources, and better security, making it
> better for the average user and easier for beginners.
>
> Task 4: Settings
>
> In this picture, we can see some basic system information that the VM has
> access to. This is based on how much I gave the system in the initial
> setup. I gave 6 GB of RAM (5973 MB), 6 processor cores, and for storage
> I gave it 60 GB. Most of these are probably more than it needed to run,
> but I chose to give it this much
>
> <img src="./zgj0zuqv.png" style="width:3.27083in;height:2.63542in" />
> 
> <img src="./3rlc3kfx.png" style="width:5.625in;height:1.30208in" />
> 
> <img src="./vwesyzih.png" style="width:6in;height:1.05208in" />
>
> to make sure I don't have any performance issues.
>
> I'm using a Bridged adapter as my network adapter. This uses the same IP
> as my actual router and gives the VM access to the internet, also needed
> later on for the operation of SSH.
>
> Using a command in the VM (ip a), I have been able to check the IP that I
> have on the VM. This command also shows and gives other important
> information about the system.
>
> IP ADDRESS: 192.168.0.170/24
>
> <img src="./hyje0ncv.png" style="width:6in;height:3.42708in" />
>
> Task 5: running commands and showing results
>
> Command: uname
>
> This command shows the name of the operating system kernel.
>
> Command: free
>
> This command displays the free and used physical memory. This checks
> performance and resource allocation of the Ubuntu Server.
>
> Command: df -h
>
> This shows the state of the disk, such as disk space used and the amount
> available on the Ubuntu Server.
>
> <img src="./d1xsjmiq.png" style="width:6.5in;height:2.11458in" />
>
> <img src="./ahoqfjqb.png" style="width:6in;height:3.11458in" />
