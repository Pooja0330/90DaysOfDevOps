Day 11 – File Ownership Challenge (chown & chgrp)

Task 1: Understanding Ownership 
(a)Run ls -l in your home directory
cmd: ls -l
<img width="623" height="677" alt="image" src="https://github.com/user-attachments/assets/e62cdc93-453d-4bd4-931a-5d4963ce8b2f" />

(b)Identify the owner and group columns
Check who owns your files
Format: -rw-r--r-- 1 owner group size date filename
=>Columns Explained:
Field	Meaning
-rw-r--r--	Permissions
1	Number of links
owner	File owner (user)
group	File group
245	File size
Date	Last modified
filename	File name

Document: What's the difference between owner and group?
=>(i)Owner → The user who owns the file (full control by default).
  (ii)Group → A collection of users who share group-level permissions.
  (iii)Owner permissions apply only to that user.
  (iv)Group permissions apply to all users inside that group.

Task 2: Basic chown Operations:-
(a)Create File
=>touch devops_file.txt

(b)Check Current Owner
=> ls -l devops_file.txt
<img width="552" height="242" alt="image" src="https://github.com/user-attachments/assets/6be78f54-5918-41a4-831c-9f2a3811e678" />

(c)Create Users
sudo useradd tokyo
sudo useradd berlin

(d)Change Owner to tokyo
sudo chown tokyo devops_file.txt

ls -l devops_fie.txt

(e) change owner to berlin
sudo chown berlin devops_files.txt

Task 3: Basic chgrp Operations:-
(a)file creation: touch team-notes.txt
check: ls -l team-notes.txt

(b)Create Group
sudo groupadd heist-team

(c)Change Group
sudo chgrp heist-team team-notes.txt
ls -l team-notes.txt

Task 4: Change Owner & Group Together
(a)Create File: touch project-config.yaml
(b)Create User: sudo useradd professor
(c) change group and owner in single cmd:-
sudo chown: professor:heist-team project-config.yaml
(d) create directory
cmd: mkdir app-logs
change owner:
sudo chown berlin:heist-team app-logs
ls -l

Task 5: Recursive Ownership
(a)Create Structure
mkdir -p heist-project/vault
mkdir -p heist-project/plans
touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf

(b)Create Group
sudo groupadd planners

(c)Recursive Change
sudo chown -R professor:planners heist-project/

(D)Verify Recursively
ls -lR heist-project/

Task 6: Practice Challenge
create users
sudo useradd tokyo
sudo useradd berlin
sudo useradd nairobi

create groups
sudo groupadd vault-team
sudo groupadd tech-team

create directories and files:
mkdir bank-heist
touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt

Set Ownership:
sudo chown tokyo:vault-team bank-heist/access-codes.txt
sudo chown berlin:tech-team bank-heist/blueprints.pdf
sudo chown nairobi:vault-team bank-heist/escape-plan.txt

ls -l bank-heist/




