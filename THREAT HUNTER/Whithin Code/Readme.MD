# Category: 
- **Digital Forensics**
# Description
- Flag rises within the code. Our developer thinks encoding is safe, try to find the location
flag format: Flag{location}.<br />

# Tools
- Kali
- Base 64 Converter
- Yara Script file
- magictool
- RapidTables

# Solution
- A link was provided to download a .zip file. After downloading the zip file, w, we found a folder that contains many binary files.To search in binary / text files, we use Yara tool (which is available in Linux, Windows):
- To start, we need to know What we’re searching in order to create a suitable Yara rule for it. Looking at the Description of the challenge, it seems like the word flag might be the word we should look for “Flag rises within the code”
To create a role that matches the word “Flag” in binary files, we need to match the binary or the hex of the word “Flag” Within the targeted folder.<br />
- I encoded the word “Flag” to base64 using Base64Guru website, and the result is: RmxhZw==<br />
- I also converted the base64 result to Hex using any tool like magictool website to use it in our Yara rule, and the Result is: 526d78685a773d3d
- Note: using either of the Base64 encoding or the Hex form would be enough to match for the word “Flag”, but i used both to avoid trying again
- Now that we have the info that need to match for, we can create our Yara rule. We wrote a simple rule to match For both the encoding and the Hex form, and the rule is:
![WC-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/9b5fdeaf-a0f2-41e3-90ef-a5ff8f76eee9)
- Finally, before running the Yara rule, we need to know which option to use with it, And since we do not want to match for the file that contains the defined string in our rule, we will not choose the -f
option as we usually do EG:
$ yara -f rule.yara wihin\code
- Instead we will use -s option which will give us the offset location of the string in the matched file (for more explanation about the Yara options use the command :yara help
![WC-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/10924c83-6420-4931-b94b-de029578ea9e)

- I tried Submitting this location (0x2460) in its Hexadecimal form but it was not accepted. So, i converted it back to decimal using Rapidtables website and had the result: 9312<br />
                                                                                                          i                                                                                                         
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{9312}</details>
</li>
