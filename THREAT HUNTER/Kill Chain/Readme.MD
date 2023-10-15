# Category: 
- **General Information**
# Description
According to Lockheed Martin's cyber kill chain,what is the name of the phase that this description applies to:
Attackers create the attack vector that will be used in the cyberattack.

Flag format: FLAG{phase name}.<br />

# Tools
- Search Engine

# Solution
-The Cyber Kill Chain is a concept and framework used in cybersecurity to describe the stages of a cyberattack. It was developed by Lockheed Martin, a global aerospace, defense, arms, security, and advanced technologies company, as a way to understand and visualize the various steps a cyber attacker takes to compromise a target. The model helps organizations and security professionals to better defend against and respond to cyber threats. The Cyber Kill Chain typically consists of the following stages:<br />

- Reconnaissance: In this initial stage, the attacker gathers information about the target. This can include identifying potential vulnerabilities, the target's infrastructure, and key individuals.
- Weaponization: At this stage, the attacker creates or acquires a weapon, typically in the form of malware, which will be used in the attack. This weapon is specifically designed to exploit known vulnerabilities.
- Delivery: The attacker delivers the weapon to the target, often through email, malicious websites, or other means of distribution. This can include phishing emails, infected attachments, or drive-by downloads.
- Exploitation: Once the weapon is delivered, the attacker takes advantage of a vulnerability in the target's system to execute the malware. This step is often automated and involves techniques like buffer overflow attacks or exploiting known software vulnerabilities.
- Installation: In this stage, the attacker installs the malware on the compromised system. This often involves establishing a backdoor or command and control channel for remote access.
- Command and Control: The attacker sets up communication channels to control the compromised system. This allows them to send commands to the malware, exfiltrate data, or make further changes to the compromised system.- 
-  Actions on Objectives: The final stage involves the attacker achieving their ultimate goals, which can include data theft, system disruption, or any other malicious objectives. This is the stage where the attacker's intent is realized.

It's important to note that the Cyber Kill Chain is not a one-size-fits-all model, and it's a simplification of complex attack scenarios. Its primary purpose is to help security professionals understand and categorize the different phases of an attack to develop strategies for detection, prevention, and response.<br />
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
FLAG{Weponization}</details>
</li>


