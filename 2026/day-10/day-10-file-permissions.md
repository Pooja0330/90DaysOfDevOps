Day 10 – File Permissions & File Operations Challenge

Master file permissions and basic file operations in Linux.

#Create and read files using touch, cat, vim

creation of file"-
cmd: touch day10file.txt
<img width="882" height="427" alt="image" src="https://github.com/user-attachments/assets/a596cf16-edc7-424e-8c01-2cf72e8e43db" />

to write inside the file:
cmd: vim day10file.txt
press i to start and write the save & exit using esc :wq

to view file in the system
cmd: cat day10file.txt
<img width="761" height="426" alt="image" src="https://github.com/user-attachments/assets/79111be3-78b0-4a2c-85b0-066894dd9634" />

#Understand and modify permissions using chmod

Challenge Tasks
Task 1: Create Files (10 minutes)
Create script.sh using vim with content: echo "Hello DevOps"
=> Create script.sh using vim
echo "Continuing with DevOps"
chmod+x script.sh
ls -l
<img width="789" height="493" alt="image" src="https://github.com/user-attachments/assets/a716a6ab-b0cd-485d-994e-c90e9d9951fa" />

Task 2: Read Files 
Read nday10file.txt using cat
<img width="761" height="426" alt="image" src="https://github.com/user-attachments/assets/79111be3-78b0-4a2c-85b0-066894dd9634" />

View script.sh in vim read-only mode
vim -r script.sh
<img width="1113" height="642" alt="image" src="https://github.com/user-attachments/assets/e3f391d7-0e8b-4dd1-8add-28169ede0e96" />

To exit:
Press Esc
Type :q
Press Enter

Display first 5 lines of /etc/passwd using head
head -n 5 /etc/passwd
<img width="550" height="241" alt="image" src="https://github.com/user-attachments/assets/6ac1184d-96b2-416a-9f3e-31ffaa752e05" />

Display last 5 lines of /etc/passwd using tail
tail -n 5 /etc/passwd
<img width="890" height="146" alt="image" src="https://github.com/user-attachments/assets/e20cb765-f054-4579-a137-8abd874e379e" />

#Task 3: Understand Permissions 
Format: rwxrwxrwx (owner-group-others)
r = read (4), w = write (2), x = execute (1)
Check your files: ls -l day10file.txt notes.txt script.sh
<img width="824" height="100" alt="image" src="https://github.com/user-attachments/assets/19c4774a-950b-43a7-b7e9-a081372e05d2" />

Answer: What are current permissions? Who can read/write/execute?
