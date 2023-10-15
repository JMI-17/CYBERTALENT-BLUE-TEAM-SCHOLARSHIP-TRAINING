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
- <br />
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{19:91.224.160.108:Finland:Blocked}</details>
</li>

