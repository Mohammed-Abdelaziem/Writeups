<div align="center">
  
# بسم الله الرحمن الرحيم  

</div>

# TryHackMe: TakeOver Writeup by Mohammed (Azima)

![image](https://github.com/user-attachments/assets/a1f2a34b-24f3-4182-8478-379161a3e110)


**Room Link:** [TakeOver](https://tryhackme.com/room/takeover)
  **Difficulty:** Easy  

## 1. Reconnaissance

### Nmap Scan
```bash
nmap -sV -A -T4 <TARGET_IP>
```
## Open Ports and Services
Ports Open:

22/tcp: SSH (OpenSSH 8.2p1 Ubuntu 4ubuntu0.4)

80/tcp: HTTP (Apache httpd 2.4.41 (Ubuntu))

443/tcp: HTTPS (Apache httpd 2.4.41 (Ubuntu))

Additional Information:
SSH Host Keys were gathered (RSA, ECDSA, ED25519).

HTTP title on port 80 indicated a redirect to HTTPS (https://futurevera.thm/).

HTTPS (port 443) presented an SSL certificate with:

Common Name: futurevera.thm

Organization: Futurevera

Location: Oregon, US

Certificate Validity: 2022-03-13 to 2023-03-13 (Expired)

### Web Enumeration


## 2. Exploitation


## 4. Lessons Learned


---

🔗 **More Writeups:** [My GitHub Security Writeups](https://github.com/Mohammed-Abdelaziem/Writeups)
