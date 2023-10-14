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
- I started the vulnerable website<br />
![Bean](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/6770c6e9-71c3-4459-a469-cd28b0a840ad)

$ DIRSEARCH -U {THE SITE URL GOES HERE}<br />
[13:14:29] Starting: <br />
[13:15:27] 301 -  185B  - /files  ->  {http://SITEURL..com/files}/<br />
[13:15:28] 200 -    9KB - /files/<br />
[13:15:31] 200 -  404B  - /index.html<br />
    <br />


- You will find the Destination Mac address: 08:00:27:66:e3:8b
> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{Internal:192.168.1.58:CVE-2011-2523:08:00:27:66:e3:8b}</details>
</li>
