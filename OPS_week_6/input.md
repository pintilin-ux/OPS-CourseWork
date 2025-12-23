CpuandMemorytestingperformance:<img src="./p42ctkaa.png" style="width:6.5in;height:0.60417in" /><img src="./ffbzmfxu.png" style="width:7.5in;height:4.6875in" />

BaseLineCpuand Memoryusagewhiletheserver isidle Cpu=%2.6

Memory=%6.6

ThisistheCpuand Memoryusagewhilethecpuisunder
stresstest,thishasbeendoneusing :stress– cpu2 –timeout60

Cpu=%99.7

Memory=%6.7

<img src="./qm5o0eav.png" style="width:6.5in;height:0.72917in" />Memory
Stresstestusingcommand :stress –vm 1–vm-bytes4G
–timeout60,thisloads4Gygabitesofdataon theRamand stressesbothcpuand ram
for 60seconds

<img src="./fqw3q10l.png" style="width:6.5in;height:0.9375in" />

NetworkPerformanceTesting

Objective,istomeasurethebaselinelatencyandthroughputthenmeasurethrouhputunder
load.

Used iperf3tomonitorserver performance.

Ping192.168.0.170 -n10:

<img src="./lndaww0p.png" style="width:6.5in;height:4.21875in" />Used
thistogetbasevaluesofthenetworkand howfastweretrieved
thedatausingping,whenthe server wasntunder load
wecanseethatthedataloaded fast.

<img src="./3ojdwhwl.png" style="width:6.5in;height:4.14583in" />

Results:

Iperf3measure26Gibts/secandalso30.3transfer over 10sasshownintherun.

Interpretation,highThroughputindicatesacapablenetworkpathonthehost,asitsbridgeadaptor
thati useonthevm,ifthroughputfallsunder other loadswecanconsider
bottleneckstoCPUorvirtualization overhead.

Analysisand findings,Baselinemeasurementsshowstheserver isunder
lightloadsatrest,lowcpuand memoryusage,Under aworkload (stress--cpu2)
Cpuusagereached near fullutilisationascoreand responsetimeincreased
accordingly.Memorywastested (--vm) showed memoryusageincreadfrom
minimalload toaveryhighload of41.7indicatingram
wassufficient,Networktestingwithiperf3shows ahighthroughputof26gb.

DiskI/O Performance:

Objectivewastomeasurethebaselinediskoutput,performanceunder baselineand
under load,tofind outifstorageisabottleneck.

Iinstalled sysstatsandfio,tomeasurethediskperformance

<img src="./353yzkkj.png" style="width:7.5in;height:6.20833in" />

Write(MiB/0s) =2195Mibs(2301MB’s) mainspeed metricthatthedrivecanwrite.

WriteIpos,2194Ipos,

<img src="./kwnrt5t3.png" style="width:7.5in;height:5in" /><img src="./bvatmctb.png" style="width:7.5in;height:1.40625in" />

Latency:443.9 usec,averagelatencyofthedrive

Command :fio --name=randrw--filename=/tmp/disk_testfile--size=1G
--bs=4k--rw=randrw--rwmixread=70
--direct=1--numjobs=4--runtime=60–time_based

Read speed:32.5MB/s

Writespeed:14MB/s<img src="./tjivnohu.png" style="width:7.5in;height:5in" /><img src="./23kig14m.png"
style="width:7.23958in;height:1.32292in" />

System Latency:

Inthisweweretryingtomeasuretheresponselatencyatidleand under load
todeterminewhether the OSresponsivenessslowsdown.

Beforeanystresstest,idlemetrics.

After stresstestingbothmemoryandCPU,thesystem latency

<img src="./ri2tctna.png" style="width:7.5in;height:2.33333in" /><img src="./kprgwgsd.png"
style="width:2.76042in;height:1.01042in" />

Results:LookingattheresultsoftheSystem
latency,wecanseeatidlethereallatencywas0.008ms
duringthestresstestwemeasured
0.003swhichisoddaswewereexpectingtoseeahigher latencyas thesystem would
havemoretohandle,these resultcould bebecausewewereonlystressing2cpu
coresand only1gb ofram whichthesystem could handlemorestress.

ServiceResponse:

Waystooptimizesystem performance:

Optimization1:Stop unused services

Ichecked activesystem serviceand havedisabled allthebackground appsand
servicesthatareunused and disabled them astheyareusingsystem
resourceswithnopurposeand itsawaste.The results showed lower background
CPUusageand slightlyimproved responsetimefor shortcommandsan expected
gainwhereitreducesoverhead.

Optimization2:SetCPUgovernortoperformance

ToreducefrequencyscalinglatencyIapplied theperformanceCPUgovernorfor
thedurationofthetest. ThiskeepsCPUfrequencyhighand reducesrampup
latencyfor workloads.Theresultsshowed reduced command latency(ms) and
slightlymorestablethroughputunder load.Thetradeoffishigher power use and
temperaturethischangewasapplied temporarilyfor measurementand document.
