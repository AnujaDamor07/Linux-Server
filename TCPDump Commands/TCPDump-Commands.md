
### Step 1: **Installation of TCPDump**

Before you can use `tcpdump`, you need to install it. Here’s how to install it using `yum`:

1. **Install TCPDump**:
   Run the following command on a system using the `yum` package manager (typically on CentOS, RHEL, or Fedora):
   ```bash
   yum install tcpdump
   ```

2. **Verify the Installation**:
   To check if `tcpdump` was installed successfully, use:
   ```bash
   tcpdump --version
   ```
   This will display the version of `tcpdump` installed on your system.

### Step 2: **Basic TCPDump Commands**

#### 1. **Display Help Information**

To view the available options and usage instructions:
```bash
tcpdump -h
```
This command will show you all the available command-line options for `tcpdump`.

#### 2. **List Available Interfaces**

To see all the network interfaces that can be used for packet capture, run:
```bash
tcpdump -D
```
or equivalently:
```bash
tcpdump --list-interfaces
```
This will display a list of interfaces like `eth0`, `enp0s3`, etc., which can be used for capturing traffic.

### Step 3: **Capturing Packets**

#### 1. **Capture Packets on a Specific Interface**

To start capturing packets on a specific interface, use the `-i` flag with the interface name. For example:
```bash
tcpdump -i enp0s3
```
This will capture packets on the `enp0s3` interface. To stop the capture, press `Ctrl+C`.

#### 2. **Capture Only TCP or UDP Packets**

- **To capture only TCP packets on `enp0s3`**:
  ```bash
  tcpdump -i enp0s3 tcp
  ```

- **To capture only UDP packets on `enp0s3`**:
  ```bash
  tcpdump -i enp0s3 udp
  ```

> **Note**: UDP traffic often includes DNS queries and responses, so if you run the UDP capture, you'll see traffic for DNS requests.

#### 3. **Capture Packets Without Resolving Hostnames**

If you want to capture packets without resolving DNS hostnames (i.e., only display numerical IP addresses), you can use the `-n` flag:
- For **TCP** packets:
  ```bash
  tcpdump -n -i enp0s3 tcp
  ```
- For **UDP** packets:
  ```bash
  tcpdump -n -i enp0s3 udp
  ```

### Step 4: **Filtering Packets by Port**

#### 1. **Capture TCP Packets on Specific Ports**

- **For HTTPS (Port 443)**:
  ```bash
  tcpdump -i enp0s3 tcp port 443
  ```

- **For SSH (Port 22)**:
  ```bash
  tcpdump -i enp0s3 tcp port 22
  ```

#### 2. **Capture UDP Packets on Specific Ports**

- **For DNS (Port 53)**:
  ```bash
  tcpdump -i enp0s3 udp port 53
  ```

#### 3. **Capture TCP Packets on a Different Interface and Port**

For example, to capture TCP packets on port 8080 on the `eth0` interface:
```bash
tcpdump -i eth0 tcp port 8080
```

### Step 5: **Advanced Filtering**

#### 1. **Capture Packets from a Specific Source or Destination**

- **To capture packets from a specific source IP address**:
  ```bash
  tcpdump -i enp0s3 src host 192.168.1.1
  ```

- **To capture packets destined for a specific IP address**:
  ```bash
  tcpdump -i enp0s3 dst host 192.168.1.2
  ```

#### 2. **Capture Packets for a Specific Network (Subnet)**

To capture traffic for a specific subnet (e.g., `192.168.1.0/24`):
```bash
tcpdump -i enp0s3 net 192.168.1.0/24
```

### Step 6: **Saving and Reading Packet Captures**

#### 1. **Save Captured Packets to a File**

You can save your packet capture to a file for later analysis. For example, to capture 50 packets on the `enp0s3` interface:
```bash
tcpdump -c 50 -i enp0s3
```

To capture UDP packets on port 53 and save them to a file (`dnsdump.pcap`):
```bash
tcpdump -v -n -i enp0s3 udp port 53 -w dnsdump.pcap
```

To capture TCP packets on port 22 and save them to a file (`ssh.pcap`):
```bash
tcpdump -v -n -i enp0s3 tcp port 22 -w ssh.pcap
```

#### 2. **Read Captured Packets from a File**

Once you have captured packets and saved them to a `.pcap` file, you can read the saved capture file using:
```bash
tcpdump -r dnsdump.pcap
```
This will display the contents of the capture file in a human-readable format.

### Step 7: **Additional Options**

#### 1. **Verbose Output**

For a more detailed capture (including additional packet details), you can use the `-vv` flag:
```bash
tcpdump -vv -i enp0s3
```

#### 2. **Limit Packet Capture to a Specific Count**

If you only want to capture a specific number of packets and then stop, you can use the `-c` flag. For example, to capture 10 packets:
```bash
tcpdump -c 10 -i enp0s3
```

To capture 50 packets:
```bash
tcpdump -c 50 -i enp0s3
```

To capture 100 packets:
```bash
tcpdump -c 100 -i enp0s3
```

### Final Thoughts

`tcpdump` is a powerful tool for capturing and analyzing network traffic. 
