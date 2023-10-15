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
- Virus Total

# Solution
- From the description the attack targeted our IIS server and the first question (X: The highest number of non existent URLs request sent by the attacker → Number) tell us that we should filter the search output to only "not found - code 404 messages". So after opening splunk, we start our search with a simple query for instances with error 404 with a time range of "all time" checking the ip addresses associated with the responses, we have 2 private ips and a public ip (40.80.148.42) as seen below: **sc_status="404"**<br />
<img width="1628" alt="404-1" src="https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/25f7a926-42c8-4def-ac7e-8b839317656f">
- This gave us 2119 events. However, we should keep filtering based on the rest of information provided to us. We check the c_ip field, and find that it has 2 values (public IP and Private IP)
Of course, we will select the public IP address to add to the search and we will copy it as an answer to:
Y: The Source IP → x.x.x.x<br />
Y = 40.80.148.42<br />
- our search query now is: sc_status="404" c_ip="40.80.148.42", we only add on more filter to it from the field sourcetype which has one value "iis"   and our search query now is: **sc_status="404" c_ip="40.80.148.42" sourcetype=iis** which is enough to get all the rest of the answers
- X: The highest number of non existent URLs request sent by the attacker → Number
- X: 2009
<img width="1628" alt="404-2" src="https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/7c5888a1-3edb-4b47-bfc8-a319de6f2e4a">
- Z: The attacker source country → xxx
- We use any IP address lookup tool to map the IP address to geolocation (ex: VirusTotal ) and the result is USA
- Z: USA<br />
![404-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/f3584a4e-3783-4875-907e-6cb3235ef4bb)

we collect all the answers and have the flag as below:<br />

> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{2009:40.80.148.42:USA}</details>
</li>
