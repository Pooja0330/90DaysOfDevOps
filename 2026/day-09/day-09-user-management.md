Task 1: Create Users 
Create three users with home directories and passwords:
tokyo
berlin
professor
Verify: Check /etc/passwd and /home/ directory

👤 Task 1: Create Users
sudo useradd -m tokyo
To set password:
sudo passwd tokyo
pass-tokyo@123
confirm pass- tokyo@123

sudo useradd -m berlin
To set password:
sudo passwd berlin
pass-berlin@123
confirm pass- berlin@123

sudo useradd -m professor
To set password:
sudo passwd professor
pass-professor@123
confirm pass- professor@123

<img width="972" height="378" alt="image" src="https://github.com/user-attachments/assets/39def722-99eb-4c84-8ab3-edf193d64e87" />

Verification:
cat /etc/passwd | grep -E "tokyo|berlin|professor"
<img width="953" height="96" alt="image" src="https://github.com/user-attachments/assets/f75b7efe-510e-4616-9bc3-71e77f509eb9" />

ls -l /home/
<img width="790" height="158" alt="image" src="https://github.com/user-attachments/assets/9646e20a-1f9b-485e-83c7-02710c798772" />

Task 2: Create Groups 
Create two groups:
developers
admins
Verify: Check /etc/group

sudo groupadd developers
sudo groupadd admins
verification: cat /etc/group | grep -E "developers|admins"
<img width="1012" height="134" alt="image" src="https://github.com/user-attachments/assets/fb779dc2-af94-4ca8-bf08-27f3533a65e4" />

Task 3: Assign Users to Groups
cmd:
sudo usermod -aG developers tokyo
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
sudo usermod -aG developers professor

to verify:
groups tokyo
groups berlin
groups professor
<img width="575" height="163" alt="image" src="https://github.com/user-attachments/assets/732f46fb-7bf3-4ac9-a611-32eb291c0914" />

OR
cat /etc/groups
<img width="660" height="602" alt="image" src="https://github.com/user-attachments/assets/d78607df-d6a5-4eca-b607-fa1d05ffdd20" />

Task 4: Shared Directory – /opt/dev-project
Create Directory
sudo mkdir -p /opt/dev-project

Set Group Ownership
sudo chown :developers /opt/dev-project

Set Permissions (775)
sudo chmod 775 /opt/dev-project

Verification
ls -ld /opt/dev-project
<img width="880" height="136" alt="image" src="https://github.com/user-attachments/assets/a9d46c21-9e4a-4094-96ee-5549c6cffc4d" />

su - tokyo
touch /opt/dev-project/tokyo-file.txt
exit

Test as berlin
su - berlin
touch /opt/dev-project/berlin-file.txt
exit

verify files:
ls -l /opt/dev-project


Task 5: Team Workspace
Create User
sudo useradd -m nairobi
sudo passwd nairobi
pass-nairobi@123
<img width="999" height="434" alt="image" src="https://github.com/user-attachments/assets/c5ee2b2a-5304-41fe-806a-37e39ceb9c3d" />

create group
sudo groupadd project-team

Add Users to Group
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
<img width="746" height="130" alt="image" src="https://github.com/user-attachments/assets/af6a977b-8cf5-40f0-8469-1547b16df410" />

Create Workspace Directory
sudo mkdir -p /opt/team-workspace

Set Group Ownership
sudo chown :project-team /opt/team-workspace

Set Permissions (775)
sudo chmod 775 /opt/team-workspace

Verification
ls -ld /opt/team-workspace
<img width="872" height="157" alt="image" src="https://github.com/user-attachments/assets/0eadd7f7-6181-4a33-809f-c97c95176a6e" />

Test as nairobi
su - nairobi
<img width="512" height="71" alt="image" src="https://github.com/user-attachments/assets/f9f369ae-bcc2-4cb1-a925-96198baef2e3" />

touch /opt/team-workspace/nairobi-file.txt
exit

Verify
ls -l /opt/team-workspace
<img width="730" height="133" alt="image" src="https://github.com/user-attachments/assets/d3162fba-922f-4112-97a1-2d4634a4b5a3" />
















