# Category: 
- **Network Security**
# Description
- let's refresh your skills  >_< .<br />

# Tools
- Kali
- Wireshark
- Virus total

# Solution
- A link was provided to Download the pcap captured, I Uploaded the "challenge_refresher.pcapng" VirusTotal will scan the file using various antivirus engines and provide you with a report <br />
![R1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/9f7b45a6-2cdc-43b3-aed9-f9ef7f02c191)
- 
![R2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/0b45a26c-a9be-4e6c-83df-1d9a31a929f7)
- Using Wireshark to filter through the pcap file for signs of FTP used in the traffic captured: <br />
- Command: tcp.stream eq 58,59,60,61.<br />
![R3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/4d146463-6a38-4f3c-a95f-71f0efe0bfe2)
![R4](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/f3d7b9e6-08af-4b80-97d4-4d6584820022)
![R5](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/81ce1ff6-617b-49c2-a032-097a89dee51a)
- for better and deeper analysis i decide to switch to kali<br />
- $ wireshark challenge_refresher.pcapng<br />
![R6](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/cdad2bdd-2fea-449e-9076-c9de54a3d5c0)
- $ ls -al<br />
- I was unable to access the secret.zip file because of password restrictions <br />
- After discusions in the forum, the hypothesis is that there is information in the pics folder that will help us access the secret.zip fil, so once i navigated to the folder holding the pics. I tried series of command to extract the information from the pics file the combination that gave us positive output:<br />
- $ ls | awk -F '[._]' '{print $1 "_" $2}' | sort -g | awk -F '_' '{print $2}' | tr -d '\n'<br />
- Output: iamsupersecretpasswordgood4uthefinding <br />
- Extract the zip file with: $ 7z e secret.zip <br />
![R7](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/d1965b00-003a-43d0-bd93-2227e0032671)
![R8](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/8450cb1e-5823-4c29-b8b7-7957ba8ed6cc)
- Once the file is extracted you will see a flag.txt file 
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{y0u_c0m3_f0r_fl1g_1nd_h3r3_1t_1s_2000}</details>
</li>
