### DNS Server Configuration Guide

---

### **DNS Server Types**

#### **1. Non-Authoritative (Recursive) Nameserver**

A non-authoritative nameserver resolves DNS queries by contacting other nameservers to find the answer. It does not store original DNS records but relies on external sources to answer queries.

##### **Caching Nameserver**
- **Description**: Caching nameservers temporarily store DNS query results to improve resolution time and reduce load on authoritative servers.
- **Example Command**: To test DNS resolution using a caching nameserver (Google's public DNS server `8.8.8.8`):
  ```bash
  dig example.com @8.8.8.8
  ```

##### **Forwarding Nameserver**
- **Description**: Forwarding nameservers receive DNS queries and forward them to another nameserver (usually a caching or authoritative server) for resolution.
- **Configuration Example**: To configure a forwarding nameserver:
  ```bash
  echo "nameserver 8.8.8.8" >> /etc/resolv.conf
  ```

#### **2. Authoritative Nameserver**

Authoritative nameservers store and provide responses for DNS queries about the domains they are responsible for. They hold the actual DNS records.

##### **Primary Nameserver**
- **Description**: The primary nameserver is the main source for DNS zone data and is responsible for updates and changes to DNS records.
- **Example Configuration (`named.conf`)** for a primary nameserver:
  ```bash
  zone "example.com" {
      type master;
      file "/etc/bind/db.example.com";
  };
  ```

##### **Secondary Nameserver**
- **Description**: The secondary nameserver obtains zone data from the primary nameserver and acts as a backup in case the primary is unavailable.
- **Example Configuration (`named.conf`)** for a secondary nameserver:
  ```bash
  zone "example.com" {
      type slave;
      file "/etc/bind/db.example.com";
      masters { 192.168.1.1; };
  };
  ```

---

### **DNS Client Tools**

#### **1. Check Installed BIND Packages**
- **Command to list installed BIND packages**:
  ```bash
  rpm -qa | grep bind
  ```

#### **2. Check Installed BIND Utilities**
- **Command to list installed BIND utilities packages**:
  ```bash
  rpm -qa | grep bind-utils
  ```

#### **3. Install BIND Utilities**
- **To install BIND utilities** using `yum`:
  ```bash
  yum install bind-utils
  ```

#### **4. List Files Installed by bind-utils**
- **Command to list all files installed by the `bind-utils` package**:
  ```bash
  rpm -ql bind-utils
  ```

#### **5. List Configuration Files for bind-utils**
- **Command to list configuration files for the `bind-utils` package**:
  ```bash
  rpm -qc bind-utils
  ```

#### **6. List Documentation Files for bind-utils**
- **Command to list documentation files for the `bind-utils` package**:
  ```bash
  rpm -qd bind-utils
  ```

---

### **Common DNS Client Tools (bind-utils)**

Below are the most commonly used DNS client tools included with `bind-utils`:

- **/usr/bin/delv**: DNS lookup and validation utility.
- **/usr/bin/dig**: Query DNS servers for information about domains.
- **/usr/bin/host**: A simple utility for performing DNS lookups.
- **/usr/bin/mdig**: A multiple query version of `dig`.
- **/usr/bin/nslookup**: Legacy tool to query DNS servers.
- **/usr/bin/nsupdate**: Dynamic DNS update utility.

---

### **DNS Records**

DNS records define how domain names are mapped to IP addresses and other resources. Below are the common types of DNS records:

#### **1. A (Address Mapping) Record**
- **Description**: Specifies an IPv4 address for a given host.
- **Example**:
  ```bash
  example.com 192.168.1.1
  ```

#### **2. AAAA (IPv6 Address) Record**
- **Description**: Specifies an IPv6 address for a given host.
- **Example**:
  ```bash
  example.com 2001:0db8::ff00:0042:8329
  ```

#### **3. CNAME (Canonical Name) Record**
- **Description**: Specifies an alias for another domain name.
- **Example**:
  ```bash
  wp.armourinfosec.com armourinfosec.wordpress.com 20.20.20.20
  ```

#### **4. NS (Name Server) Record**
- **Description**: Specifies an authoritative name server for a given domain.
- **Example**:
  ```bash
  example.com ns1.example.com
  ```

#### **5. PTR (Pointer) Record**
- **Description**: Used for reverse DNS lookups (mapping IP addresses to hostnames).
- **Example**:
  ```bash
  192.168.1.1 example.com
  ```

#### **6. SOA (Start of Authority) Record**
- **Description**: Specifies authoritative information about a DNS zone, including the primary nameserver and zone serial number.
- **Example**:
  ```bash
  example.com. IN SOA ns1.example.com. admin.example.com. (
      2025031101 ; serial
      3600       ; refresh
      1800       ; retry
      1209600    ; expire
      86480      ; minimum TTL
  )
  ```

#### **7. HINFO (Host Information) Record**
- **Description**: Provides information about a host's hardware and operating system.
- **Example**:
  ```bash
  example.com IN HINFO "Intel i7" "Linux"
  ```

#### **8. MX (Mail Exchanger) Record**
- **Description**: Specifies a mail exchange server for a domain.
- **Example**:
  ```bash
  example.com mail.example.com (priority 10)
  ```

#### **9. TXT (Text) Record**
- **Description**: Holds arbitrary text data for a domain, often used for SPF (Sender Policy Framework) or DKIM (DomainKeys Identified Mail) records.
- **Example**:
  ```bash
  example.com IN TXT "v=spf1 include:spf.google.com -all"
  ```

---

