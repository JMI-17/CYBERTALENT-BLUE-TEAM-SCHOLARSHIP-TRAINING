# Category: 
- **Digital** **Forensics**
# Description
We observed a huge traffic towards our SSH Server<br />
X: How many source IPs attempting to connect  → Number<br />
Y: The Source IP with the most connections → x.x.x.x<br />
Z: The Source IP with the most connections country → xxxxxxx<br />
W: The Firewall action taken from the security control → xxxxxxx<br />
Flag format: flag{X:Y:Z:W}<br />
Note: our company uses Fortinet FortiGate firewall.<br />

# Tools
- Splunk Enterprise
- VirusTotal

# Solution
- A Link to a virtual machine hosting a splunk SIEM was provided and on getting to the interface i was provided with a serch bar to begining my investigation into the malicious activity <br />
- I searched for ssh service and made use of [All time] as our time range, we get the first answer from the src_ip field = **19**.
![5HH-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/def9c64c-6dce-4d0c-99be-4b26c881ed86)
- I was able to get the ip address with the most connections from the same field as the firewall action is gotten by checking the action field which is blocked.
![5HH-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/2a1d346e-e015-43dc-81be-4f9872681a36)
- To get the country of the ip with the most connections, we use an VirusTotal service and we get finland as our answer.
![5HH-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/e6d882b4-de13-49f3-99d6-892aff330e79)
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{19:91.224.160.108:Finland:Blocked}</details>
</li>

