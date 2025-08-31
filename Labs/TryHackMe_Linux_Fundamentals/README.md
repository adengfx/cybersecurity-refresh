## Room 3

### Objectives
- Learn to create and edit text files using terminal-based editors  
- Explore utilities for downloading and transferring files  
- Understand Linux process management  
- Automate tasks using cron  
- Manage packages and repositories  
- Access and review system logs  

### Tools Used
- Linux terminal  
- `nano` text editor  
- `wget`  
- `scp`  
- `python3` (for local web server)  

---

### Task: Terminal Text Editors  
**Action:** Explored how to create and edit text files directly from the terminal.  

**Observation:**  
- `nano [filename]` creates a file (if it doesn’t exist) and opens it in the Nano text editor.  

**Lesson Learned:**  
Learned how to quickly create and edit files within the Linux terminal. This can be faster than opening a GUI text editor, especially when working on servers without a desktop environment.  

**Screenshots:**  
![Screenshot](screenshots/room3/nano.png)  
![Screenshot](screenshots/room3/text_editor.png)  

---

### Task: General / Useful Utilities  
**Action:** Looked at ways to download and transfer files.  

**Observation:**  
- `python3 -m http.server` starts a simple web server in the current directory.  
- `wget [URL]` downloads files from the web or from a hosted server.  
- `scp [file] user@host:/path` securely transfers files between systems.  

**Lesson Learned:**  
Learned how to host a quick web server using Python and download files via `wget`. Also practiced transferring files with `scp`, which is useful for securely moving files between machines.  

**Screenshots:**  
![Screenshot](screenshots/room3/webserver.png)  

---

### Task: Processes 101  
**Action:** Explored how processes work in Linux, including monitoring and managing them.  

**Observation:**  
- `ps` shows processes tied to the current session, while `ps aux` lists all system-wide processes.  
- `top` provides a live, continuously updating view of running processes and their resource usage.  
- `kill [PID]` ends a process, with behavior depending on the signal (`SIGTERM` for graceful stop, `SIGKILL` for force).  
- Services (e.g., Apache) can be managed using `systemctl start/stop/enable/disable`.  

**Lesson Learned:**  
Learned how Linux manages processes and how to monitor, control, and terminate them. This is useful for troubleshooting, system monitoring, and identifying malicious or unresponsive processes.  

---

### Task: Maintaining Your System — Automation  
**Action:** Looked at scheduling tasks to run automatically after boot or at specific times.  

**Observation:**  
- The `cron` service allows scheduling commands or scripts.  
- Online tools like *Crontab Generator* can help generate correct cron syntax.  
- `crontab -e` opens the cron configuration for editing.  

**Lesson Learned:**  
Learned how to use `cron` to automate tasks. In this lab, a script named `processes.sh` was configured to run automatically at boot.  

---

### Task: Maintaining Your System — Package Management  
**Action:** Explored how packages are added, removed, and updated in Linux.  

**Observation:**  
- Repositories can be added manually after importing the developer’s GPG key for security.  
- `apt update` refreshes package lists, making new software available.  
- `apt install [package]` installs software.  
- Repositories can be removed with `add-apt-repository --remove` or by deleting the repo file manually.  
- `apt remove [package]` uninstalls software.  

**Lesson Learned:**  
Learned how package management works in Ubuntu/Debian. Adding repositories expands available software, while GPG keys ensure authenticity. The `apt` system makes updates, installations, and removals straightforward.  

---

### Task: Maintaining Your System — Logs  
**Action:** Investigated how Linux stores logs and where to find them.  

**Observation:**  
- Logs are stored in `/var/log/`.  
- Within `apache2/`, logs are split into `access.log` and `error.log`.  

**Lesson Learned:**  
Learned how to access and interpret Linux logs. Logs are critical for troubleshooting, monitoring performance, and detecting suspicious or malicious activity.  

**Screenshots:**  
![Screenshot](screenshots/room3/logs.png)  

---

### Conclusion  
Room 3 introduced additional Linux administration skills, including text editing in the terminal, file transfer, process management, automation, package management, and log analysis. These are essential for both daily system administration and security monitoring.  
