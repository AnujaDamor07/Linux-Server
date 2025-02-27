### **Step-by-Step Guide: Network Configuration in Linux**

---

## **📌 Step 1: Check Current Network Configuration**

Before making any changes, it's useful to view the current network configuration.

### **🔹 1.1 Check Network Interfaces**
To see all available network interfaces on your system, use the following command:

```bash
ip a
```
Or:
```bash
ifconfig
```

**Output Example:**
```bash
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0
       valid_lft forever preferred_lft forever
```

**This shows the network interfaces along with their IP addresses.**

---

## **📌 Step 2: Configure Network Interface**

You can configure network settings manually or using **NetworkManager** (which is available in many modern Linux distributions).

### **🔹 2.1 Configure Static IP Address**
To configure a static IP, edit the network interface configuration file based on your distribution.

#### **For Ubuntu/Debian:**
1. Edit the `/etc/netplan/00-installer-config.yaml` file:

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

2. Update the file to configure a static IP. Example configuration:
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
```

3. Apply the changes:
```bash
sudo netplan apply
```

#### **For CentOS/RHEL/Fedora:**
1. Edit the network interface configuration file located in `/etc/sysconfig/network-scripts/` (e.g., `/etc/sysconfig/network-scripts/ifcfg-eth0`).

```bash
sudo nano /etc/sysconfig/network-scripts/ifcfg-eth0
```

2. Update it to the following static configuration:

```plaintext
DEVICE=eth0
BOOTPROTO=none
ONBOOT=yes
IPADDR=192.168.1.100
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
DNS1=8.8.8.8
DNS2=8.8.4.4
```

3. Restart the network service:
```bash
sudo systemctl restart network
```

---

### **🔹 2.2 Configure DHCP (Dynamic IP Address)**

If you'd like your system to obtain an IP address automatically using DHCP, ensure the `BOOTPROTO` is set to `dhcp` in the configuration file:

#### **For Ubuntu/Debian:**
In `/etc/netplan/00-installer-config.yaml`, use:

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: yes
```

Then apply:

```bash
sudo netplan apply
```

#### **For CentOS/RHEL/Fedora:**
Edit `/etc/sysconfig/network-scripts/ifcfg-eth0`:

```plaintext
DEVICE=eth0
BOOTPROTO=dhcp
ONBOOT=yes
```

Then restart the network:

```bash
sudo systemctl restart network
```

---

## **📌 Step 3: Configure DNS Settings**

### **🔹 3.1 Edit `/etc/resolv.conf`**

If you need to manually set DNS servers, edit the `/etc/resolv.conf` file:

```bash
sudo nano /etc/resolv.conf
```

Add your desired DNS servers, e.g., Google's public DNS servers:

```plaintext
nameserver 8.8.8.8
nameserver 8.8.4.4
```

**Note:** This file can be automatically overwritten by network managers (e.g., `dhclient`), so consider making your changes persistent using network manager tools.

---

## **📌 Step 4: Restart Networking Service**

After making changes to network configurations, restart the network service to apply them.

### **For Ubuntu/Debian (using `systemd`):**
```bash
sudo systemctl restart systemd-networkd
```

### **For CentOS/RHEL/Fedora (using `network` service):**
```bash
sudo systemctl restart network
```

### **For systems using `NetworkManager`:**
```bash
sudo systemctl restart NetworkManager
```

---

## **📌 Step 5: Verify Configuration**

After configuring your network, verify the changes:

### **5.1 Check IP Address:**

```bash
ip a
```

Or:

```bash
ifconfig
```

### **5.2 Check Network Connectivity:**

You can check the network connectivity using `ping`:

```bash
ping 192.168.1.1   # Ping your gateway
ping google.com    # Test internet connectivity
```

---

## **📌 Step 6: Troubleshooting**

If you're facing network issues after configuration, here are some steps to troubleshoot:

### **6.1 Check Network Status:**

Check the status of the network service:

```bash
sudo systemctl status network
```

For `NetworkManager`:

```bash
sudo systemctl status NetworkManager
```

### **6.2 Restart Network Interface:**

If the interface is not behaving correctly, restart it:

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Or with `ip` commands:

```bash
sudo ip link set eth0 down
sudo ip link set eth0 up
```

### **6.3 Check Logs:**

Check network-related logs for any errors:

```bash
sudo journalctl -xe | grep network
```

---

## **📊 Summary of Common Network Commands**

| Command                                | Description                             |
|----------------------------------------|-----------------------------------------|
| `ip a`                                 | View network interfaces and IP addresses |
| `ifconfig`                             | View network interfaces (older command)  |
| `sudo nano /etc/netplan/00-installer-config.yaml` | Configure static IP (Ubuntu/Debian)  |
| `sudo systemctl restart network`       | Restart network service (CentOS/RHEL/Fedora) |
| `sudo systemctl restart NetworkManager` | Restart NetworkManager service         |
| `sudo nano /etc/resolv.conf`           | Configure DNS servers manually         |
| `ping google.com`                      | Check internet connectivity            |
| `sudo systemctl status network`        | Check the status of the network service |
| `sudo systemctl status NetworkManager` | Check the status of the NetworkManager service |



