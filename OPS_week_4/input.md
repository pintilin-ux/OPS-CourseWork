**Week** **4—Remote** **Administration&** **Security(Tasks1–7)**

**Server:**UbuntuVM(headless)—192.168.0.170

**Workstation:**Windows10/11(PowerShell)

**Objective:**Deploytheserverandimplement foundationalsecuritycontrols.
Document allworkperformed**overSSH**fromtheworkstation, provide
before/afterconfigurationcomparisons, capturescreenshots ofsuccessful
SSHsessionsandcommands, andproduceaclearevidencebundleforthe
recordeddemonstration.

**Summaryof** **tasks** **completed**

> 1\. ConfigureSSHwith key-basedauthentication
>
> 2\. ConfigureUFW firewallpermitting SSHfromonespecificworkstation only
>
> 3\. Createanon-root administrativeuserandconfiguresudoprivileges 4.
> SSHAccessEvidence(screenshots + commandoutputs)
>
> 5\. ConfigurationFileswith before/aftercomparisons
> (/etc/ssh/sshd_config, ufwrules)
>
> 6\. FirewallDocumentationshowing completeruleset
>
> 7\. RemoteAdministrationEvidencedemonstrating commandsexecuted viaSSH

Task1–Sshkeybased authentication

Inthistaskwillreplacepassword
authenticationwithpublickeyauthenticationfor remote login.

Ssh-keygen–ted25519 –[c
<u>pintilii.narcis7@gmail.com,</u>](mailto:pintilii.narcis7@gmail.com)commandtocreatekeypair
onthe shellworkstation

<img src="./xs2neq4g.png" style="width:6.5in;height:4.02083in" /><img src="./zbkezm4m.png" style="width:6.5in;height:3.77083in" />

Ssh-keygencreatesapulic/privatekeypair thepublicisinstalled in
~/.ssh/authorised_keysontheserver

chmod commandsenforcesecurepermissionsonthekeysdirectoryand file

<img src="./sfmofhxb.png" style="width:6.5in;height:3.45833in" />

1-------------------------

Task2–Firewall:allowSSH onlyfrom workstation

InthistaskIwillmakethefirewalltoallowsshfrom onetrusted admin.

Inthescreenshoticonnected tothesshserver from shell

Disabled passwordauthenticationrootloginno,and pukeyautheticationyes

Ialsoeddited /etc/ssh/sshd_configand disabled
botPasswordaAuthenticationand PermitRotLoginand ensured
PubKeysAuthenticationisenabled,thenrestarted theserver

s

<img src="./xfmm4lvf.png" style="width:6.5in;height:3.57292in" /><img src="./fosvdodi.png" style="width:6.5in;height:2.89583in" />

InthenextscreenshotIallowed a specificIpwitha specificportand added
ittothefirewall toallowremotelogin,alsoused
sudoufwenable,toenablethefirewall

alsochecked itsstatuswith,sudoufwstatusnumbered.

Task3-User managementandprivialeges Thegoalofthistaskwastocreateanewuser
adminuser,andgivehimsomeprivialge management,

<img src="./ekxnk50y.png" style="width:6.5in;height:2.46875in" />

Commands: sudoadduser adminuser

Sudousermod –aG sudoadminuser getentpasswdadminuser

Adduser creatsanewaccount and usermod–agsudoaddstheuser tothesudogroup
for adminprivileges

Task4connected tothenewadminuser thatwascreated inthetaskabove

<img src="./f45li0ls.png" style="width:6.5in;height:5.89583in" /><img src="./v0m4z5un.png" style="width:6.5in;height:0.95833in" />

task5–configurefiles:before&after

Beforeand after saved filesofthe/etc/ssh/sshd_config

task6–Firewalldocumentation

Commands:

Sudoufwstatusverbose
Theufwverboseoutputs,labeleachruleanddescribeswhatitsfor

<img src="./tjpxje3d.png" style="width:6.5in;height:2.86458in" />

<img src="./jsom1jii.png" style="width:6.08333in;height:6.5in" />
