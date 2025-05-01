
## 🔐 Squid Proxy ACL (Access Control List) Configuration

---

### **📘 Basic ACL Syntax**

```
acl [name] [type] [data]
```

- **name**: Identifier (e.g., `localnet`, `deny_client`)
- **type**: Match type (e.g., `src`, `dstdomain`, `port`, `url_regex`)
- **data**: Matching value(s)

---

### **🛡️ Allow Local Network Only**

```bash
acl localnet src 192.168.0.0/16
http_access allow localnet
http_access deny all
```

- Allows access only from the 192.168.x.x subnet
- Denies all other IPs

---

### **🔐 Safe Ports Only**

```bash
acl SSL_ports port 443
acl Safe_ports port 80 21 443 70 210 1025-65535 280 488 591 777
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
```

- Ensures only known safe ports are allowed
- Blocks any traffic trying to use unsafe ports

---

### **✅ Minimal Working ACL Configuration (Example)**

```bash
acl localnet src 192.168.0.0/16
acl SSL_ports port 443
acl Safe_ports port 80 21 443 70 210 1025-65535 280 488 591 777

http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access deny all

http_port 3128
```

---

### **🌐 Allow Specific Websites**

#### Method 1: Inline ACL

```bash
acl allow_website dstdomain .google.com .youtube.com
http_access allow allow_website
http_access deny all
```

#### Method 2: External Domain List

1. **Create the list file**:
```bash
vim /etc/squid/allow_website_list
```

**Contents**:
```
.google.com
.youtube.com
.facebook.com
```

2. **Update config**:
```bash
acl allow_website dstdomain "/etc/squid/allow_website_list"
http_access allow allow_website
http_access deny all
```

3. **Restart Squid**:
```bash
systemctl restart squid
```

---

### **🚫 Deny Specific Websites**

#### Method 1: Inline ACL

```bash
acl deny_website dstdomain .facebook.com
http_access deny deny_website
```

#### Method 2: External Deny List

```bash
vim /etc/squid/deny_website_list
```

**Contents**:
```
.facebook.com
.netflix.com
.tiktok.com
```

**Config**:
```bash
acl deny_website dstdomain "/etc/squid/deny_website_list"
http_access deny deny_website
```

---

### **🔎 Block URLs with Specific Keywords**

#### Inline Keywords

```bash
acl deny_keywords url_regex -i reports news game
http_access deny deny_keywords
```

#### External Keyword File

1. **Create file**:
```bash
vim /etc/squid/deny_keywords
```

**Contents**:
```
torrent
game
sports
```

2. **Update config**:
```bash
acl deny_keywords url_regex -i "/etc/squid/deny_keywords"
http_access deny deny_keywords
```

---

### **🙅 Deny Specific Clients by IP**

#### Method 1: Single IP

```bash
acl deny_client src 192.168.2.51
http_access deny deny_client
```

#### Method 2: Multiple IPs

```bash
acl deny_client src 192.168.2.51 192.168.2.52 192.168.2.100
http_access deny deny_client
```

#### Method 3: External File

1. **Create file**:
```bash
vim /etc/squid/deny_clients
```

**Contents**:
```
192.168.2.51
192.168.2.52
```

2. **Update config**:
```bash
acl deny_client src "/etc/squid/deny_clients"
http_access deny deny_client
```

---

### **📁 Clean and View Configuration**

- Remove comments and blank lines:
```bash
cat /etc/squid/squid.conf | grep -v "^#" | sed '/^$/d'
```

---

### **🧪 Testing and Monitoring**

- **Check logs in real-time**:
```bash
tail -f /var/log/squid/access.log
```

- **Verify Squid ACL functionality**:
  - Try accessing allowed/blocked websites or test with different client IPs.

---

## 🧠 Pro Tips

- **ACLs are processed in order**, so sequence matters!
- Always **restart Squid** after changes:
```bash
systemctl restart squid
```
- Use rich ACLs and external files for easier management in production.

