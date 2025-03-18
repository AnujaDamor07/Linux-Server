### **dig (Domain Information Groper) DNS Client Tool**

`dig` (Domain Information Groper) is a powerful DNS lookup tool used to query DNS servers for information about host addresses, mail exchanges, name servers, and other DNS records. It provides detailed insights into how DNS queries are resolved and is commonly used for troubleshooting DNS issues or gathering DNS information.

---

### **Basic `dig` Commands**

#### **1. Perform a Basic DNS Lookup**
- Use `dig` without any arguments to query DNS servers for root servers:
  ```bash
  dig
  ```
  This will provide information about the root servers.

#### **2. Lookup a Specific Domain**
- Query DNS records for a specific domain:
  ```bash
  dig google.com
  ```

#### **3. Query a Specific DNS Server**
- Query `google.com` using a specific DNS server (e.g., `8.8.8.8`):
  ```bash
  dig google.com @8.8.8.8
  ```

---

### **Query Specific DNS Record Types**

#### **1. A Record (IPv4)**
- Query the IPv4 address of a domain:
  ```bash
  dig google.com A
  ```

#### **2. AAAA Record (IPv6)**
- Query the IPv6 address of a domain:
  ```bash
  dig google.com AAAA
  ```

#### **3. NS Record (Name Server)**
- Query the name server for a domain:
  ```bash
  dig google.com NS
  ```

#### **4. MX Record (Mail Exchange)**
- Query the mail exchange server for a domain:
  ```bash
  dig google.com MX
  ```

#### **5. SOA Record (Start of Authority)**
- Query the SOA (Start of Authority) record for a domain:
  ```bash
  dig google.com SOA
  ```

#### **6. TXT Record (Text)**
- Query the TXT records for a domain:
  ```bash
  dig google.com TXT
  ```

#### **7. ANY Record (All available records)**
- Retrieve all available DNS records for a domain:
  ```bash
  dig google.com ANY
  ```

#### **8. HINFO Record (Host Information)**
- Query the HINFO record for a domain:
  ```bash
  dig armourinfosec.com HINFO
  ```

---

### **Shortened Output**

#### **1. Short Answer Format**
- Display simplified output (only the answer section):
  ```bash
  dig google.com +short
  ```

#### **2. A Record in Short Format**
- Query the A record and display a short format:
  ```bash
  dig armourinfosec.com A +short
  ```

#### **3. AAAA Record in Short Format**
- Query the AAAA record and display a short format:
  ```bash
  dig armourinfosec.com AAAA +short
  ```

#### **4. NS Record in Short Format**
- Query the NS record and display a short format:
  ```bash
  dig armourinfosec.com NS +short
  ```

#### **5. MX Record in Short Format**
- Query the MX record and display a short format:
  ```bash
  dig armourinfosec.com MX +short
  ```

#### **6. ANY Record in Short Format**
- Query the ANY record and display a short format:
  ```bash
  dig google.com ANY +short
  ```

---

### **Customizing Output**

#### **1. Suppress All Output**
- To suppress all output (only error messages will show):
  ```bash
  dig google.com +noall
  ```

#### **2. Display Only the Answer Section**
- Display only the answer section of the query:
  ```bash
  dig google.com +noall +answer
  ```

#### **3. Display the Question and Answer Section**
- Display both the question and answer sections:
  ```bash
  dig google.com +noall +answer +question
  ```

#### **4. Fine-tune Output Display**
- Suppress comments, questions, authority, additional, and stats sections:
  ```bash
  dig google.com +nocomments +noquestion +noauthority +noadditional +nostats
  ```

---

### **Bulk DNS Lookup**

#### **1. Create a File with Domains**
- Create a text file (`domain_list.txt`) that contains a list of domains:
  ```bash
  vim domain_list.txt
  ```
  Example content:
  ```bash
  google.com
  facebook.com
  armourinfosec.com
  youtube.com
  ```

#### **2. Query Multiple Domains from a File**
- Use `dig` to query all domains listed in the file:
  ```bash
  dig -f domain_list.txt
  ```

#### **3. Shortened Output for Multiple Domains**
- Get a simplified output for all domains listed:
  ```bash
  dig -f domain_list.txt +short
  ```

#### **4. Save Output to a File**
- Save the output to a file:
  ```bash
  dig -f domain_list.txt +short > ip_add_list.txt
  ```

---

### **Reverse DNS Lookup**

#### **1. Reverse DNS Lookup (PTR Record)**
- Find the hostname associated with an IP address:
  ```bash
  dig -x 8.8.8.8
  ```
  or
  ```bash
  dig -x 8.8.8.8 PTR
  ```

#### **2. Shortened Reverse Lookup Output**
- Get a simplified reverse lookup output:
  ```bash
  dig -x 8.8.8.8 +short
  ```

#### **3. Reverse Lookup Using Bulk IPs**

- **Create a File with IP Addresses**:
  ```bash
  vim ip_add_list2.txt
  ```
  Example content:
  ```bash
  8.8.8.8
  64.6.64.6
  8.8.4.4
  1.1.1.1
  28.20.20.20
  ```

- **Generate -x Format Using `awk`**:
  Convert IPs to -x format:
  ```bash
  awk '$0="-x " $0' ip_add_list2.txt >> ip_add_list3.txt
  ```

- **Generate -x Format Using `sed`**:
  Convert IPs to -x format:
  ```bash
  cat ip_add_list2.txt | sed -e "s/.*/-x &/" > ip_add_list4.txt
  ```

- **Query Reverse DNS for Multiple IPs**:
  Perform reverse lookups using the modified file:
  ```bash
  dig -f ip_add_list3.txt +short
  ```

  Or using the `sed` file:
  ```bash
  dig -f ip_add_list4.txt +short
  ```

---

