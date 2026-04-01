# Hack The Box - Ignition

Difficulty: Very Easy  
OS: Linux  
IP: 10.129.1.27  

---

# 0. Task Answers

Task 1: Which service version is found to be running on port 80?  
nginx 1.14.2  

Task 2: What is the 3-digit HTTP status code returned when you visit http://{machine IP}/?  
302  

Task 3: What is the virtual host name the webpage expects to be accessed by?  
ignition.htb  

Task 4: What is the full path to the file on a Linux computer that holds a local list of domain name to IP address pairs?  
/etc/hosts  

Task 5: What is the full URL to the Magento login page?  
http://ignition.htb/admin  

Task 6: Which password provides access to the admin account?  
qwerty123  

Flag:  
797d6c988d9dc5865e010b9410f247e0  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- 10.129.1.27

Result:

PORT     STATE SERVICE VERSION  
80/tcp   open  http    nginx 1.14.2  

Notes:

- HTTP service running on port 80  

Moje notatki:

nmap -sC -sV -p- 10.129.1.27 -> nginx 1.14.2 port 80  

---

# 2. Enumeration

## Web enumeration

Visit website:

http://10.129.1.27  

Findings:

- HTTP 302 redirect  
- page requires proper hostname  

Moje notatki:

burp przy wejsciu na strone pokazuje blad http 302  

---

## Virtual Host configuration

Add to `/etc/hosts`:

10.129.1.27 ignition.htb  

Moje notatki:

musimy dodac host ignition.htb do /etc/hosts  

---

## Web enumeration (correct host)

Visit website:

http://ignition.htb  

Findings:

- Magento application detected  

---

## Directory brute force

Command:

gobuster dir -u http://ignition.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt  

Discovered directories:

/admin  

Moje notatki:

enumeracja gobuster dir -u http://ignition.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt  
/admin status 200  

---

## Login panel

URL:

http://ignition.htb/admin  

Findings:

- Magento admin panel  
- hint about password requirements  
- suggestion to check common passwords  

Moje notatki:

dostajemy podpowiedz zeby sprawdzic wymagania hasel dla Magento oraz zeby sprawdzic najczesciej uzywane hasla w 2023  
Wiemy ze login to admin  

---

# 3. Exploitation

## Vulnerability

Weak credentials  

---

## Payload

Username: admin  
Password: qwerty123  

Result:

- successful login  
- access to admin panel  

Moje notatki:

po krotkim researchu sprawdzamy haslo qwerty123 -> sukces  

---

# 4. Privilege Escalation

Not required  

---

# 5. Flags

Root flag:

cat from admin panel  

Result:

797d6c988d9dc5865e010b9410f247e0  

Moje notatki:

po zalogowaniu sie dostajemy flage: 797d6c988d9dc5865e010b9410f247e0  

---

# 6. Lessons Learned

- virtual hosts must be configured locally  
- always check `/etc/hosts` when encountering redirects  
- directory brute forcing is essential  
- weak passwords remain a major vulnerability  

---

# Tools Used

- nmap  
- gobuster  
- burp suite  
- seclists  

---

# References

- https://github.com/danielmiessler/SecLists  
