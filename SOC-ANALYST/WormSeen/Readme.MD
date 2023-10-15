# Description
OOur EDR has flagged suspicious traffic from production endpoint, after reviewing the respective process generating the traffic and another alert has been alerted “Worm Detected” in our SIEM.<br>
You decided to escalate the case to IR team to further investigate and answer the below questions 

### Questions:

What is the range of worm spreading (x.x.x.x/xx) ?<br>

Destination target port of the attack (XX)?<br>

How many hosts might be affected by the worm (XX)?<br>

Flag format: flag{Answer1:Answer2:Answer3}.<br>
# Description
We observed a huge traffic towards our SSH Server<br />
X: How many source IPs attempting to connect  → Number<br />
Y: The Source IP with the most connections → x.x.x.x<br />
Z: The Source IP with the most connections country → xxxxxxx<br />
W: The Firewall action taken from the security control → xxxxxxx<br />
Flag format: flag{X:Y:Z:W}<br />
Note: our company uses Fortinet FortiGate firewall.<br />

# Tools
- Windows OS [Isolated Test Box]
- WireShark
- Process Hacker

# Solution
- A Link to a worm.zip file was provided, I ran it in an isolated windows 10 machine, and show the result in Process Hacker tool.<br />
![WS-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/27296215-1afb-4127-93f2-c35f304234ce)
- I checked the network tap to see the connection that the file make:.
![WS-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/1b107596-01e2-4773-8972-7229d5165e45)
- Freom the above information, after the file was executed it started to scan the network Lets open Wireshark to see the range of scaned network and answer the flag.!<br />
![WS-4](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/f241a2bf-562d-40ce-9ae6-081554ef19e0)
- Now we want to know the range of ip address that the file scaned lets know from wireshark direct from first ip 192.168.1.171 and the last one 192.168.1.255
![WS-5](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/a5b5d484-6ad4-476c-80de-c59a062c1d64)

> [!IMPORTANT]
> Using the information gotten and the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{192.168.1.0/24:22:85}</details>
</li>
