# Category
- **Web** **Security**
# Description
Massive web bruteforce attack observed on our IIS server, Your lead has informed you to initiate some investigation to identify the following:<br />
X: The highest number of non existent URLs request sent by the attacker → Number<br />
Y: The Source IP → x.x.x.x<br />
Z: The attacker source country → xxx<br />
Flag format: flag{X:Y:Z}<br />

# Tools
- Splunk Enterprise
- dirsearch

# Solution
- A Link to a virtual machine hosting a splunk SIEM was provided and on getting to the interface i was provided with a serch bar to begining my investigation into the malicious activity <br />
- I searched for ssh service and made use of [All time] as our time range, we get the first answer from the src_ip field = **19**.

- I was able to get the ip address with the most connections from the same field as the firewall action is gotten by checking the action field which is blocked.

- To get the country of the ip with the most connections, we use an VirusTotal service and we get finland as our answer.
$ Dirsearch -u {THE SITE URL GOES HERE}<br />
going to: (http://SITEURL..com/files/../home/)<br />
- Dowload the flag.txt filethe la is present there<br />

> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{19:91.224.160.108:Finland:Blocked}</details>
</li>
