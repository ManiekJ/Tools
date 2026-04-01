# Hack The Box - Explosion

Difficulty: Very Easy  
OS: Windows  
IP: TARGET.IP  

---

# 0. Task Answers

Task 1: What does the 3-letter acronym RDP stand for?  
Remote Desktop Protocol  

Task 2: What is a 3-letter acronym for command line interface?  
CLI  

Task 3: What about graphical user interface?  
GUI  

Task 4: What is the name of the old remote access tool on TCP port 23?  
Telnet  

Task 5: What is the name of the service running on port 3389 TCP?  
ms-wbt-server  

Task 6: What switch is used to specify the target host IP in xfreerdp?  
/v:  

Task 7: What username successfully returns a desktop with a blank password?  
Administrator  

Flag:  
951fa96d7830c451b536be5a6be008a0  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- TARGET.IP  

Result:

PORT      STATE SERVICE        VERSION  
3389/tcp  open  ms-wbt-server  

Notes:

- RDP service exposed on port 3389  
- Windows Remote Desktop enabled  

Moje notatki:

nmap -sC -sV -p- TARGET.IP -> ms-wbt-server  

---

# 2. Enumeration

## RDP Access

Tool:

xfreerdp  

Command:

xfreerdp /v:TARGET.IP /u:Administrator  

Notes:

- tried connecting with blank password  

Moje notatki:

xfreerdp /v:TARGET.IP /u:Administrator  

---

# 3. Exploitation

## Remote Desktop Access

Result:

- successful login using:  
  - username: Administrator  
  - password: (blank)  

Alternative:

- Remmina (GUI client)  

Moje notatki:

użycie remmina  
Administrator + blank password  

---

# 4. Privilege Escalation

Not required  

---

# 5. Flags

Flag:

951fa96d7830c451b536be5a6be008a0  

---

# 6. Lessons Learned

- RDP can be exposed with weak or no authentication  
- default accounts like Administrator are often targeted  
- always test blank passwords  
- GUI tools can simplify exploitation  
- remote desktop services should be properly secured  

---

# Tools Used

- nmap  
- xfreerdp  
- remmina  

---

# References

- https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/  
