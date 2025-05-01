
## 🐙 Squid Proxy Server Setup
---

### **1. Check Repositories and Existing Installation**

Ensure required repositories are enabled and check if Squid is already installed.

```bash
# List all available yum repositories
yum repolist all

# Check if Squid is already installed
rpm -qa | grep squid
```

---

### **2. Install Squid**

Install Squid and all related packages.

```bash
yum install squid*
```

---

### **3. Verify Installation**

After installing, check Squid’s presence and inspect its files.

```bash
# List all installed Squid-related packages
rpm -qa | grep squid

# Show detailed info about the Squid package
rpm -qi squid

# List all configuration files
rpm -qc squid

# List documentation files
rpm -qd squid

# List all files installed by the Squid package
rpm -ql squid
```

---

### **4. Edit Squid Configuration**

Modify the main configuration file to define ACLs, ports, and access rules.

```bash
vim /etc/squid/squid.conf
```

> Example: Allow only your internal network (e.g., `192.168.1.0/24`) and block others.

---

### **5. Manage Squid Service**

Enable and manage the Squid service.

```bash
# Enable on boot
systemctl enable squid.service

# Start the service now
systemctl start squid.service

# Check status
systemctl status squid.service
```

---

### **6. Check If Squid is Listening**

Verify that Squid is listening on the default port (3128).

```bash
# Using netstat
netstat -nltup | grep squid

# Or using ss
ss -nltup | grep squid
```

> Look for `LISTEN` on TCP port `3128`.

---

### **7. Configure Firewalld Instead of iptables**

Use `firewalld` for dynamic and zone-based firewall management.

```bash
# Check if firewalld is running
systemctl status firewalld

# Start and enable firewalld
systemctl start firewalld
systemctl enable firewalld

# Open Squid port
firewall-cmd --permanent --add-port=3128/tcp

# Optional: Open DNS ports if Squid resolves domains
firewall-cmd --permanent --add-port=53/tcp
firewall-cmd --permanent --add-port=53/udp

# Reload to apply changes
firewall-cmd --reload

# List active rules
firewall-cmd --list-all
```

---

### **8. Restrict Access to Internal Network (Optional Security Enhancement)**

Allow access **only** from a specific subnet:

```bash
firewall-cmd --permanent --add-rich-rule='rule family=ipv4 source address=192.168.1.0/24 port protocol=tcp port=3128 accept'
firewall-cmd --reload
```

> 🔒 This enhances security by limiting who can use the proxy.

---

### **9. Monitor Logs and Traffic**

Keep an eye on usage and troubleshoot effectively.

```bash
# View access logs in real-time
tail -f /var/log/squid/access.log

# Capture network packets (replace enp0s8 with your interface)
tcpdump -i enp0s8 -w /root/1.pcap

# Read captured packet data
tcpdump -r /root/1.pcap
```

---

### 🔍 Main Differences Between firewalld and iptables

| Feature                | firewalld                         | iptables                      |
|------------------------|-----------------------------------|-------------------------------|
| Rule Application       | Dynamic (no restart needed)       | Static (requires restart)     |
| Management             | Zone & service-based              | Manual rule-based             |
| Ease of Use            | Easier with `firewall-cmd`        | More complex configuration    |

---

### ✅ Conclusion

You've now successfully set up a secure Squid proxy server with firewall protection using `firewalld`. Monitoring logs and limiting network access help ensure security and proper use.

