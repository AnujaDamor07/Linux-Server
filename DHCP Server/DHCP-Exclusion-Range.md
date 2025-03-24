### **Configuring DHCP Exclusion Range**

The purpose of configuring an exclusion range in DHCP is to prevent specific IP addresses from being dynamically assigned to clients. These addresses are often reserved for static IP addresses, network infrastructure devices, or any other devices that require fixed IPs.

Here’s a step-by-step guide on how to configure a DHCP exclusion range.

---

### **Step 1: Edit the DHCP Configuration File**

To begin, open the DHCP configuration file for editing.

1. Open the terminal and use a text editor (like `vim`) to edit the configuration file:
   ```bash
   vim /etc/dhcp/dhcpd.conf
   ```

---

### **Step 2: Define the Exclusion Range**

In the DHCP configuration file, you can define a range of IP addresses that the DHCP server will **exclude** from being assigned dynamically to clients. The exclusion range prevents the DHCP server from assigning those IPs, ensuring that only IPs outside the excluded range are handed out.

#### **Example 1: Exclude IP Range 192.168.1.52 to 192.168.1.70**

Here’s an example where we want to **exclude IP addresses** between `192.168.1.52` and `192.168.1.70` from being assigned by the DHCP server.

```bash
# DHCP Server Configuration file.
# See /usr/share/doc/dhcp-server/dhcpd.conf.example
# See dhcpd.conf(5) man page

authoritative;

# Specify network address and subnet mask
subnet 192.168.1.0 netmask 255.255.255.0 {

    # Specify the range of lease IP addresses
    range 192.168.1.51 192.168.1.51;      # Assign this single IP (192.168.1.51) to a specific PC
    range 192.168.1.71 192.168.1.150;     # Assign IPs from 192.168.1.71 to 192.168.1.150

    # Exclude IP addresses from 192.168.1.52 to 192.168.1.70

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

#### **Explanation of the Configuration:**
- **Range 1**: `range 192.168.1.51 192.168.1.51` — This assigns the IP `192.168.1.51` to a specific device. In this case, it's only one device and not a range.
- **Range 2**: `range 192.168.1.71 192.168.1.150` — This range will be dynamically assigned to devices requesting an IP.
- **Exclusion**: The IP range from `192.168.1.52` to `192.168.1.70` is **excluded** from the DHCP pool. The DHCP server will not assign any IPs in this range.

---

### **Step 3: Restart the DHCP Service**

Once you've made the necessary changes to the `dhcpd.conf` file, you need to restart the DHCP service to apply those changes.

1. Restart the DHCP server service to ensure it starts using the updated configuration:
   ```bash
   systemctl restart dhcpd
   ```

2. After restarting, you can verify the lease assignments and exclusions by checking the **DHCP leases** file:
   ```bash
   cat /var/lib/dhcpd/dhcpd.leases
   ```

This file contains information about the IPs assigned by the DHCP server and any exclusions will be evident in the lease history.

---

### **Additional Example of Multiple Exclusion Ranges**

You can exclude more than one range of IP addresses within the same subnet. For example:

```bash
# Exclude multiple ranges: 
# Exclude 192.168.1.51 to 192.168.1.60 and 192.168.1.211 to 192.168.1.230

subnet 192.168.1.0 netmask 255.255.255.0 {
    # Exclude IPs between 192.168.1.51 and 192.168.1.60
    range 192.168.1.61 192.168.1.150;
    
    # Exclude IPs between 192.168.1.211 and 192.168.1.230
    range 192.168.1.231 192.168.1.254;
    
    # Other DHCP options like routers, DNS, etc.
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
}
```

---

### **Explanation of Exclusion Configuration:**

- **Excluded IP Range**: IPs between `192.168.1.51` and `192.168.1.60` are excluded, and `192.168.1.211` to `192.168.1.230` are excluded, while the server will assign IPs from `192.168.1.61` to `192.168.1.150` and `192.168.1.231` to `192.168.1.254`.
- This configuration is especially useful for excluding IP addresses assigned to **static devices** (like printers, servers, etc.).

---
