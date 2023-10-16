# Category: 
- **Network Security**
# Description
- An attacker in the network is trying to poison the arp table of 11.0.0.100, the admin captured this PCAP. 
- Flag format: FLAG{host+process_Name+IP}.<br />

# Tools
- Kali
- Wireshark
- Tshark

# Solution
- A link was provided to Download the pcap captured, i aimed to collect text values that are sent as Hex values for the opcode option in the ARP Messages
And here are the assigned ones with their description: Iana-arp-parameters<br />
![Enc-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/52c3ad52-1cbd-457f-8939-3a8f9400736e)

- To collect them, we start by dumping those ARP messages into a text file using tshark tool with the command:
<br />
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{y0u_c0m3_f0r_fl1g_1nd_h3r3_1t_1s_2000}</details>
</li>
