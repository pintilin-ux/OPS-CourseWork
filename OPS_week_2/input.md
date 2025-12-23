**<u>1.Create aperformance testing plandescribing your</u>** **<u>remote
monitoringmethodologyandtestingapproach:</u>**

Firstly,illneed tobeabletodotheperformanceofthecomponentssuchas CPU,
RAM, and more,illneed toseetheir resourceusagewheninidleand whenunder
load. IllbetestingtheCpu,ram,disk,networkand server
performancewithallofthem combined.

<img src="./2sef4vj2.png"
style="width:6.26042in;height:3.90625in" />-Top, isacommand
dodisplaythesystemsresourceusageshowsthingssuchas
CPU,MEMORYandmorethiswillhelp memonitor theperformance
whilstalsotesting.

-sudoaptinstallhtop,installingadifferentmodelofviewing
resources,thisinstallsthe packesfor theapplication.

-Htop,iscolourcoded and youcaninteractwiththedatamorecompared totop
soyou havemoreoptionsandmorepower .

<img src="./hpljkavo.png"
style="width:6.26042in;height:3.95833in" /><img src="./rcd2dldi.png"
style="width:6.26042in;height:0.89583in" />

-Vmstat,reportssystem performancesuchasinputoutpucpu,
thingslikecachebuffer,
howmanyappsarewaitingforcputimeetc,isavitalcommand thatisveryhelpful for
performancetestingand evaluatingpotentialbottlenecks.

<img src="./ekrz5gnn.png" style="width:6.26042in;height:3in" />-Iostat,displaystheresourcesused
byeachindividualused ifitsashared device, showsthereadand
writeofthedisk,thisprimarlyisused tochecktheperformanceof thedisk,hard
drive,ssd or m.2

sudoaptinstalliftop, installsthepackagesfortheapptobeabletorun

<img src="./43fiqenj.png"
style="width:6.26042in;height:0.96875in" /><img src="./gyxu1x1h.png"
style="width:6.26042in;height:2.83333in" /><img src="./41fsenea.png"
style="width:6.26042in;height:1.54167in" /><img src="./3skiux25.png"
style="width:6.26042in;height:1.45833in" />

-Iftop,issupposed toshownetworkperformance,would displaybandwithusageand
more

-Sudoaptinstallnmon,installthepackagesfor theappnmon

-nmon,nmonisvery versatileitcanbeused for manythingitcanmonitor
mostofthe thingsthatalloftheother commandsdid,itsaallinone
withasemisimpleinterface.

-sudoaptinstallstress

<img src="./5ynwhbey.png"
style="width:6.26042in;height:4.13542in" /><img src="./gmtju1xq.png"
style="width:6.26042in;height:2.40625in" />

-sudoaptinstalliperf3

Iperf3,didntgettoworkproperlydidntshowmuch(dontknowhowtouse)

Proofofremotemonitoringaccesability,viaSSH

Command:sudosystemctlstatussshd

Used thiscommand tocheckiftheserver isrunningand
ifIwillbeabletoconnecttoit.

Commnad used:ssh
[<u>vboxuser@192.168.0.170</u>,](mailto:vboxuser@192.168.0.170)used
toconnecttotheSSH server

<img src="./vhqw25cc.png"
style="width:6.26042in;height:3.625in" />

Thisprovesthatthesshserver isup and runningbutalsoproofofbeinglogged
intoit and beingabletoruncommandsasaadministrator.

**<u>Task2</u>**

||
||
||
||
||
||
||

<img src="./e1e03bog.png"
style="width:6.26042in;height:0.76042in" /><img src="./vfdbfyor.png"
style="width:2.22917in;height:0.30208in" /><img src="./jlo5ax4x.png"
style="width:1.30208in;height:0.27083in" /><img src="./qk00jsip.png"
style="width:6.26042in;height:0.66667in" />

||
||
||
||

Disablerootlogging

-sudoaptupdate,updatesthesoftwatrepackges.

-sudoaptinstallopenssh-server–y -sudonano/etc/ssh/sshd_config

changeportfrom22to2222,PermitRootLoginnoandPasswordAuthenticationno,this
isasweareswitchtousingkeysinstead for authentication,thisissafer
asthekeysare encrypted and willstop brutforceattacks.

Firewall,inhereI'veinstalled thefirewallandconfigured
ittodenyallconnectionsthat dontspecificlymatchtheallowed one.
Whichwillbeconnectionfrom specifically

<img src="./aidrn2bk.png"
style="width:6.26042in;height:4.79167in" />port:2222

<img src="./3fmk1zxw.png"
style="width:6.26042in;height:3.72917in" /><img src="./kyaq4u5b.png"
style="width:6.26042in;height:0.76042in" />

NetworkSecurity

Tsk3

1)BrutoforceSSH attacks

Theresmultiplewaythatpeoplegainunauthorised accesstosystem
thattheyshould nothaveaccessto,itsimportanttoknowhowtheydoitand
whatwecandotoprevent itfromhappening.

OneverycommonattackisBrute-ForceSSH Attacks:
Thisusuallyhappenswhenrepeated attemptstoguessSSH password
usingautomated
botstotryandguessthepassword,theyhavealgorithmswithmostcommonpassword
tomakeitmoreefficient.

ThisisverybigastheycangetUnauthorized remoteaccesswhichleadstodatatheft,
deletionor changeor changeofdata,makingdata unusable.

Howtoprotectyourselffromjustattacks: \* Disablepassword authentication

\*Changedefaultport,toreducebotscanningfor ports \*Enablefirewall(ufw)
tolimitportsallowed,and controllthenetworkactivity

\*Usingencrypted keysalsomakeitmuchharder almostimposiblefor thistowork
anymore

Thiswilllimittheattacker asitwillmakeitharder tofind theportbutalsospam
passwords.

2)PrivilegeEscalation

Another threattomany systemsthathavemanyusersisprivilegeescalation,user
accountattempttogetunauthorised administrativeaccess
bytakingadvantageofthe accessrightsthattheyhave.

Iftheymanageto,theywillhavefull control ofthesystem,and
willbeabletoaccess datadeletedownload,mightevenopenbackdoorsor
installmalware.

Howtopreventthisfrom happening:

Bydisableoftherootlogin,alsotheruleofleasprivilegeprincipleonlyallowusersto
accesswhattheyneed,alsoinstallingapparmorto restrictapplication
behaviour, meaninggivinguser theleastamountof privilegesthattheyneed
tohaveaccess,this makessurethattheused don'thaveaccessanythingthatthey
shouldn't.

3)DenialofServiceDOS

Thishappensbyattackersfloodingthenetworkwith
loadingmaterialssuchasloading
theCPU,memory,diskcausingtheperformancetogodownor evenstop.

Thisleadstosystem slowdownor
evencompletefailureduetooverload,interruptionof accesstothesystem and
intheworstcasescenariohardwaredamagebutunlikely.

Howtostop thesetypesofattacks:

Byenablingthefirewalltopreventspamofunwanted traffic/suspicious.

Usingperformancemonitorstoolstocheckifanythinglooksodd
Automaticupdatespreventold system beingattacked from older
softwarethathas exploitstogetunathorised access

Apparmor tolimitresoursemisuse

Thesestepswillmakethesystem morestableand willmakeitharder for
Dosattacksto

occur.
