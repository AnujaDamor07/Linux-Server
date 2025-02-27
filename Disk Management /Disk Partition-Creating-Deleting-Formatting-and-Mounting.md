### **Linux Disk Partitioning & Management – Complete Guide**

Disk partitioning in Linux is essential for managing storage on your system. This guide will walk you through various steps including checking available disks, creating partitions, formatting, mounting, and managing partitions.

This guide applies to **Ubuntu, Debian, CentOS, RHEL, Fedora, Rocky Linux, and AlmaLinux**.

---

### **1. Check Available Disks & Partitions**

#### **🔹 1.1 List All Disks and Partitions (`lsblk`)**
To list all block devices and partitions, use:
```bash
lsblk
```

**📌 Output Example**:
```bash
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   500G  0 disk 
├─sda1   8:1    0   100G  0 part /
└─sda2   8:2    0   400G  0 part /data
sdb      8:16   1   8G    0 disk 
```
**✅** This command shows all block devices, their partitions, and mount points.

#### **🔹 1.2 Check Disk Details (`fdisk -l`)**
To view detailed disk information, including disk size and partition table, run:
```bash
sudo fdisk -l
```

**📌 Output Example**:
```bash
Disk /dev/sda: 500 GiB, 500107862016 bytes, 976773168 sectors
Disk /dev/sdb: 8 GiB, 8589934592 bytes, 16777216 sectors
```
**✅** This command lists detailed information about each disk including size and partition info.

---

### **2. Create a New Partition Using `fdisk`**

#### **🔹 2.1 Start `fdisk` for the Target Disk (/dev/sdb)**
To start partitioning a disk, run:
```bash
sudo fdisk /dev/sdb
```

**📌 Output**:
```bash
Command (m for help):
```

#### **🔹 2.2 Create a New Partition (`n`)**
Type `n` to create a new partition.

**📌 Output**:
```bash
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): 
```
Press **Enter** to select the default **Primary** partition.

#### **🔹 2.3 Choose Partition Number & Size**
1. Select partition number (e.g., `1` for the first partition) → Press **Enter**.
2. Select the first sector (press **Enter** for the default).
3. Set the partition size. For example, to create a 4GB partition:
   ```bash
   +4G
   ```

**📌 Output**:
```bash
Partition size set to 4 GiB
```
**✅** This creates a 4GB partition.

#### **🔹 2.4 Save & Exit `fdisk` (`w`)**
To save the partition and exit:
```bash
w
```

**✅** This writes changes to the disk and exits `fdisk`.

---

### **3. Format the New Partition**

#### **🔹 3.1 Format as ext4 Filesystem**
To format the new partition as ext4:
```bash
sudo mkfs.ext4 /dev/sdb1
```

**📌 Output**:
```bash
Creating filesystem with 1048576 4k blocks and 262144 inodes
```
**✅** This formats `/dev/sdb1` as ext4.

#### **🔹 3.2 Format as FAT32 (Optional)**
If you need to format it as FAT32 instead of ext4:
```bash
sudo mkfs.fat /dev/sdb2
```

**📌 Output**:
```bash
mkfs.fat 4.1 (2017-01-24)
```
**✅** This formats `/dev/sdb2` as FAT32.

---

### **4. Mount the Partition**

#### **🔹 4.1 Create a Mount Point**
First, create a directory where the partition will be mounted:
```bash
sudo mkdir /mnt/data1
```
**✅** This creates the directory `/mnt/data1`.

#### **🔹 4.2 Mount the Partition**
To mount the partition:
```bash
sudo mount /dev/sdb1 /mnt/data1
```
**✅** This mounts `/dev/sdb1` to `/mnt/data1`.

#### **🔹 4.3 Verify Mounted Partitions (`df -h`)**
Check the mounted partitions:
```bash
df -h
```

**📌 Output Example**:
```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   20G   80G  20% /
/dev/sdb1       4.0G  1.0G  3.0G  25% /mnt/data1
```
**✅** The partition `/dev/sdb1` is successfully mounted.

---

### **5. Automount Partition on Boot**

#### **🔹 5.1 Find Partition UUID**
To find the UUID of the partition:
```bash
sudo blkid
```

**📌 Output Example**:
```bash
/dev/sdb1: UUID="e99b27a0-9b32-4f89-91f3-1f6e3c7884b4" TYPE="ext4"
```

**✅** Copy the UUID of `/dev/sdb1`.

#### **🔹 5.2 Edit `/etc/fstab` to Add Auto-Mount Entry**
1. Open the `fstab` file for editing:
   ```bash
   sudo nano /etc/fstab
   ```
2. Add the following line at the end of the file (replace UUID with the actual one):
   ```bash
   UUID=e99b27a0-9b32-4f89-91f3-1f6e3c7884b4  /mnt/data1  ext4  defaults  0  2
   ```

**✅** This ensures the partition auto-mounts on boot.

#### **🔹 5.3 Apply Changes**
To apply the changes and mount all partitions from `/etc/fstab`:
```bash
sudo mount -a
```

**✅** This confirms the changes and mounts the partition.

---

### **6. Unmount & Remove Partitions**

#### **🔹 6.1 Unmount a Partition**
To unmount a partition:
```bash
sudo umount /mnt/data1
```

**✅** This unmounts the partition.

#### **🔹 6.2 Remove Partition (`fdisk`)**
1. Start `fdisk` for the target disk:
   ```bash
   sudo fdisk /dev/sdb
   ```
2. Inside `fdisk`, type `d` to delete a partition.
3. Write changes and exit by typing `w`.

**✅** This deletes the partition.

---

### **📊 Summary of Linux Disk Partitioning Commands**

| Command                       | Purpose                                |
|-------------------------------|----------------------------------------|
| `lsblk`                        | Show all disks and partitions         |
| `fdisk -l`                     | List disk details                      |
| `fdisk /dev/sdb`               | Start partitioning tool                |
| `n`                            | Create a new partition                 |
| `w`                            | Save changes & exit `fdisk`            |
| `mkfs.ext4 /dev/sdb1`          | Format partition as ext4               |
| `mount /dev/sdb1 /mnt/data1`   | Mount partition                        |
| `df -h`                        | Check mounted partitions               |
| `blkid`                        | Find partition UUID                   |
| `nano /etc/fstab`              | Edit `fstab` for auto-mount           |
| `mount -a`                     | Apply `fstab` changes                  |
| `umount /mnt/data1`            | Unmount partition                      |
| `fdisk /dev/sdb → d`           | Delete partition                       |

---

