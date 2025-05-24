---
title: "🧪 Linux Proficiency Test – 3 Years Experience (90 Questions)"
datePublished: Sat May 24 2025 07:28:23 GMT+0000 (Coordinated Universal Time)
cuid: cmb1wraz6000009l5e20qgdji
slug: linux-proficiency-test-3-years-experience-90-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1748071627628/96541c7f-8031-4152-a0d0-4cfd7386bef1.jpeg
tags: interview, linux, aws, devops, interview-questions, shell-script

---

---

## 🔹 Section 1: Command Line Basics (10 questions)

1. What does the command `pwd` do?
    
2. How do you list all hidden files?
    
3. What is the output of `echo $HOME`?
    
4. How do you view the last 20 lines of a file?
    
5. Explain the difference between `>` and `>>`.
    
6. How can you check your current shell?
    
7. Which command will find the absolute path of an executable?
    
8. How do you display file sizes in a human-readable format with `ls`?
    
9. What does `man` do?
    
10. Write a command to find the number of `.conf` files in `/etc`.
    

---

## 🔹 Section 2: File and Directory Operations (10 questions)

11. How do you create a directory called `projects`?
    
12. What is the command to remove a directory and all its contents?
    
13. Explain how to use `find` to locate all `.log` files in `/var/log`.
    
14. How can you rename a file?
    
15. How do you move a file from one directory to another?
    
16. What does `du -sh *` do?
    
17. How can you compress a directory using `tar` and `gzip`?
    
18. What’s the command to extract a `.tar.gz` file?
    
19. Write a command to compare two text files.
    
20. How do you delete all `.tmp` files recursively?
    

---

## 🔹 Section 3: Permissions and Ownership (10 questions)

21. What does `chmod 755` [`script.sh`](http://script.sh) mean?
    
22. How do you make a script executable?
    
23. What command changes file ownership?
    
24. Explain the difference between `chown` and `chgrp`.
    
25. What is the output of `ls -l`?
    
26. What are SUID, SGID, and Sticky Bit?
    
27. How can you set default permissions using `umask`?
    
28. What is the command to view ACLs of a file?
    
29. How do you grant read and write permissions to the group only?
    
30. What does `chmod o-rwx file.txt` do?
    

---

## 🔹 Section 4: Process Management (10 questions)

31. How do you list all running processes?
    
32. What is the function of `top` and `htop`?
    
33. How do you kill a process by name?
    
34. What does `ps aux | grep nginx` show?
    
35. Explain zombie and orphan processes.
    
36. What does the `nice` value control?
    
37. How do you change the priority of a process?
    
38. What command pauses a running job?
    
39. How can you bring a background job to the foreground?
    
40. What’s the difference between `&`, `nohup`, and `disown`?
    

---

## 🔹 Section 5: Networking (10 questions)

41. What does `ip a` show?
    
42. How do you test if a server is reachable on port 80?
    
43. How do you display the routing table?
    
44. What is the command to download a file using the terminal?
    
45. How do you see your public IP address?
    
46. How do you open a port using `iptables`?
    
47. What does `ss -tuln` do?
    
48. What’s the difference between TCP and UDP?
    
49. How do you view active network interfaces?
    
50. What is the use of `/etc/hosts`?
    

---

## 🔹 Section 6: Package Management (10 questions)

51. What is the difference between `apt` and `yum`?
    
52. How do you update all installed packages on a Debian-based system?
    
53. How do you install a `.deb` file?
    
54. What does `yum remove` do?
    
55. How can you check which package provides a command?
    
56. What’s the command to list installed packages?
    
57. How do you upgrade a single package?
    
58. How can you add a PPA repository?
    
59. Explain the difference between `dpkg` and `apt`.
    
60. How do you remove unused dependencies?
    

---

## 🔹 Section 7: Users and Groups (10 questions)

61. How do you add a user?
    
62. What’s the command to change a user’s password?
    
63. How do you delete a user and their home directory?
    
64. How do you add a user to a group?
    
65. What’s the default shell for a new user?
    
66. How do you lock/unlock a user account?
    
67. What is stored in `/etc/passwd`?
    
68. How do you list all users on the system?
    
69. How can you change a user's shell?
    
70. What command shows a user’s group memberships?
    

---

## 🔹 Section 8: Shell Scripting and Automation (10 questions)

71. What is `#!/bin/bash`?
    
72. How do you pass arguments to a shell script?
    
73. What does `$1`, `$2`, `$@` mean?
    
74. Write a script to display the current date and time.
    
75. How can you make a script run every hour?
    
76. What’s the difference between `cron` and `at`?
    
77. How do you debug a shell script?
    
78. What command schedules a cron job?
    
79. How do you redirect errors to a file?
    
80. Write a `for` loop to list numbers 1 to 10.
    

---

## 🔹 Section 9: System Monitoring & Logs (10 questions)

81. How do you check system load average?
    
82. Where are system logs stored?
    
83. What does `journalctl` do?
    
84. How do you watch real-time logs?
    
85. What command shows memory usage?
    
86. How do you check disk usage?
    
87. What tool can you use to monitor IO activity?
    
88. What is the use of `uptime`?
    
89. How do you track login attempts?
    
90. What is the purpose of `/var/log/auth.log`?
    

## ✅ **Answer Key: Linux 90 Questions**

### 🔹 Section 1: Command Line Basics

1. Prints current working directory
    
2. `ls -a`
    
3. Displays the path to the user's home directory
    
4. `tail -n 20 filename`
    
5. `>` overwrites, `>>` appends
    
6. `echo $SHELL`
    
7. `which`
    
8. `ls -lh`
    
9. Shows manual/help pages
    
10. `find /etc -name "*.conf" | wc -l`
    

---

### 🔹 Section 2: File and Directory Operations

11. `mkdir projects`
    
12. `rm -rf directory_name`
    
13. `find /var/log -name "*.log"`
    
14. `mv oldname newname`
    
15. `mv file /new/location/`
    
16. Shows size of each item in human-readable format
    
17. `tar -czvf archive.tar.gz directory/`
    
18. `tar -xzvf archive.tar.gz`
    
19. `diff file1 file2`
    
20. `find . -name "*.tmp" -delete`
    

---

### 🔹 Section 3: Permissions and Ownership

21. rwx for owner, rx for group, r for others
    
22. `chmod +x` [`script.sh`](http://script.sh)
    
23. `chown user:group filename`
    
24. `chown` changes user & group, `chgrp` only group
    
25. Lists permissions, owner, group, size, etc.
    
26. Special permissions for exec, group files, and directories
    
27. Sets default permissions mask
    
28. `getfacl filename`
    
29. `chmod g+rw filename`
    
30. Removes all permissions from others
    

---

### 🔹 Section 4: Process Management

31. `ps aux` or `top`
    
32. Real-time process monitoring tools
    
33. `pkill processname`
    
34. Filters for processes named nginx
    
35. Zombie: finished but not reaped; Orphan: no parent
    
36. Process priority
    
37. `renice`
    
38. `Ctrl + Z` or `kill -STOP pid`
    
39. `fg`
    
40. `&` runs in background, `nohup` ignores hangups, `disown` removes job from shell
    

---

### 🔹 Section 5: Networking

41. Shows all IP addresses and interfaces
    
42. `telnet host 80` or `nc -zv host 80`
    
43. `ip route` or `route -n`
    
44. `wget` or `curl -O`
    
45. `curl` [`ifconfig.me`](http://ifconfig.me)
    
46. `iptables -A INPUT -p tcp --dport 80 -j ACCEPT`
    
47. Shows listening ports and services
    
48. TCP = connection-based, UDP = connectionless
    
49. `ip link show` or `ifconfig`
    
50. Maps hostnames to IPs locally
    

---

### 🔹 Section 6: Package Management

51. Different package managers: apt = Debian, yum = RHEL
    
52. `sudo apt update && sudo apt upgrade`
    
53. `sudo dpkg -i package.deb`
    
54. Removes a package
    
55. `dpkg -S /path/to/file` or `yum provides`
    
56. `dpkg -l` or `yum list installed`
    
57. `sudo apt install package-name`
    
58. `add-apt-repository ppa:name`
    
59. `dpkg` is low-level, `apt` is higher-level
    
60. `apt autoremove`
    

---

### 🔹 Section 7: Users and Groups

61. `adduser username` or `useradd`
    
62. `passwd username`
    
63. `userdel -r username`
    
64. `usermod -aG groupname username`
    
65. Usually `/bin/bash`
    
66. `passwd -l username` / `passwd -u username`
    
67. Basic user info and UID/GID
    
68. `cut -d: -f1 /etc/passwd`
    
69. `chsh -s /bin/zsh username`
    
70. `groups username`
    

---

### 🔹 Section 8: Shell Scripting and Automation

71. Shebang – tells the shell to use Bash
    
72. `./`[`script.sh`](http://script.sh) `arg1 arg2`
    
73. `$0` = script name, `$1` = first arg, `$@` = all args
    
74. `echo "Today is $(date)"`
    
75. Cron: `0 * * * * /path/to/`[`script.sh`](http://script.sh)
    
76. `cron` = recurring, `at` = one-time
    
77. `bash -x` [`script.sh`](http://script.sh)
    
78. `crontab -e`
    
79. `command 2> error.log`
    
80. `for i in {1..10}; do echo $i; done`
    

---

### 🔹 Section 9: System Monitoring & Logs

81. `uptime` or `top`
    
82. `/var/log`
    
83. Views logs from `systemd` journal
    
84. `tail -f /var/log/syslog`
    
85. `free -h`
    
86. `df -h`
    
87. `iotop` or `iostat`
    
88. Shows uptime and load
    
89. `last` or `who`
    
90. Contains authentication logs