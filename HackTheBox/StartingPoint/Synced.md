Task 1:
What is the default port for rsync?
873
Task 2:
How many TCP ports are open on the remote host?
nmap -sC -sV -p- TARGET.IP -> 1 otwarty port TCP
Task 3:
What is the protocol version used by rsync on the remote machine?
nmap pokazuje wersje 31
Task 4:
What is the most common command name on Linux to interact with rsync?
rsync
Task 5:
What credentials do you have to pass to rsync in order to use anonymous authentication? anonymous:anonymous, anonymous, None, rsync:rsync
none
Task 6:
What is the option to only list shares and files on rsync? (No need to include the leading -- characters)
list-only
Flag:
komenda rsync -av rsync://TARGET.IP/public/flag.txt flag.txt
cat flag.txt
72eaf5344ebb84908ae543a719830519
