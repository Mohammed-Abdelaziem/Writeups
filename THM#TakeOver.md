<div align="center">
  
# بسم الله الرحمن الرحيم  

</div>

# TryHackMe: TakeOver Writeup by Mohammed (Azima)

![image](https://github.com/user-attachments/assets/a1f2a34b-24f3-4182-8478-379161a3e110)


**Room Link:** [TakeOver](https://tryhackme.com/room/takeover)
  **Difficulty:** Easy  

## Reconnaissance



```bash
nmap -sV -A -T4 <TARGET_IP>
````

### Open Ports and Services

|   Port  | Service |              Version              |
| :-----: | :-----: | :-------------------------------: |
|  22/tcp |   SSH   | OpenSSH 8.2p1 (Ubuntu 4ubuntu0.4) |
|  80/tcp |   HTTP  |    Apache httpd 2.4.41 (Ubuntu)   |
| 443/tcp |  HTTPS  |    Apache httpd 2.4.41 (Ubuntu)   |

### Additional Information:

* SSH host keys (RSA, ECDSA, ED25519) were collected.
* Port 80 redirected to HTTPS (`https://futurevera.thm/`).
* The SSL certificate details on port 443:

  * **Common Name:** `futurevera.thm`
  * **Organization:** Futurevera
  * **Location:** Oregon, US
  * **Validity:** Expired (2022-03-13 to 2023-03-13)

---

## Exploring the Website

From the room description, hints suggested the development of a **Support** section and a **Blog**.
I added common subdomains (like `support.futurevera.thm` and `blog.futurevera.thm`) to my `/etc/hosts` file.

Result after visiting:

![Subdomains Result](https://github.com/user-attachments/assets/c277ca0c-6b86-4e55-8ea8-4026262c5de7)

---

## SSL Certificate Insights

Before proceeding further, I reviewed the SSL certificate:

![SSL Certificate](https://github.com/user-attachments/assets/688c71ea-6692-4367-a4a2-fa4a9b92a605)

---

## DNS Discovery and Adding to Hosts

After discovering the DNS records, I added them to my local `/etc/hosts` file. Upon visiting the new domain...

**BOOM! Access achieved:**

![Access Success](https://github.com/user-attachments/assets/ce464e83-aa2b-4942-bdbe-4ebdb567fdb0)

---

## 🎯 Flag Found!

---

## 📚 Lessons Learned

* Always explore SSL certificates for potential subdomains.
* Pay attention to small hints in web pages (like "Support" and "Blogs").
* Subdomain enumeration and manual DNS mapping are critical skills in reconnaissance.
* Expired certificates and misconfigured DNS entries can lead to critical findings.


---

🔗 **More Writeups:** [My GitHub Security Writeups](https://github.com/Mohammed-Abdelaziem/Writeups)
