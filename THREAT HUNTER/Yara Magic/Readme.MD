# Category: 
- **Digital** **Forensics**
# Description
- Help us!Here is a copy of a folder of ours, we need to scan this folder with this Yara rule and check if we have any matches!,scan this folder with the rule and provide us with the matched filename.
Flag format: FLAG{filename}.<br />

# Tools
- kali
- Yara Script file

# Solution
- A link was provided to the archive file. After downloading the archive file, we found a Yara rule file (rule.yara) <br />
![YM-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/964874db-df06-4d92-8e5f-f4bed70d64c4)
- I used the yara rule to serch for IOCs in the folder, the following CMD:<br />
$ yara -f rule.yara ./[folder name]<br />
- output<br />
MySuperCoolRule Folder/12776<br />

> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{12776}</details>
</li>
