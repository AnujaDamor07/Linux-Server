### How to Add a New Virtual Disk in VirtualBox (VM Box) – Step-by-Step Guide

Adding a new virtual disk to a VirtualBox Virtual Machine (VM) expands your storage without needing to reinstall the OS.

This guide applies to **Windows**, **Linux**, and **macOS Virtual Machines**.

---

#### **1. Add a New Virtual Disk to the VM in VirtualBox**

**🔹 Step 1: Open VirtualBox and Select Your VM**
1. Open VirtualBox.
2. Select your Virtual Machine (e.g., Ubuntu, CentOS, Windows).
3. Click on **Settings** (⚙️ icon).

**🔹 Step 2: Add a New Virtual Disk**
1. In the settings, go to **Storage** → **Controller: SATA**.
2. Click on **Add Hard Disk** (📂 icon with a + sign).
3. Choose **Create a New Disk**.
4. Select **VDI (VirtualBox Disk Image)** → Click **Next**.
5. Choose **Dynamically Allocated** → Click **Next**.
6. Set the desired disk size (e.g., 20GB) → Click **Create**.

**📌 Result**: A new virtual disk (e.g., vdb) is added to the VM.

---

#### **2. Boot the VM and Check the New Disk**

**🔹 Step 1: Start the VM**
1. Boot your VM.

**🔹 Step 2: Open a Terminal or Disk Management**
- **Linux**: Open a terminal.
- **Windows**: Open Disk Management.

**🔹 Step 3: Check the New Disk**
Run the following command in Linux to check if the new disk is recognized:
```bash
lsblk
```

**📌 Output Example**:
```bash
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   50G  0 disk /
vdb      8:16   0   20G  0 disk
```

**✅** The new disk (vdb) is detected.

---

#### **3. Partition, Format, and Mount the Disk in Linux**

**🔹 Step 1: Create a Partition (fdisk)**
In the terminal, run:
```bash
sudo fdisk /dev/vdb
```
- Inside **fdisk**:
  - Type `n` to create a new partition.
  - Type `p` for a primary partition.
  - Type `1` for partition number.
  - Press **Enter** for the default first sector.
  - Press **Enter** for the default last sector (uses the full disk).
  - Type `w` to write changes and exit.

**🔹 Step 2: Format the Partition (ext4)**
Run the following command to format the new partition as ext4:
```bash
sudo mkfs.ext4 /dev/vdb1
```

**📌 Output Example**:
```bash
Creating filesystem with 5242880 4k blocks and 1310720 inodes
```

**✅** The partition `/dev/vdb1` is now formatted as ext4.

**🔹 Step 3: Create a Mount Point & Mount the Disk**
To mount the disk, follow these steps:
1. Create a directory to mount the disk:
   ```bash
   sudo mkdir /mnt/newdisk
   ```
2. Mount the partition:
   ```bash
   sudo mount /dev/vdb1 /mnt/newdisk
   ```

**✅** The disk is now mounted at `/mnt/newdisk`.

**🔹 Step 4: Verify the Mounted Disk**
Run the following command to check the disk space:
```bash
df -h
```

**📌 Output Example**:
```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/vdb1       20G  1.0G  19G   5% /mnt/newdisk
```

**✅** The new disk is successfully mounted!

---

#### **4. Auto-Mount the Disk at Boot**

To ensure the disk mounts automatically when the system reboots, follow these steps:

**🔹 Step 1: Get the UUID of the New Disk**
Run:
```bash
sudo blkid
```

**📌 Example Output**:
```bash
/dev/vdb1: UUID="1234-abcd-5678-efgh" TYPE="ext4"
```

**🔹 Step 2: Edit `/etc/fstab` to Auto-Mount**
1. Open the fstab file:
   ```bash
   sudo nano /etc/fstab
   ```
2. Add the following line at the end of the file:
   ```bash
   UUID=1234-abcd-5678-efgh  /mnt/newdisk  ext4  defaults  0  2
   ```

**✅** This ensures the disk mounts automatically at boot.

**🔹 Step 3: Apply Changes & Test**
To confirm the changes, run:
```bash
sudo mount -a
```

**✅** The changes are confirmed.

---

#### **5. Verify Everything**

**🔹 Step 1: Check Disk Space**
Run:
```bash
lsblk
df -h
```

**✅** Ensure the new disk is properly mounted.

**🔹 Step 2: Reboot & Test**
Run:
```bash
sudo reboot
```

**✅** After rebooting, verify that `/mnt/newdisk` is still available.

---

### 🚀 **Summary Table**

| Step                            | Command                             | Purpose                 |
|----------------------------------|-------------------------------------|-------------------------|
| 1. Add Disk in VirtualBox        | VirtualBox → Storage → Add New Disk | Create virtual disk     |
| 2. Detect New Disk               | `lsblk`                             | Check if new disk appears|
| 3. Partition Disk                | `fdisk /dev/vdb`                    | Create partition        |
| 4. Format Disk                   | `mkfs.ext4 /dev/vdb1`               | Format as ext4          |
| 5. Mount Disk                    | `mount /dev/vdb1 /mnt/newdisk`      | Temporary mount         |
| 6. Auto-Mount on Boot            | Edit `/etc/fstab`                   | Permanent mount         |
| 7. Verify & Reboot               | `df -h`, `lsblk`, `reboot`          | Check & confirm         |



