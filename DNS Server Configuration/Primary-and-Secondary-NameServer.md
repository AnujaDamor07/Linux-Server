### **👑 Primary (Master) Nameserver Setup with BIND:**

This guide outlines the complete steps to set up a **Primary (Master) Nameserver** and a **Secondary (Slave) Nameserver** using BIND for DNS.

---

### **Step-by-Step: Primary (Master) Nameserver Setup**

---

### **1️⃣ Install BIND:**

On the master server, install the necessary BIND packages using `yum` (CentOS/RHEL-based systems):

```bash
yum install bind bind-utils -y
```

- `bind`: DNS server software.
- `bind-utils`: Utilities like `dig`, `nslookup`, etc., for DNS querying.

---

### **2️⃣ Edit the Main Configuration File:**

The main configuration file for BIND is located at `/etc/named.conf`. Edit this file to configure your master server.

```bash
vim /etc/named.conf
```

**Example Configuration for Master Server:**

```bash
options {
    listen-on port 53 { any; };
    directory "/var/named";          # Directory where zone files are stored
    allow-transfer { 192.168.1.2; }; # Slave server IP address
    recursion no;                    # Disable recursion (for authoritative DNS)
};

zone "example.com" IN {
    type master;                     # This is a master zone
    file "/var/named/example.com.zone"; # Path to the zone file
    allow-transfer { 192.168.1.2; };   # Slave server IP address to allow zone transfers
};
```

- **options block**: Configures listening port, directory for zone files, and allows transfer to the slave server.
- **zone block**: Defines the DNS zone for `example.com` and specifies that this server is the master for that domain.

---

### **3️⃣ Create the Zone File:**

Next, create the zone file that holds DNS records for your domain (`example.com`). This file will contain mappings for domain names to IP addresses, among other records.

```bash
vim /var/named/example.com.zone
```

**Example Zone File for `example.com`:**

```bash
$TTL 86400
@   IN  SOA  ns1.example.com. admin.example.com. (
        2024031401  ; Serial number (increment when you make changes)
        3600        ; Refresh interval (1 hour)
        1800        ; Retry interval (30 minutes)
        604800      ; Expiration time (1 week)
        86400 )     ; Minimum TTL (1 day)

    IN  NS  ns1.example.com.
    IN  NS  ns2.example.com.

ns1 IN  A   192.168.1.1
ns2 IN  A   192.168.1.2

www IN  A   192.168.1.10
mail IN  A   192.168.1.20
ftp  IN  A   192.168.1.30
db   IN  A   192.16831.40
```

- **SOA (Start of Authority)**: Defines essential information about the zone, including the primary nameserver and contact email (with `.` replacing `@`).
- **NS (Nameserver)**: Specifies the authoritative nameservers for the domain.
- **A (Address)**: Maps domain names (e.g., `www.example.com`) to IP addresses.
- **Mail Record**: The `mail` record maps to the mail server IP (`192.168.1.20`).

---

### **4️⃣ Restart the BIND Service:**

Once the configuration and zone file are set up, restart the BIND service to apply the changes.

```bash
systemctl restart named
systemctl enable named
```

- `systemctl restart named`: Restarts the BIND service.
- `systemctl enable named`: Ensures the BIND service starts automatically on boot.

---

### **📦 Secondary (Slave) Nameserver Setup**

Now, let’s set up the **Secondary (Slave) Nameserver**. The slave server will pull zone data from the master server.

---

### **1️⃣ Install BIND:**

On the slave server, install the BIND packages as well:

```bash
yum install bind bind-utils -y
```

---

### **2️⃣ Edit the Main Configuration File:**

Edit the `/etc/named.conf` file on the slave server to configure it as a slave.

```bash
vim /etc/named.conf
```

**Example Configuration for Slave Server:**

```bash
options {
    listen-on port 53 { any; };
    directory "/var/named";
    recursion no;                    # Disable recursion (for authoritative DNS)
};

zone "example.com" IN {
    type slave;                        # This is a slave zone
    file "/var/named/slaves/example.com.zone"; # Path to the zone file
    masters { 192.168.1.1; };           # IP of the master server (192.168.1.1)
};
```

- **type slave**: Configures this server as a slave for the `example.com` zone.
- **masters block**: Specifies the master server’s IP (e.g., `192.168.1.1`), from which the slave will pull zone data.

---

### **3️⃣ Restart the BIND Service:**

Restart the BIND service on the slave server to apply the changes.

```bash
systemctl restart named
systemctl enable named
```

---

### **✅ Test the Setup (On Both Master & Slave Servers)**

After configuring both the master and slave servers, you should verify the setup and check that the zone is transferred from the master to the slave.

---

#### **1️⃣ Test SOA Record on the Master Server:**

Use `dig` to query the **Start of Authority (SOA)** record from the master server:

```bash
dig @192.168.1.1 example.com SOA
```

- This command queries the master server (IP: `192.168.1.1`) for the SOA record of `example.com`.

---

#### **2️⃣ Test SOA Record on the Slave Server:**

Use `dig` to query the **SOA** record from the slave server:

```bash
dig @192.168.1.2 example.com SOA
```

- This ensures that the slave server has successfully fetched the SOA record from the master.

---

#### **3️⃣ Test Zone Transfer on the Slave Server:**

Use `dig` to check if the zone transfer (`AXFR`) from the master server is successful:

```bash
dig @192.168.1.2 example.com AXFR
```

- This command queries the slave server (IP: `192.168.1.2`) and asks for a complete zone transfer.
- If successful, it will return the full DNS zone data, including A records, MX records, etc.

---

