# Description
Our server compromised due to known vulnerability introduced from many years, Kindly check and identify this flow

X: Attack source → EX. “Internal/External” <br />
Y: The Source IP → x.x.x.x <br />
Z: CVE Num of the attack → xxx <br />
W: Destination Mac Address <br />
Flag format: flag{X:Y:Z:w}

# Solution
- First I used an online pcap analysis tool called PacketTotal but this can be used on the terminal with capinfos to see informations of the file

**$ capinfos /Downloads/backdoor.pcap** <br />
File name:           backdoor.pcap <br />
File type:           Wireshark/tcpdump/... - pcap <br />
File encapsulation:  Ethernet
File timestamp precision:  microseconds (6) <br />
Packet size limit:   file hdr: 96 bytes <br />
Packet size limit:   inferred: 96 bytes <br />
Number of packets:   739 <br />
File size:           71 kB <br />
Data size:           134 kB <br />
Capture duration:    72.785513 seconds <br />
First packet time:   2022-04-26 18:07:31.244931 <br />
Last packet time:    2022-04-26 18:08:44.030444 <br />
Data byte rate:      1,850 bytes/s <br />
Data bit rate:       14 kbps <br />
Average packet size: 182.21 bytes <br />
Average packet rate: 10 packets/s <br />
SHA256:              91a780295b31dac44d5357bf63bfe2cfddb990f447fd60a9048eb16ec5c7ec15 <br />
RIPEMD160:           01a55a5fe78f4db4ae13d90b031b6d5e5c8845fd <br />
SHA1:                6a8a80c755676757b2a77b01f0282c46b4f87f9d <br />
Strict time order:   True <br />
Number of interfaces in file: 1 <br />
Interface #0 info: <br />
                     Encapsulation = Ethernet (1 - ether) <br />
                     Capture length = 96 <br />
                     Time precision = microseconds (6) <br />
                     Time ticks per second = 1000000 <br />
                     Number of stat entries = 0 <br />
                     Number of packets = 739 br />


- After getting basic info about the packet, i used tshark to search if this pcap have a http, ssh  and FTP, eventually FTP gave the following out put.<br />
**$ tshark -r backdoor.pcap -Y ssh**<br />
  420  42.263303 61.177.173.18 → 192.168.1.80 SSH 81 Client: Encrypted packet (len=15)<br />
  422  42.269874 192.168.1.80 → 61.177.173.18 SSH 104 Protocol (SSH-2.0-OpenSSH_4.7p1 Debian-8), Encrypted packet (len=8)[Packet size limited during capture]<br />
  425  42.273049 61.177.173.18 → 192.168.1.80 SSH 81 Client: Encrypted packet (len=15)<br />
  429  42.274837 192.168.1.80 → 61.177.173.18 SSH 104 Protocol (SSH-2.0-OpenSSH_4.7p1 Debian-8), Encrypted packet (len=8)[Packet size limited during capture]<br />
  439  43.378167 61.177.173.18 → 192.168.1.80 SSH 922 Encrypted packet (len=856)[Packet size limited during capture]<br />
  450  44.576726 192.168.1.80 → 61.177.173.18 SSH 850 Encrypted packet (len=784)[Packet size limited during capture]<br />
  471  44.928592 61.177.173.18 → 192.168.1.80 SSH 90 Client: Encrypted packet (len=24)<br />
  478  44.935800 192.168.1.80 → 61.177.173.18 SSH 282 Encrypted packet (len=216)[Packet size limited during capture]<br />
  481  45.336474 61.177.173.18 → 192.168.1.80 SSH 274 Encrypted packet (len=208)[Packet size limited during capture]<br />
  484  45.356874 192.168.1.80 → 61.177.173.18 SSH 850 Encrypted packet (len=784)[Packet size limited during capture]<br />

- some intresting information was found here but nothing to really help with the task at hand<br />

**$ tshark -r backdoor.pcap -Y ftp**<br />
Running as user "root" and group "root". This could be dangerous.<br />
  165  10.000115 192.168.1.80 → 192.168.1.58 FTP 86 Response: 220 (vsFTPd 2.3.4)<br />
  167  10.000865 192.168.1.58 → 192.168.1.80 FTP 78 Request: USER zH9:)<br />
  169  10.000901 192.168.1.80 → 192.168.1.58 FTP 100 Response: 331 Please specify the passwor<br />
  171  10.001580 192.168.1.58 → 192.168.1.80 FTP 77 Request: PASS utEt<br />

- Here i see vsFTPD 2.3.4, after a quick google search>> it's the vulnerability and is tied to CVE-2011-2523.<br />
- Also, you can see that in these FTP request, you will see the source IP, that's 192.168.1.58, and destination IP : 192.168.1.80.<br />
- A quick filter using FTP on NMAP or from the online analysis tool you will find the Destination Mac address.<br />
- Consiquently the following command produces the same out put.<br />

$ tshark -r backdoor.pcap -Y ftp -V | less<br />
Frame 165: 86 bytes on wire (688 bits), 86 bytes captured (688 bits)<br />
    Encapsulation type: Ethernet (1)<br />
    Arrival Time: Apr 26, 2022 18:07:41.245046000 EDT<br />
    [Time shift for this packet: 0.000000000 seconds]<br />
    Epoch Time: 1651010861.245046000 seconds<br />
    [Time delta from previous captured frame: 0.005825000 seconds]<br />
    [Time delta from previous displayed frame: 0.000000000 seconds]<br />
    [Time since reference or first frame: 10.000115000 seconds]<br />
    Frame Number: 165<br />
    Frame Length: 86 bytes (688 bits)<br />
    Capture Length: 86 bytes (688 bits)<br />
    [Frame is marked: False]<br />
    [Frame is ignored: False]<br />
    [Protocols in frame: eth:ethertype:ip:tcp:ftp]<br />
Ethernet II, Src: PcsCompu_66:e3:8b (08:00:27:66:e3:8b), Dst: IntelCor_c5:20:65 (4c:1d:96:c5:20:65)<br />


- You will find the Destination Mac address: 08:00:27:66:e3:8b
> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{Internal:192.168.1.58:CVE-2011-2523:08:00:27:66:e3:8b}</details>
</li>
