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

- I was able to get the ip address with the most connections from the same field as the firewall action is gotten by checking the action field which is blocked.

- To get the country of the ip with the most connections, we use an VirusTotal service and we get finland as our answer.


> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{19:91.224.160.108:Finland:Blocked}</details>
</li>

