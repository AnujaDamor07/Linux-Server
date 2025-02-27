 **`netstat` and `ss` Commands for Network Configuration in Linux**

The `netstat` and `ss` commands are both used for monitoring network connections and diagnosing network issues in Linux. While `netstat` is the older, traditional tool, `ss` is a newer, faster tool that is now often preferred for network diagnostics and configuration. Here's how you can use these tools for network configuration and troubleshooting.

---

## **📌 `netstat` Command**

### **1. Check Active Network Connections (`netstat`)**

To see the active network connections, use the following command:

```bash
netstat -tuln
```

**Explanation:**
- `-t`: Show TCP connections.
- `-u`: Show UDP connections.
- `-l`: Display only listening sockets.
- `-n`: Show numeric addresses instead of resolving hostnames.

**Example Output:**
```bash
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
```

**Key Information:**
- `Local Address`: The address and port the service is listening on.
- `Foreign Address`: The address and port of any connected clients.
- `State`: The state of the connection (e.g., `LISTEN`).

---

### **2. Check Listening Ports (`netstat -tuln`)**

To see which ports your machine is listening on, you can use:

```bash
netstat -tuln
```

This will display listening ports and services associated with them.

**Example Output:**
```bash
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
```

In this example, the system is listening on port `22` for SSH and on port `80` for HTTP.

---

### **3. Display Routing Table (`netstat -r`)**

To view the routing table, which shows the paths your data will take, use:

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

**Key Information:**
- `Destination`: The destination network.
- `Gateway`: The gateway to reach the destination.
- `Iface`: The interface used for the route (e.g., `eth0`).

---

### **4. Check Network Interface Statistics (`netstat -i`)**

To get statistics about the network interfaces (packets received, errors, etc.), use:

```bash
netstat -i
```

**Example Output:**
```bash
Kernel Interface table
Iface       MTU  Met   RX-OK RX-ERR RX-DRP RX-OVR TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500  0     10000     0      0      0    15000     0      0      0 BMRU
```

**Key Information:**
- `RX-OK`: Number of received packets without errors.
- `TX-OK`: Number of transmitted packets without errors.
- `RX-ERR` / `TX-ERR`: Number of errors while receiving or transmitting packets.

---

### **5. View Network Connections by Program (`netstat -p`)**

To display the process that is associated with each network connection, use:

```bash
sudo netstat -tulnp
```

**Explanation:**
- `-p`: Show the program (PID) associated with each connection.

**Example Output:**
```bash
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1234/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      5678/apache2
```

---

---

## **📌 `ss` Command**

The `ss` command is a modern tool that can be used for similar purposes as `netstat` but is more efficient and provides more detailed information.

### **1. Check Active Network Connections (`ss`)**

To display active network connections, use the following command:

```bash
ss -tuln
```

**Explanation:**
- `-t`: Show TCP sockets.
- `-u`: Show UDP sockets.
- `-l`: Display only listening sockets.
- `-n`: Show numerical addresses.

**Example Output:**
```bash
State      Recv-Q Send-Q Local Address:Port               Peer Address:Port
LISTEN     0      128          *:22                        *:*                  
LISTEN     0      128          *:80                        *:* 
```

**Key Information:**
- `State`: The connection state (e.g., `LISTEN`).
- `Local Address:Port`: The IP and port of the listening service.
- `Peer Address:Port`: The IP and port of the connected client (only shown for established connections).

---

### **2. View Detailed Information on Connections (`ss -tulnp`)**

To display detailed information about the processes associated with each connection, use:

```bash
ss -tulnp
```

**Explanation:**
- `-p`: Show process ID (PID) and program name.

**Example Output:**
```bash
State      Recv-Q Send-Q Local Address:Port               Peer Address:Port Process
LISTEN     0      128          *:22                        *:*    users:(("sshd",pid=1234,fd=3))
LISTEN     0      128          *:80                        *:*    users:(("apache2",pid=5678,fd=4))
```

---

### **3. Check Connection Status by Protocol (`ss -s`)**

To display summary statistics by protocol (TCP, UDP, etc.), use:

```bash
ss -s
```

**Example Output:**
```bash
Total: 58 (kernel 78)
TCP:   25 (estab 10, closed 15)
UDP:   3 (active 3)
```

This command shows how many active connections there are for each protocol.

---

### **4. Display All TCP Connections (`ss -t`)**

To view all active TCP connections, run:

```bash
ss -t
```

**Example Output:**
```bash
State       Recv-Q Send-Q Local Address:Port               Peer Address:Port
ESTAB       0      0       192.168.1.100:ssh               192.168.1.200:12345
```

---

### **5. View Socket Statistics (`ss -i`)**

To view the socket information, including internal socket states:

```bash
ss -i
```

**Example Output:**
```bash
State    Recv-Q Send-Q Local Address:Port               Peer Address:Port
LISTEN   0      128          *:80                        *:*    info:16
```

This will display details about socket connections, such as state and the buffer size.

---

### **📊 Summary of `netstat` and `ss` Commands**

| Command                    | Description                                         |
|----------------------------|-----------------------------------------------------|
| `netstat -tuln`             | Display active TCP and UDP listening connections   |
| `netstat -r`                | Show the routing table                             |
| `netstat -i`                | Show network interface statistics                  |
| `netstat -p`                | Show network connections with process ID (PID)     |
| `ss -tuln`                  | Display active listening TCP and UDP connections   |
| `ss -tulnp`                 | Display active listening connections with PID info |
| `ss -s`                     | Show protocol summary statistics                   |
| `ss -t`                     | Show all active TCP connections                    |
| `ss -i`                     | Display socket information                         |



