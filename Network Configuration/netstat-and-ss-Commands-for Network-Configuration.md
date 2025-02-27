**`netstat` and `ss` Commands for Network Configuration in Linux**

Both `netstat` and `ss` are powerful tools used to view and analyze network connections in Linux. While `netstat` is the older and traditional command for network configuration, `ss` is a newer and faster alternative. Here's how you can use these commands step-by-step for network configuration and troubleshooting.

---

## **📌 1. `netstat` Command for Network Configuration**

The `netstat` command provides network statistics, open connections, routing tables, interface statistics, etc.

---

### **Step 1: Check Active Network Connections**

To display the active network connections on your system, run:

```bash
netstat -tuln
```

**Explanation:**
- `-t`: Display only TCP connections.
- `-u`: Display only UDP connections.
- `-l`: Display only listening connections.
- `-n`: Show numerical addresses instead of resolving hostnames.

**Example Output:**
```bash
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
```

**Explanation:**
- The system is listening on port `22` for SSH (`0.0.0.0:22`) and port `80` for HTTP (`:::80`).

---

### **Step 2: Display the Routing Table**

To view the routing table on your system, run:

```bash
netstat -r
```

**Example Output:**
```bash
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

**Explanation:**
- `Destination`: The network destination.
- `Gateway`: The gateway to use to reach the destination.
- `Iface`: The interface used to reach the destination (e.g., `eth0`).

---

### **Step 3: Check Network Interface Statistics**

To view network statistics like the number of packets received or transmitted, use:

```bash
netstat -i
```

**Example Output:**
```bash
Kernel Interface table
Iface       MTU  Met   RX-OK RX-ERR RX-DRP RX-OVR TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500  0     10000     0      0      0    15000     0      0      0 BMRU
```

**Explanation:**
- `RX-OK`: Number of packets received without errors.
- `TX-OK`: Number of packets transmitted without errors.
- `RX-ERR`: Number of received packets with errors.

---

### **Step 4: Check Network Connections by Program**

To see which process is associated with each network connection, use:

```bash
sudo netstat -tulnp
```

**Example Output:**
```bash
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1234/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      5678/apache2
```

**Explanation:**
- `PID/Program name`: The process ID (PID) and the associated program name (e.g., `sshd`, `apache2`).

---

### **Step 5: Check Listening Ports**

To check which ports your system is listening on, run:

```bash
netstat -tuln
```

**Explanation:**
- `-t`: Show TCP connections.
- `-l`: Show only listening sockets.
- `-n`: Show numerical IPs and port numbers (instead of resolving hostnames).

---

## **📌 2. `ss` Command for Network Configuration**

`ss` (Socket Stat) is a faster and more efficient replacement for `netstat`. It's useful for gathering network connection details, and it's often the preferred tool for modern Linux network troubleshooting.

---

### **Step 1: Check Active Network Connections**

To list all active network connections:

```bash
ss -tuln
```

**Explanation:**
- `-t`: Show only TCP sockets.
- `-u`: Show only UDP sockets.
- `-l`: Show listening sockets.
- `-n`: Show numerical addresses instead of resolving hostnames.

**Example Output:**
```bash
State      Recv-Q Send-Q Local Address:Port               Peer Address:Port
LISTEN     0      128          *:22                        *:*                  
LISTEN     0      128          *:80                        *:* 
```

**Explanation:**
- This shows that the system is listening on TCP port `22` (SSH) and TCP port `80` (HTTP).

---

### **Step 2: View Detailed Information About Active Connections**

To get more detailed information about active connections, including the program name (PID) that owns each connection, use:

```bash
ss -tulnp
```

**Explanation:**
- `-p`: Show the process ID (PID) and program name associated with each connection.

**Example Output:**
```bash
State      Recv-Q Send-Q Local Address:Port               Peer Address:Port Process
LISTEN     0      128          *:22                        *:*    users:(("sshd",pid=1234,fd=3))
LISTEN     0      128          *:80                        *:*    users:(("apache2",pid=5678,fd=4))
```

**Explanation:**
- The `users` field shows the process name and its PID that is listening on the respective port (e.g., `sshd` for SSH and `apache2` for HTTP).

---

### **Step 3: View Socket Statistics**

To view general socket statistics, run:

```bash
ss -s
```

**Example Output:**
```bash
Total: 58 (kernel 78)
TCP:   25 (estab 10, closed 15)
UDP:   3 (active 3)
```

**Explanation:**
- The summary provides a quick overview of the current network connections by protocol (e.g., `TCP`, `UDP`), including the number of established, closed, and active connections.

---

### **Step 4: Display Socket Information for All TCP Connections**

To view all active TCP connections, run:

```bash
ss -t
```

**Example Output:**
```bash
State       Recv-Q Send-Q Local Address:Port               Peer Address:Port
ESTAB       0      0       192.168.1.100:ssh               192.168.1.200:12345
```

**Explanation:**
- `ESTAB`: Established connection.
- This shows the local and remote IP address with port information for established connections.

---

### **Step 5: Display Socket Information for a Specific Network Interface**

To show socket information for a specific interface (e.g., `eth0`), run:

```bash
ss -i eth0
```

This provides socket-specific information, such as buffer sizes and internal socket states, for the `eth0` interface.

---

### **Step 6: Display UDP Connections**

To list all UDP connections, use:

```bash
ss -u
```

**Example Output:**
```bash
State     Recv-Q Send-Q Local Address:Port               Peer Address:Port
UNCONN     0      0       192.168.1.100:53               *:*
```

This shows all the UDP sockets that are currently active.

---

## **📊 Summary of Key `netstat` and `ss` Commands**

| Command                     | Description                                         |
|-----------------------------|-----------------------------------------------------|
| `netstat -tuln`              | List active listening TCP/UDP connections          |
| `netstat -r`                 | Show the routing table                             |
| `netstat -i`                 | Show interface statistics                          |
| `netstat -tulnp`             | Show active connections with program/process info  |
| `ss -tuln`                   | List active TCP/UDP listening connections          |
| `ss -tulnp`                  | Show active listening connections with program info|
| `ss -s`                      | Show socket statistics summary                    |
| `ss -t`                      | List all active TCP connections                    |
| `ss -u`                      | Show all active UDP connections                    |

---
