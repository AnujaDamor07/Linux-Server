
# 📂 Anonymous FTP Server Setup using `vsftpd` (RHEL / CentOS / Rocky Linux)

---

## 🔹 1. Check for Existing FTP Packages

```bash
rpm -qa | grep ftp
```

---

## 🔹 2. Install `vsftpd` and FTP Client

```bash
yum install vsftpd ftp -y
```
--- 

### ✔ Verify Installation:

```bash
rpm -qa | grep ftp
```

Example output:
```
vsftpd-3.0.5-6.el9.x86_64  
ftp-0.17-89.el9.x86_64
```

---

## 🔹 3. Inspecting `vsftpd` Package

```bash
rpm -qi vsftpd          # Package details  
rpm -ql vsftpd          # List installed files  
rpm -qc vsftpd          # Show config files  
rpm -qd vsftpd          # Documentation files  
```

---

## 🔹 4. Configure `vsftpd`

Edit the config:

```bash
vim /etc/vsftpd/vsftpd.conf
```

### 🛠 Sample Configuration:

```ini
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
listen=NO
listen_ipv6=YES
pam_service_name=vsftpd
userlist_enable=YES
pasv_min_port=55000
pasv_max_port=55999
pasv_enable=YES
```

✅ Enables:
- Anonymous and local user login  
- Uploads and directory creation for anonymous users  
- Passive mode (for clients behind firewalls)

---

## 🔹 5. Manage `vsftpd` Service

```bash
systemctl status vsftpd.service   # Check status  
systemctl start vsftpd.service    # Start now  
systemctl restart vsftpd.service  # Restart after config changes  
systemctl enable vsftpd.service   # Start on boot  
```

---

## 🔹 6. Verify FTP Listening Ports

```bash
netstat -nltup | grep ftp
```

---

## 🔹 7. Set Up Anonymous Content Directory

```bash
cd /var/ftp/
mkdir -p pub
chown -Rv nobody:nobody pub/
chmod -Rv 777 pub/
```

✅ Copy some content for public access:

```bash
cp -vr /var/www/html/site* /var/ftp/pub/
```

> 🗂️ You can also use `/srv/ftp/pub/` depending on your vsftpd root.

---

## 🔹 8. Check Open Files Used by FTP

```bash
lsof | grep ftp
netstat -nltup
```

---

# 🔥 Configuring `firewalld` for FTP Access

---

## 1. Start & Enable `firewalld`

```bash
systemctl start firewalld
systemctl enable firewalld
systemctl status firewalld
```

---

## 2. Allow FTP Control Port (21)

```bash
firewall-cmd --permanent --add-service=ftp
```

---

## 3. Allow Passive Mode Ports (55000–55999)

```bash
firewall-cmd --permanent --add-port=55000-55999/tcp
```

---

## 4. Reload Firewall

```bash
firewall-cmd --reload
```

---

## 5. Verify Rules

```bash
firewall-cmd --list-all
```

---

## 6. (Optional) Set Rules for Specific Zone

```bash
firewall-cmd --zone=public --permanent --add-service=ftp
firewall-cmd --zone=public --permanent --add-port=55000-55999/tcp
firewall-cmd --reload
```

---

## 7. SELinux Consideration (If Enforcing)

Enable the required booleans:

```bash
setsebool -P ftp_home_dir=1
setsebool -P allow_ftpd_full_access=1
```

Confirm:

```bash
getsebool -a | grep ftp
```

---

## 📌 Summary of Required Ports

| Service    | Port(s)         | Description               |
|------------|------------------|---------------------------|
| FTP        | TCP 21           | Control connection        |
| FTP-PASV   | TCP 55000–55999  | Passive data connections  |

