# Description
Come back home Mr. Bean [Note: A Static Webpage was provided]

# Tools
- kali
- dirsearch

# Solution
- I did a quick search for simple tools that can enable me analyze a stattic webpage i got:
Dirsearch, Wfuzz, od1n.<br />
- i installed Dirsearch
**$ apt-get install dirsearch<br />
- I started the vulnerable website<br />
![Bean](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/6770c6e9-71c3-4459-a469-cd28b0a840ad)

$ Dirsearch -u {THE SITE URL GOES HERE}<br />
[13:14:29] Starting: <br />
[13:15:27] 301 -  185B  - /files  ->  (http://SITEURL..com/files)/<br />
[13:15:28] 200 -    9KB - /files/<br />
[13:15:31] 200 -  404B  - /index.html<br />
![Bean2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/48046dcc-5cd4-418a-ae47-cb35af344c5b)
-After trying to look into several directories i decided to check the descrition line that tell us Come back home Mr. Bean.<br />
-Navigate to the home directory of Mr. Bean on ur prowser by going to: (http://SITEURL..com/files/../home/)<br />
- Dowload the flag.txt filethe la is present there<br />
![Bean-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/8b6b75be-aca4-4eee-96f4-401301ce2cf5)
> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
FLAG{Nginx_nOt_aLWays_sEcUre_bY_The_waY}</details>
</li>
