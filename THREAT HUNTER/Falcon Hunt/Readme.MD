# Category: 
- **Network Security**
# Description
- Falcon language can guide your hunt, try to hunt the machine developed this challenge. Developer used the port 8888 for the system
- password: falcon 
- Flag format: FLAG{host+process_Name+IP}.<br />

# Tools
- kali
- Yara Script file

# Solution
- A link was provided to the jupyter enviroment, the password has already been provided. 
- I did a cmd + f search and sercherd for tyhe following:
- on the process.csv file i searcherd for the the port provied [8888] and found 2 entries.<br />
![FH](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/79aa221d-b2c6-472c-a842-43f1d47b79a4)
- on the Network.csv i did the same search and got two IP associated with there port 8888 [127.0.0.1, 172.17.0.1]
![FH-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/d69cf42b-a03e-4437-a40d-274c3b32a52b)
- and I put the corresponding values into the flag until i got an answer

> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{nice_williamson+docker-proxy+172.17.0.2}</details>
</li>
