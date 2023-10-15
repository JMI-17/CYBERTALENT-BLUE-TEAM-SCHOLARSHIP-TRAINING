# Description 
Your Team Lead ask you to develop splunk use case for detecting USB plugged on any device in your environment he shared with you also this link https://lantern.splunk.com/Security/Use_Cases
Develop the use case and answer the below questions based on botsv1 dataset <br /> 

X: Date and time when the USB plugged on device  (YYYY-MM-DD:HH:MM:SS) <br />
Y: The Machine name <br />
Z: Name of the USB device <br />
Flag format: flag{X:Y:Z:A}<br />


# Solution

To solve this challenge, I was provided with a link and granted temporary access to the webpage for Spluk Enterprise SIEM.<br />
On the Splunk SIEM i Navigated to Serch and Reporting TAB to use my Search query. <br />

Note: the initial strings i searched for are "USB and Removable", I investigated the logs and from the output i was able to deduce X and Y which represents the Date and time stamp, Nmae of the machine<br />
## OUTPUT<br />
```
8/24/16 6:10:46.000 PM	<Event xmlns='http://schemas.microsoft.com/win/2004/08/events/event'><System><Provider Name='Microsoft-Windows-Sysmon' Guid='{5770385F-C22A-43E0-BF4C-06F5698FFBD9}'/><EventID>7</EventID><Version>3</Version><Level>4</Level><Task>7</Task><Opcode>0</Opcode><Keywords>0x8000000000000000</Keywords><TimeCreated SystemTime='2016-08-24T18:10:46.773764400Z'/><EventRecordID>442043</EventRecordID><Correlation/><Execution ProcessID='1216' ThreadID='1924'/><Channel>Microsoft-Windows-Sysmon/Operational</Channel><Computer>we8105desk.waynecorpinc.local</Computer><Security UserID='S-1-5-18'/></System><EventData><Data Name='UtcTime'>2016-08-24 18:10:43.871</Data><Data Name='ProcessGuid'>{0F2D76F0-E314-57BD-0000-0010B7E2A400}</Data><Data Name='ProcessId'>4728</Data><Data Name='Image'>C:\Windows\System32\rundll32.exe</Data><Data Name='ImageLoaded'>C:\Program Files (x86)\Intel\Intel(R) USB 3.0 eXtensible Host Controller Driver\uninstall\x64\Drv64.exe</Data><Data Name='Hashes'>SHA1=208C0787DFE8D4508134DB2F438CBE223AD7D4B2,MD5=DEBF43E44458EF0C7CC9D0A2BA4A5F57,SHA256=72ABC81CA40B0F1936FE28AF7975A5EB6BEC1456D35F73D9C56DB54AE0938FE2,IMPHASH=69B2DC9C85375DC85DA8CF1DDAAF614E</Data><Data Name='Signed'>true</Data><Data Name='Signature'>Intel Corporation</Data></EventData></Event> 
Event Actions
Type	                Field	             Value	                                                                               Actions 
Selected	        host                 we8105desk	
                        source               WinEventLog:Microsoft-Windows-Sysmon/Operational
                        sourcetype           xmlwineventlog
Event	                Channel              Microsoft-Windows-Sysmon/Operational
                        Computer             we8105desk.waynecorpinc.local
                        EventCode            7	
                        EventData_Xml        <Data Name='UtcTime'>2016-08-24 18:10:43.871</Data><Data Name='ProcessGuid'>{0F2D76F0-E314-57BD-0000-0010B7E2A400}</Data><Data Name='ProcessId'>4728</Data><Data Name='Image'>C:\Windows\System32\rundll32.exe</Data><Data 
                                             Name='ImageLoaded'>C:\Program Files (x86)\Intel\Intel(R) USB 3.0 eXtensible Host Controller Driver\uninstall\x64\Drv64.exe</Data><Data 
                                             Name='Hashes'>SHA1=208C0787DFE8D4508134DB2F438CBE223AD7D4B2,MD5=DEBF43E44458EF0C7CC9D0A2BA4A5F57,SHA256=72ABC81CA40B0F1936FE28AF7975A5EB6BEC1456D35F73D9C56DB54AE0938FE2,IMPHASH=69B2DC9C85375DC85DA8CF1DDAAF614E</Data><Data                                                 Name='Signed'>true</Data><Data Name='Signature'>Intel Corporation</Data> 

Time	              	_time               2016-08-24T18:10:46.000+00:00 
Default	<br> 
                        index               botsv1	
                        linecount           1	
                        punct               <_='://../////'><><_='--'_='{----}'/><></><></><><
                        splunk_server       635bd95b7c6e

- Then i seached with the following query name "sourcetype=winregistry friendlyname", and analyzed the logs for the flag which is Z 
> [!IMPORTANT]
> Using the format of the Flag provided<br />


<li>
	<details>
		<summary>Flag</summary>
flag{2016-08-24:10:42:17:we8105desk:MIRANDA_PRI} </details>
</li>
