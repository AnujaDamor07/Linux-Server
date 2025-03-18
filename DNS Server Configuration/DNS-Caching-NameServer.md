### **Caching Nameserver Setup Using BIND (Berkeley Internet Name Domain)**

A **caching nameserver** is used to store DNS query results temporarily, improving performance by reducing load on authoritative nameservers and speeding up subsequent queries for the same domain. 

---

### **1. Check Hostname**
   - **Display Current Hostname:**
     ```bash
     hostname
     ```

---

### **2. Update Hostname**
   - **Edit the hostname configuration:**
     ```bash
     vim /etc/hostname
     ```
     Change the hostname as needed (e.g., `ns1.Admin.local`).

### **3. Check DNS Resolver Configuration**
   - **View DNS Settings** (check `/etc/resolv.conf`):
     ```bash
     cat /etc/resolv.conf
     ```

---

### **4. Install and Configure BIND**
   - **Check if BIND is Installed**:
     ```bash
     rpm -qa | grep bind
     ```

   - **Install BIND and Utilities**:
     ```bash
     yum install bind*
     ```

   - **Verify Installation**:
     ```bash
     rpm -qa | grep bind
     ```

   - **Get Information about the Installed Package**:
     ```bash
     rpm -qi bind
     ```

   - **List Installed Files**:
     ```bash
     rpm -ql bind
     ```

   - **List Configuration Files**:
     ```bash
     rpm -qc bind
     ```

---

### **5. Key Configuration Files for BIND**
   - **/etc/named.conf**: Main configuration file.
   - **/etc/named.iscdlv.key**: TSIG key for secure communication between DNS servers.
   - **/etc/named.rfc1912.zones**: Default zones as per RFC 1912.
   - **/etc/named.root.key**: Root trust anchor key for DNSSEC validation.
   - **/var/named/**: Contains zone files and cache data.

   **Important Subdirectories under `/var/named`:**
   - `/var/named/data`: Contains BIND-generated data files.
   - `/var/named/dynamic`: Stores dynamically generated zone files.
   - `/var/named/named.ca`: Contains the list of root DNS servers.
   - `/var/named/named.empty`: Used for unresponsive zones.
   - `/var/named/named.localhost`: Defines zone for localhost (127.0.0.1).
   - `/var/named/named.loopback`: Used for reverse lookup of loopback address.
   - `/var/named/slaves`: Directory for zone files from master DNS servers.

---

### **6. Manage BIND Service**
   - **Check Service Status**:
     ```bash
     systemctl status named.service
     ```

   - **Start the Service**:
     ```bash
     systemctl start named.service
     ```

   - **Check Open Ports for BIND (DNS Port 53)**:
     ```bash
     netstat -nltup | grep named
     netstat -nltup | grep 53
     ```

---

### **7. Test Using `dig`**
   - **Test Localhost Resolution**:
     ```bash
     dig google.com @127.0.0.1
     ```

---

### **8. Configure Network Settings on CentOS 9**
   - **Modify NetworkManager Configuration**:
     ```bash
     vim /etc/NetworkManager/system-connections/enp0s3.nmconnection
     ```
     Example configuration:
     ```ini
     [connection]
     id=enp0s3
     uuid=5dabe1f1-79aa-3751-8ba8-b0f01d817434
     type=ethernet
     interface-name=enp0s3
     autoconnect-priority=-999
     timestamp=1730811905

     [ipv4]
     address1=192.168.1.61/24
     address2=192.168.1.62/24
     dns=127.0.0.1; 
     method=manual
     ```

   - **Restart Network Service**:
     ```bash
     systemctl restart named.service
     reboot
     ```

---

### **9. Configuration of BIND in `/etc/named.conf`**
   - **Edit `named.conf`**:
     ```bash
     vim /etc/named.conf
     ```

   Example configuration for BIND to listen on specific IPs (`192.168.1.61` and `192.168.1.62`):
   ```ini
   options {
       listen-on port 53 { 127.0.0.1; 192.168.1.61; };
       listen-on-v6 port 53 { ::1; };
       directory "/var/named";
       dump-file "/var/named/data/cache_dump.db";
       statistics-file "/var/named/data/named_stats.txt";
       memstatistics-file "/var/named/data/named_mem_stats.txt";
       secroots-file "/var/named/data/named.secroots";
       recursing-file "/var/named/data/named.recursing";
       allow-query { localhost; 192.168.1.0/24; };
       recursion yes;
       dnssec-validation yes;
       managed-keys-directory "/var/named/dynamic";
       geoip-directory "/usr/share/GeoIP";
       pid-file "/run/named/named.pid";
       session-keyfile "/run/named/session.key";
       include "/etc/crypto-policies/back-ends/bind.config";
   };
   ```
   
   - **Restart BIND Service**:
     ```bash
     systemctl restart named
     ```

   - **Check BIND's Listening IPs**:
     ```bash
     ip a
     netstat -nltup
     ```

---

### **10. Configure Firewall Rules (Firewalld)**
   - **Allow DNS Traffic (TCP and UDP Port 53)**:
     ```bash
     firewall-cmd --permanent --add-port=53/udp
     firewall-cmd --permanent --add-port=53/tcp
     firewall-cmd --reload
     ```

---

### **11. Test DNS Queries**
   - **Test from CentOS**:
     ```bash
     dig google.com
     ```

   - **Test from a Windows machine using `nslookup`**:
     Configure DNS server on Windows machine (`192.168.1.61`).
     ```bash
     nslookup google.com 192.168.1.61
     ```

---

### **12. Configure Forwarders**
   - **Add Forwarders in `named.conf`**:
     Forward unresolved queries to Google's public DNS servers:
     ```ini
     forwarders { 8.8.8.8; 8.8.4.4; };
     ```

   - **Restart BIND**:
     ```bash
     systemctl restart named.service
     ```

---

### **13. Capture DNS Traffic Using `tcpdump`**
   - **Capture DNS Traffic on Port 53**:
     ```bash
     tcpdump -i enp0s3 port 53
     tcpdump -n udp port 53
     ```

---

### **14. Define Access Control Lists (ACL) in `named.conf`**
   - **Example ACL Configuration**:
     Define which IP addresses or networks are allowed to query the DNS server:
     ```ini
     acl ns_ip_add {
         127.0.0.1;
         192.168.1.61;
         192.168.1.62;
     };

     acl mynetwork {
         127.0.0.1;
         192.168.1.0/24;
     };

     options {
         listen-on port 53 { ns_ip_add; };
         allow-query { mynetwork; };
     };
     ```

   - **Restart BIND**:
     ```bash
     systemctl restart named.service
     ```

---

