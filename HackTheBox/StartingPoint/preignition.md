Task 1:
Directory Brute-forcing is a technique used to check a lot of paths on a web server to find hidden pages. Which is another name for this? (i) Local File Inclusion, (ii) dir busting, (iii) hash cracking.
dir busting
Task 2: 
What switch do we use for nmap's scan to specify that we want to perform version detection
-sV
Task 3:
What does Nmap report is the service identified as running on port 80/tcp?
http
Task 4:
What server name and version of service is running on port 80/tcp?
nginx 1.14.2
Task 5:
What switch do we use to specify to Gobuster we want to perform dir busting specifically?
dir
Task 6:
When using gobuster to dir bust, what switch do we add to make sure it finds PHP pages?
-x php
Task 7:
What page is found during our dir busting activities?
gobuster dir -u http://10.129.13.19 -w /usr/share/seclists/Discovery/Web-Content/DirBuster-2007_directory-list-lowercase-2.3-small.txt -x php ---> admin.php
Task 8:
What is the HTTP status code reported by Gobuster for the discovered page?
200
Flag:
pod adresem TARGET.IP/admin.php znajduje sie panel admina. Probujemy admin:admin i otrzymujemy flage:
6483bee07c1c1d57f14e5b0717503c73
