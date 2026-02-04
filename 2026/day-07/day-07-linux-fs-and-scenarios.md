1. File System Hierarchy

   Part 1: Linux File System Hierarchy (30 minutes)

Core Directories:

(a) / (root) - The starting point of everything
cmd: ls -l /
=> All other directories and files branch from here.
<img width="1920" height="815" alt="image" src="https://github.com/user-attachments/assets/6573f105-0e88-4aba-816f-a20d2e589246" />
I would use this when.I need to navigate the entire filesystem or understand the system’s overall structure.

(b) /home - User home directories
cmd: ls -l /home
=>This directory contains personal home directories for regular users.
=>I would use this when, I need to access or manage user files and personal data.
<img width="935" height="191" alt="image" src="https://github.com/user-attachments/assets/50b55bd1-1719-4eae-ba7e-25ddca50b125" />

(c) /root - Root user's home directory
=> The home directory for the root (administrator) user.
=> I would use this when, I am logged in as root and need to manage administrative configuration files.

(d) /etc - Configuration files
=>System-wide configuration files and settings for installed services and applications.
=>I would use this when, I need to configure system services like SSH, networking, or hostname settings.
cmd : ls -l/etc
<img width="1817" height="866" alt="image" src="https://github.com/user-attachments/assets/285dce10-b2c2-46b2-978d-d6a9b17553b9" />

(e) /var/log - Log files (very important for DevOps!)
=>System and application log files. These are critical for troubleshooting and DevOps monitoring.
cmd: ls -l /var/log
=>I would use this when, I need to debug errors, check system activity, or investigate security issues.
<img width="1177" height="498" alt="image" src="https://github.com/user-attachments/assets/aacdd592-f548-406c-a63a-53bc3a74873a" />

(f) /tmp - Temporary files
=>Temporary files created by the system or applications. Files may be deleted automatically after reboot.
=>I would use this when, I need to store temporary data during testing or script execution.
cmd: ls -l /tmp
<img width="791" height="251" alt="image" src="https://github.com/user-attachments/assets/6f14d501-857f-44e4-a7ce-d3073cb2ae81" />

(g) /bin - Essential command binaries
=>Essential system command binaries required for booting and basic system operation.
=>I would use this when, I need access to core commands like ls, cp, or mv.
cmd: ls -l /bin
<img width="1075" height="392" alt="image" src="https://github.com/user-attachments/assets/4a9ab7c6-bdea-4f21-ad07-64980b85f62e" />

(h) /usr/bin - User command binaries
=>User-level command binaries and applications installed by the system.
cmd: ls -l /usr/bin
=> I would use this when,I run common applications like Python, Git, or Vim.
<img width="1065" height="871" alt="image" src="https://github.com/user-attachments/assets/bd78a17b-1c7d-43b2-ab01-f8d7d4c61af3" />
<img width="641" height="130" alt="image" src="https://github.com/user-attachments/assets/742eb828-2750-4d52-a4e0-3500ea6e9600" />


Hands-on task:

1. Find the largest log file in /var/log
cmd: du -sh /var/log/* 2>/dev/null | sort -h | tail -5
<img width="943" height="502" alt="image" src="https://github.com/user-attachments/assets/f09564ce-7f05-4d0d-b248-54159a8fd721" />


# Look at a config file in /etc
=>View a config file in /etc.
cmd: cat /etc/hostname
<img width="491" height="80" alt="image" src="https://github.com/user-attachments/assets/995fd6d7-67f8-4421-9b10-ca57b87f363a" />

# Check your home directory
=>Check your home directory.
cmd: ls -la ~
<img width="907" height="814" alt="image" src="https://github.com/user-attachments/assets/49da1126-6b3d-4008-85f8-0435d2ceb437" />
<img width="633" height="140" alt="image" src="https://github.com/user-attachments/assets/5f344375-0639-4384-8f80-15b093cde231" />

(A)du -sh → Shows size of each file/folder
(b)sort -h → Sorts by size
(c)tail -5 → Shows the 5 largest entries

