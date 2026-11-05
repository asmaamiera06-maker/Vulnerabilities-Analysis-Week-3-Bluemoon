ASMA AMIERA BINTI MOHAMAD HAFEDZ 52215125506 Vulnerabilities Anlysis Bluemoon  LAB : L01-B01 


PENTEST TESTING METHADOLOGY 

1. Reconnaissance - netdiscover
2. Scanning - nmap
3. Gaining Access - gobuster, ftp, hydra, ssh
4. Privilege Escalation - sudo -l, feedback.sh
5. Maintain Access - Python shell upgrade
6. Clear Tracks - history -c

First open the Kali Linux And go to root terminal and type ifconfig to know our ip (attacker ip)  

<img width="365" height="173" alt="image" src="https://github.com/user-attachments/assets/d3517763-3561-49db-b02c-23d51f0e12fc" />

Then use netdiscover to find the target of network 

<img width="340" height="151" alt="image" src="https://github.com/user-attachments/assets/c4c75845-bdf3-4792-933a-255d0446df57" />

I started with finding the open ports with nmap. The IP assigned to the virtual box is 192.168.56.100

<img width="272" height="128" alt="image" src="https://github.com/user-attachments/assets/644baa74-2c11-4e5f-ad6f-3e305d882132" />

Let's visit the web page in the browser. There is nothing unusual here, but let's try using gobuster to find hidden directories.

<img width="635" height="232" alt="image" src="https://github.com/user-attachments/assets/d5c81670-da9d-4168-b336-82b1bdf73938" />

gobuster dir -u http://192.168.56.100/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

<img width="448" height="156" alt="image" src="https://github.com/user-attachments/assets/55d802ef-2ce4-4674-a527-522b2a46bb65" />

directory /hidden_text . Let's check it out

<img width="634" height="127" alt="image" src="https://github.com/user-attachments/assets/042fed51-db0e-481c-a49a-56f14d31e6ba" />

The "Thank You" text is in blue color which means clickable. Click on it. 12. A QR code is displayed.

<img width="672" height="235" alt="image" src="https://github.com/user-attachments/assets/605e60f7-81fb-4f22-b55f-a295588e537e" />

FTP Access

When I scanned the QR code, it showed the following credentials:

HOST = ip USER = userftp PASSWORD = fttp@ssword

Proceed to log in and I found two .txt files: information.txt p_lists.txt

Download both files using: get information.txt get p_lists.txt

<img width="678" height="68" alt="image" src="https://github.com/user-attachments/assets/0c588b54-c713-41c7-b0f5-b84a49ee7144" />

Password Wordlist p_lists.txt

<img width="146" height="400" alt="image" src="https://github.com/user-attachments/assets/3036a838-0170-462f-bc70-830a0e634e92" />

GAINING ACCESS

I used Hydra to brute-force SSH login using the username and password list.

<img width="676" height="172" alt="image" src="https://github.com/user-attachments/assets/64d39893-e14e-4cd6-bd51-a0b21c04e02d" />

Credentials discovered:

Login: robin Password: k4rv3ndh4nh4ck3r SSH Login

Login using SSH:

ssh robin@192.168.56.100

<img width="290" height="114" alt="image" src="https://github.com/user-attachments/assets/d4bfa655-0c3b-4390-af67-c2af6c0158c5" />

I found the first flag in Robin's home directory.

PRIVILEGE ESCALATION

Check what commands the user can run as sudo.

sudo -l

<img width="641" height="238" alt="image" src="https://github.com/user-attachments/assets/be05677b-b1e8-42a9-a5ad-d5c2ddf305c3" />

It shows that the user can run feedback.sh as user jerry.

Execute it: sudo -u jerry ./feedback.sh

After switching to jerry, I captured the second flag.

<img width="351" height="272" alt="image" src="https://github.com/user-attachments/assets/6b87041c-4e9c-4ad4-ab8c-6eb620c288cf" />

MAINTAIN ACCESS

Shell Upgrade To get the third flag, we must escalate to root.

Upgrade the current shell:

python -c 'import pty; pty.spawn("/bin/bash")'

Now we can proceed to find the last flag.

<img width="680" height="428" alt="image" src="https://github.com/user-attachments/assets/3cc86831-060f-47d6-84ca-b323842178d9" />

CLEAR TRACKS

delete or clear all the logsn and history.




