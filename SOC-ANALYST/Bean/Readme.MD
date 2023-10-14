# Description
Come back home Mr. Bean [Note: A Static Webpage was provided]

#Tools
- kali
- dirsearch

# Solution
- I did a quick search for simple tools that can enable me analyze a stattic webpage i got:
Dirsearch, Wfuzz, od1n.<br />
- i installed Dirsearch
**$ apt-get install dirsearch<br />
- I started the vulnerable website and 
https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/issues/1#issue-1943416464


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
