Task1:AppArmorConfigand testing

Objects

ToenableAppArmor,verifyitisrunningandtesthowitlogssecurityeventsbeforeand
after exectuing.

For thistaskIhaveimplemented
afewnewfeatures,whichareMandatoryaccesscontroland thisis
usingapparmor,thishelp mesetrulesfor differentpeopleand
role,whichreducetheir abilitiesto accessthingsoutsidetheir
jobrole(accessto onlywhatyouneed) ,thishelpsreduceattacks.

Imadesureinthelinesbellowthat AppArmorwasinstalled and
activatedinontheUbuntoVM Looked atthelistofactivesecuritymodules

Checked ifapparmor wasrunning

-sudoaptupdate

-sudoaptinstall-yapparmor apparmor-utils

-sudoaptinstall–y auditspd-plugins

Thesegiveacesstocomandslikeapparmor-utils,aa-status,aa-enforce,aa-complain,aa-logprofand
auditd andausearch

Sudosystemctlenable–nowapparmor

Sudosystemctlstatusapparmor –no-pager

<img src="./2nwclcbc.png" style="width:6.5in;height:1.69792in" />Sudoaa-status–thisshowsthenumber
ofloaded profiles,and howmanyprograrm areinenforceor complain and
listsprofiles.

Sudoapparmor_status

Ls–letc/apparmor.d\| sed 0n‘1,200p’

Sudoaa-status\| sed –n‘/profilesareinenforcemode/,\$p’ \|\| true

<img src="./truoemsn.png" style="width:6.5in;height:3.47917in" /><img src="./blfendqs.png" style="width:7.5in;height:3.63542in" /><img src="./o4dlej4s.png" style="width:7.5in;height:0.3125in" />

sudojournalctl-k --since"1hour ago"\| grep -iapparmor
\|sudotee/tmp/apparmor_journal_recent.txt

sudogrep -iapparmor /var/log/syslog\|
tail-n50\>/tmp/apparmor_syslog_tail.txt

Sudoaa-complain/etc/apparmor.d/usr.sbin.apache2 sudoaa-statuts\|grep
–iapache–n\|\|true

Toensurethesystem
wasactuallyenforcingsecuritypolicies.Byusingthecommandsudoaa-status.
Thisconfirmed that57 profileswerein“enforcemode,”meaningAppArmor
isblockingrested actions

notonlyjustloggingthem.Thenwith“journalact”ilooked attheauditlogsand
also grep tomakesure thatAppArmorwasstartedcorrectlyand
logsalltheevents.Thisshowsthatthekerneliscorrectly
trackingapplicationbehaviorandisready.

Confirmsmodechange

I observedthat:

Apparmor wasactiveand thatitwasloadingprofiles

Logsshowed status:profileloadmessagesmeaningthat Apparmorwasworking
Thetestwascompleted andapparmor functionalitywasverified
evenwithoutblocked events.

Task2:

Tomakesurethattheserver
remainssecureagainstnewpossiblevulnerabilitieswithoutrequiring
constantmanualinterventionIhaveactivatedautomaticsecurityupdates,Iinstalled
unattended upgradesandsetitupwithdpkgreconfiguretodownload
andinstallcriticalsecurityupadtes,thisisvital
tomakesureanynewthreadsarebeingcaught.

Iverified
theconfigureationbychekingthe20autoupgradesfiles,whichconfirmedthattheupdatelist
and
theupgradesaresettostartbythemselves.Thenlastlyichecksthelogfiletomakesuretheservice
wasworking.Thissetup makessuretheserver staysup
todateagainstthenewsttypeofthreats,even whennotlogged in,updatesmanualy.

Objective:

Toenableautomaticsystem sothemachinesstayssecure.

sudoaptupdate

Sudoaptinstallunattended-upgrades–y

sudodpkg-reconfigure–priority-lowunattended-upgrade

Observation:atutomaticupdatessuccessfullyenabled.Theconfigurationfileconfirmed

<img src="./0yfrkgfk.png" style="width:7.5in;height:0.98958in" /><img src="./2aufabl1.png" style="width:7.5in;height:3.35417in" />

Sudotail –n30 /var/log/unattended-upgrades/unattended-upgrades.log

Task3:Confgurefail2ban

InthistaskIinstalled and configured Fail2BantoprotecttheSSH
connectionfrom beingattacked from
thingslikebruteforce.Fail2Banworksbyscanninglogfilesfor repeated failed
loginattemptsand updatingthefirewalltobaniftherestoomanyfailed
attempsfromaspecificip,thentheip isbanned to preventthem from
continuiongtheattack.

After installingit,imadesuretheserver
isrunningwith“systemctlstatusfail2ban”.Theniused
“fail2ban-cleintstatussshd ”tocheck SSH connectionand itsjail.Thisshowed
methatthefilter is workingand lookingfor pottentialattacks.Thisisanother
layer ofsecuritythathelpstheover system to makesureitremainsprotected
againsautomaticblockingbotsor attackerstryingtoguesspasswords.

Objective,Installand configureFAIL2BAN ontheserver toprotectSSH
againstbrute-forceattacks.
BellowtherespicturewithsomeofthethingsI'vedonetodothis.

Sudoaptinstallfail2ban -installsthepackagesnecessarytorun fail2ban

sudosystemctlrestartfail2ban

Sudosystemctlstatusfail2ban<img src="./iapbcgay.png"
style="width:7.0625in;height:2.88542in" />

Sudofail2ban-clientstatussshd

ThesearethecommandsI'veused togetfail2baninstalled alsoadded
somethingsintothelocalfileof
Fail2bantomakeitmoresecure,inthescreenshotbelowyoull
beabletoseethatFAIL2BAN isup and running.

Task4:Security

Manualsecuritycheckscanbedonebyhumansbutcanhaveerrors,sobycreatingascript,toautomate
theverificationoftheserverssecurity.Thisscriptwill
checkthestatusofthemainserveiceand checks thatSSH
isactive,checksthefirewallisworkingtoolastlychecksfail2banisrunningtoo.

Thiswayitmakessurethateverytimethescriptisbeingrun,allourlevelsofsecurityarebingchecked
to
makesuretheyareactiveandrunning.Ifanyservicesfailthisscripwouldimmediatlyshowthemissing
securitycontrolallowingfor quickcomeback,thishelpsreducehumanerror
alsomakesitmuchquicker and
moreefficientbytypingrunningonesinglescriptyoucanfindoutalotofinformation.

Icreated ascriptthatiscalled securitybaseline.sh.

Imadethescriptexecutableand alsoexecuteditviaSSH tovalidatethemyserver
securitybaseline

<img src="./tfakcjvo.png" style="width:7.5in;height:6.17708in" /><img src="./qv4suv1p.png" style="width:7.5in;height:3.13542in" />

Task5:RemoteMonitoringScript<img src="./q4iqd3ur.png" style="width:7.5in;height:3.5625in" />

Toenableremoteadminwithoutneedingdirectconsoleaccess.Imadeascript
utilizesSSH toconnect totheUbuntuserver,executed
performancecommandslikeCPU,memoryand diskspace and savesthe
outputtoalocallogfile.

Thiswayitallowsmeto createasnapshotoftheserver healthover
time.ByrunningthescrpitIgather metricsintimeand logged inusersand
resourceconsumption,showingthaticanmonitorthe server
performancesecurelyfrom aremotelocation.

Objective:Wastocreateand runascriptform mylaptopthatconnectstothe
ubuntusever withthessh and collectsperformancemetricsremotely

Script,thescriptmonitorstheseversperformance,itsnamed
monitor-server.sh,thescriptconnectsto theserver usingSSH and
gatherssystem performanceinformationsuchas:

Cpuload

Memoryusage

Diskusage

System uptime

Logged-inusers

Command used tocreatescript:nano~/monitor-server.sh

Command used tomakethescriptexecutable:chmod +x ~/monitor-server.sh

Iexecuted thefiletoconnectremotelyand collectmetrics

<img src="./mnyot3u0.png" style="width:7.5in;height:0.41667in" /><img src="./e1x02ral.png" style="width:7.5in;height:0.72917in" />

Verificationoflogfilea

ThistaskDemonstratedsuccessfulremotemonitoringusingsshfrom
mylaptop.Thescriptwas collected and stored system performancemetricsfrom
theserver,verifyingsecureremote administrationandmonitoringabilities.
