**firewalld** commands, which manage firewall rules on RHEL, CentOS, Fedora, and other Linux distributions. 

### **1. Start and Enable Firewalld**
To start and enable **firewalld** (if it’s not already running), use these commands:

#### Start Firewalld:
```bash
sudo systemctl start firewalld
```

#### Enable Firewalld to start on boot:
```bash
sudo systemctl enable firewalld
```

---

### **2. Check Firewalld Status**
To check if **firewalld** is running:

```bash
sudo systemctl status firewalld
```

To check the current active zone and other details of the firewall:

```bash
sudo firewall-cmd --state
```

---

### **3. Check Default Zone**
To see the default zone:

```bash
sudo firewall-cmd --get-default-zone
```

The default zone is typically **public**, but it can be customized.

---

### **4. View Active Rules in the Default Zone**
To list all active rules in the default zone:

```bash
sudo firewall-cmd --list-all
```

---

### **5. List All Zones**
To see all available zones:

```bash
sudo firewall-cmd --list-zones
```

---

### **6. Add or Remove a Service from a Zone**
To allow a service, like HTTP (port 80), in the default zone:

#### Add service (allow):
```bash
sudo firewall-cmd --zone=public --add-service=http
```

#### Remove service (deny):
```bash
sudo firewall-cmd --zone=public --remove-service=http
```

To make these changes permanent, use the `--permanent` flag.

#### Permanent service addition:
```bash
sudo firewall-cmd --zone=public --add-service=http --permanent
```

---

### **7. Add or Remove Specific Port**
To open a specific port (e.g., port 8080):

#### Add port (allow):
```bash
sudo firewall-cmd --zone=public --add-port=8080/tcp
```

#### Remove port (deny):
```bash
sudo firewall-cmd --zone=public --remove-port=8080/tcp
```

To make the changes permanent:

#### Permanent port addition:
```bash
sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
```

---

### **8. Set Default Zone**
To change the default zone:

```bash
sudo firewall-cmd --set-default-zone=work
```

---

### **9. Reload Firewalld**
Whenever you make changes that you want to apply, you need to reload **firewalld**:

```bash
sudo firewall-cmd --reload
```

---

### **10. Allow/Block an IP Address**
To allow an IP address (e.g., `192.168.1.10`) access to the firewall:

```bash
sudo firewall-cmd --zone=public --add-source=192.168.1.10
```

To block an IP address:

```bash
sudo firewall-cmd --zone=public --remove-source=192.168.1.10
```

To make these changes permanent:

```bash
sudo firewall-cmd --zone=public --add-source=192.168.1.10 --permanent
```

---

### **11. Allow/Deny a Service Temporarily or Permanently**
To allow a service for HTTP (for example):

#### Allow temporarily (until next reboot/reload):
```bash
sudo firewall-cmd --zone=public --add-service=http
```

#### Deny a service temporarily:
```bash
sudo firewall-cmd --zone=public --remove-service=http
```

#### Allow permanently:
```bash
sudo firewall-cmd --zone=public --add-service=http --permanent
```

#### Deny permanently:
```bash
sudo firewall-cmd --zone=public --remove-service=http --permanent
```

---

### **12. Check Open Ports**
To check which ports are currently open:

```bash
sudo firewall-cmd --zone=public --list-ports
```

---

### **13. View Rich Rules**
You can also add rich rules for more complex firewall configurations. For example, to allow a specific service on port 8080 from an IP address `192.168.1.10`:

```bash
sudo firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="192.168.1.10" port port="8080" protocol="tcp" accept'
```

To remove the rich rule:

```bash
sudo firewall-cmd --zone=public --remove-rich-rule='rule family="ipv4" source address="192.168.1.10" port port="8080" protocol="tcp" accept'
```

---

### **14. Set Firewall to Block All Incoming by Default**
To block all incoming traffic by default and allow only specific services:

```bash
sudo firewall-cmd --zone=public --set-target=DROP
```

To allow specific services (e.g., HTTP and HTTPS):

```bash
sudo firewall-cmd --zone=public --add-service=http --permanent
sudo firewall-cmd --zone=public --add-service=https --permanent
```

---

### **15. Disable Firewalld**
To stop and disable **firewalld** (if you want to use another firewall or no firewall at all):

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```

---

### **16. Check Firewalld's Configuration**
You can dump the configuration and check the active configuration:

```bash
sudo firewall-cmd --dump
```

---

### **17. List Services Available**
To view available services in **firewalld**:

```bash
sudo firewall-cmd --get-services
```

---

### **18. Enable/Disable Firewalld for a Specific Zone**
To enable or disable specific zones:

#### Enable a zone:
```bash
sudo firewall-cmd --zone=public --add-interface=eth0
```

#### Disable a zone:
```bash
sudo firewall-cmd --zone=public --remove-interface=eth0
```

---

### **19. Get the Rules in a Zone**
You can view all the active rules in a zone:

```bash
sudo firewall-cmd --zone=public --list-all
```

---

