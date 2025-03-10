
### **1. Installation of `tcpdump`**

To install `tcpdump` on a system using `yum`:

```bash
sudo yum install tcpdump
```

To verify the installation:

```bash
tcpdump --version
```

### **2. Basic Commands**

#### **Display Help Information**

To view available options and usage instructions:

```bash
tcpdump -h
```

#### **List Available Interfaces**

To display network interfaces that can be used for packet capture:

```bash
tcpdump -D
```

Or equivalently:

```bash
tcpdump --list-interfaces
```

#### **Capturing Packets**

##### **Capture Packets on a Specific Interface**

To capture packets on a specific network interface (e.g., `enp0s3`):

```bash
tcpdump -i enp0s3
```

Press `Ctrl + C` to stop capturing packets.

##### **Capture TCP Packets**

To capture only TCP packets on `enp0s3`:

```bash
tcpdump -i enp0s3 tcp
```

##### **Capture UDP Packets**

To capture only UDP packets on `enp0s3`:

```bash
tcpdump -i enp0s3 udp
```

For instance, DNS traffic usually uses UDP. You can capture it with:

```bash
tcpdump -i enp0s3 udp
```

#### **Capture Packets Without Resolving Hostnames**

To avoid DNS resolution and display only numerical IP addresses:

- For TCP packets:

```bash
tcpdump -n -i enp0s3 tcp
```

- For UDP packets:

```bash
tcpdump -n -i enp0s3 udp
```

#### **Filtering by Port**

##### **Capture TCP Packets on Specific Ports**

To capture TCP packets on port 443 (HTTPS):

```bash
tcpdump -i enp0s3 tcp port 443
```

To capture TCP packets on port 22 (SSH):

```bash
tcpdump -i enp0s3 tcp port 22
```

##### **Capture UDP Packets on Specific Ports**

To capture UDP packets on port 53 (DNS Queries):

```bash
tcpdump -i enp0s3 udp port 53
```

To capture TCP packets on port 8080:

```bash
tcpdump -i enp0s3 tcp port 8080
```

### **3. Advanced Filtering**

#### **Capture Packets from a Specific Source or Destination**

To capture packets from a specific source IP:

```bash
tcpdump -i enp0s3 src host 192.168.1.1
```

To capture packets destined for a specific IP:

```bash
tcpdump -i enp0s3 dst host 192.168.1.2
```

#### **Capture Packets for a Specific Network**

To capture traffic for a subnet (e.g., `192.168.1.0/24`):

```bash
tcpdump -i enp0s3 net 192.168.1.0/24
```

### **4. Saving and Reading Packet Captures**

#### **Save Captured Packets to a File**

To capture 50 packets on `enp0s3`:

```bash
tcpdump -c 50 -i enp0s3
```

To capture 100 packets on `enp0s3`:

```bash
tcpdump -c 100 -i enp0s3
```

To capture UDP packets on port 53 and save them to a file for later analysis:

```bash
tcpdump -v -n -i enp0s3 udp port 53 -w dnsdump.pcap
```

To capture TCP packets on port 22 and save them:

```bash
tcpdump -v -n -i enp0s3 tcp port 22 -w ssh.pcap
```

#### **Read Captured Packets from a File**

To read the saved capture file:

```bash
tcpdump -r dnsdump.pcap
```

### **5. Additional Options**

#### **Verbose Output**

To capture packets with detailed output:

```bash
tcpdump -vv -i enp0s3
```

#### **Limit Packet Capture to a Specific Count**

To capture only 10 packets and stop:

```bash
tcpdump -c 10 -i enp0s3
```

To capture 50 packets and stop:

```bash
tcpdump -c 50 -i enp0s3
```

To capture 100 packets and stop:

```bash
tcpdump -c 100 -i enp0s3
```

