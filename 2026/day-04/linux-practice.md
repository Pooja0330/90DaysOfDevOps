1.Check running processes

(a)-This shows all running processes.
ps aux
<img width="1484" height="598" alt="image" src="https://github.com/user-attachments/assets/92ed1233-99c0-474b-8ea7-286320ec8677" />

(b)-This shows running processes live.
top
<img width="1262" height="556" alt="image" src="https://github.com/user-attachments/assets/e1da0039-5bd2-4493-87f6-e62f0d36fe48" />

2.Inspect one systemd service
(a)-This shows if the service is running or not.
systemctl status ssh
<img width="1904" height="572" alt="image" src="https://github.com/user-attachments/assets/14953125-d74e-468b-945b-7c65570f8ccc" />

(b)-List running services
systemctl list-units --type=service --state=running | head
<img width="1413" height="265" alt="image" src="https://github.com/user-attachments/assets/3c388f18-2256-4aa3-8f40-a190817d6d00" />

3.Shows last 20 log lines for ssh.
(a)Include 2 log commands
journalctl -u ssh | tail -n 20
<img width="1920" height="605" alt="image" src="https://github.com/user-attachments/assets/e6ab49cb-9179-4145-95ec-9e9ac9fb17c1" />

(b)Shows system logs.
tail -n 20 /var/log/syslog
Shows system logs.
<img width="1920" height="577" alt="image" src="https://github.com/user-attachments/assets/c56bb9f8-877d-4673-aecb-1a21757cae21" />

4.Small troubleshooting example
(a)Checked process
pgrep ssh
<img width="469" height="127" alt="image" src="https://github.com/user-attachments/assets/d30afec1-0a67-421f-a4b9-94d7593c2c94" />

(b)Checked Logs
journalctl -u ssh
<img width="1915" height="607" alt="image" src="https://github.com/user-attachments/assets/7207988c-dda6-4f32-9ea3-784589396397" />









