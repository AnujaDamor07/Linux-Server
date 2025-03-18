### **nslookup - DNS Client Tool**

`nslookup` (Name Server Lookup) is a network administration tool used to query the Domain Name System (DNS) to obtain domain name or IP address mapping and other DNS records. It helps network administrators and users to troubleshoot DNS issues or retrieve information about domain names.

---

### **Basic `nslookup` Commands**

#### **1. Lookup a Domain's IP Address**
- Use `nslookup` to find the IP address of a domain:
  ```bash
  nslookup google.com
  ```
  This command will provide the IPv4 address for `google.com`.

#### **2. Lookup a Domain Using a Specific DNS Server**
- Query a domain using a specific DNS server:
  ```bash
  nslookup google.com 64.6.64.6
  ```
  This uses `64.6.64.6` as the DNS server to query for `google.com`.

---

### **Query Specific DNS Record Types**

#### **1. A Record (IPv4)**
- Query the A record (IPv4 address) for a domain:
  ```bash
  nslookup -type=A google.com
  ```
  This will return the IPv4 address of `google.com`.

#### **2. AAAA Record (IPv6)**
- Query the AAAA record (IPv6 address) for a domain:
  ```bash
  nslookup -type=AAAA google.com
  ```

#### **3. NS Record (Name Server)**
- Query the name server (NS) for a domain:
  ```bash
  nslookup -type=NS google.com
  ```

#### **4. MX Record (Mail Exchange)**
- Query the mail exchange (MX) servers for a domain:
  ```bash
  nslookup -type=MX google.com
  ```

#### **5. SOA Record (Start of Authority)**
- Query the SOA (Start of Authority) record for a domain:
  ```bash
  nslookup -type=SOA google.com
  ```

#### **6. TXT Record (Text)**
- Query the TXT records for a domain:
  ```bash
  nslookup -type=TXT google.com
  ```

---

### **Other Useful Lookups**

#### **1. Lookup a Subdomain**
- Query a specific subdomain:
  ```bash
  nslookup www.armourinfosec.com
  ```
  This will provide DNS details for the subdomain `www.armourinfosec.com`.

#### **2. Query All Available Records**
- Retrieve all available DNS records for a domain:
  ```bash
  nslookup -type=ANY google.com
  ```

---

### **Interactive `nslookup` Mode**

`nslookup` can also be run interactively, allowing you to perform multiple queries without reopening the tool each time.

#### **Start Interactive Mode**
- Launch `nslookup` without any arguments:
  ```bash
  nslookup
  ```

  Once in interactive mode, you can perform various queries.

#### **Example Interactive Commands**

1. **Query a Specific Domain:**
   - To query `facebook.com`, just type:
     ```bash
     facebook.com
     ```

2. **Set the Query Type to NS Records:**
   - Set the query type to NS (Name Server) records:
     ```bash
     set type=ns
     facebook.com
     ```

3. **Set the Query Type to TXT Records:**
   - Set the query type to TXT (Text) records:
     ```bash
     set type=txt
     facebook.com
     ```

4. **Use a Specific DNS Server:**
   - To use a specific DNS server (e.g., `64.6.64.6`):
     ```bash
     server 64.6.64.6
     ```

---

