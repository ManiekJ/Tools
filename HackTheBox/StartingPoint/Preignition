# Hack The Box - Preignition

Difficulty: Very Easy  
OS: Linux  
IP: TARGET.IP  

---

# 0. Task Answers

Task 1: Directory Brute-forcing is also known as:  
dir busting  

Task 2: What switch do we use for nmap's scan to specify version detection?  
-sV  

Task 3: What service is identified as running on port 80/tcp?  
http  

Task 4: What server name and version is running on port 80/tcp?  
nginx 1.14.2  

Task 5: What switch do we use in gobuster for directory busting?  
dir  

Task 6: What switch is used to find PHP pages in gobuster?  
-x php  

Task 7: What page is found during directory busting?  
admin.php  

Task 8: What HTTP status code is reported by Gobuster for the discovered page?  
200  

Flag:  
6483bee07c1c1d57f14e5b0717503c73  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV TARGET.IP  

Result:

PORT     STATE SERVICE VERSION  
80/tcp   open  http    nginx 1.14.2  

Notes:

- Web server running on port 80  
- nginx version 1.14.2  

Moje notatki:

nmap -sV -> -sV  
port 80 -> http  
nginx 1.14.2  

---

# 2. Enumeration

## Directory brute forcing

Tool:

gobuster  

Command:

gobuster dir -u http://TARGET.IP -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-lowercase-2.3-small.txt -x php  

Switches used:

- dir → directory mode  
- -x php → search for PHP files  

Moje notatki:

gobuster dir  
-x php  

---

## Findings

- discovered page: admin.php  
- HTTP status: 200  

Moje notatki:

admin.php  
status 200  

---

# 3. Exploitation

## Accessing admin panel

URL:

http://TARGET.IP/admin.php  

Login attempt:

- username: admin  
- password: admin  

Result:

- successful login  
- flag retrieved  

Moje notatki:

admin:admin → flag  

---

# 4. Privilege Escalation

Not required  

---

# 5. Flags

Flag:

6483bee07c1c1d57f14e5b0717503c73  

---

# 6. Lessons Learned

- directory brute forcing is essential in web enumeration  
- always test common credentials like admin:admin  
- hidden admin panels are often exposed via weak configurations  
- gobuster is a powerful tool for discovering hidden content  
- combining enumeration + default creds often leads to quick wins  

---

# Tools Used

- nmap  
- gobuster  

---

# References

- https://github.com/OJ/gobuster  
- https://nmap.org/book/man.html  
