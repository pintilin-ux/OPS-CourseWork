Inthisweek7idid afocused securityauditontheubuntoheadlessserver.Iused
toolslikelynisand nmap whicharesecuritytools,and alsochecked
thingsmanuallylikesshconfig,ufwrules,fail2ban, apparmor and
logs.Alltheoutputsand screenshotsicollected arestored inafolder called
\$EVID.The mainaim wastoseehowsecurethesystem wasbefore,find openportsor
weaksettings,and thenfix theimportantproblemsthatcould bearisk.

Whenifirstranlynisthehardeningindexwas60whichmeansthesystem
wasmissingsome recommended securitysettings.From thenmap
scanisawthatport22for sshwasopenwhichis expected,butalsoport80for
apachewaslisteningwhichisnotneeded for thisserver.Inthessh
configurationPermitRootLoginwasalreadysettonowhichisgood,but
PasswordAuthentication wasstillenabled whichisnotsecure.UFWwasenabled
butthesshruleswereabittooopen,while fail2banand apparmor
werealreadyrunningonthesystem.

After findingtheseissuesiapplied fixesusingsshonly.Idisabled password
based sshloginand enforced
keyonlyauthentication,keepingrootlogindisabled.Istopped and disabled
apachebecause theserver doesnotneed aweb serviceand thisreduced
theattacksurface.Ialsorestricted sshaccess
inufwsoonlymyworkstationIPisallowed toconnect.After
thisiranlynisagainandthehardeningscore increased
to61whichshowssomeimprovementevenifsmall.Asecond nmapscanconfirmed
thatport 80isnowclosed and onlysshisaccessible.

Ialsochecked therunningservicesand justified whytheyareneeded
suchassshforadministration, loggingservices,fail2banandapparmorfor
security.Anyservicethatwasnotneeded wasremoved.
Therearestillsomeremaininglowriskwarningsfrom lyniswhicharedocumentedand
could be improved later,suchasmoreregular auditsand
logmonitoring.Overallthisauditshowsthatthesystem securitywasimproved
andtheconfigurationismoresuitableforaheadlessserver.

**Service** **inventory(table** **—paste** **this,thenfill)**

> **Service** **name**
>
> sshd
>
> fail2ban
>
> apache2
>
> apparmor
>
> **Role**

Remote administration Brute-force protection

Web server

Mandatory access

control

> **Running?**

running

running

stopped/disabled (after)

running/enforced

> **Justification**

Required;hardened withpubkey authand firewallrestriction

Blocksrepeated SSH attempts

Notrequired for server rolein coursework

Providesprocessconfinement

> **Actionif** **not** **required**

Keep enabled

Disabled

Keep

enabled

NMAP:

Mappingtomarkingcriteria:Thisweek7submissionimplementsallthenecessarysecuritycontrolls
suchas:SSH,KEY AUTHENTICATION,ACCESSCONTROLL viaAppArmor,fail2banand
alsoincluded automated updates,Asecurityauditwascompleted and
remediatedperformancewithLynisimproving from 60to61.Cliusageand
scriptsused for evidencecollectionaredocumented inearlier weeks.

<img src="./0evr0ndk.png" style="width:6.5in;height:3.53125in" /><img src="./5biss1lw.png" style="width:7.5in;height:0.70833in" />Bellow,aretheresultsand
proofofrunningmostofthecommandsnecessary,alsoproofofperformance
improvementsand theservicesthatarerunning.

<img src="./10xsdsla.png" style="width:7.5in;height:2.9375in" /><img src="./fjxzjedq.png" style="width:7.5in;height:2.29167in" />

<img src="./335bhm3f.png" style="width:7.5in;height:3.08333in" /><img src="./ajzpworx.png" style="width:7.5in;height:3.91667in" /><img src="./2ijtmkz5.png" style="width:7.5in;height:0.92708in" />

<img src="./5gkxz1vy.png" style="width:7.5in;height:4.04167in" /><img src="./hcobgpx4.png" style="width:7.5in;height:3.67708in" />

<img src="./ikrc4huh.png" style="width:7.5in;height:5.85417in" /><img src="./mtdqhzey.png"
style="width:7.32292in;height:3.97917in" />

<img src="./jfyvagou.png" style="width:7.5in;height:4.17708in" /><img src="./tlgd1zol.png"
style="width:6.83333in;height:4.57292in" />
