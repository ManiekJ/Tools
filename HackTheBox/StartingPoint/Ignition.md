nmap -sC -sV -p- 10.129.1.27 -> nginx 1.14.2 port 80
burp przyu wejsciu na strone pokazuje blad hhtp 302
musimy dodac host ignition.htb do /etc/hosts
enumeracja gobuster dir -u http://ignition.htb -w /usr/share/seclists/Discovery
/DNS/subdomains-top1million-20000.txt
/admin status 200
dostajemy podpowiedz zeby sprawdzic wymagania hasel dla Magento oraz zeby sprawdzic najczesciej uzywane hasla w 2023. Wiemy ze login to admin. po krotkim researchu sprawdzamy haslo qwerty123 -> sukces.
po zalogowaniu sie dostajemy flage: 797d6c988d9dc5865e010b9410f247e0

Task 1:
Which service version is found to be running on port 80?
nginx 1.14.2
Task 2:
What is the 3-digit HTTP status code returned when you visit http://{machine IP}/?
302
Task 3:
What is the virtual host name the webpage expects to be accessed by?
ignition.htb
Task 4:
What is the full path to the file on a Linux computer that holds a local list of domain name to IP address pairs?
/etc/hosts
Task 5:
Use a tool to brute force directories on the webserver. What is the full URL to the Magento login page?
http://ignition.htb/admin
Task 6:
Look up the password requirements for Magento and also try searching for the most common passwords of 2023. Which password provides access to the admin account?
qwerty123
Flag: 
797d6c988d9dc5865e010b9410f247e0
