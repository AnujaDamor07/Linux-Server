
## 🔐 Squid Proxy - Basic User Authentication (NCSA)

---

### **Step 1: Install Required Package**

Install `httpd-tools`, which includes the `htpasswd` utility.

```bash
yum install httpd-tools -y
```

---

### **Step 2: Create Password File and Users**

#### ✅ Create the password file with the first user:

```bash
htpasswd -c /etc/squid/passwd u1
```
> Enter password when prompted (example: `123`)

#### ➕ Add more users:

```bash
htpasswd /etc/squid/passwd u2
```
> Password: `1234` (for example)

#### 🔍 Verify the file:

```bash
cat /etc/squid/passwd
```

---

### **Step 3: Set Secure Permissions**

```bash
chgrp squid /etc/squid/passwd
chmod 640 /etc/squid/passwd
ls -lh /etc/squid/passwd
```

---

### **Step 4: Configure Squid for Authentication**

Edit your Squid config:

```bash
vim /etc/squid/squid.conf
```

#### Add these lines (preferably near the top or in a custom rules section):

```bash
auth_param basic program /usr/lib64/squid/basic_ncsa_auth /etc/squid/passwd
auth_param basic realm Squid Proxy Authentication
acl ncsa_users proxy_auth REQUIRED
http_access allow ncsa_users
```

#### (Optional) Restrict to specific users:

```bash
acl allowed_users proxy_auth u1 u2
http_access allow allowed_users
```

> ⚠️ Ensure any `http_access deny all` rule appears **after** the authentication rules.

---

### **Step 5: Restart Squid**

```bash
systemctl restart squid
```

---

### **Step 6: Test Authentication**

- Configure a browser to use the proxy.
- Try visiting any website — you should be prompted for a **username and password**.
- Only users listed in `/etc/squid/passwd` will be allowed.

---

### 📝 Notes & Tips

- **Backup** `squid.conf` before editing:

```bash
cp /etc/squid/squid.conf /etc/squid/squid.conf.bak
```

- **Manage users**:

```bash
# Add user
htpasswd /etc/squid/passwd newuser

# Remove user (manually delete the line)
vim /etc/squid/passwd
```

- **Monitor logins and usage**:

```bash
tail -f /var/log/squid/access.log
```

---

### 🔒 Want to Combine This with IP or Website Filtering?

You can enforce **both user authentication and IP/domain filtering**. For example:

```bash
acl localnet src 192.168.1.0/24
acl ncsa_users proxy_auth REQUIRED
acl deny_sites dstdomain "/etc/squid/deny_sites"

http_access allow ncsa_users localnet
http_access deny deny_sites
http_access deny all
```

> This setup ensures only authenticated users from your internal network can access the proxy and blocks specified sites.

