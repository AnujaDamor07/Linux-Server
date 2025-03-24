
### **1. Check Available Repositories**

Ensure that the necessary repositories are available for installing the DHCP server package:
```bash
yum repolist all
```
This command lists all available repositories. Verify that the repository containing the `dhcp-server` package is available.

---

### **2. Verify if DHCP Package is Installed**

Check whether the DHCP package is already installed on your system:
```bash
rpm -qa | grep dhcp
```
This will return any installed packages related to `dhcp`, if they exist.

---

### **3. Install DHCP Server**

Install the `dhcp-server` package if it's not already installed:
```bash
yum install dhcp-server.x86_64
```
This command will install the DHCP server package on your system.

---

### **4. Verify Installation**

Check if the DHCP package and server are correctly installed:
```bash
rpm -qa | grep dhcp
rpm -qa | grep dhcp-server
```
Both commands verify that the DHCP-related packages (`dhcp` and `dhcp-server`) are installed.

---

### **5. Get Detailed Information About the DHCP Server**

To display detailed information about the installed DHCP server package:
```bash
rpm -qi dhcp-server
```
This will provide information like the version, release, and description of the DHCP server package.

---

### **6. List Documentation Files for DHCP Server**

List all documentation files included with the DHCP server package:
```bash
rpm -qd dhcp-server
```
This shows the documentation files installed with the `dhcp-server` package, which can be useful for reference.

---

### **7. List Configuration Files for DHCP Server**

List the configuration files included with the DHCP server:
```bash
rpm -qc dhcp-server
```
This command shows the configuration files used by the DHCP server.

---

### **8. List All Files Installed by DHCP Server**

To see all files installed by the `dhcp-server` package, including binaries, configuration, and documentation:
```bash
rpm -ql dhcp-server
```

---

### **9. Edit DHCP Configuration File**

The DHCP configuration file is where you define the network settings for the DHCP server. Open it with an editor (like `vim`):
```bash
vim /etc/dhcp/dhcpd.conf
```

#### Sample DHCP Configuration:
```bash
# DHCP Server Configuration file. 
# See /usr/share/doc/dhcp-server/dhcpd.conf.example 
# See dhcpd.conf(5) man page 

authoritative;

# Specify network address and subnet mask 
subnet 192.168.1.0 netmask 255.255.255.0 { 
    # Specify the range of lease IP addresses 
    range 192.168.1.50 192.168.1.150; 

    # Specify default gateway 
    option routers 192.168.1.1; 

    # DNS servers for name resolution 
    option domain-name-servers 8.8.8.8, 8.8.4.4; 

    # Specify broadcast address 
    option broadcast-address 192.168.1.255; 

    # Default lease time 
    default-lease-time 600; 

    # Max lease time 
    max-lease-time 7200; 
}
```
Save and exit the file after editing (`:wq!`).

---

### **10. Reference Example Configuration**

You can view an example configuration file provided with the DHCP server package:
```bash
vim /usr/share/doc/dhcp-server/dhcpd.conf.example
```
This file serves as a reference for setting up a custom DHCP configuration.

---

### **11. Start and Check DHCP Service**

#### Check DHCP Service Status:
To check the current status of the DHCP service:
```bash
systemctl status dhcpd.service
```

#### Start the DHCP Service:
To start the DHCP service:
```bash
systemctl start dhcpd.service
```

#### Restart the DHCP Service:
To restart the service (useful after configuration changes):
```bash
systemctl restart dhcpd.service
```

#### Enable Service to Start on Boot:
To enable the service to start automatically during boot:
```bash
systemctl enable dhcpd.service
```

---

### **12. Check Open Ports**

Check which ports are open and listening on your system:
```bash
netstat -nltup
```

To check if the DHCP ports (67/UDP) are open:
```bash
netstat -nltup | grep dhcp
```

---

### **13. Update Firewall Rules (Firewalld)**

#### Open DHCP Port in Firewall:
Allow DHCP traffic through the firewall using the `firewalld`:
```bash
firewall-cmd --add-port=67/udp --permanent
```

#### Reload Firewall:
To apply the changes and reload the firewall:
```bash
firewall-cmd --reload
```

#### Verify Firewall Rules:
Check if the DHCP port is open:
```bash
firewall-cmd --list-ports
```
Alternatively, check the detailed firewall configuration:
```bash
firewall-cmd --list-all
```

---

### **14. Check DHCP Leases**

To view the current DHCP leases, which show which IP addresses have been assigned to clients:
```bash
cat /var/lib/dhcpd/dhcpd.leases
```
This file contains information about active DHCP leases, such as the assigned IP addresses, lease times, and client identifiers.

---

