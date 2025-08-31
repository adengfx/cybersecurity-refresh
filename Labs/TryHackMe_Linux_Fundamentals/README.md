# Linux Fundamentals Lab

## Lab Navigation
- [Room 1](#room-1)
- [Room 2](#room-2)
- [Room 3](#room-3)

---

## Room 1

### Objectives
- Understand basic Linux commands
- Navigate the filesystem
- Manage users and permissions
- Learn basic shell operators and command chaining

### Tools Used
- Linux VM
- Terminal / Shell

### Task: Running Your First Few Commands
#### Action
Familiarised myself with the Linux terminal by running basic commands and observing their output.

#### Observation
- `echo` prints text to the terminal  
- `whoami` shows the currently logged-in user

#### Lesson Learned
Linux is primarily operated through the terminal, making command-line familiarity essential.

#### Screenshots
![Terminal](screenshots/room1/terminal.png)

---

### Task: Interacting with the Filesystem
#### Action
Learned commands for navigating and managing the filesystem.

#### Observation
Commands like `ls`, `cd`, `pwd`, and `mkdir` allow for efficient directory and file navigation. Mostly familiar but needed a refresher.

#### Lesson Learned
Some Linux commands are identical or similar to Windows commands, easing the transition.

#### Screenshots
![Filesystem](screenshots/room1/filesystem.png)

---

### Task: Searching for Files
#### Action
Used the `find` and `grep` commands to locate files and search their contents.

#### Observation
- `find` locates files based on name and path  
- `grep` searches file contents for specific patterns

#### Lesson Learned
These commands greatly improve efficiency for locating files and searching contents.

#### Screenshots
![Find and Grep](screenshots/room1/find_grep.png)

---

### Task: An Introduction to Shell Operators
#### Action
Explored shell operators and their use cases.

#### Observation
- `&` runs a command in the background  
- `&&` chains commands, running the next only if the previous succeeds  
- `>` overwrites a file with command output  
- `>>` appends output to a file without overwriting existing content

#### Lesson Learned
Shell operators allow more efficient workflows by chaining commands and controlling output.

#### Screenshots
![Shell Operators](screenshots/room1/shell_operators.png)

---

### Conclusion
This room reinforced previously learned Linux concepts and introduced practical tools. Similarity to Windows commands makes learning easier, and shell operators plus file search commands improve efficiency.

---

## Room 2

### Objectives
- Understand how to use flags and switches in Linux commands  
- Practice filesystem interaction and manipulation  
- Learn about Linux file permissions  
- Explore common Linux directories and their purposes  

### Tools Used
- Linux terminal  

### Tasks / Steps  

#### Task: Introduction to Flags and Switches  
**Action:** Explored how flags work within Linux commands.  

**Observation:**  
- `ls -a` → Displays hidden files and folders  
- `--help` → Lists available options for a command  
- `man` → Opens the manual page for a command  

**Lesson Learned:**  
Gained a better understanding of how flags provide extra functionality to commands. The `--help` and `man` commands are essential for learning more about how a command works and what options it supports. The `-a` flag is especially useful for locating hidden files and directories.  

**Screenshots:**  
![Screenshot](screenshots/room2/flags.png)  

---

#### Task: Filesystem Interaction Continued  
**Action:** Practiced commands to interact with the filesystem.  

**Observation:**  
- `touch` → Creates a file  
- `mkdir` → Creates a directory  
- `cp` → Copies a file or directory  
- `mv` → Moves or renames a file or directory  
- `rm` → Removes a file or directory  
- `file` → Displays file type information  

**Lesson Learned:**  
Learned how to quickly create, copy, move, and remove files and directories directly from the terminal, which is faster than using a GUI. The `file` command is also useful for identifying file types when working with multiple files that share similar names.  

**Screenshots:**  
![Screenshot](screenshots/room2/filesys.png)  

---

#### Task: Permissions 101  
**Action:** Explored how Linux permissions work and how to switch users to access files.  

**Observation:**  
- `ls -lh` → Displays file permissions and ownership details  
- `su -l [username]` → Switches to another user’s account (with `-l` preserving the login environment)  

**Lesson Learned:**  
Learned how to identify file ownership and permissions using `ls -lh`. Using `su -l` allows switching to another user account, which can grant access to files based on ownership and permissions.  

**Screenshots:**  
![Screenshot](screenshots/room2/perm.png)  

---

#### Task: Common Directories  
**Action:** Reviewed common Linux directories and their purposes.  

**Observation:**  
- `/etc` → Stores system configuration files  
- `/var` → Stores variable data used by services and applications (e.g., logs)  
- `/root` → Home directory for the root (system admin) user  
- `/tmp` → Temporary storage, cleared on reboot  

**Lesson Learned:**  
Although mainly a reading task, this was helpful in understanding the purpose of important system directories. This knowledge is useful when troubleshooting or searching for specific files such as logs.  

**Screenshots:**  
![Screenshot](screenshots/room2/dir.png)  

---

### Conclusion
Room 2 helped reinforce core Linux skills: using flags and switches, interacting with the filesystem, understanding file permissions, and recognizing key system directories. These fundamentals are crucial for navigating and managing Linux effectively.  


---

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
Learned how to host a quick web server using Python and download files via `wget`. Also practised transferring files with `scp`, which is useful for securely moving files between machines.  

**Screenshots:**  
![Screenshot](screenshots/room3/webserver.png)  

---

### Task: Processes 101  
**Action:** Explored how processes work in Linux, including monitoring and managing them.  

**Observation:**  
- `ps` shows processes tied to the current session, while `ps aux` lists all system-wide processes.  
- `top` provides a live, continuously updating view of running processes and their resource usage.  
- `kill [PID]` ends a process, with behaviour depending on the signal (`SIGTERM` for graceful stop, `SIGKILL` for force).  
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
