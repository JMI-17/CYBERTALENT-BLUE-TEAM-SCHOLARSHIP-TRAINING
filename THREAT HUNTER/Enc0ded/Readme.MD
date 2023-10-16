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
- Note: ARP opcode are categorized by IANA into 3 categories:
1) Assigned values (1 – 25)br />
2) Unassigned values (25 – 65534)<br />
3) Reserved (65535)br />
And here are the assigned ones with their description: Iana-arp-parameters<br />
![Enc-1](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/52c3ad52-1cbd-457f-8939-3a8f9400736e)

- To collect them, we start by dumping those ARP messages into a text file using tshark tool with the command:
$ Tshark -r ARP+Storm.pcap<br />
- Now, in order to extract only the opcode value, we will use the cut command, which will let us choose which column (field) of the output to extract after specifying the diameter between the columns And also will redirect the output into a text file to save it
using this command:<br />
$ Tshark -r ARP+Storm.pcap | cut -d -f 19,20 > encoded_flag.txt<br />
- The result output in the file is:<br />
![Enc-2](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/7c7a786c-c634-4472-b1ff-c5f6bb7da967)
- We need to organize it by (deleting the *opcode*) so we use the cut command again and have only the last section of the 
value (without the 0x). This is the file context when done:<br />
![Enc-3](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/5f75c78c-e4b9-4d10-94fa-561cf79ba211)
- Now, to extract the last section of the hex (delete the 0x) to be able to decode it into a readable text, we use the following command:<br />
![Enc-4](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/50556479-c0f8-4cd8-9bc9-22e48b6df7cf)
- which is a base64 encoded value. We decode with:<br />
![Enc-5](https://github.com/JMI-17/CYBERTALENT-BLUE-TEAM-SCHOLARSHIP-TRAINING/assets/69071528/93954882-ab72-4348-a388-aa0206cbe932)
<br />
> [!IMPORTANT]
> Using the format of the Flag provided
<li>
	<details>
		<summary>Flag</summary>
flag{gr@tuit0us_0pcOde_1s_Alw@ys_A6uSed_t0_p01s0n}</details>
</li>
