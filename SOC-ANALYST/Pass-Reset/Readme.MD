# Description
You have received the email below,  Please examine the email and answer the below questions

###Required in flag:
X: Sender email
Y: The date that user received the email
Z: The domain name of the phishing link that was sent in the email body
W: Do you think that the email is safe or malicious ?
Flag format: flag{X:Y:Z:w}

# Solution
- After Dowloading the file from the link provided i tried to unzip it which i discovered was passworded, so i carried out a bruteforce Attack on the file using a tool called fackzip to reveal the password

**$ fcrackzip -u -D -p rockyou.txt  ~/Desktop/passreset.msg.zip (br/)
PASSWORD FOUND!!!!: pw == infected (br/)
**$ unzip passreset.msg.zip  (br/)                                 
Archive:  passreset.msg.zip  (br/)
[passreset.msg.zip] Password Reset Request.msg password: (br/) 
inflating: Password Reset Request.ms (br/)

**$ ls (br/)
'Password Reset Request.msg' (br/)

**$ cat 'Password Reset Request.msg' (br/)

Disclaimer: The content of this email is confidential and intended for the recipient named in the message only. It is strictly forbidden to share any part of this message with any third party, without the written consent  of the sender. If you are not the named addressee and received this message by mistake, please notify the sender and delete this email from your system immediately. Email transmission cannot be guaranteed to be secure or error-free as information could be intercepted, corrupted, lost, destroyed, arrive late or be incomplete, or contain viruses. The sender therefore does not accept liability for any errors or omissions in the contents of this message which arise as a result of email transmission. (br/)
10338048-193a-4298-abea-3596ae88b05e������B��j1/00000002/o=ExchangeLabs/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=7ceaf73a696a407f869911b2f2b12a9a T04370nelson.laureano@novobanco.ptgestao.operacao.monitorizacao@noFrom: Password Request <roger@captech.com> (br/)
To: "Patricia Oliveira (novobanco Digital)" <paoliveira@novobanco.pt> (br/)
Subject: Password Reset Request (br/)
Thread-Topic: Password Reset Request (br/)
Thread-Index: AQHYKlMOQpovkzWfuUqYkPmXdPe1VQ== (br/)
Date: Fri, 25 Feb 2022 14:22:02 +0000 (br/)
Message-ID: <PR3P189MB0953E4E9763DCB128D8DE8AFBB3E9@PR3P189MB0953.EURP189.PROD.OUTLOOK.COM> (br/)
Content-Language: en-US (br/)
X-MS-Has-Attach: (br/)
X-Auto-Response-Suppress: -4 (br/)
X-MS-Exchange-Organization-SCL: -1 (br/)
X-MS-TNEF-Correlator: (br/)
X-MS-Exchange-Organization-RecordReviewCfmType: 0 (br/)
x-ms-exchange-crosstenant-id: 10338048-193a-4298-abea-3596ae88b05e (br/)
x-microsoft-antispam-message-info: (br/)
1uws6HFpk3dCEF9dudGqgD/6wYUBss2LQcc2iUnLc/zBKQ/MohMXB1pIDlsvoYKiSjtcqyuHs+tq1DDU8EhMLB0rkMJIwnDSFWZica6BAvL3rlFVkQGULGcgxzfiMNGslrfvfwIvzAL+1chLmKK61L9Bu4KXwBrewarWFXWfh0Rs8q6WrGBpPzXrUDuRAuvUlmJAflqz0G65/ax9LQRHLQ/yDKFuHApakQqDJDNI+vWQ1rQ+qetIthj+7Uwx/bLPORo10vyyI3ukFNTKi3FvhFLtsN+J3dyiQxtBTYk2LaVhcd58G2QA0Tk4HFaQxFU2BI62rupm4nUtGNuwDjshWcosoDWB2y2YvrHSeTo4bA2AHzfB3fFiI9tpbuvwEvFU (br/)
x-ms-exchange-organization-network-message-id: 1284b588-f2b0-42e4-2506-08d9f86a312f (br/)
Content-Type: multipart/alternative; (br/)
        boundary="_000_PR3P189MB0953E4E9763DCB128D8DE8AFBB3E9PR3P189MB0953EURP_" (br/)
MIME-Version: 1.0 (br/)

--_000_PR3P189MB0953E4E9763DCB128D8DE8AFBB3E9PR3P189MB0953EURP_ (br/)
Content-Type: text/plain; charset="utf-8" (br/)
Content-Transfer-Encoding: base64 (br/)

DQrwn5uIIEVtYWlsIHByb3ZlbmllbnRlIGRlIHVtIGVuZGVyZcOnbyBleHRlcm5vLiBOw6NvIGNs
aXF1ZSBlbSBsaW5rcyBvdSBhYnJhIGFuZXhvcywgYSBtZW5vcyBxdWUgcmVjb25oZcOnYSBvIHJl
bWV0ZW50ZSBlIHRlb3IgZGEgbWVuc2FnZW0uDQoNCg0KDQpbWF0NCg0KUGFzc3dvcmQgUmVzZXQg
UmVxdWVzdA0KDQpUaGUgcGFzc3dvcmQgYXNzb2NpYXRlZCB3aXRoIHRoaXMgYWNjb3VudCBoYXMg
YmVlbiByZXF1ZXN0ZWQgdG8gYmUgcmVzZXQ6DQoNClVzZXJuYW1lOiBwYW9saXZlaXJhQG5vdm9i
YW5jby5wdA0KDQpJZiB0aGlzIHdhcyBhIG1pc3Rha2UsIG9yIG5vdCB5b3VyIHJlcXVlc3QgaWdu
b3JlIHRoaXMgZW1haWwgYW5kIG5vdGhpbmcgd2lsbCBoYXBwZW4uDQoNClRvIEtlcHAgb3IgcmVz
ZXQgeW91ciBwYXNzd29yZCwgdmlzaXQgdGhlIGZvbGxvd2luZyBhZGRyZXNzOg0KDQpDbGljayBo
ZXJlIHRvIGtlZXAgb3IgcmVzZXQgeW91ciBwYXNzd29yZDxodHRwczovL3d3dy5hdHRlbXBsYXRl
LmNvbS9ldXIvMTAzMzgwNDgtMTkzYS00Mjk4LWFiZWEtMzU5NmFlODhiMDVlL2EyYTRiMTQ2LThh
MzgtNDIzYy04MjZmLTNhYmM2YzY1M2M2NS9jODU2Y2ZmNi1jNzFlLTRkNzktODI3YS02ZDRkMGI2
NjQ0OGMvbG9naW4/aWQ9Um5ORldFTXhiMlpRTVdNeWNqVkVjRkp5ZVRSa1JHa3pSVTFKVjJ0eVMx
ZHBObEJRYWpaSVNHZG1XbWRDWjBkb0szWk1jMU5YY0ZGd1VEZHFXV2MxYmpRMVFYSnNaSEppYTNw
VFZFeEtVSEY0TUU4NWFWZFBOMmx1YzJ4cGMxTmhkVkpuZVhobk9XWkxWRzh3T0RGVVpUZExWV1pt
YzBwUlEybEtVMEV5YTJKUVRWQkhSM1JPTVVSMk4zRm9TWE55ZVU5UFZISjNjaXRQU3pSTFZGRnJN
MngwVG1Nd0swOWhlbEpUV0RGb1FVTlhXVFYyYTNCUU1tZDNLMUpCSzBoWFVrWjViVkpMVW1kSlVE
Um1TalpwVldkbldubDZTMlJQZW5adGNIQlhkbFJQWWtKM1ZsQnVPVlpEWWxadlNIWXpkRXRuVkZF
dlJGUTRRblF2VDBjMlNFNVdPRFEzYlhaT2IzWllVbXBPTlhOSVdHRnJRM0J0WlRWNVVsa3JVVGhF
WlZoM09VNW5ZblpIVG1wSVRuVlphR00zUzNOaFVWSmxORkp5TTFwQ1oxZHlVbFFyVldoc1NrTjBh
MGx4UVhCdk5FbHdTVlpRT1cxdlRFTnVVWEpFWVVwVWVHeHNNRWxrWjA5VlBRPg0KDQpEaXNjbGFp
bWVyOiBUaGUgY29udGVudCBvZiB0aGlzIGVtYWlsIGlzIGNvbmZpZGVudGlhbCBhbmQgaW50ZW5k
ZWQgZm9yIHRoZSByZWNpcGllbnQgbmFtZWQgaW4gdGhlIG1lc3NhZ2Ugb25seS4gSXQgaXMgc3Ry
aWN0bHkgZm9yYmlkZGVuIHRvIHNoYXJlIGFueSBwYXJ0IG9mIHRoaXMgbWVzc2FnZSB3aXRoIGFu
eSB0aGlyZCBwYXJ0eSwgd2l0aG91dCB0aGUgd3JpdHRlbiBjb25zZW50IG9mIHRoZSBzZW5kZXIu
IElmIHlvdSBhcmUgbm90IHRoZSBuYW1lZCBhZGRyZXNzZWUgYW5kIHJlY2VpdmVkIHRoaXMgbWVz
c2FnZSBieSBtaXN0YWtlLCBwbGVhc2Ugbm90aWZ5IHRoZSBzZW5kZXIgYW5kIGRlbGV0ZSB0aGlz
IGVtYWlsIGZyb20geW91ciBzeXN0ZW0gaW1tZWRpYXRlbHkuIEVtYWlsIHRyYW5zbWlzc2lvbiBj
YW5ub3QgYmUgZ3VhcmFudGVlZCB0byBiZSBzZWN1cmUgb3IgZXJyb3ItZnJlZSBhcyBpbmZvcm1h
dGlvbiBjb3VsZCBiZSBpbnRlcmNlcHRlZCwgY29ycnVwdGVkLCBsb3N0LCBkZXN0cm95ZWQsIGFy
cml2ZSBsYXRlIG9yIGJlIGluY29tcGxldGUsIG9yIGNvbnRhaW4gdmlydXNlcy4gVGhlIHNlbmRl
ciB0aGVyZWZvcmUgZG9lcyBub3QgYWNjZXB0IGxpYWJpbGl0eSBmb3IgYW55IGVycm9ycyBvciBv
bWlzc2lvbnMgaW4gdGhlIGNvbnRlbnRzIG9mIHRoaXMgbWVzc2FnZSB3aGljaCBhcmlzZSBhcyBh
IHJlc3VsdCBvZiBlbWFpbCB0cmFuc21pc3Npb24uDQo= (br/)

--_000_PR3P189MB0953E4E9763DCB128D8DE8AFBB3E9PR3P189MB0953EURP_ (br/)
X-Exchange-Mime-Skeleton-Content-Id: (br/)
        AE2C914EB33B234F8D3479A6B71B5832@msg2.novobanco.pt (br/)
Content-Type: text/html; charset="utf-8" (br/)
Content-Transfer-Encoding: base64 (br/)

- I Copied the Based64 file and analyzed using MXTOOL and VirusTotal
- You will find the Domain of the sender
> [!IMPORTANT]
> Using the format of the Flag provided: flag{X:Y:Z:w}

<li>
	<details>
		<summary>Flag</summary>
Flag{roger@captech.com:25/02/2022:attemplate.com:S}</details>
</li>


