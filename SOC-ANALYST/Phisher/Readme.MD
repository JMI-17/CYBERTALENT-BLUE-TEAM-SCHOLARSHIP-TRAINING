# Category
**Digital Forensics**
# Description
We suspect that one of our employees fell as a victim for a phishing attack, this is a disk image from his machine, can you tell us what happened?<br />

# Tools
- FTK TOOL
- EM Client

# Solution
- A Link to a a Disk imaged in a zip file was provided, and we’re told we have an employee who fell as a victim for a phishing attack. So, we’re going to use FTK imager tool on windows to open the Disk image file, and check for any lead for the phishing attack (an email, a malicious website, malicious file.). After adding the evidence file (the disk image) to the FTK tool, we realise that the user of the machine called “chrollo”.
![PH-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/01b23485-8de8-48c5-8ef2-e636411845ca)

- We start investigating for any lead for the phishing attack by expanding the “Roaming” folder under Users >>>> chrollo >>>> App Data. We find a folder called “eM Client”, and by googling it we find that it belongs to an e-mail client!. In order to investigate the messages of this account, we have to import them into an installed eM-client. So, we first export this folder from the FTK tool to our machine:<br />
![PH-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/ba88db57-519b-4044-b894-697d71d3e34a)
- After Downloading and Installing eM Client, replace the folder “eM Client” in the path “C:\Users\user\AppData\Roaming” with the one we extracted from FTK tool in order to open the mails of the chrollo user, When opening the eM Client, we find nothing suspicious in the inbox <br />
![PH-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/a6866d7d-43ea-4497-a05c-f4b40c491dac)
- But on cheacking the junk folder we find our target in the Junk E-mail folder a suspicious email named “Well Done” and contains a suspicious link
![PH-4](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/c2d51594-4f62-4126-a911-e5e9e2cc2c6c)
- Opening the contained link take us to a webpage that has the flag! 

> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
Flag{Phishing_1S_an_ART!}</details>
</li>
