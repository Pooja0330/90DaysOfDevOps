Part 2: Scenario-Based Practice

SOLVED EXAMPLE: Understanding How to Approach Scenarios

Question: How do you check if the 'nginx' service is running?
Ans: 
step:1=> It shows if the service is active, failed, or stopped.
cmd: systemctl status nginx.

step:2=> Step 2: If service is not found, list all services
cmd: systemctl list-units --type=service.

Step 3: Check if service is enabled on boot
cmd: systemctl is-enabled nginx.

Scenario-1:
Service Not Starting:=>
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.

step-1: check if the status is active or not.
cmd: systemctl status myapp.

step-2: What do the logs say?
cmd: systemctl is-enabled myapp.

step-3: Finally check: Is it enabled to start on boot?
journalctl -u myapp -n 50.

since, the myapp isn't installed in the sys it showed error, to resolve that issue.
I ran commands:
Step 1: List existing services (find the real name)
first: systemctl list-units --type=service | grep app
<img width="1920" height="136" alt="image" src="https://github.com/user-attachments/assets/df9a1e58-fd86-4766-8890-6d34778c0cd0" />

Step 2: Check service files directly
cmd: ls /etc/systemd/system/
<img width="1920" height="223" alt="image" src="https://github.com/user-attachments/assets/250ea26f-4a1d-4ff8-b292-4827c97d6739" />

then, ls /lib/systemd/system/
<img width="1902" height="611" alt="image" src="https://github.com/user-attachments/assets/fb1fbf64-f2b4-4b1d-baa1-5f87d9aa619d" />
<img width="1907" height="599" alt="image" src="https://github.com/user-attachments/assets/987642c3-dd83-444e-8c76-85d52317bce9" />
<img width="1915" height="602" alt="image" src="https://github.com/user-attachments/assets/955cb6dd-27fd-46d9-815e-0ca2409a4a2f" />
=> Because custom apps often install their .service files here.

⚠️ Scenario 2: High CPU Usage
Goal: Identify which process is consuming CPU.
Step 1: View live CPU usage
cmd: top
=>Shows real-time CPU usage and highlights the most resource-hungry processes.
<img width="1920" height="661" alt="image" src="https://github.com/user-attachments/assets/189a4715-a637-4171-9e10-2378cb445191" />

step2: Sort processes by CPU usage.
Brings the highest CPU-consuming process to the top.
=> Shift+P

step3: Note the PID of the top process
Why: The PID is needed for deeper investigation or to restart/kill the process.

step4: Confirm with a snapshot view
cmd: ps aux --sort=-%cpu | head -10
Why: Gives a quick, sorted list of top CPU consumers without live interaction.
<img width="1283" height="274" alt="image" src="https://github.com/user-attachments/assets/65543cac-3c73-4731-a9e9-ae2abe801301" />

📄 Scenario 3: Finding Service Logs (docker)
Step 1: Check service status\
cmd: systemctl status docker

since docker wasn't installed into the system, did these following steps
1️⃣ Update package index
sudo apt update
2️⃣ Install prerequisite packages
sudo apt install -y \ca-certificates \curl \gnupg \lsb-release
=>These help add Docker’s official repository.
3️⃣ Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
4️⃣ Add Docker’s repository
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  <img width="1502" height="550" alt="image" src="https://github.com/user-attachments/assets/c7ebf230-5ee0-47e3-8b93-1e2e04040ad8" />

5️⃣ Update package index again
sudo apt update
6️⃣ Install Docker Engine
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
7️⃣ Start and enable Docker
=> sudo systemctl start docker
=> sudo systemctl enable docker
<img width="1335" height="99" alt="image" src="https://github.com/user-attachments/assets/60183bf7-2296-4a50-8439-d67162c47abb" />

8️⃣ Verify installation
docker --version
<img width="613" height="73" alt="image" src="https://github.com/user-attachments/assets/7b57b194-8d0e-47d3-b29f-a3224df7f15d" />

Now, sudo usermod -aG docker $USER
  check whether docker installed or not, and it's staus
  sudo usermod -aG docker $USER
  sudo systemctl status docker
  <img width="1920" height="582" alt="image" src="https://github.com/user-attachments/assets/6b2819bf-a2a4-4127-a6a3-7ec4652dece1" />
then test, sudo docker run hello-world
<img width="1920" height="598" alt="image" src="https://github.com/user-attachments/assets/a847cc4f-bee4-43df-a719-a59b8db1b813" />

🔐 Scenario 4: File Permissions Issue (backup.sh)
Step 1: Check current permissions
cmd: cd ~
pwd
step2: create a file.
vim backup.sh
<img width="740" height="250" alt="image" src="https://github.com/user-attachments/assets/0332885d-438d-48aa-ba46-11d714e05225" />
Step 3 — Check permissions
ls -l backup.sh
<img width="807" height="107" alt="image" src="https://github.com/user-attachments/assets/9e4112c7-b797-478b-bc8f-4bb031806ba4" />

Step 4 — Try running it (this should fail)
<img width="589" height="109" alt="image" src="https://github.com/user-attachments/assets/35995403-9c21-435d-a056-aba333a676f7" />
Step 5 — Fix the permission
chmod +x backup.sh
then, ls -l backup.sh
<img width="617" height="105" alt="image" src="https://github.com/user-attachments/assets/f6c9748b-12cd-44d5-9b3f-749cdacaca2b" />
<img width="744" height="67" alt="image" src="https://github.com/user-attachments/assets/da1b81cd-11c4-4373-8931-f6adb9ce136a" />













