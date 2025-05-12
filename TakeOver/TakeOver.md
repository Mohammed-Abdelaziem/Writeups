<div align="center">
  
# بسم الله الرحمن الرحيم  

</div>

# TryHackMe: TakeOver Writeup by Mohammed (Azima)

![image](https://github.com/user-attachments/assets/a1f2a34b-24f3-4182-8478-379161a3e110)


**Room Link:** [TakeOver](https://tryhackme.com/room/takeover)
  **Difficulty:** Easy  

## Reconnaissance

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


##I thinked of what was Written that he is building “Support” also he writes “Blogs” so lets see them 
#first added them:


Result:

![image](https://github.com/user-attachments/assets/c277ca0c-6b86-4e55-8ea8-4026262c5de7)


Lets see Certificate first before continuing:

![image](https://github.com/user-attachments/assets/688c71ea-6692-4367-a4a2-fa4a9b92a605)


Have DNS Lets add it to local host and open it in new tab and BOOM:

![442798695-04c0938f-3cd1-4d26-9594-f0f1c997e190](https://github.com/user-attachments/assets/ce464e83-aa2b-4942-bdbe-4ebdb567fdb0)

# Flag Found
## Lessons Learned


---

🔗 **More Writeups:** [My GitHub Security Writeups](https://github.com/Mohammed-Abdelaziem/Writeups)
