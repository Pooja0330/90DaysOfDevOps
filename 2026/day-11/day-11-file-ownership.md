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
