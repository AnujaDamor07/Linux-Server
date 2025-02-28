Service management in Linux is essential for controlling and managing the various services (or daemons) running on the system.

### Step 1: Check Service Status
To check the status of a service, use the `systemctl status` command. This shows whether the service is running or inactive.

```bash
systemctl status <service-name>
```
Example:
```bash
systemctl status apache2
```

### Step 2: Start a Service
To start a service, use the `systemctl start` command. This command initiates a service.

```bash
sudo systemctl start <service-name>
```
Example:
```bash
sudo systemctl start apache2
```

### Step 3: Stop a Service
To stop a running service, use the `systemctl stop` command. This command will immediately stop the service.

```bash
sudo systemctl stop <service-name>
```
Example:
```bash
sudo systemctl stop apache2
```

### Step 4: Restart a Service
To restart a service (stop and then start), use the `systemctl restart` command. This is useful when a service needs to be reloaded with new configurations.

```bash
sudo systemctl restart <service-name>
```
Example:
```bash
sudo systemctl restart apache2
```

### Step 5: Reload a Service
To reload a service without fully restarting it (useful for configuration changes), use the `systemctl reload` command. This command applies new configurations without fully stopping the service.

```bash
sudo systemctl reload <service-name>
```
Example:
```bash
sudo systemctl reload apache2
```

### Step 6: Enable a Service
To enable a service means configuring it to start automatically at boot time. Use the `systemctl enable` command for this.

```bash
sudo systemctl enable <service-name>
```
Example:
```bash
sudo systemctl enable apache2
```

### Step 7: Disable a Service
If you don’t want a service to start at boot time, you can disable it using the `systemctl disable` command.

```bash
sudo systemctl disable <service-name>
```
Example:
```bash
sudo systemctl disable apache2
```

### Step 8: Check if a Service is Enabled
To check if a service is enabled to start automatically at boot time, use the `systemctl is-enabled` command.

```bash
systemctl is-enabled <service-name>
```
Example:
```bash
systemctl is-enabled apache2
```

### Step 9: List All Active Services
To see all active services running on the system, use the `systemctl list-units` command. This lists the status of all active units (services, devices, etc.).

```bash
systemctl list-units --type=service
```

### Step 10: View Service Logs
To view the logs for a specific service, use the `journalctl` command. This shows logs for services managed by `systemd`.

```bash
journalctl -u <service-name>
```
Example:
```bash
journalctl -u apache2
```

### Step 11: Mask a Service
If you want to completely prevent a service from starting (even manually), you can "mask" it using the `systemctl mask` command.

```bash
sudo systemctl mask <service-name>
```
Example:
```bash
sudo systemctl mask apache2
```

### Step 12: Unmask a Service
To unmask a service, use the `systemctl unmask` command, allowing it to be started again.

```bash
sudo systemctl unmask <service-name>
```
Example:
```bash
sudo systemctl unmask apache2
```
