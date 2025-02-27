This guide on **Disk Quotas in Linux** provides a clear, step-by-step approach to setting up and managing disk usage limits for users and groups. Below is a concise breakdown of how to set up disk quotas on your system:

---

### **1. Enable Quotas on the File System**

- Edit `/etc/fstab` to include `usrquota` and `grpquota` for the partition (e.g., `/home`).
  
```bash
sudo nano /etc/fstab
```
Add `usrquota,grpquota` to the desired partition entry:
```plaintext
/dev/sdb1   /home   ext4   defaults,usrquota,grpquota   0 2
```

---

### **2. Remount the File System**

After modifying `/etc/fstab`, remount the file system to apply the changes:

```bash
sudo mount -o remount /home
```

Alternatively, reboot the system:
```bash
sudo reboot
```

---

### **3. Create Quota Database Files**

Run the `quotacheck` command to create the quota files:

```bash
sudo quotacheck -cug /home
```

---

### **4. Assign Quotas to a User**

To assign quotas to a specific user (`testuser`), use the `edquota` command:

```bash
sudo edquota testuser
```

In the editor, set the **soft** and **hard** limits for disk space and inodes.

Example (soft limit: 5GB, hard limit: 5.5GB):
```plaintext
/dev/sdb1   1000000   5000000   5500000   1000   5000   5500
```

---

### **5. Assign Quotas to a Group**

Similarly, assign quotas to a group (e.g., `developers`) using:

```bash
sudo edquota -g developers
```

---

### **6. Set Grace Period for Soft Limits**

To set grace periods before enforcing the soft limit:

```bash
sudo edquota -t
```

Example (grace period: 7 days for blocks, 5 days for inodes):
```plaintext
/dev/sdb1   7days   5days
```

---

### **7. Turn on Quotas**

Activate quotas with:

```bash
sudo quotaon -v /home
```

---

### **8. Verify Quotas**

To check a user’s disk quota:

```bash
sudo quota testuser
```

---

### **9. Check All Users & Groups**

- To check all user quotas:

```bash
sudo repquota -a
```

- To check a group’s quota:

```bash
sudo quota -g developers
```

---

### **10. Disable Quotas (if needed)**

To temporarily disable quotas:

```bash
sudo quotaoff -v /home
```

---

### **Summary of Useful Commands**

| Command | Description |
|---------|-------------|
| `nano /etc/fstab` | Add `usrquota,grpquota` to enable quotas |
| `mount -o remount /home` | Apply `/etc/fstab` changes |
| `quotacheck -cug /home` | Create quota database files |
| `quotaon -v /home` | Enable quotas |
| `quotaoff -v /home` | Disable quotas |
| `edquota testuser` | Set quotas for a user |
| `edquota -g developers` | Set quotas for a group |
| `edquota -t` | Set grace periods |
| `quota testuser` | Check quota for a user |
| `quota -g developers` | Check quota for a group |
| `repquota -a` | Show all quota usage |

---

