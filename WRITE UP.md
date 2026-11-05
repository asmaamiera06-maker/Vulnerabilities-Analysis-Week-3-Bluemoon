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
I started with finding the open ports with nmap. The IP assigned to the virtual box is 192.168.100.35

<img width="272" height="128" alt="image" src="https://github.com/user-attachments/assets/644baa74-2c11-4e5f-ad6f-3e305d882132" />

Let's visit the web page in the browser. There is nothing unusual here, but let's try using gobuster to find hidden directories.
<img width="635" height="232" alt="image" src="https://github.com/user-attachments/assets/d5c81670-da9d-4168-b336-82b1bdf73938" />
gobuster dir -u http://192.168.56.100/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
<img width="448" height="156" alt="image" src="https://github.com/user-attachments/assets/55d802ef-2ce4-4674-a527-522b2a46bb65" />


<img width="634" height="127" alt="image" src="https://github.com/user-attachments/assets/042fed51-db0e-481c-a49a-56f14d31e6ba" />






