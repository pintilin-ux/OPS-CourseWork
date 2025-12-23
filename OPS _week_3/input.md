**1**. Select applications representing different workload types (e.g. CPU-intensive, RAM intensive, I/O-intensive, Network-intensive, and Server applications such as game servers) for performance evaluation and create an Application Selection Matrix listing applications with justifications for choosing them.

||
||
||

Cpu intensive  -Stress -ng  -Cpu stress tool to stress cores with mothods -Because with this tool you can see how much the cpu is being used. 

RAM Intensive -memtester  -Find and test blocks of memory from userspace  -Simple comand to see the amount of resources 

I/O intensive -fio  -Flexible I/O benchmarks read/write controls block size  -Storage I/O testing produces. 

Network intensive -iperf3 -Network tester between client and server. -Accurate measurements of bandwith and packet loss for network. 

Server  -apache2 -HTTP server that handles multiple connections -Provids real world server workload handling memory network. 



||
||
||
 
**Task2:**

Firstly I needed to use whoami to find the username which was vboxuser.

Then using ip a to find the ip to connect to SSH.

this is the command I've used to connect to ssh:
ssh [<u>vboxuser@192.168.0.170</u>](mailto:vboxuser@192.168.0.170)

sudo apt update, to update the system,

sudo apt install openssh-server –y, istall the ssh server that allows remote login

<img src="./al2pcnlm.png" style="width:6.5in;height:4.20833in" />

then used “systemctl status ssh” to check if the system is running. And it was showing active running

<img src="./hcctedzi.png" style="width:6.5in;height:4.375in" /><img src="./xkrp5fuw.png" style="width:6.5in;height:3.1875in" />

I also added UFW rules, if firewall is enabled, I allow SSH

**Task 3:** **Expected resources Profile**
This section will have the resource usage of each selected application before performance testing is done. The profile will describe the cpu load, memory load, disk load, and network. These will be from normal benchmarking tools.

1. Cpu Intensive

First was cpu intensive using stress –ng, it puts a lot of load on the cpu by running multiple threads.

I expect:

Cpu usage to be extremely high 90-100%

Ram usage will be low to moderate 100-500MB mostly from code

Disk usage should stay the same as base values as it testing mainly the cpu

Network also should stay the same as it a test on the cpu and has nothing to do with the network.

||
||
||

CPU -Very High 

RAM -Low 

DISK -None 

NETWORK -None 


||
||
||
||

2. Ram Intensive

Using –vm this will stress the ram by allocating memory I expect:

Cpu usage to be moderate as memory requires cpu support

Ram usage to be Extremely High - also depends on the value that is passed, for example --vm-bytes 2G will allocate 2GB of ram

Disk Usage:

None as it only stresses the ram

Network:

None.

||
||
||
||
||

CPU Moderate 

RAM Very High 

DISK None 

NETWORK None 


||
||
||
||

3. Disk I/O intensive

Using the command dd that writes large files and measures disk throughput.

Expected Usage:

Cpu, I expect it to be very low

Ram, also should be very low almost baseline

Disk, Very high as it will be using it to write and read large file. Command example dd if=/dev/zero of=testfile bs=1g count=1, which writes 1GB

Network, none

||
||
||

CPU Very low 

RAM Very low 

DISK Very HIgh 

NETWORK None 


||
||
||
||

4. Network Intensive

Measure network activity between a client and a server

Expected usage:

Cpu, usage moderated due to high speeds network

Ram, low

Disk, low

Network, Extremely High – saturates available bandwidth 100-1000MBPS

||
||
||

CPU Moderate 

RAM Low 

DISK None 

NETWORK Very high 


||
||
||
||

5. Server type application

A standard HTTP web server used to simulates server behavior

Expected usage:

Cpu, low at idle, but moderate while under load testing

Ram Usage:

Moderate 200-400MB depending on the load of the cpu and what is being used

Disk:

Low to moderate, saving files and doing other activities

Network usage:

Moderate to high depending on the amount of requests are being sent from and to the server.

||
||
||
||

CPU Low - Moderate 

RAM Moderate 

DISK Low 

NETWORK Moderate - High 


||
||
||

Task 4: Monitoring Strategy for performance Evaluation
In task 4 I will be monitoring approach used to evaluate resource usage for each selected application, cpu, ram, disk, network and server. A combination of time and recorded monitoring tools is used to capture the performance and resource usage of the cpu, ram, disk and network.

Commands to install some of the monitoring systems.

sudo apt update (updates all of the systems to make sure everything works good, also the installing process works smoothly)

sudo apt install stress-ng fio iperf3 apache2 –y (some of the tools that we will use to monitor specific or multiple components and their performance.)

1. Cpu Monitoring

Commands:

> • Top • Htop
> 
> • Mpstat

Top and htop give real time cpu usage and show how much each application uses

Mpstat give accurate cpu usage over time across all cores

I will start with <u>htop.</u> Then use stress-ng –cpu 4 –timeout 60s

I will record :

Cpu% per core

Load average

Temperature

To log the data:

Mpstat 1 60, this will capture cpu usage every second for 60 seconds

2. Ram Monitoring

Commands

> • Free –h • Vmstat • Htop

Free – shows total and used ram

Vmstat – shows memory activity

Htop – visualises memory usage per process

How to run:

Free –h, check base ram usage

Stress-ng –vm 2 –vm-bytes 2g –timeout 60s, runs memory load, to stress test

Watch –n1 free –h, monitor changes

Vmstat 1 60, captures system activity

Data to record:

Total ram consumption

Activity

Buffer and cache changes

3. Disk monitoring

Commands

> • Iostat • Iotop • Df –h

Iostat – shows disk read and write speeds

Iotop – shows which processes caused disk load

Df –h – confirms disk capacity and free space before tests

How to run:

Iostat –xz 1, start disk monitoring

Dd if=/dev/zero of=testfile bs=1g count=1 oflag=direct, runs disk stress test

Data recorded:

MB/s throughput

Disk utilisation

Read and write speeds

4. Network monitoring

Commands:

> • Iftop • Nload
> 
> • Sar –n DEV

Iftop, shows live incoming/outgoing traffic

Nload, visualises total bandwidth usage

Sar, records continuous network statistics

How to run:

Sudo iftop, starts monitoring

Iperf3 –s, on the server

iperf3 –c SERVER_IP –t 30, on client, stress tools

Data recorded: Bandwidth MBPs

Packet rate

Network utilization

Sar –n DEV 1 30, to log metrics

5. Server Application monitoring

Commands

> • Htop
> 
> • Apache2ctl status • Iftop
> 
> • Ab

Web servers require most of the above to monitor cpu, ram and network

Ab, generate measurable HTTP loads

How to run:

Sudo systemctl start apache2, starts apache service

Htop

Sudo iftop , starts monitoring performance and resources usage

Ab -n2000 -c50 [<u>http://server</u>](http://server/) ip/

Recorded data:

Requests per second

Apache memory usage

Cpu spikes

Network
