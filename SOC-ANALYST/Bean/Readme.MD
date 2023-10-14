# Description
Come back home Mr. Bean [Note: A Static Webpage was provided]

#Tools
- kali
- dirsearch

# Solution
- I did a quick search for simple tools that can enable me analyze a stattic webpage i got:
Dirsearch, Wfuzz, od1n.
- i installed Dirsearch
**$ apt-get install dirsearch







- I started the vulnerable website and 


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
