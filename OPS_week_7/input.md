In this week 7 I did a focused security audit on the Ubuntu headless server. I used tools like lynis and nmap which are security tools, and also checked things manually like ssh config, ufw rules, fail2ban, apparmor and logs. All the outputs and screenshots I collected are stored in a folder called $EVID. The main aim was to see how secure the system was before, find open ports or weak settings, and then fix the important problems that could be a risk.

When I first ran lynis the hardening index was 60 which means the system was missing some recommended security settings. From the nmap scan I saw that port 22 for ssh was open which is expected, but also port 80 for apache was listening which is not needed for this server. In the ssh configuration PermitRootLogin was already set to no which is good, but PasswordAuthentication was still enabled which is not secure. UFW was enabled but the ssh rules were a bit too open, while fail2ban and apparmor were already running on the system.

After finding these issues I applied fixes using ssh only. I disabled password based ssh login and enforced key only authentication, keeping root login disabled. I stopped and disabled apache because the server does not need a web service and this reduced the attack surface. I also restricted ssh access in ufw so only my workstation IP is allowed to connect. After this I ran lynis again and the hardening score increased to 61 which shows some improvement even if small. A second nmap scan confirmed that port 80 is now closed and only ssh is accessible.

I also checked the running services and justified why they are needed such as ssh for administration, logging services, fail2ban and apparmor for security. Any service that was not needed was removed. There are still some remaining low risk warnings from lynis which are documented and could be improved later, such as more regular audits and log monitoring. Overall this audit shows that the system security was improved and the configuration is more suitable for a headless server.

**Service inventory (table — paste this, then fill)**

> **Service name**
>
> sshd  
> fail2ban  
> apache2  
> apparmor  

> **Role**
>
> Remote administration  
> Brute-force protection  
> Web server  
> Mandatory access control  

> **Running?**
>
> running  
> running  
> stopped/disabled (after)  
> running/enforced  

> **Justification**
>
> Required; hardened with pubkey auth and firewall restriction  
> Blocks repeated SSH attempts  
> Not required for server role in coursework  
> Provides process confinement  

> **Action if not required**
>
> Keep enabled  
> Disabled  
> Keep enabled  

NMAP:

Mapping to marking criteria: This week 7 submission implements all the necessary security controls such as SSH key authentication, access control via AppArmor, fail2ban and also included automated updates. A security audit was completed and remediated performance with Lynis improving from 60 to 61. CLI usage and scripts used for evidence collection are documented in earlier weeks.

<img src="./0evr0ndk.png" style="width:6.5in;height:3.53125in" />
<img src="./5biss1lw.png" style="width:7.5in;height:0.70833in" />

Bellow are the results and proof of running most of the commands necessary, also proof of performance improvements and the services that are running.

<img src="./10xsdsla.png" style="width:7.5in;height:2.9375in" />
<img src="./fjxzjedq.png" style="width:7.5in;height:2.29167in" />

<img src="./335bhm3f.png" style="width:7.5in;height:3.08333in" />
<img src="./ajzpworx.png" style="width:7.5in;height:3.91667in" />
<img src="./2ijtmkz5.png" style="width:7.5in;height:0.92708in" />

<img src="./5gkxz1vy.png" style="width:7.5in;height:4.04167in" />
<img src="./hcobgpx4.png" style="width:7.5in;height:3.67708in" />

<img src="./ikrc4huh.png" style="width:7.5in;height:5.85417in" />
<img src="./mtdqhzey.png" style="width:7.32292in;height:3.97917in" />

<img src="./jfyvagou.png" style="width:7.5in;height:4.17708in" />
<img src="./tlgd1zol.png" style="width:6.83333in;height:4.57292in" />
