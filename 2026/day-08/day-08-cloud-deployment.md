Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

Part 1: Launch Cloud Instance & SSH Access
Step 1: Create a Cloud Instance
go to aws console>login>EC2>instances>create instance>create keypair>launch>connect>SSH Client>Launch

Step 2: Connect via SSH
cmd: cd /c/Users/YourWindowsUsername/Downloads
=>ls
=>cd Downloads/(where your keypair is downloaded)
=>ls keyname
=>chmod 400"keyname-keypair.pem"
=>ssh -i keynanme ubuntu@ public-ip

Part 2: Install Nginx and Docker
step1: in gitbash/linux
cmd: sudo apt update
step2: sudo apt upgrade
step3: sudo apt install nginx
<img width="1156" height="378" alt="image" src="https://github.com/user-attachments/assets/1887955b-cabe-4b65-86f7-bf3aba2af82d" />
step4:Verify Nginx is running:
=>systemctl status nginx
<img width="1324" height="474" alt="image" src="https://github.com/user-attachments/assets/d5534ea1-4121-4bab-9dee-654dee06a7f1" />

Part 3: Security Group Configuration 
steps: go to instance> security>security Groups>Edit Inbound Rules>Add rule>port range-80>give CIDR-blocks(0.0.0.0/0)>save rules.
Then take publich ipv from instances and test in web browser using http only not https.
Test Web Access: Open browser and visit: http://<your-instance-ip>
You should see the Nginx welcome page!
📸 Screenshot 
<img width="1917" height="822" alt="image" src="https://github.com/user-attachments/assets/c0eee41b-3c34-437b-b853-0e125e753cc8" />

Part 4: Extract Nginx Logs
Step 1: Connect your server from local machine
cmd: ssh -i day-08-keypair.pem ubuntu@44.252.6.156

STEP 2 — View Nginx Logs
cmd: sudo tail -n 20 /var/log/nginx/access.log
<img width="1909" height="140" alt="image" src="https://github.com/user-attachments/assets/53d46f64-8cd1-482e-8b04-9d97ac00608a" />

To view Error logs
cmd: sudo tail -n 20 /var/log/nginx/error.log
<img width="874" height="53" alt="image" src="https://github.com/user-attachments/assets/05b0af18-185d-41f5-97e1-d835f601decf" />

Step 3: Save Logs to New File
=> Copy Logs to Your Home Directory
cmd: sudo cp /var/log/nginx/access.log /home/ubuntu/nginx-logs.txt

You cannot directly download from /var/log/ easily because of permissions.
Giving ownership 
cmd: sudo chown ubuntu:ubuntu /home/ubuntu/nginx-logs.txt
cmd: ls /home/ubuntu

STEP 4 — Exit Server
cmd:exit

STEP 5 — Download Log File to Local Machine
cmd: scp -i day-08-keypair.pem ubuntu@44.252.6.156:/home/ubuntu/nginx-logs.txt 
<img width="1916" height="148" alt="image" src="https://github.com/user-attachments/assets/a1ddd558-4c6f-4007-b0d0-09bdc3e93bce" />

STEP 6 — Confirm Download
cmd: ls nginx-logs.txt
then, cmd: cat nginx-logs.txt
<img width="1920" height="167" alt="image" src="https://github.com/user-attachments/assets/b976d1aa-29f2-41f8-98dd-6a83ed90f2cd" />







