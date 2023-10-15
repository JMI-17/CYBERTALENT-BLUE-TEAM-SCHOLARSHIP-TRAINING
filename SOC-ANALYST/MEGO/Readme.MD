# Category
- **Digital Forensics**

# Description
Mego is hiding something on his desktop and he always kept the secrets on the cloud<br />

# Tools
- Kali
- Volatility Tool
- John the Ripper

# Solution
- I was provided with a Link to download a file named: memdump123456789.mem.tar
- First, I tried to check the strings inside the mem dump file , and filtering the output to match only the word "flag" since that is what we are looking for.
- I tried a different CMD commands to get information from the file, for simplicity i will be showing just one with the result of useful info:<br />
$ cat file_name | strings | grep "flag"<br />
C:\Users\admin\Downloads\flag.txt.zip<br />

- I needed another tool to better analyze the dump,So after a brief research and some recommendations from other learners i found a couple of tools to dump info from our file, But we will be sticking with (Volatility Tool.
- I brife intro on how i set the tool up on kali:
1. Download Volatility3 source code zip file from: https://www.volatilityfoundation.org/...<br />
2. Extract it & rename it for ease of use.<br />
3. Install Python if not available (in my system it is already installed): <br />
$ sudo apt install python3<br />
4. Open Terminal and install dependencies for volatililty using below cmd:<br />
$ sudo apt install python3-pip python-setuptools build-essential<br />
5. Navigate into the volatility directory and hit the below cmd to install volatility:<br />
$ sudo python3 setup.py install<br />
- To confirm your installation using cmd:
$ python3 vol.py<br />
- I started by trying to determine image info by using the volatility tool:
$ python3 vol.py -f ./dir/path_to_mem_dump_file windows.info<br />

-  From the result we notice that the image belongs to: NTBuildLab 7601.17514.amd64fre.win7sp1_rtm.      so... windows7sp1
- Now, we know which profile to use: (win7sp1) and we know which file to scan for **(the "flag.txt.zip" file)**. So, we use it with the command:
$ python3 vol.py -f /path_to_mem_dump_file windows.filescan | grep -i "flag"<br />

I got result of all the files that matches "falg", i choose the one that located in the path (C:\Users\admin\Downloads\flag.txt.zip) to dump it by specifying its physical address in the command:<br />
$ python3 vol.py -f ./path_to_mem_dump_file windows.dumpfiles --physaddr 0x50dc4370<br />
I got a file.flag.txt.zip.dat. To get a .zip file we rename the file to enable us open it, But its passworded. we can use any password cracking tools like (fcrackzip , John the Ripper). To use john the Ripper tool, we need to have the hash of the file and in order to do so, we will convert our zip file into a txt file using the command:<br />
$ zip2john zip_file_name.zip > zip_file_name.txt <br />
now, we confirm that we have a hash for the file by using the command:<br />
# cat zip_file_name.txt<br />
I got a hash!After that, it's time to crack that hash by the tool "John the Ripper or Cyber Chef" with the command:<br />
# john zip_file_name.txt <br />

- **NOTE:** The default wordlist of john the ripper did not crack the password, Based on the challenge intro (the user always keeps his secrets on the cloud), we try to check the browser history. However, volatility3 does not support the needed plugin (iehistory) which only works on volatility2.
- Another Linux machine was setup which has volatility2 to check the browser history) the command is:
$ python2 vol.py -f memdump.mem --profile=Win7SP1x64 iehistory<br />
- from the output, this link was interesting:<br />
Record length: 0x480<br />
Location: Visited: admin@https://www.google.com/search?hl=arAE&source=hp&q=**aHR0cHM6Ly9naXN0LmdpdGh1Yi5jb20vZWd5Y29uZG9yL2VlYTQyZWZkY2M4YWZmZjZlY2E3ODllZmFkMDkyNGY0**&btnG=%D8%A8%D8%AD%D8%AB+Google%E2%80%8F&iflsig=AINFCbYAAAAAYNklBnHZ11BsWPswjKaNT4sXGZcL73d&gbv=1<br />
Last modified: 2021-06-28 00:25:40 UTC+0000<br />
- So, we’ll try to decode it using base64 with the command:<br />
$ echo "aHR0cHM6Ly9naXN0LmdpdGh1Yi5jb20vZWd5Y29uZG9yL2VlYTQyZWZkY2M4YWZmZjZlY2E3ODllZmFkMDkyNGY0" | base64 -d <br />
And the result was a link for a repository of a wordlist:https://gist.github.com/egycondor/eea42efdcc8afff6eca789efad0924f4<br />
I downloaded the new wordlist from that link and used it with john the ripper to crack the .txt file. When finished, we can see the cracked hash password among the result. However, to make the result (password) clearer we can use the command:<br />
$ john zip_file_name.txt --show<br />
- The password was: **g=ax6w{JPtHL./FdE&8ASVbu$rcmG?zZ**, and after using to open the .zip file, I got the flag :)
> [!IMPORTANT]
> Using the format of the Flag provided

<li>
	<details>
		<summary>Flag</summary>
flag{FF571983C5693A57024858E6529A7408D16791846918}</details>
</li>
