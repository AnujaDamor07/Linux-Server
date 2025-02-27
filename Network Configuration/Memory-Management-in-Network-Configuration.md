
## **📌 1. Checking Memory Usage with `free` Command**

The `free` command displays memory usage in the system, showing both available and used memory. It provides memory statistics in human-readable formats (KB, MB, GB, etc.).

---

### **Step 1: Display Memory Usage in a Human-Readable Format**

To display memory usage in a human-readable format (i.e., auto-convert to GB, MB, KB):

```bash
free -h
```

**Example Output:**
```bash
               total        used        free      shared  buff/cache   available
Mem:           8.0Gi       3.1Gi       1.5Gi       0.3Gi       3.4Gi       4.2Gi
Swap:          2.0Gi       0.0Gi       2.0Gi
```

- **total**: Total memory available.
- **used**: Memory used by processes and cache.
- **free**: Memory that is not being used.
- **available**: Memory available for starting new processes without swapping.

---

### **Step 2: Display Memory Usage in Gigabytes**

To display memory usage in gigabytes:

```bash
free -g
```

---

### **Step 3: Display Memory Usage in Megabytes**

To display memory usage in megabytes:

```bash
free -m
```

---

### **Step 4: Display Memory Usage in Kilobytes**

To display memory usage in kilobytes:

```bash
free -k
```

---

## **📌 2. Monitoring System Performance with `vmstat`**

The `vmstat` (virtual memory statistics) command provides detailed system performance statistics, including CPU, memory, and disk usage.

---

### **Step 1: Display CPU and Memory Usage Statistics**

To display CPU and memory usage statistics:

```bash
vmstat
```

**Example Output:**
```bash
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si  so   bi   bo   in   cs us sy id wa st
 0  0      0 123456  23456  45678    0   0    3    4   89   67  1  3 95  0  1
```

- `r`: Number of processes waiting for run time.
- `b`: Number of processes in uninterruptible sleep.
- `swpd`: Amount of swap space used.
- `free`: Free memory.
- `buff`: Memory used as buffers.
- `cache`: Memory used as cache.
- `si`: Memory swapped in from disk (swap-in).
- `so`: Memory swapped out to disk (swap-out).
- `bi`: Blocks received from a block device (disk).
- `bo`: Blocks sent to a block device (disk).
- `in`: Number of interrupts per second.
- `cs`: Number of context switches per second.
- `us`: Percentage of CPU time spent in user space.
- `sy`: Percentage of CPU time spent in kernel space.
- `id`: Percentage of CPU time spent idle.
- `wa`: Percentage of CPU time spent waiting for I/O.
- `st`: Percentage of CPU time stolen by virtual machines.

---

### **Step 2: Show Active and Inactive Memory**

To display statistics for active and inactive memory:

```bash
vmstat -a
```

---

### **Step 3: Display Statistics in Kilobytes**

To display the statistics in kilobytes:

```bash
vmstat -S k
```

---

### **Step 4: Display Statistics in Megabytes**

To display the statistics in megabytes:

```bash
vmstat -S m
```

---

### **Step 5: Continuous Monitoring with `vmstat`**

To continuously monitor system performance and display 5 reports every 4 seconds:

```bash
vmstat 4 5
```

**Explanation:**
- `4`: The interval (in seconds) between each report.
- `5`: The number of reports.

---

### **Step 6: Continuous Monitoring in Megabytes**

To continuously monitor system performance and display 5 reports every 4 seconds in megabytes:

```bash
vmstat -S M 4 5
```

---

### **Step 7: Include Timestamps in the Output**

To display continuous reports with timestamps, use:

```bash
vmstat -t 4 5 -S M
```

---

## **📌 3. Disk and CPU Performance with `iostat`**

The `iostat` command helps analyze CPU and disk I/O performance. It provides information about CPU usage, as well as input/output statistics for devices and partitions.

---

### **Step 1: Install `iostat` (If Not Installed)**

If `iostat` is not available, you can install it using:

```bash
yum install sysstat
```

---

### **Step 2: Display CPU and Disk Performance Statistics**

To display CPU and disk performance statistics:

```bash
iostat
```

**Example Output:**
```bash
Linux 3.10.0-1127.el7.x86_64 (hostname)  02/27/2025  _x86_64_    (2 CPU)

avg-cpu:  %user   %nice    %system   %iowait   %steal   %idle
           9.00    0.00      1.00      0.00      0.00     90.00

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               12.00      800.00       120.00    1600.00     240.00
```

---

### **Step 3: Update Statistics with a 4-Second Interval**

To update the statistics 5 times, with a 4-second interval:

```bash
iostat 4 5
```

---

## **📌 4. Listing Open Files with `lsof`**

The `lsof` (List Open Files) command displays all open files and network connections used by processes.

---

### **Step 1: Install `lsof` (If Not Installed)**

If `lsof` is not available, install it using:

```bash
yum install lsof
```

---

### **Step 2: List All Open Files**

To list all open files:

```bash
lsof
```

---

### **Step 3: Filter by User (e.g., `root`)**

To list open files for a specific user (e.g., `root`):

```bash
lsof -u root
```

---

### **Step 4: Show Open Files for User `armour`**

To show open files for a specific user (`armour`):

```bash
lsof -u armour
```

---

### **Step 5: Show Open Files Without Resolving Hostnames**

To show open files for `root` without resolving hostnames:

```bash
lsof -u root -n
```

---

### **Step 6: Display Open Network Files**

To display open network files:

```bash
lsof -i
```

---

### **Step 7: Show Open Network Connections Without Resolving Hostnames**

To show open network connections without resolving hostnames:

```bash
lsof -i -n
```

---

### **Step 8: Filter by Protocol (TCP)**

To list open TCP connections:

```bash
lsof -n -i TCP
```

---

### **Step 9: Filter by Protocol (UDP)**

To list open UDP connections:

```bash
lsof -n -i UDP
```

---

### **Step 10: Show Processes Using Port 22 (SSH)**

To show the process using port 22 (SSH):

```bash
lsof -n -i TCP:22
```

---

### **Step 11: Show Processes Using Ports 80, 443, and 22**

To show processes using ports 80 (HTTP), 443 (HTTPS), and 22 (SSH):

```bash
lsof -n -i TCP:80,443,22
```

---

### **Step 12: Show TCP Connections in a Port Range (80-500)**

To show TCP connections within the port range 80-500:

```bash
lsof -n -i TCP:80-500
```

---

### **Step 13: Show UDP Connections on Port 53 (DNS)**

To show UDP connections on port 53 (DNS):

```bash
lsof -n -i UDP:53
```

---

### **Step 14: Managing Open File Descriptors for a Process**

To list open files for a process with a specific ID (e.g., 6020):

```bash
lsof -n -p 6020
```

---

### **Step 15: Show Open Network Files for Process 1571**

To display open network files for a specific process (e.g., 1571):

```bash
lsof -n -i -p 1571
```

---

### **Step 16: Show IPv6 Connections**

To show IPv6 connections:

```bash
lsof -n -i 4
```

---

### **Step 17: Killing Processes Using `lsof`**

To kill all processes owned by the user `armour`:

```bash
kill -9 $(lsof -t -u armour)
```

---

## **📊 Summary of Memory and Process Monitoring Commands**

| Command                             | Purpose                                               |
|-------------------------------------|-------------------------------------------------------|
| `free -h`                           | Show memory usage in human-readable format            |
| `vmstat 4 5`                        | Monitor CPU and memory stats every 4 seconds, 5 times |
| `iostat`                            | View CPU and disk performance                        |
| `lsof -u armour`                    | List files opened by user `armour`                    |
| `lsof -n -i TCP:22`                 | Show process using port 22 (SSH)                     |
| `kill -9 $(lsof -t -u armour)`      | Kill all processes owned by `armour`                 |

---


