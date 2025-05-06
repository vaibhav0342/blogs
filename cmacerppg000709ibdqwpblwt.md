---
title: "most useful Linux commands for DevOps engineers"
datePublished: Tue May 06 2025 11:10:35 GMT+0000 (Coordinated Universal Time)
cuid: cmacerppg000709ibdqwpblwt
slug: most-useful-linux-commands-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1746529784737/68406e73-ad50-44d4-a476-6823cc1a809c.jpeg
tags: linux, aws, command-line, devops

---

## 🔧 **1\. System & Process Monitoring**

| Command | Description |
| --- | --- |
| `top` or `htop` | View real-time CPU, memory, and process usage. |
| `ps aux` | Show running processes with detailed info. |
| `free -h` | Check available and used memory. |
| `df -h` | Display disk space usage. |
| `du -sh *` | Show folder sizes in the current directory. |
| `uptime` | Show system load average and uptime. |
| `vmstat` | Monitor memory, CPU, I/O, and system processes. |

---

## 📦 **2\. Package Management**

| Command | Description |
| --- | --- |
| `apt update && apt upgrade` | (Debian/Ubuntu) Update and upgrade packages. |
| `yum update` or `dnf update` | (CentOS/RHEL) Update packages. |
| `snap install <package>` | Install via Snap. |
| `dpkg -i <package.deb>` | Install a .deb package manually. |

---

## 📁 **3\. File & Directory Management**

| Command | Description |
| --- | --- |
| `ls -lh` | List files with size and permissions. |
| `cd`, `pwd` | Change and print working directory. |
| `cp`, `mv`, `rm` | Copy, move, and remove files. |
| `find . -name "*.log"` | Find files recursively. |
| `tar -czvf file.tar.gz folder/` | Compress files using tar + gzip. |
| `unzip` [`file.zip`](http://file.zip) | Extract zip files. |

---

## 🌐 **4\. Networking**

| Command | Description |
| --- | --- |
| `curl -I` [`http://example.com`](http://example.com) | Check HTTP response headers. |
| `ping <host>` | Check network connectivity. |
| `netstat -tulpn` | Show open ports and listening services. |
| `ss -tuln` | Faster alternative to netstat. |
| `traceroute <host>` | Show network path to destination. |
| `dig`, `nslookup` | DNS query tools. |
| `iptables` / `ufw` | Manage firewall rules. |

---

## 🗂 **5\. Disk, Logs, and Permissions**

| Command | Description |
| --- | --- |
| `chmod`, `chown` | Change file permissions and ownership. |
| `ls -l` | View file permissions. |
| `tail -f /var/log/syslog` | Watch logs in real-time. |
| `journalctl -u <service>` | View systemd service logs. |
| `lsof -i :80` | List processes using port 80. |

---

## 🛠 **6\. Services and Systemd**

| Command | Description |
| --- | --- |
| `systemctl status nginx` | Check service status. |
| `systemctl start/stop/restart nginx` | Manage service. |
| `systemctl enable nginx` | Enable service at boot. |
| `service nginx status` | Alternative to `systemctl`. |

---

## 🔄 **7\. Users and SSH**

| Command | Description |
| --- | --- |
| `adduser <username>` | Add new user. |
| `passwd <username>` | Set/change user password. |
| `sudo` | Run command with elevated privileges. |
| `ssh user@host` | Connect to remote server. |
| `scp file user@host:/path` | Securely copy files to/from remote servers. |

---

## ⚙️ **8\. Scripting and Automation**

| Command | Description |
| --- | --- |
| `crontab -e` | Schedule recurring tasks. |
| `bash` [`script.sh`](http://script.sh) | Execute shell scripts. |
| `chmod +x` [`script.sh`](http://script.sh) | Make script executable. |
| `env` / `export VAR=value` | Manage environment variables. |

---

## 🧪 **9\. DevOps-Specific Tools**

| Tool | Command |
| --- | --- |
| Git | `git clone`, `git pull`, `git status` |
| Docker | `docker ps`, `docker exec`, `docker-compose up` |
| Kubernetes | `kubectl get pods`, `kubectl logs` |
| Ansible | `ansible-playbook play.yml` |
| Terraform | `terraform init`, `terraform apply` |
| Jenkins | `jenkins-cli.jar` commands |